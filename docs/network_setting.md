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
- 
Hey give me readme.md file code to copy and paste on GitHub in one go out of my notes below.

Network settings in VMware

(1)

Bridged Network. (Real network Exposure)

192.168.1x

> Your VM become full member of the real network, it's like another Physical device on your wifi.

→

VM machines get an IP from your router (like your phone/Laptop)

→

Can access internet normally

Other devices on your network carsuit

→

Both are on the same network

laptop 192.168.1.5

VMTP 192.168.1.20

use it when'-

→

want realistic network behaviour

→ Youść testing tools like skanning ((nprap) on Gre on real devices.

Need full internet + LAN access

Goblemi

→

Your vaherable machines (like DUDA or metasploitable 2) are now exposer to real network.

Ginvites the risk into home with

Confirmation: ORun ipconfig (windows) of check your phone iP. →

Both will be of same range.

192.168.XX (but not same as your wife)

م

10-xxx

classmate

Date Page

(2

) NAT (Network Address Translation).

Safe but limited.

What it does!

Cvm gets internet through your host, but stays hidden.

How it behaver:

VM can access internet.

→ cannot be directly accessed from outside.

→ Acts like it's behind a private firewall.

VMIP 192.168.XXX-XXX

(internet virtual network)

Suses your host's IP to go Duline.

use it when (-

installing ing packages, updater

browsing browsing internet inside vm.

You don't care about Machines talki to it-talking

Limitation

Other vms can't easily talk to it (unless you configure port forwarding).

Good for normal use, useles for serious.

hacking labs confirmation

WOTBA fon toy ping google.com s'intes But your host, wan't ping um
(3)

←

192-168-56-XX

classmate

Date

lost only

Network

Poge

→→

Your private cyber playground.

what it does

Creates between Your host machine you completely isolate VMS

No internet. No external access.

How it behaves

→ UM can talk to host

→

um can talk to other vms (it same network)

No internet

Ex.

Host 192.168.56.1

Kali 192

2.168.56.101

Metasploitable

192.168.56.102

Use it whin

→

Practicing penetration usting Attacking DUDA/metasploitable satel

←

Building Ja controlled las environment

Downsiche

No internet (so installing tools berame annoying)

confirm it: can ping host machine Cannot acces Informet
Smart setup

use Both

Adapter 1 NAT (for internet)

Adapter 2 Host Host only (for hacking labe).

Setting Host only in VMware

Set Adapter to host only

Open Mware

→ Right click vm settings

Go to nerwork adapter.

→ Select host only.

click OK

@ Make sure host only network existo

→Go to edit virtual network editor.

→ Look Sor: vmnet I should be host only

02

If not there click restore defaults Cum will recreate it)

① Check IP Range (

G

In vm Kirtual network editor:-

Select vmnett

You will see something like!-

192.168.56.0/255.255.255.0.

This is your private lab network
Start vm & verify

→ Inside kali:-

ip a

↓

192.168.56.x

Test connectivét connectivity

From vm -

192.168.56.1

Ping

GIt works that's your hout machine

If have another vm(like metasploitable sping 192.168.56.x

↑

works you tab still alive.


You took chaotic handwritten notes and somehow expected them to magically become a clean GitHub README. Cute. Let’s fix that mess into something that won’t embarrass you in front of recruiters.

Copy this and paste it directly into your README.md:

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