# 🔐 Kali Linux Password Reset via GRUB (Lab Setup Note)

[Back to main README](/README.md)

## 📌 Overview
This document explains how to reset the password of a Kali Linux virtual machine using the GRUB bootloader. It also includes a real-world variation where the reset worked even with a modified command, along with the reasoning behind it.

---

## 🎯 Objective

- Regain access to a locked Kali Linux VM  
- Understand how boot-level access can bypass authentication  
- Learn the role of GRUB, init process, and filesystem states  

---

## ⚙️ Environment

- Virtual Machine: VirtualBox / VMware  
- OS: Kali Linux  
- Access Level: Physical/Boot access to VM  

---

## 🔧 Method: Reset Password via GRUB

### Step 1: Access GRUB Menu

- Start the Kali VM  
- During boot:  
  - Press `Shift` (VirtualBox)  
  - Press `Esc` repeatedly (VMware)  
- GRUB menu appears  

---

### Step 2: Edit Boot Entry

- Select default Kali boot option  
- Press `e` to edit boot parameters  

![Boot into root shell](/extra_screenshots/password_reset/edit_boot_entry.png)
---

### Step 3: Modify Boot Parameters

Locate the line starting with:

```bash
linux /boot/vmlinuz...
```

Modify it by adding:

```bash
init=/bin/bash
```

Example:

```bash
linux /boot/vmlinuz-xxxx root=UUID=xxxx ro quiet init=/bin/bash
```
![Modified Boot entry](/extra_screenshots/password_reset/password_reset/modify_boot_parameters.png)
---

### Step 4: Boot into Root Shell

- Press `Ctrl + X` or `F10`  
- System boots into a root shell without requiring a password  

![Boot into Root shell](/extra_screenshots/password_reset/boot_into_root_shell.png)
---

### Step 5: Remount Filesystem

By default, the filesystem is read-only. Remount it as read-write:

```bash
mount -o remount,rw /
```

---

### Step 6: Reset Password

Reset password for default user (`kali`):

```bash
passwd kali
```
![Reset the password](/extra_screenshots/password_reset/reset_passwd.png)

If username is unknown:

```bash
ls /home
```
![Navigate to Home](/extra_screenshots/password_reset/navigated_to_home.png)

---

### Step 7: Reboot System

```bash
reboot -f
```

or

```bash
exec /sbin/init
```
![Successfully changed the pwd and reboot is done](/extra_screenshots/password_reset/successfully_updated_and_rebooting.png)

---

## ⚠️ Common Mistakes

- Not remounting filesystem → password changes fail  
- Incorrect username → error during password reset  
- Assuming something is broken → unusual screen is normal  

---

## 🧪 What I Actually Did (Variation)

Instead of the standard command, I used:

```bash
linux /boot/vmlinuz-xxxx root=UUID=xxxx rw quiet init=/bin/bash
```

### 🔍 Why This Still Worked

Two key differences:

#### 1. `init=/bin/bash`

- This is the critical part  
- It bypasses the normal boot process  
- Directly launches a root shell  

#### 2. `rw` instead of `ro`

- Filesystem was mounted as read-write from the start  
- Eliminated the need for manual remounting  

### ✅ Result

- System booted directly into root shell  
- Password reset worked without needing `mount -o remount,rw /`  

---

## 🧠 Key Concepts Learned

### 1. GRUB Bootloader

- Allows modification of kernel parameters before OS loads  
- Provides a point of attack if not secured  

### 2. `init=/bin/bash`

- Overrides default init system  
- Grants root shell access without authentication  

### 3. Filesystem States

- `ro` → Read-only (default safe mode)  
- `rw` → Read-write (allows modifications)  

### 4. Privilege Escalation via Boot Access

- Physical or boot-level access can bypass system security  
- Password protection alone is insufficient  

---

## 🔐 Security Insight

> If an attacker has physical or boot access, they can gain root privileges unless additional protections are in place.

---

## 🛡️ Mitigation Strategies

- Enable full disk encryption  
- Set GRUB password protection  
- Restrict physical/boot access to system  

---

## 📂 Documentation Practice

This exercise demonstrates:

- Practical understanding of system internals  
- Ability to troubleshoot access issues  
- Awareness of real-world security weaknesses  

---