# 02. Oracle VirtualBox Setup

---

# 📖 Overview

Oracle VirtualBox provides the virtualization platform used to deploy the OpenSOC-Lab environment. In this guide, you will install Oracle VirtualBox, configure the Extension Pack, create a dedicated NAT Network, and verify that the virtualization environment is ready before deploying the virtual machines.

A properly configured virtualization environment ensures stable networking, resource isolation, and seamless communication between all components of the SOC laboratory.

---

| Information | Details |
|-------------|---------|
| **Document** | 02-virtualbox-setup.md |
| **Version** | v1.0 |
| **Difficulty** | Beginner |
| **Estimated Time** | 20–30 Minutes |
| **Related Screenshots** | `images/deployment/virtualbox/` |

---

# 🎯 Objectives

After completing this guide, you will be able to:

- Install Oracle VirtualBox.
- Install the Oracle VirtualBox Extension Pack.
- Create a dedicated NAT Network.
- Configure VirtualBox preferences.
- Verify that VirtualBox is ready for deployment.

---

# 📋 Prerequisites

Before continuing, ensure the following requirements have been completed.

- Host Machine Preparation completed.
- Hardware Virtualization enabled.
- Oracle VirtualBox installer downloaded.
- VirtualBox Extension Pack downloaded.
- Administrator privileges available.

---

# 💻 Installing Oracle VirtualBox

## Step 1 – Launch the Installer

Run the VirtualBox installer downloaded from the official website.

Accept the default installation options unless customization is required.

> **💡 Tip**
>
> Installing VirtualBox with the default settings is recommended for most users.

---

## Step 2 – Install Network Drivers

During installation Windows may display security prompts requesting permission to install Oracle networking drivers.

Click:

**Install**

for each driver.

These drivers are required for:

- Virtual Networking
- NAT Network
- Host-Only Adapter
- Bridged Networking

---

## Step 3 – Complete Installation

Once installation finishes,

Click

**Finish**

Launch Oracle VirtualBox.

---

# 📦 Installing the Extension Pack

The Extension Pack enables additional VirtualBox functionality including:

- USB 2.0 / USB 3.0 Support
- NVMe Support
- Disk Encryption
- PXE Boot
- Remote Display (VRDP)

---

## Installation Steps

1. Open Oracle VirtualBox.
2. Select

```
Tools
```

3. Open

```
Extensions
```

4. Click

```
Install
```

5. Select the downloaded Extension Pack.

6. Accept the license agreement.

7. Wait for the installation to complete.

---

## ✅ Verification

Navigate to

```
Tools
→
Extensions
```

The installed Extension Pack should be visible.

---

# 🌐 Creating the NAT Network

The OpenSOC-Lab uses a dedicated NAT Network allowing all virtual machines to communicate while maintaining internet access.

---

## Step 1

Open

```
File
→
Tools
→
Network Manager
```

---

## Step 2

Select

```
NAT Networks
```

---

## Step 3

Click

```
Create
```

---

## Step 4

Configure the network.

Example configuration:

| Setting | Value |
|----------|-------|
| Network Name | OpenSOC-NAT |
| IPv4 Prefix | 10.0.2.0/24 |
| DHCP | Enabled |

> **💡 Note**
>
> The actual network name may vary. During this deployment, all virtual machines were connected to the same VirtualBox NAT Network.

---

# 🔍 Why Use NAT Network?

Using a NAT Network provides several advantages.

- Internet access for every VM.
- Communication between virtual machines.
- Network isolation from the physical host.
- Easy deployment.
- Suitable for attack simulation labs.

---

# ⚙️ Recommended VirtualBox Preferences

The following settings are recommended before creating virtual machines.

| Setting | Recommendation |
|----------|---------------|
| Default Machine Folder | Dedicated OpenSOC-Lab Folder |
| Input | Auto Capture Keyboard Enabled |
| Update Check | Optional |
| Language | English |

---

# 📁 Recommended Virtual Machine Naming

To maintain consistency throughout the documentation, use the following names.

| Virtual Machine | Recommended Name |
|-----------------|------------------|
| Ubuntu Server | soc-server |
| Windows Endpoint | windows-victim |
| Ubuntu Endpoint | ubuntu-vic |
| Kali Linux | kali |

These names are used throughout the remaining deployment documentation.

---

# 📸 Screenshot References

Screenshots associated with this guide should be stored in:

```text
images/
└── deployment/
      └── virtualbox/
```

The following screenshots should be captured.

| Figure | Screenshot | Filename |
|---------|------------|----------|
| Figure 2.1 | Oracle VirtualBox Installed | virtualbox-installed.png |
| Figure 2.2 | Extension Pack Installed | extension-pack.png |
| Figure 2.3 | Network Manager | network-manager.png |
| Figure 2.4 | NAT Network Configuration | nat-network.png |
| Figure 2.5 | VirtualBox Home Screen | virtualbox-home.png |

> **📝 Note**
>
> Screenshots will be added after completing the deployment documentation.

---

# ✅ Verification Checklist

Verify the following before continuing.

- [ ] Oracle VirtualBox Installed
- [ ] Extension Pack Installed
- [ ] NAT Network Created
- [ ] VirtualBox Opens Successfully
- [ ] Internet Connectivity Available
- [ ] Ready to Create Virtual Machines

---

# 🛠️ Common Issues

## Extension Pack Version Mismatch

### Symptoms

- Extension Pack installation fails.
- Compatibility warning appears.

### Resolution

Ensure that the Extension Pack version exactly matches the installed VirtualBox version.

---

## VirtualBox Does Not Start

### Symptoms

- VirtualBox closes immediately.
- Driver initialization errors appear.

### Resolution

Restart Windows and reinstall VirtualBox using Administrator privileges.

---

## Network Adapter Missing

### Symptoms

- NAT Network cannot be created.
- Virtual adapters are unavailable.

### Resolution

Repair or reinstall Oracle VirtualBox to restore the networking drivers.

---

# 📌 Summary

Oracle VirtualBox has now been successfully configured for OpenSOC-Lab.

The following tasks have been completed:

- Oracle VirtualBox installed.
- Extension Pack installed.
- NAT Network created.
- Virtualization environment verified.

The system is now ready to begin creating the virtual machines required for the SOC infrastructure.

---

## ➡️ Next Guide

**03-ubuntu-server-installation.md**

The next guide covers the installation of Ubuntu Server, including virtual machine creation, hardware allocation, storage configuration, operating system installation, and initial system setup.
