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

```
cd /var/www/html
sudo git clone https://github.com/digininja/DVWA.git
🔹 Step 2: Set Permissions
sudo chmod -R 777 DVWA
🔹 Step 3: Configure DVWA
cd DVWA/config
cp config.inc.php.dist config.inc.php
sudo mousepad config.inc.php

Update:

$_DVWA['db_user'] = 'admin';
$_DVWA['db_password'] = 'password';
🔹 Step 4: Setup Database

Start MySQL:

sudo systemctl start mysql
sudo systemctl status mysql

Login:

sudo mysql -u root -p

Run:

CREATE DATABASE dvwa;
CREATE USER 'admin'@'127.0.0.1' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON dvwa.* TO 'admin'@'127.0.0.1';
FLUSH PRIVILEGES;
EXIT;
🔹 Step 5: Configure Apache & PHP

Start Apache:

sudo systemctl start apache2
sudo systemctl status apache2

Edit PHP config:

cd /etc/php
cd */apache2
sudo mousepad php.ini

Enable:

allow_url_fopen = On
allow_url_include = On

Restart Apache:

sudo systemctl restart apache2
🔹 Step 6: Access DVWA

🌍 Open browser in Kali:

http://127.0.0.1/DVWA

🔐 Login:

Username: admin
Password: password

👉 Click Create / Reset Database

💀 3. Installing Metasploitable2
🔹 Step 1: Download

Search: "Metasploitable2 download SourceForge"

Download and extract

🔹 Step 2: Setup in VMware

Open VMware → Open Virtual Machine

Select .vmx / .vmdk file

Click Power On

Choose "I copied it"

🔹 Step 3: Login
Username: msfadmin
Password: msfadmin
🔹 Step 4: Verify Connectivity

Find IP:

ifconfig

Test from Kali:

ping <Metasploitable_IP>
📸 Screenshots

Add inside /screenshots folder:

VMware setup

Kali running

DVWA working

Metasploitable terminal

Successful ping

✅ Conclusion

Successfully created a virtual cybersecurity lab:

⚔️ Kali Linux → Attacker

🎯 DVWA & Metasploitable2 → Targets

This environment is ready for:

Penetration Testing

Vulnerability Analysis

Security Experimentation

📝 Notes

Ensure all machines are on the same network (Host-Only/NAT)

Use consistent VM naming

Always verify connectivity before attacks