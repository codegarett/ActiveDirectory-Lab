# 🧱 Active Directory Home Lab

This repository documents the setup, configuration, and automation of a Windows Server Active Directory (AD) environment built in a home lab. It is designed for IT Support Technicians, Cybersecurity Analysts, and Systems Administrators looking to gain hands-on experience with Windows Server, Active Directory Domain Services (AD DS), Group Policy, and PowerShell scripting.

---

## 📚 Purpose

This project simulates a real-world domain environment using virtual machines to demonstrate:
- Domain controller deployment
- Organizational Unit (OU) design
- User/group management
- Group Policy configuration
- Security baseline enforcement
- PowerShell automation

This repo serves as a learning and showcase tool for understanding enterprise-grade infrastructure while applying scripting and automation for common IT tasks.

---

## 🧰 Technologies Used

- **Windows Server 2019/2022**
- **Active Directory Domain Services (AD DS)**
- **Group Policy Management Console (GPMC)**
- **PowerShell (v5.1+)**
- **VirtualBox / VMware / Hyper-V**
- **Windows 10/11 Clients**

---

## 🏗️ Lab Architecture

- One **Windows Server** VM as the Domain Controller (`dc1.local.lab`)
- One or more **Windows 10/11** clients joined to the domain
- Custom Organizational Units for Users, Computers, and Service Accounts
- Group Policies linked at OU level for management and security enforcement
- DNS and DHCP hosted on the domain controller
- Optional firewall with internet access for testing outbound traffic

---

## 📂 Repository Structure

```
ActiveDirectory-Lab/
├── README.md                          # Main project overview
├── architecture.png                   # Visual diagram of AD lab setup
├── setup-notes.md                     # Step-by-step setup notes
├── scripts/
│   ├── create-users.ps1               # PowerShell script to bulk-create users
│   ├── disable-user.ps1               # Script to disable a compromised user account
│   └── query-group-members.ps1        # Get AD group membership info
└── docs/
    └── ActiveDirectoryLab_SOPs_README.md  # Combined SOPs for AD management tasks
```

---

## 📘 Documentation / SOPs

Detailed step-by-step SOPs are available in [`docs/ActiveDirectoryLab_SOPs_README.md`](docs/ActiveDirectoryLab_SOPs_README.md). Topics include:
- Creating AD users manually
- Applying GPO security baselines
- Locking out and auditing compromised accounts
- Joining clients to the domain
- Resetting user passwords

---

## ⚙️ Example Use Cases

- **Bulk User Creation**: Automate the creation of test accounts in a dev environment
- **Security Testing**: Use AD for pentesting, blue teaming, or lab CTF simulations
- **Group Policy Configuration**: Enforce password policies, disable control panel access, map drives
- **Incident Response**: Practice detection, isolation, and remediation in an AD-connected setup

---

## 📌 Getting Started

1. Set up Windows Server in a virtualized environment.
2. Install AD DS and promote to domain controller.
3. Configure DNS, DHCP (optional), and create Organizational Units.
4. Clone this repo to access scripts and documentation.
5. Follow `setup-notes.md` and start testing AD functionality with PowerShell and GPOs.

---

## 🧠 Learning Outcomes

- Learn core identity and access management (IAM) concepts
- Practice scripting in a secure lab environment
- Understand how enterprise environments structure and secure their domain
- Build a portfolio-ready project to showcase AD skills

---

## 🤝 Contributing

Feel free to fork, use, and improve! Pull requests for new SOPs, lab ideas, and automation tools are welcome.

---

## 📄 License

MIT License

