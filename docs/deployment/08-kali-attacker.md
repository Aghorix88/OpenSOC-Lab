# 08. Kali Linux Attacker Machine Setup

---

# 📖 Overview

Kali Linux serves as the dedicated attacker machine within the OpenSOC-Lab environment. It is used to simulate reconnaissance, vulnerability assessment, brute-force attempts, exploitation, and other offensive security activities against the monitored endpoints.

The purpose of using a separate attacker machine is to safely generate realistic security events that can be detected, analyzed, and investigated through the Wazuh SIEM platform.

This chapter focuses on preparing Kali Linux for attack simulations. The actual attack scenarios are documented separately.

---

| Information | Details |
|-------------|---------|
| **Document** | 08-kali-attacker.md |
| **Version** | v1.0 |
| **Difficulty** | Beginner |
| **Estimated Time** | 20–30 Minutes |
| **Related Screenshots** | `images/deployment/kali/` |

---

# 🎯 Objectives

After completing this chapter, you will be able to:

- Deploy a Kali Linux virtual machine.
- Configure the network adapter.
- Verify connectivity with all virtual machines.
- Update the operating system.
- Verify that common penetration testing tools are available.
- Prepare the environment for attack simulations.

---

# 📋 Prerequisites

Before continuing, ensure that:

- Oracle VirtualBox is installed.
- Ubuntu Server (Wazuh) is operational.
- Windows Endpoint is running.
- Ubuntu Endpoint is running.
- All systems are connected to the same VirtualBox NAT Network.

---

# 🖥️ Recommended Virtual Machine Configuration

Create the Kali Linux virtual machine using the following recommended configuration.

| Setting | Recommended Value |
|----------|-------------------|
| Name | kali |
| Operating System | Kali Linux (64-bit) |
| Memory | 4 GB |
| Processor | 2 vCPU or higher |
| Disk Size | 30 GB (VDI, Dynamically Allocated) |
| Network Adapter | NAT Network |

> **💡 Best Practice**
>
> Allocate additional CPU cores and memory if resource-intensive tools such as Metasploit or Burp Suite will be used.

---

# 💿 Install Kali Linux

1. Create a new virtual machine in Oracle VirtualBox.
2. Attach the Kali Linux ISO.
3. Boot the virtual machine.
4. Complete the operating system installation.
5. Create a local user account.
6. Restart the virtual machine after installation.

---

# 🌐 Verify Network Configuration

Determine the assigned IP address.

```bash
hostname -I
```

or

```bash
ip addr show
```

Example Output

```text
10.0.2.x
```

---

# 📡 Verify Connectivity

Verify communication with the Wazuh Server.

```bash
ping -c 4 10.0.2.4
```

Verify communication with the Windows endpoint.

```bash
ping -c 4 <WINDOWS-IP>
```

Verify communication with the Ubuntu endpoint.

```bash
ping -c 4 <UBUNTU-ENDPOINT-IP>
```

Expected Result

```text
64 bytes from ...
```

All systems should respond successfully.

---

# 🔄 Update Kali Linux

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

Verify the operating system version.

```bash
cat /etc/os-release
```

---

# 🛠 Verify Security Tools

Verify that commonly used penetration testing tools are installed.

Check Nmap.

```bash
nmap --version
```

Check Hydra.

```bash
hydra -h
```

Check Nikto.

```bash
nikto -Version
```

Check Metasploit.

```bash
msfconsole --version
```

---

# 📦 Install Missing Tools (If Required)

If any required tool is not available, install it using the package manager.

Install Nmap.

```bash
sudo apt install nmap -y
```

Install Hydra.

```bash
sudo apt install hydra -y
```

Install Nikto.

```bash
sudo apt install nikto -y
```

Install Metasploit Framework.

```bash
sudo apt install metasploit-framework -y
```

---

# 🔍 Verify Internet Connectivity

Verify internet access.

```bash
ping -c 4 google.com
```

Expected Result

```text
4 packets transmitted
4 packets received
```

---

# ⚠ Safe Attack Simulation Guidelines

This laboratory is intended for educational purposes only.

Before performing any attack:

- Verify that all targets belong to the OpenSOC-Lab environment.
- Never attack systems outside the lab.
- Ensure that snapshots or backups are available.
- Monitor the Wazuh Dashboard while attacks are running.
- Record observations for later analysis.

---

# ✅ Deployment Verification Checklist

Before continuing, verify the following.

- [ ] Kali Linux Installed
- [ ] Virtual Machine Running
- [ ] Internet Connectivity Verified
- [ ] Wazuh Server Reachable
- [ ] Windows Endpoint Reachable
- [ ] Ubuntu Endpoint Reachable
- [ ] Security Tools Installed
- [ ] Ready for Attack Simulation

---

# 📸 Screenshot References

Store screenshots in:

```text
images/
└── deployment/
      └── kali/
```

Recommended screenshots.

| Figure | Screenshot | Filename |
|---------|------------|----------|
| Figure 8.1 | Kali Linux Desktop | kali-desktop.png |
| Figure 8.2 | IP Address Verification | kali-ip.png |
| Figure 8.3 | Successful Ping to Wazuh Server | ping-server.png |
| Figure 8.4 | Successful Ping to Windows Endpoint | ping-windows.png |
| Figure 8.5 | Successful Ping to Ubuntu Endpoint | ping-ubuntu.png |
| Figure 8.6 | Installed Security Tools | installed-tools.png |

---

# 🛠 Common Issues

## Unable to Ping Other Virtual Machines

### Symptoms

The Kali Linux virtual machine cannot communicate with the Wazuh Server or monitored endpoints.

### Resolution

- Verify that all virtual machines are connected to the same VirtualBox NAT Network.
- Check each VM's IP address.
- Restart the network adapter if necessary.
- Verify that the target system is powered on.

---

## Missing Security Tools

### Symptoms

Commands such as `nmap`, `hydra`, or `nikto` are not recognized.

### Resolution

Update the package repository.

```bash
sudo apt update
```

Install the missing package.

Example:

```bash
sudo apt install nmap -y
```

---

## No Internet Connectivity

### Symptoms

Package updates fail or external hosts cannot be reached.

### Resolution

- Verify the NAT Network configuration.
- Restart the virtual machine.
- Check DNS settings.
- Confirm internet access from the host operating system.

---

# 📌 Summary

The Kali Linux attacker machine has now been successfully prepared for use within the OpenSOC-Lab environment.

Completed tasks:

- Kali Linux installed.
- Virtual machine configured.
- Network connectivity verified.
- Security tools verified.
- Internet access confirmed.
- Environment prepared for attack simulations.

The attacker machine is now ready to generate controlled security events for detection and analysis by the Wazuh platform.

---

# 🎓 Learning Outcomes

After completing this chapter, you should be able to:

- Configure Kali Linux for use in a SOC home lab.
- Verify communication with monitored endpoints.
- Prepare an attacker machine for controlled security testing.
- Validate that required penetration testing tools are available.
- Safely prepare for attack simulation exercises.

---

## ➡️ Next Guide

**09-network-configuration.md**

The next chapter explains the complete network architecture of the OpenSOC-Lab environment, including NAT Network configuration, IP addressing, connectivity validation, and communication between all virtual machines.
