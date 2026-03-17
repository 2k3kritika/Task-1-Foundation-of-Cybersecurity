# 🧠 Day 1: Cybersecurity Fundamentals

[Back to main README](/README.md)

## 📌 Objective
Understand the **core principles of cybersecurity**, common threats, and how attacks actually happen. This forms the **foundation** for everything in this lab.

---

## 🔺 CIA Triad (Core Security Model)
The CIA Triad defines the **3 fundamental goals of cybersecurity**:

| Pillar | Goal | Real-World Example |
| :--- | :--- | :--- |
| 🔐 **Confidentiality** | Protect sensitive data from unauthorized access. | Accessing a bank account without permission. |
| 🧾 **Integrity** | Ensure data is not altered or tampered with. | A hacker modifying transaction data. |
| ⚡ **Availability** | Ensure systems/services are always accessible. | A website crashing due to a DDoS attack. |

### 🛠️ CIA In Action
When a user requests data, the system performs a triple-check:
1. **Confidentiality:** Is the user authorized?
2. **Integrity:** Is the data unchanged?
3. **Availability:** Is the system accessible?

---

## ⚠️ Common Cybersecurity Threats
These are the real-world attacks you will simulate later in this lab.

* **🎣 Phishing:** Tricking users into revealing sensitive data via fake emails/links.
* **🦠 Malware:** Malicious software (Viruses, Worms, Trojans, Spyware) designed to damage systems.
* **🌐 DDoS:** Overloading a system with massive traffic to cause a crash.
* **💉 SQL Injection:** Injecting malicious queries into input fields to manipulate databases.
* **🔑 Brute Force:** Attempting every possible password combination until access is granted.
* **💰 Ransomware:** Encrypting user data and demanding payment for the decryption key.

---

## 🎯 Attack Vectors (Entry Points)
Attack vectors are the paths or means by which an attacker gains access to a computer or network server.

### 1. Social Engineering
Manipulating humans instead of systems (e.g., fake support calls, job offers).
### 2. Wireless Attacks
Exploiting insecure WiFi networks (e.g., Evil Twin attacks, Packet Sniffing).
### 3. Insider Threats
Threats originating from within the organization, whether malicious or negligent.

---

## 🔗 The Big Picture
Security is a continuous cycle of **Preventing**, **Detecting**, and **Responding**. Understanding "how it breaks" is more important than knowing which buttons to click in a tool.

> [!IMPORTANT]
> Without these fundamentals, tools like **Nmap**, **Burp Suite**, and **Wireshark** will feel like random noise.

---

## 🧾 Key Takeaways
- **CIA Triad** = The foundation of all security decisions.
- **Threats** = What can go wrong.
- **Attack Vectors** = How it happens.

---

## 📂 Linked Documentation
- 🖥️ [Lab Setup](./docs/day1_lab_setup.md)
- 🐧 [Linux Basics](./docs/day2_linux.md)

## 🚀 Next Step
Move to the **Lab Setup**: [day1_lab_setup.md](./docs/day1_lab_setup.md)