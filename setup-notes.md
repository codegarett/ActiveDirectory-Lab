# 🛠️ Active Directory Homelab Setup Notes

This document outlines the setup process and configuration for a virtualized Active Directory environment using VirtualBox and Kali Linux.

---

## 🧱 Lab Architecture Overview

**Environment Type:** VirtualBox  
**Host OS:** [Your Host OS]  
**Networking Mode:** Internal Network or NAT with Host-Only Adapter  
**Main Components:**
- Windows Server 2019 (Domain Controller)
- Windows 10 Client VM(s)
- Kali Linux (Attacker Box / Analyst)
- Optional: DNS/DHCP Server (if not included in DC)

---

## 🔧 VM Configuration

### 🖥️ Windows Server 2019 – Domain Controller
- **Hostname:** `DC01`
- **IP Address:** `192.168.10.10`
- **Role:** Active Directory Domain Services (AD DS), DNS, DHCP (optional)
- **Domain Name:** `homelab.local`
- **Specs:** 2 CPUs, 4 GB RAM, 40 GB disk

### 🖥️ Windows 10 – Client VM
- **Hostname:** `CLIENT01`
- **IP Address:** `192.168.10.20`
- **Role:** Domain-joined workstation
- **Specs:** 2 CPUs, 2 GB RAM, 30 GB disk

### 🖥️ Kali Linux – Analyst/Attacker
- **Hostname:** `kali`
- **IP Address:** `192.168.10.30`
- **Tools:** BloodHound, CrackMapExec, Nmap, etc.
- **Specs:** 2 CPUs, 2 GB RAM, 30 GB disk

---

## 🌐 Networking Setup

- All VMs connected to a VirtualBox **Internal Network** (`intnet`) or use **Host-Only + NAT** for internet access
- Static IPs manually set for DC and clients
- Windows DC is configured as the DNS server for the domain

---

## 🪪 Domain Configuration Steps (Windows Server)

1. Rename server to `DC01`
2. Set static IP: `192.168.10.10`, DNS: `127.0.0.1`
3. Install **Active Directory Domain Services**
4. Promote to Domain Controller
5. Create domain: `homelab.local`
6. Create OU structure and user accounts:
    - `OU=Workstations`
    - `OU=Users`
    - Users: `alice`, `bob`, `admin.user`
7. Create Group Policies (optional)

---

## 🧑‍💻 Domain Join (Windows 10)

1. Set static IP: `192.168.10.20`, DNS: `192.168.10.10`
2. Rename PC to `CLIENT01`
3. Join to domain: `homelab.local`
4. Reboot and log in with domain credentials

---

## 🧪 Kali Linux (Testing/Recon)

1. Set static IP: `192.168.10.30`
2. Verify connectivity:
    ```bash
    ping 192.168.10.10
    nslookup homelab.local
    ```
3. Tools to install:
    ```bash
    sudo apt update
    sudo apt install bloodhound neo4j crackmapexec ldap-utils smbclient
    ```

---

## 🔐 Sample AD Test Users

| Username     | Role           | Password         |
|--------------|----------------|------------------|
| `alice`      | Standard User  | `P@ssw0rd123!`    |
| `bob`        | Standard User  | `P@ssw0rd123!`    |
| `admin.user` | Domain Admin   | `Adm1n!Pass123`   |

*Note: Never reuse these passwords outside the lab.*

---

## 📁 Shared Folders (Optional)

- Configure shared folder in VirtualBox for easy tool/script transfer
- Mount in Kali:
  ```bash
  sudo mount -t vboxsf SharedFolderName /mnt/share
