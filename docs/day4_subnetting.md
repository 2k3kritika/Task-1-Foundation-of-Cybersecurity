[Back to main README](/README.md)
# 🌐 IP Addressing & Network Configuration

This repository documents core concepts of IP addressing, including IPv4, IPv6, subnet masks, and NAT (Network Address Translation). These are fundamental for networking, system administration, and cybersecurity.

---

# 📡 1. IPv4 Basics

IPv4 (Internet Protocol version 4) is the most widely used addressing system.

---

## 🔹 Structure

* 32-bit address
* Divided into 4 octets (8 bits each)

Example:

```bash
192.168.1.1
```

Each octet ranges from **0–255**

---

## 🔹 Types of IPv4 Addresses

### Private IP Ranges

Used inside local networks.

* 192.168.0.0 – 192.168.255.255
* 10.0.0.0 – 10.255.255.255
* 172.16.0.0 – 172.31.255.255

---

### Public IP

* Assigned by ISP
* Accessible over the internet

---

### Loopback Address

```bash
127.0.0.1
```

Used to refer to the local machine.

---

## 🔹 Key Insight

* IPv4 is limited (~4.3 billion addresses)
* This limitation led to IPv6

---

# 🌍 2. IPv6 Basics

IPv6 is the modern version of IP addressing.

---

## 🔹 Structure

* 128-bit address
* Written in hexadecimal

Example:

```bash
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

---

## 🔹 Features

* Vast address space
* Built-in security (IPsec support)
* No need for NAT (in most cases)

---

## 🔹 Simplified IPv6

Leading zeros can be removed:

```bash
2001:db8::8a2e:370:7334
```

---

## 🔹 Key Insight

* IPv6 removes address exhaustion
* Still not fully adopted everywhere

---

# 📏 3. Subnet Masks

Subnet masks define the network and host portions of an IP address.

---

## 🔹 Example

```bash
IP Address:     192.168.1.10
Subnet Mask:    255.255.255.0
```

---

## 🔹 CIDR Notation

```bash
192.168.1.0/24
```

* `/24` → first 24 bits are network
* Remaining bits → hosts

---

## 🔹 Common Subnet Masks

| CIDR | Subnet Mask   | Hosts          |
| ---- | ------------- | -------------- |
| /24  | 255.255.255.0 | 256            |
| /16  | 255.255.0.0   | 65,536         |
| /8   | 255.0.0.0     | Large networks |

---

## 🔹 Why Subnetting?

* Efficient IP usage
* Network segmentation
* Improved security

---

## 🔹 Key Insight

* Subnetting controls how networks are divided
* Essential for routing and access control

---

# 🔄 4. NAT (Network Address Translation)

NAT allows multiple devices in a private network to share a single public IP.

---

## 🔹 How NAT Works

```bash
Private IP → NAT → Public IP
```

Example:

* Device: 192.168.1.10
* Public IP: 203.x.x.x

---

## 🔹 Types of NAT

### Static NAT

* One-to-one mapping

---

### Dynamic NAT

* Pool of public IPs assigned dynamically

---

### PAT (Port Address Translation)

* Multiple devices share one public IP using different ports
* Most common type

---

## 🔹 Why NAT?

* Conserves IPv4 addresses
* Adds basic security (internal IPs hidden)

---

# ⚙️ 5. Basic NAT Configuration (Conceptual)

> Note: Actual commands depend on system (Linux router, firewall, etc.)

---

## 🔹 Enable IP Forwarding (Linux)

```bash
echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

## 🔹 Configure NAT using iptables

```bash
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

---

## 🔹 Explanation

* `-t nat` → NAT table
* `POSTROUTING` → applied after routing
* `-o eth0` → outgoing interface
* `MASQUERADE` → dynamic NAT

---

## 🔹 Verify Rules

```bash
sudo iptables -t nat -L -n -v
```

---
