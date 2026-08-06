# 01. Host Machine Preparation

---

# 📖 Overview

Before deploying the OpenSOC-Lab environment, it is essential to prepare the host machine to ensure that virtualization software and multiple virtual machines can operate efficiently. Proper preparation helps prevent performance issues, virtualization errors, and installation failures during deployment.

This guide covers the hardware requirements, software prerequisites, BIOS configuration, and system preparation steps required before creating any virtual machines.

---

| Information | Details |
|-------------|---------|
| **Document** | 01-host-machine-preparation.md |
| **Version** | v1.0 |
| **Difficulty** | Beginner |
| **Estimated Time** | 15–20 Minutes |
| **Related Screenshots** | `images/deployment/host-machine/` |

---

# 🎯 Objectives

Upon completing this guide, you will be able to:

- Verify that your system meets the minimum hardware requirements.
- Enable hardware virtualization in BIOS/UEFI.
- Install the required software.
- Download the required operating system images.
- Prepare the host operating system for virtualization.
- Verify that the host machine is ready for deployment.

---

# 🖥️ Host Machine Specifications

The following host machine specifications were used during the deployment of OpenSOC-Lab.

| Component | Specification |
|------------|---------------|
| Host Operating System | Windows 11 |
| Processor | Intel Core i5 |
| Memory (RAM) | 16 GB |
| Storage | SSD (Recommended) |
| Internet Connection | Required |
| Virtualization Software | Oracle VirtualBox |

> **💡 Note**
>
> Systems with higher specifications will provide better performance when multiple virtual machines are running simultaneously.

---

# 💻 Minimum Hardware Requirements

| Component | Minimum | Recommended |
|------------|----------|-------------|
| CPU | Quad-Core Processor | Intel Core i5 / AMD Ryzen 5 or higher |
| RAM | 8 GB | 16 GB or higher |
| Storage | 100 GB Free | 250 GB SSD or higher |
| Internet | Required | Stable Broadband Connection |

---

# 📦 Required Software

Download and install the following software before beginning the deployment.

| Software | Purpose |
|-----------|---------|
| Oracle VirtualBox | Virtual Machine Platform |
| Oracle VirtualBox Extension Pack | Additional VirtualBox Features |
| Ubuntu Server 24.04 LTS ISO | SOC Server |
| Ubuntu Desktop 24.04 LTS ISO | Linux Endpoint |
| Windows 11 ISO | Windows Endpoint |
| Kali Linux ISO | Attacker Machine |

---

# 🌐 Required Downloads

Download the latest stable versions from their official websites.

| Software | Official Website |
|-----------|------------------|
| Oracle VirtualBox | https://www.virtualbox.org |
| Ubuntu Server | https://ubuntu.com/download/server |
| Ubuntu Desktop | https://ubuntu.com/download/desktop |
| Kali Linux | https://www.kali.org/get-kali |
| Windows 11 ISO | https://www.microsoft.com/software-download/windows11 |

---

# ⚙️ Enable Hardware Virtualization

Virtualization must be enabled in the BIOS or UEFI firmware before virtual machines can be created.

## Common Virtualization Technologies

| Processor | Technology |
|------------|------------|
| Intel | Intel VT-x |
| AMD | AMD-V |

---

## ✅ Verification

On Windows:

1. Open **Task Manager**.
2. Navigate to the **Performance** tab.
3. Select **CPU**.
4. Verify that **Virtualization** is displayed as **Enabled**.

Expected Output:

```text
Virtualization : Enabled
```

> **⚠️ Warning**
>
> If virtualization is disabled, VirtualBox may fail to start virtual machines or display VT-x / AMD-V related errors.

---

# 🧹 Prepare the Host Operating System

Before creating virtual machines, perform the following tasks:

- Install the latest Windows updates.
- Ensure sufficient free disk space.
- Close unnecessary background applications.
- Disable unused startup applications.
- Connect to a stable internet connection.
- Restart the system if required.

---

# 📁 Recommended Project Directory Structure

Organize the project files using the following directory structure.

```text
OpenSOC-Lab/
│
├── ISOs/
├── Virtual Machines/
├── Screenshots/
├── Documentation/
└── Backups/
```

Keeping files organized simplifies maintenance, backup, and future deployment.

---

# ✅ Pre-Deployment Checklist

Verify the following before proceeding:

- [ ] Hardware Virtualization Enabled
- [ ] Oracle VirtualBox Installed
- [ ] VirtualBox Extension Pack Installed
- [ ] Ubuntu Server ISO Downloaded
- [ ] Ubuntu Desktop ISO Downloaded
- [ ] Windows 11 ISO Downloaded
- [ ] Kali Linux ISO Downloaded
- [ ] Minimum 100 GB Free Storage Available
- [ ] Stable Internet Connection

---

# 📸 Screenshot References

The screenshots associated with this guide will be stored in the following directory.

```text
images/
└── deployment/
      └── host-machine/
```

The following screenshots will be included after the deployment documentation has been completed.

| Figure | Screenshot | Filename |
|---------|------------|----------|
| Figure 1.1 | Hardware Virtualization Enabled | virtualization-enabled.png |
| Figure 1.2 | Oracle VirtualBox Installed | virtualbox-installed.png |
| Figure 1.3 | Downloaded ISO Files | downloaded-isos.png |
| Figure 1.4 | Host Machine Specifications | host-specifications.png |

> **📝 Note**
>
> Screenshots will be added in a later documentation phase after all deployment guides have been completed.

---

# 🛠️ Common Issues

## Virtualization Disabled

### Symptoms

- Virtual machines fail to start.
- VT-x / AMD-V errors appear.
- Hypervisor initialization fails.

### Resolution

Enable Intel VT-x or AMD-V in the BIOS/UEFI settings and restart the system.

---

## Insufficient RAM

### Symptoms

- Slow virtual machine performance.
- Installation freezes.
- Wazuh Indexer crashes due to insufficient memory.

### Resolution

Increase the available RAM or reduce the number of simultaneously running virtual machines.

---

## Low Disk Space

### Symptoms

- Installation failures.
- Virtual disks cannot expand.
- Operating system updates fail.

### Resolution

Free additional storage before beginning the deployment.

---

# 📌 Summary

The host machine is now prepared for the deployment of the OpenSOC-Lab environment.

The following prerequisites should now be complete:

- Hardware virtualization enabled.
- Required software installed.
- Operating system images downloaded.
- Adequate hardware resources available.
- Host operating system prepared for virtualization.

You are now ready to install Oracle VirtualBox and begin creating the virtual infrastructure.

---

## ➡️ Next Guide

**02-virtualbox-setup.md**

Continue with the installation and configuration of Oracle VirtualBox, including the Extension Pack, NAT Network creation, and virtual machine provisioning.
