[Back to main README](/README.md)
# 🛠️ Cybersecurity Tools: Practical Guide

This repository documents hands-on usage of essential cybersecurity tools used for network analysis, scanning, web testing, and debugging.

---

# 📡 1. Wireshark (Packet Capture & Analysis)

Wireshark is a network protocol analyzer used to capture and inspect packets in real time.

---

## 🔹 What It Does

* Captures live network traffic
* Shows packet-level details
* Helps analyze protocols (HTTP, DNS, TCP, etc.)

---

## 🔹 Start Capture

1. Open Wireshark
2. Select active network interface (Wi-Fi/Ethernet)
3. Click **Start Capture**

---

## 🔹 Common Filters

### Capture Filter (before capture)

```bash id="ws1"
port 80
```

---

### Display Filters (after capture)

```bash id="ws2"
http
dns
tcp.port == 443
ip.addr == 192.168.1.1
```

---

## 🔹 Example Use Cases

* Inspect HTTP requests and responses
* Analyze DNS queries
* Detect suspicious traffic
* Debug network issues

---

## 🔹 Key Insight

* Packets show **real data flow**, not assumptions
* Helps understand how protocols actually behave

---

# 🌐 2. Nmap (Network Scanning)

Nmap is used for discovering hosts, open ports, and services on a network.

---

## 🔹 Basic Scan

```bash id="nm1"
nmap 192.168.1.1
```

---

## 🔹 Scan Specific Ports

```bash id="nm2"
nmap -p 1-1000 192.168.1.1
```

---

## 🔹 Service Version Detection

```bash id="nm3"
nmap -sV 192.168.1.1
```

---

## 🔹 OS Detection

```bash id="nm4"
nmap -O 192.168.1.1
```

---

## 🔹 Aggressive Scan

```bash id="nm5"
nmap -A 192.168.1.1
```

---

## 🔹 Scan Entire Network

```bash id="nm6"
nmap 192.168.1.0/24
```

---

## 🔹 Key Insight

* Reveals attack surface
* Shows open ports and services
* Essential for reconnaissance

---

# 🌍 3. Burp Suite (Web Proxy & Security Testing)

Burp Suite is used to intercept and manipulate web traffic between browser and server.

---

## 🔹 Setup Proxy

* Default: `127.0.0.1:8080`
* Configure browser proxy settings to match

---

## 🔹 Intercept Requests

1. Turn **Intercept ON**
2. Open browser and visit a website
3. Request is captured in Burp

---

## 🔹 Modify Request

* Change parameters (GET/POST)
* Modify headers
* Replay requests

---

## 🔹 Common Use Cases

* Test login forms
* Modify request data
* Identify vulnerabilities (XSS, SQLi)

---

## 🔹 Key Insight

* You see what the server actually receives
* Frontend validation becomes irrelevant

---

# 🔌 4. Netcat (Network Debugging Tool)

Netcat is a versatile tool for reading/writing data across network connections.

---

## 🔹 Start a Listener (Server)

```bash id="nc1"
nc -lvp 4444
```

---

## 🔹 Connect as Client

```bash id="nc2"
nc <IP> 4444
```

---

## 🔹 Send Messages

* Type in terminal after connection
* Data is transmitted in real-time

---

## 🔹 Transfer File

### Sender:

```bash id="nc3"
nc -lvp 4444 < file.txt
```

### Receiver:

```bash id="nc4"
nc <IP> 4444 > received.txt
```

---

## 🔹 Key Insight

* Raw communication tool
* Useful for debugging and exploitation basics
* Often used in reverse shells

---

