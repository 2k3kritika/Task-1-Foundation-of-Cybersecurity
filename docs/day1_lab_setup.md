# Lab Engineering: Virtualization & Environment Isolation (Day 1)

[Back to main README](/README.md)

## 1. Purpose & Scope
The objective of this module is the deployment of a **sandboxed penetration testing environment**. This infrastructure is designed to facilitate safe exploitation, prevent accidental lateral movement into production networks, and ensure legal compliance through total isolation.

### Network Topology Overview


---

## 2. Infrastructure Components
| Role | OS / Platform | Resource Allocation | Purpose |
| :--- | :--- | :--- | :--- |
| **Attacker** | Kali Linux (Rolling) | 2 vCPU / 4GB RAM | Primary exploitation & reconnaissance workstation. |
| **Target A** | Metasploitable 2 | 1 vCPU / 512MB RAM | Intentionally vulnerable Linux-based server. |
| **Target B** | DVWA (Web App) | 1 vCPU / 1GB RAM | PHP/MySQL environment for web-based vulnerability testing. |

---

## 3. Provisioning Workflow

### 3.1 Hypervisor Installation
Choose a Type-2 Hypervisor for workstation-level virtualization.
* **VirtualBox:** Ensure the *Oracle VM VirtualBox Extension Pack* is installed for USB 2.0/3.0 support.
* **VMware Player/Workstation:** Ensure **Intel VT-x** or **AMD-V** is enabled in the host BIOS/UEFI.

### 3.2 Attacker Node Deployment (Kali Linux)
1.  **Image Source:** Use the official [Kali Linux Custom Image](https://www.kali.org/get-kali/#kali-virtual-machines) for your specific hypervisor.
2.  **Naming Convention:** `LAB-ATK-KALI-01`
3.  **Disk Provisioning:** 20GB+ (Dynamic Allocation).

### 3.3 Target Node Deployment
* **Metasploitable2:** Download the `.zip` file, extract, and "Open/Add" the `.vmdk` or `.vbox` file.
* **DVWA:** Can be deployed via Docker on a Debian/Ubuntu base or as a standalone LAMP stack.

---

## 4. Critical Network Configuration (Isolation Protocol)
**Mandatory Requirement:** All Virtual Machines must be assigned to a **Host-Only Adapter**.

> [!CAUTION]
> **DO NOT USE NAT or BRIDGED modes.** Bridged mode exposes vulnerable targets to your physical local network, posing a significant security risk to other devices in your home/office.

**Configuration Steps:**
1.  Navigate to **Settings > Network**.
2.  Set **Attached to:** `Host-only Adapter`.
3.  Ensure the Name matches across all VMs (e.g., `vboxnet0`).

---

## 5. Connectivity Verification (Verification Phase)
Before proceeding to Day 2, validate that the nodes can communicate within the isolated segment.

**Execute from Attacker Node (`LAB-ATK-KALI-01`):**
```bash
# Discover active hosts on the host-only segment
sudo arp-scan --localnet

# Verify ICMP reachability to target
ping -c 4 <TARGET_IP_ADDRESS>