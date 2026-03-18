# Day 1 – Lab Setup & Virtualization

## Objective
Set up a cybersecurity lab environment using virtual machines for penetration testing practice. This includes installing Kali Linux (attacker), DVWA (web target), and Metasploitable2 (vulnerable system).

---

## Lab Architecture
- **Host Machine**: Windows
- **Virtualization Tool**: VMware Workstation Pro
- **Attacker Machine**: Kali Linux
- **Target Machines**: DVWA, Metasploitable2

---

## Tools & Technologies Used
- **VMware Workstation Pro**: Type-2 Hypervisor.
- **Kali Linux**: Debian-based distribution for penetration testing.
- **DVWA**: PHP/MySQL web application that is damn vulnerable.
- **Metasploitable2**: An intentionally vulnerable Linux virtual machine.
- **Services**: Apache2, MySQL.

---

# 1. Installing Kali Linux on VMware

## Step 1: Install VMware Workstation Pro
1. Visit the official **Broadcom/VMware** website.
2. Register or log in to your account.
3. Download **VMware Workstation Pro (Personal Use/Free Version)** for Windows.
4. Run the installer and follow the default prompts to complete the installation.

---

## Step 2: Download Kali Linux VM
1. Go to the [Kali Linux Official Download Page](https://www.kali.org/get-kali/#kali-virtual-machines).
2. Select the **Virtual Machines** platform.
3. Download the pre-built **VMware image (.7z file)**.

---

## Step 3: Setup Kali Linux in VMware
1. **Extract** the downloaded `.7z` file using 7-Zip or WinRAR.
2. Open VMware Workstation Pro and click on **"Open a Virtual Machine"**.
3. Navigate to the extracted folder and select the `.vmx` file.
4. **Configure Hardware Settings**:
   - **RAM**: Minimum 4 GB (Recommended).
   - **CPU**: 2 Cores.
5. Click **Power On this virtual machine**.

### Default Credentials:
> **Username**: `kali`  
> **Password**: `kali`

---

# 2. Installing DVWA in Kali Linux

## Step 1: Clone DVWA Repository
Open the terminal in Kali Linux and navigate to the web root directory:

```bash
cd /var/www/html
sudo git clone [https://github.com/digininja/DVWA.git](https://github.com/digininja/DVWA.git)
