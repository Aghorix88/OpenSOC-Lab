# 03. Ubuntu Server Installation

---

# 📖 Overview

The Ubuntu Server virtual machine serves as the core infrastructure of the OpenSOC-Lab environment. It hosts the Wazuh Manager, Wazuh Indexer, and Wazuh Dashboard, making it the central component responsible for log collection, analysis, indexing, and visualization.

This chapter covers the complete process of creating the Ubuntu Server virtual machine, installing the operating system, performing the initial configuration, and preparing the server for the Wazuh platform deployment.

---

| Information | Details |
|-------------|---------|
| **Document** | 03-ubuntu-server-installation.md |
| **Version** | v1.0 |
| **Difficulty** | Beginner |
| **Estimated Time** | 30–45 Minutes |
| **Related Screenshots** | `images/deployment/ubuntu-server/` |

---

# 🎯 Objectives

After completing this guide, you will be able to:

- Create an Ubuntu Server virtual machine.
- Configure the recommended hardware resources.
- Install Ubuntu Server.
- Perform the initial system configuration.
- Update the operating system.
- Verify network connectivity.
- Prepare the server for Wazuh installation.

---

# 📋 Prerequisites

Before continuing, ensure that:

- Oracle VirtualBox has been installed.
- The VirtualBox Extension Pack is installed.
- The NAT Network has been created.
- The Ubuntu Server ISO has been downloaded.

---

# 🖥️ Virtual Machine Configuration

Create a new virtual machine using the following recommended configuration.

| Setting | Recommended Value |
|----------|-------------------|
| Name | soc-server |
| Type | Linux |
| Version | Ubuntu (64-bit) |
| Memory | 8 GB |
| Processor | 5 vCPU |
| Hard Disk | 40 GB (VDI, Dynamically Allocated) |
| Network Adapter | NAT Network |

> **💡 Best Practice**
>
> Allocate sufficient RAM and CPU resources to ensure stable operation of the Wazuh Manager, Indexer, and Dashboard.

---

# 🚀 Creating the Virtual Machine

## Step 1 — Create a New Virtual Machine

1. Open Oracle VirtualBox.
2. Click **New**.
3. Enter the virtual machine name.
4. Select **Linux** as the operating system type.
5. Select **Ubuntu (64-bit)**.
6. Allocate the recommended hardware resources.
7. Create a virtual hard disk.

---

## Step 2 — Attach the Ubuntu Server ISO

1. Open **Settings**.
2. Select **Storage**.
3. Choose the Optical Drive.
4. Attach the downloaded Ubuntu Server ISO.
5. Save the configuration.

---

## Step 3 — Configure Networking

Navigate to:

```
Settings → Network
```

Configure:

| Option | Value |
|---------|-------|
| Adapter 1 | Enabled |
| Attached To | NAT Network |
| NAT Network | OpenSOC-NAT (or your configured NAT network) |

---

# 💿 Installing Ubuntu Server

Start the virtual machine.

When the installer loads:

- Select your preferred language.
- Choose the keyboard layout.
- Configure the network (DHCP is recommended for most home lab deployments).
- Configure the storage using the default guided installation unless custom partitioning is required.
- Create a user account.
- Configure the hostname.
- Install OpenSSH Server if remote administration is required.

> **💡 Note**
>
> Installation screens may vary slightly depending on the Ubuntu Server release. The overall workflow remains the same.

---

# 🔐 First Login

After the installation completes:

1. Remove the installation ISO if prompted.
2. Reboot the virtual machine.
3. Log in using the account created during installation.

---

# 🌐 Verify Network Connectivity

Determine the assigned IP address.

```bash
ip addr show
```

or

```bash
hostname -I
```

Example Output

```text
10.0.2.x
```

---

Verify internet connectivity.

```bash
ping -c 4 google.com
```

Expected Output

```text
64 bytes from ...
```

Stop the ping process if required using:

```bash
Ctrl + C
```

---

# 🔄 Update the Operating System

Refresh the package repository.

```bash
sudo apt update
```

Upgrade installed packages.

```bash
sudo apt upgrade -y
```

Remove unnecessary packages.

```bash
sudo apt autoremove -y
```

Reboot the server if kernel updates are installed.

```bash
sudo reboot
```

---

# 🖥️ Verify System Information

Verify the operating system version.

```bash
lsb_release -a
```

Verify the kernel version.

```bash
uname -r
```

Verify disk usage.

```bash
df -h
```

Verify available memory.

```bash
free -h
```

Verify processor information.

```bash
lscpu
```

---

# 🔑 Install OpenSSH (If Not Installed)

Update the package index.

```bash
sudo apt update
```

Install OpenSSH Server.

```bash
sudo apt install openssh-server -y
```

Enable the SSH service.

```bash
sudo systemctl enable ssh
```

Start the SSH service.

```bash
sudo systemctl start ssh
```

Verify the service status.

```bash
sudo systemctl status ssh
```

---

# ✅ Verification Checklist

Before continuing, verify the following.

- [ ] Ubuntu Server Installed
- [ ] User Account Created
- [ ] Internet Connectivity Available
- [ ] Operating System Updated
- [ ] SSH Service Running
- [ ] IP Address Assigned
- [ ] Ready for Wazuh Installation

---

# 📸 Screenshot References

Store the screenshots for this guide in:

```text
images/
└── deployment/
      └── ubuntu-server/
```

Recommended screenshots:

| Figure | Screenshot | Filename |
|---------|------------|----------|
| Figure 3.1 | Virtual Machine Configuration | vm-configuration.png |
| Figure 3.2 | Ubuntu Installer | ubuntu-installer.png |
| Figure 3.3 | Successful Login | ubuntu-login.png |
| Figure 3.4 | System Update | system-update.png |
| Figure 3.5 | IP Address Verification | ip-address.png |
| Figure 3.6 | SSH Service Status | ssh-status.png |

> **📝 Note**
>
> Screenshots will be added after the deployment documentation has been completed.

---

# 🛠️ Common Issues

## No Internet Connectivity

### Symptoms

- Package updates fail.
- DNS resolution errors occur.
- Unable to reach external websites.

### Resolution

Verify the NAT Network configuration in VirtualBox and ensure the network adapter is attached to the correct NAT Network.

---

## SSH Service Not Running

### Symptoms

- Remote SSH connections fail.
- SSH service status reports inactive.

### Resolution

Start the SSH service.

```bash
sudo systemctl start ssh
```

Enable the service at boot.

```bash
sudo systemctl enable ssh
```

---

## Incorrect IP Address

### Symptoms

- The server cannot communicate with other virtual machines.

### Resolution

Restart the network interface or reboot the virtual machine. Verify that the network adapter is attached to the configured NAT Network.

---

# 📌 Summary

The Ubuntu Server virtual machine has now been successfully deployed and configured.

The following tasks have been completed:

- Ubuntu Server installed.
- Virtual machine configured.
- Operating system updated.
- Network connectivity verified.
- SSH service enabled.
- Server prepared for Wazuh installation.

The system is now ready for deploying the Wazuh platform.

---

## ➡️ Next Guide

**04-wazuh-installation.md**

The next chapter covers the installation and verification of the Wazuh Manager, Wazuh Indexer, and Wazuh Dashboard using the official Wazuh deployment method.
