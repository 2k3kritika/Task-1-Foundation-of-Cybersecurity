# 🔐 Task 1: Cybersecurity Foundations & Lab Setup

## 📌 Overview
This repository documents the setup of a personal cybersecurity lab and covers foundational concepts in cybersecurity, networking, Linux, and cryptography.

The goal is to build a **secure, isolated testing environment** and develop **practical skills with basic automation using Python**.

---

## 📚 How to Navigate This Repository

This repository is structured to keep the main README clean and easy to read.

- 📄 **Main README (this file)** → Overview of all topics
- 📁 **docs/** → Detailed day-wise notes and explanations
- 🧪 **scripts/** → Python automation tools
- 📸 **screenshots/** → Lab setup and results
- 📊 **reports/** → Final reports

👉 If you want **detailed step-by-step explanations**, go to the `docs/` folder.

---

## 🧠 Cybersecurity Fundamentals

### 🔺 CIA Triad
- **Confidentiality** – Protecting sensitive data
- **Integrity** – Ensuring data is not altered
- **Availability** – Ensuring systems are accessible

### ⚠️ Common Threats
- Phishing
- Malware
- DDoS Attacks
- SQL Injection
- Brute Force Attacks
- Ransomware

### 🎯 Attack Vectors
- Social Engineering
- Wireless Attacks
- Insider Threats

📄 Detailed Notes → [Day 1 Basics](./docs/day1_basics.md)

---

## 🖥️ Lab Environment Setup

### 🔧 Tools Used
- Kali Linux (Attacker Machine)
- Metasploitable2 / DVWA (Target Machine)
- VirtualBox / VMware

### 🌐 Network Configuration
- Host-Only Adapter (Isolated Network)
- No external exposure
- Safe for testing

### 🧪 Lab Architecture
```
[Kali Linux] ---> [Metasploitable2]
            \---> [DVWA]
```

📄 Full Setup Guide → [Day 1 Lab Setup](./docs/day1_lab_setup.md)

📸 Screenshots:
- `screenshots/kali_setup.png`
- `screenshots/network_config.png`

---

## 🐧 Linux Fundamentals

### 📂 Commands Covered
- Navigation: `cd`, `ls`, `pwd`
- File Management: `mkdir`, `rm`
- Permissions: `chmod`, `chown`
- Package Management: `apt`, `dpkg`

- 📄 Detailed Notes → [Day 2 Linux](./docs/day2_linux.md)
- 📄 Detailed notes → [Types of Network setting in VMware](./docs/network_setting.md)

---

## 🌐 Networking Basics

### 📡 Commands
- `ifconfig` / `ip`
- `ping`
- `netstat`
- `traceroute`

### 🧱 Concepts
- OSI Model
- TCP/IP Model
- DNS & HTTP/HTTPS
- IP Addressing & NAT

📄 Detailed Notes → [Day 3 Networking](./docs/day3_networking.md)

---

## 🔢 Subnetting & IP Concepts

- IPv4 / IPv6 basics
- Subnet masks
- NAT configuration

📄 Detailed Notes → [Day 4 Subnetting](./docs/day4_subnetting.md)

📄 Script: `scripts/subnet_calculator.py`

---

## 🔐 Cryptography Basics

### 🔑 Concepts
- Symmetric vs Asymmetric Encryption
- Hashing (MD5, SHA256)
- SSL/TLS & Digital Certificates

### 🧪 Hands-on
- File encryption/decryption
- Password hashing

📄 Detailed Notes → [Day 5 Cryptography](./docs/day5_crypto.md)

📄 Script: `scripts/crypto_tool.py`

---

## 🛠️ Tool Familiarization

### 🔍 Tools Used
- Wireshark (Packet Analysis)
- Nmap (Network Scanning)
- Burp Suite (Web Proxy)
- Netcat (Networking Utility)

📄 Detailed Notes → [Day 6 Tools](./docs/day6_tools.md)

---

## 🧪 Python Automation Scripts

| Script | Description |
|--------|------------|
| `file_report.py` | File listing + permission analysis |
| `ping_sweep.py` | Detect active hosts in subnet |
| `subnet_calculator.py` | Subnet calculations |
| `crypto_tool.py` | Encryption/Decryption tool |
| `nmap_automation.py` | Automated network scanning |

📁 Scripts Folder → `./scripts/`

---

## 📁 Repository Structure

```
Task1_Foundation/
│
├── README.md   ← (Main overview file - YOU ARE HERE)
│
├── docs/       ← (All detailed daily documentation goes here)
│   ├── day1_basics.md
│   ├── day1_lab_setup.md
│   ├── day2_linux.md
│   ├── day3_networking.md
│   ├── day4_subnetting.md
│   ├── day5_crypto.md
│   └── day6_tools.md
│
├── scripts/    ← (All Python automation scripts)
│   ├── file_report.py
│   ├── ping_sweep.py
│   ├── subnet_calculator.py
│   ├── crypto_tool.py
│   └── nmap_automation.py
│
├── screenshots/  ← (Images of lab setup & outputs)
│
│
│
├── extra_screenshots/  ← (Images of extra lab setup & outputs)
│
├── kali/  ← (Documentation of extra lab setup & outputs)
│
└── reports/      ← (Final reports or PDFs)

```

---

## 🎥 Demo Video

📌 LinkedIn Video: [Task 1 video tutorial](https://www.linkedin.com/posts/kritika-sharma-0150b6396_cybersecurity-ethicalhacking-kalilinux-activity-7442180051242033152-pEDj?utm_source=share&utm_medium=member_android&rcm=ACoAAGEww5EBVvPI4u2oCblZQLHt_Y9Hl0saEIk)

---

## 🧾 Key Learnings

- Built a secure virtual cybersecurity lab
- Understood core cybersecurity concepts
- Learned Linux and networking fundamentals
- Applied cryptography basics
- Developed automation scripts using Python

---

## ⚠️ Disclaimer

This project is for **educational purposes only**.  
All activities were performed in a **controlled lab environment**.

---

## Extras
- [Kali Password reset using GRUB](kali/password-reset.md)

---

## 🚀 Next Step

➡️ [Task 2: Network Security & Scanning](../Task2_NetworkSecurity/README.md)

---
