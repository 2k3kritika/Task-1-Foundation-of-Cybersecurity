# 🛠️ Day 1 – Lab Setup & Virtualization

## 🎯 Objective
Set up a cybersecurity lab environment using virtual machines for penetration testing practice.  
This includes installing:
- 🐉 Kali Linux (Attacker)
- 🌐 DVWA (Web Target)
- 💀 Metasploitable2 (Vulnerable System)

---

## 🧩 Lab Architecture

- 💻 **Host Machine**: Windows  
- 🖥️ **Virtualization Tool**: VMware Workstation Pro  
- ⚔️ **Attacker Machine**: Kali Linux  
- 🎯 **Target Machines**: DVWA, Metasploitable2  

---

## 🧰 Tools & Technologies Used

- VMware Workstation Pro  
- Kali Linux  
- DVWA (Damn Vulnerable Web Application)  
- Metasploitable2  
- Apache2, MySQL  
- Git  

---

# ⚙️ 1. Installing Kali Linux on VMware

## 🔹 Step 1: Install VMware Workstation Pro
1. Visit the official VMware (Broadcom) website  
2. Register/Login  
3. Download **VMware Workstation Pro (Free Version)**  
4. Install with default settings  

---

## 🔹 Step 2: Download Kali Linux VM
1. Search **"Kali Linux download"**  
2. Go to official website  
3. Navigate to:
   - Downloads → Virtual Machines  
4. Download the **VMware image (.7z file)**  

---

## 🔹 Step 3: Setup Kali Linux in VMware
1. Extract the downloaded file  
2. Open VMware → **Open a Virtual Machine**  
3. Select the `.vmx` file  
4. Configure:
   - RAM: 4 GB  
   - CPU: 2 cores  
5. Click **Power On**  

### 🔐 Default Credentials

- Username: kali
- Password: kali


---

# 🌐 2. Installing DVWA in Kali Linux

