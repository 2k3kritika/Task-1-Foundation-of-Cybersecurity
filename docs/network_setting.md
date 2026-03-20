# 🌐 VMware Network Modes for Cybersecurity Lab

This guide explains different network configurations in VMware and how to set up a secure penetration testing lab.

---

## 🧠 1. Bridged Network (Real Network Exposure)

### 📌 What it does
- VM becomes part of your real network (like another physical device)
- Gets IP from your router
- Full internet + LAN access

### 🔍 Example
- Laptop → `192.168.1.5`
- VM → `192.168.1.20`

### ✅ Use Cases
- Realistic network behavior testing
- Scanning real devices using tools like Nmap
- Full internet + LAN interaction

### ⚠️ Risk
- Vulnerable machines (DVWA, Metasploitable2) are exposed to your real network
- Can be accessed by other devices on your WiFi

### 🧪 Verification
- Run `ipconfig` (Windows) or check phone IP
- VM and host should be in same range (`192.168.1.x`)

---

## 🔐 2. NAT (Network Address Translation)

### 📌 What it does
- VM accesses internet through host
- VM is hidden from external network

### 🔍 Behavior
- Internet access ✅
- Cannot be accessed from outside ❌
- Acts behind a virtual firewall

### ✅ Use Cases
- Installing packages
- Browsing internet inside VM
- Safe general usage

### ⚠️ Limitation
- Other VMs cannot easily communicate
- Requires port forwarding for interaction

### 🧪 Verification
- `ping google.com` → Works ✅
- Host cannot ping VM ❌

---

## 🧪 3. Host-Only Network (Private Lab)

### 📌 What it does
- Creates isolated network between host and VMs
- No internet access

### 🔍 Behavior
- VM ↔ Host communication ✅
- VM ↔ VM communication ✅
- Internet access ❌

### 🔍 Example
- Host → `192.168.56.1`
- Kali → `192.168.56.101`
- Metasploitable → `192.168.56.102`

### ✅ Use Cases
- Penetration testing practice
- Safe lab environment
- Attacking DVWA / Metasploitable

### ⚠️ Downside
- No internet (tool installation becomes harder)

### 🧪 Verification
- `ping 192.168.56.1` → Host reachable ✅
- Internet not accessible ❌

---

## ⚡ Recommended Setup (Best Practice)

Use **dual adapters**:

- **Adapter 1 → NAT** (for internet)
- **Adapter 2 → Host-Only** (for hacking lab)

This gives:
- Internet access ✅
- Safe isolated lab ✅

---

# ⚙️ Setting Up Host-Only Network in VMware

## 🛠️ Step 1: Configure VM Network
1. Open VMware
2. Right-click VM → **Settings**
3. Go to **Network Adapter**
4. Select **Host-Only**
5. Click **OK**

---

## 🛠️ Step 2: Ensure Host-Only Network Exists
1. Go to **Edit → Virtual Network Editor**
2. Look for **VMnet1 (Host-Only)**

👉 If missing:
- Click **Restore Defaults**
- VMware will recreate it

---

## 🛠️ Step 3: Check IP Range
In Virtual Network Editor:
- Select **VMnet1**
- Example range:
- 192.168.56.0 / 255.255.255.0


This is your **private lab network**

---

## 🚀 Step 4: Start VM & Verify

### In Kali Linux:
```
ip a
```
- 👉 You should see:
    - 192.168.56.x

---

## 🔗 Step 5: Test Connectivity
- Ping Host Machine:
    - ping 192.168.56.1

- ✔ If it works → Host connection is successful

- Ping Another VM (e.g. Metasploitable):
    - ping 192.168.56.102

- ✔ If it works → VM-to-VM communication is working

---

## 🎯 Final Goal

You now have:

- 🔒 Isolated hacking lab
- 🌐 Optional internet access (via NAT)
- 💻 Safe environment for practicing cybersecurity

---
## ⚠️ Important Reminder

- Never expose vulnerable machines like:
    - DVWA
    - Metasploitable2

to Bridged Network, unless you know exactly what you're doing.
You’re basically inviting chaos into your home network.

---