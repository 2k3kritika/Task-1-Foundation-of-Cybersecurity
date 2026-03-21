# 🐧 Linux Basics for Cybersecurity

This repository documents essential Linux commands required for system navigation, permission handling, package management, and networking. These commands form the foundation for cybersecurity, scripting, and system-level operations.

---

# 📁 1. File System Navigation

## 🔹 pwd (Print Working Directory)

Displays the current directory path.

```bash
pwd
```

---

## 🔹 ls (List Directory Contents)

```bash
ls        # Basic listing
ls -l     # Detailed view
ls -a     # Show hidden files
ls -la    # Detailed + hidden files
```

---

## 🔹 cd (Change Directory)

```bash
cd folder_name   # Move into folder
cd ..            # Move back
cd ~             # Home directory
cd /             # Root directory
```

---

# 🔐 2. File & Directory Permissions

## 🔹 Permission Basics

| Symbol | Meaning | Value |
| ------ | ------- | ----- |
| r      | Read    | 4     |
| w      | Write   | 2     |
| x      | Execute | 1     |

---

## 🔹 chmod (Change Permissions)

```bash
chmod 755 file.sh
```

Example:

```bash
chmod +x script.sh   # Make file executable
```

---

## 🔹 chown (Change Ownership)

```bash
chown user:group file.txt
```

Example:

```bash
chown root:root config.conf
```

---

# 📦 3. Package Management

## 🔹 apt (Advanced Package Tool)

```bash
sudo apt update        # Update package list
sudo apt upgrade       # Upgrade packages
sudo apt install nmap  # Install package
```

Remove package:

```bash
sudo apt remove nmap
```

Search package:

```bash
apt search nmap
```

---

## 🔹 dpkg (Debian Package Manager)

```bash
sudo dpkg -i package.deb
```

Fix broken installs:

```bash
sudo apt --fix-broken install
```

---

# 🌐 4. Networking Commands

## 🔹 ifconfig / ip a

```bash
ifconfig
```

Recommended:

```bash
ip a
```

---

## 🔹 ping

```bash
ping google.com
```

---

## 🔹 netstat

```bash
netstat -tuln
```

---

## 🔹 traceroute

```bash
traceroute google.com
```

---

# 🧪 Practice Tasks

## ✅ Task 1: Navigation

* Navigate using only terminal commands:

  * `/home`
  * `/etc`
  * `/var/log`

---

## ✅ Task 2: Permissions

* Create a file
* Change permissions using `chmod`
* Break permissions and fix them

---

## ✅ Task 3: Package Management

* Install a tool (example: `nmap`)
* Remove it
* Reinstall it

---

## ✅ Task 4: Networking

* Run:

  ```bash
  ip a
  ping google.com
  netstat -tuln
  ```

---

# 🎯 Learning Outcome

After completing this, you should be able to:

* Navigate Linux efficiently
* Manage file permissions securely
* Install and manage software packages
* Perform basic network diagnostics

---

# ⚠️ Notes

* Avoid running commands as `root` unless necessary
* Always double-check commands before execution
* Breaking things is part of learning — fixing them is the real skill

---

# 🌐 Networking Fundamentals for Cybersecurity

This repository documents core networking concepts required for cybersecurity, including the OSI model, TCP/IP suite, DNS, HTTP/HTTPS, and IP addressing.

---

# 🧱 1. OSI Model (7 Layers)

The OSI (Open Systems Interconnection) model defines how data moves across a network in seven layers.

| Layer | Name         | Function                          |
| ----- | ------------ | --------------------------------- |
| 7     | Application  | User interaction (HTTP, FTP, DNS) |
| 6     | Presentation | Data formatting, encryption       |
| 5     | Session      | Session management                |
| 4     | Transport    | Reliable delivery (TCP/UDP)       |
| 3     | Network      | Routing (IP addressing)           |
| 2     | Data Link    | MAC addressing, switching         |
| 1     | Physical     | Hardware transmission             |

---

## 🔹 Key Understanding

* Each layer has a specific role
* Data moves **top → bottom (sender)** and **bottom → top (receiver)**
* Encapsulation happens at each layer

---

# 🌍 2. TCP/IP Protocol Suite

The TCP/IP model is the practical version used in real-world networking.

| Layer          | Protocols             |
| -------------- | --------------------- |
| Application    | HTTP, HTTPS, FTP, DNS |
| Transport      | TCP, UDP              |
| Internet       | IP, ICMP              |
| Network Access | ARP, Ethernet         |

---

## 🔹 TCP vs UDP

### TCP (Transmission Control Protocol)

* Connection-oriented
* Reliable (acknowledgements, retransmission)
* Slower

### UDP (User Datagram Protocol)

* Connectionless
* Faster
* No guarantee of delivery

---

# 🌐 3. DNS & HTTP/HTTPS Deep Dive

## 🔹 DNS (Domain Name System)

Converts domain names into IP addresses.

Example:

```bash id="dns1"
google.com → 142.250.x.x
```

### DNS Process:

1. User enters domain
2. Query goes to DNS resolver
3. Resolver queries root → TLD → authoritative server
4. Returns IP address

---

## 🔹 HTTP (HyperText Transfer Protocol)

* Used for web communication
* Stateless protocol
* Runs on port **80**

Example request:

```bash id="http1"
GET /index.html HTTP/1.1
Host: example.com
```

---

## 🔹 HTTPS (Secure HTTP)

* Encrypted using SSL/TLS
* Runs on port **443**

### HTTPS Flow:

1. Client sends request
2. Server responds with certificate
3. SSL/TLS handshake
4. Encrypted communication starts

---

# 📡 4. IP Addressing, Subnetting & NAT

## 🔹 IP Address

Unique identifier for a device on a network.

Example:

```bash id="ip1"
192.168.1.1
```

---

## 🔹 Types of IP

### Private IP Ranges:

* 192.168.x.x
* 10.x.x.x
* 172.16.x.x – 172.31.x.x

### Public IP:

* Assigned by ISP
* Accessible over the internet

---

## 🔹 Subnetting

Divides a network into smaller sub-networks.

Example:

```bash id="subnet1"
192.168.1.0/24
```

* `/24` → 255.255.255.0
* Helps in:

  * Network organization
  * Security segmentation
  * Efficient IP usage

---

## 🔹 NAT (Network Address Translation)

Maps private IPs to a public IP.

### Types:

* Static NAT
* Dynamic NAT
* PAT (Port Address Translation)

### Why NAT?

* Saves IP addresses
* Adds a layer of security

---

# 🧪 Practice Tasks

## ✅ Task 1: OSI Mapping

* Map real protocols to OSI layers
* Example: HTTP → Application Layer

---

## ✅ Task 2: TCP vs UDP

* List use cases:

  * TCP → Web browsing
  * UDP → Streaming, gaming

---

## ✅ Task 3: DNS Lookup

Run:

```bash id="dns2"
nslookup google.com
```

---

## ✅ Task 4: IP & Network Info

```bash id="net1"
ip a
```

---

# 🎯 Learning Outcome

After completing this, you should:

* Understand how data flows across networks
* Differentiate TCP and UDP
* Know how DNS and HTTP/HTTPS work
* Understand IP addressing and subnet basics

---