## 🔹 Step 1: Clone DVWA Repository
1. Search **DVDA github** on google.
2. Click on 1st link and download it → code → https://github.com/digininja/DVWA.git 
3. In Kali Linux terminal go to this folder (it's the default directory of web server): 
    `cd /var/www/html`
4. Type:
    `sudo git clone https://github.com/digininja/DVWA.git`
5. Set Permissions:
    `sudo chmod -R 777 DVWA`
6. Go to Configure DVWA and type `ls` to get list items → `cd DVDA` → `ls`→ `cd config`.
    - directly: `cd DVWA/config`
7. Get list items `ls` → and find this file `config.inc.php.dist` and copy it at the same directory.
    `cp config.inc.php.dist config.inc.php`
8. Go to any editor: `sudo mousepad config.inc.php`
9. Update:
    - `$_DVWA['db_user'] = 'admin';`
    - `$_DVWA['db_password'] = 'password';`

---

## 🔹 Step 2: Database Setup
10. Setup Database
    - Start MySQL:
        - `sudo systemctl start mysql` → starting the database mysql.
        - `sudo systemctl status mysql` → To check whether mysql started or not (shows db → active/running)
11. Change to sudo user: `sudo su`
12. To configure the database now, Login:
    - `sudo mysql -u root -p`

    - Note: currently no password is set so just press enter.

13. To create the database now, Run:
    - `CREATE DATABASE dvwa;`
14. To create the user for the database now: 
    - `CREATE USER 'admin'@'127.0.0.1' IDENTIFIED BY 'password';`

    - Note: Here username and password should match to the configured file we set earlier.
15. Grant all privileges to this user. 
    - `GRANT ALL PRIVILEGES ON dvwa.* TO 'admin'@'127.0.0.1';`
    - `FLUSH PRIVILEGES;` →  `exit;`

    - Now database is configured, only webserver is left now.
---

## 🔹 Step 3: Webserver Setup
16. Configure Apache & PHP webserver:
    - Start Apache:
    - `sudo systemctl start apache2`
    - `sudo systemctl status apache2` → to check running status

17. Now configure the webserver, Edit PHP config:
    - go to this folder: `cd /etc/php` → `ls` → `cd 8.2` → `ls` → `cd apache2` → `ls` → Find & make changes to this file `php.ini`.
    - `sudo mousepad php.ini`
18. Press `ctrl + F` and find `fopen` & Enable:
    - `allow_url_fopen = On`
    - `allow_url_include = On` → save this file and exit.
19. Restart Apache:
    `sudo systemctl restart apache2`
20. Access DVWA
    - 🌍 Open browser in Kali:
    - http://127.0.0.1/DVWA

    🔐 Login:
    - Username: admin
    - Password: password

    👉 Click Create / Reset Database → press enter
    - Username: admin
    - Password: password

Now we have started DVDA on Kali Linux and now we can perform any attacks on this web app.

---

# 💀 3. Installing Metasploitable2

## 🔹 Step 1: Download Metasploitable2
1. Search: **Metasploitable2 download SourceForge**
2. Open the official SourceForge link.
3. Download the `.zip` file.
4. Extract the downloaded file.

---

## 🔹 Step 2: Setup in VMware
1. Open **VMware Workstation / Player**.
2. Click on **Open a Virtual Machine**.
3. Navigate to the extracted Metasploitable2 folder.
4. Select the `.vmx` file (or `.vmdk` if required).
5. Click **Open**.
6. Power on the virtual machine.
7. When prompted, select:
   - **"I copied it"**

---

## 🔹 Step 3: Login to Metasploitable2
- **Username:** `msfadmin`
- **Password:** `msfadmin`

---

## 🔹 Step 4: Verify Network Connectivity

### 📌 Find IP Address (Metasploitable2)
Run:
    `ifconfig [Metasloitable 2 IP address]`

---

# Full VMs (Kali + Metasploitable 2/ DVWA) setup on host only network in VMware

## 🧪 Setting Up Private Host-Only Cybersecurity Lab (VMware)

This guide walks through setting up a **safe and isolated penetration testing lab** using:

- 🐉 Kali Linux (Attacker)
- 🎯 Metasploitable2 / DVWA (Target)

---

# ⚙️ 1. Create Host-Only Network

### 🛠️ Steps
1. Open **VMware**
2. Go to **Edit → Virtual Network Editor**
3. Find **VMnet1**
4. Set it to **Host-Only**

### ✅ Ensure Configuration
- Subnet IP: `192.168.56.0`
- Subnet Mask: `255.255.255.0`
- DHCP: **Enabled**

---

# 💻 2. Configure Virtual Machines

## 🐉 Kali Linux (Attacker)

### Network Setup:
- **Adapter 1 → NAT** (Internet access)
- **Adapter 2 → Host-Only (VMnet1)** (Lab access)

### 🎯 Result:
- Internet access ✅
- Can attack target machines ✅

---

## 🎯 Target Machine (Metasploitable2 / DVWA)

### Network Setup:
- **Only 1 Adapter → Host-Only (VMnet1)**

### 🎯 Result:
- No internet ❌
- Fully isolated target ✅

---

# 📥 3. Installing Metasploitable2

### 🛠️ Steps:
1. Download **Metasploitable2 (.vmdk file)**
2. Open VMware
3. Click **Create New VM**
4. Select: **Use an existing virtual disk**
5. Choose the `.vmdk` file
6. Start the VM

### 🔑 Login Credentials:
``` id="i6k8x1"
Username: msfadmin
Password: msfadmin
```
### 🌐 Check IP Address:
``` ifconfig 
```
#### 👉 Expected: 192.168.56.x

---

# 🌐 4. Alternative Target: DVWA Setup (Inside Kali)
 
 ### 📦 Install Required Packages:

```
sudo apt update
sudo apt install apache2 mysql-server php php-mysqli git -y
```
