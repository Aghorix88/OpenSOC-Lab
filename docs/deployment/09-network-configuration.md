# 09. Network Configuration

---

# 📖 Overview

A properly configured network is the foundation of the OpenSOC-Lab environment. All virtual machines must be able to communicate with each other while maintaining internet connectivity for software installation, updates, and package management.

This chapter explains the network architecture, VirtualBox NAT Network configuration, IP addressing, connectivity verification, and common networking issues encountered during deployment.

---

| Information | Details |
|-------------|---------|
| **Document** | 09-network-configuration.md |
| **Version** | v1.0 |
| **Difficulty** | Intermediate |
| **Estimated Time** | 20–30 Minutes |
| **Related Screenshots** | `images/deployment/network/` |

---

# 🎯 Objectives

After completing this chapter, you will be able to:

- Configure the VirtualBox NAT Network.
- Connect all virtual machines to the same network.
- Verify IP address allocation.
- Verify communication between all systems.
- Troubleshoot common network connectivity issues.

---

# 📋 Prerequisites

Before continuing, ensure that:

- Oracle VirtualBox is installed.
- NAT Network has been created.
- Ubuntu Server is operational.
- Windows Endpoint is operational.
- Ubuntu Endpoint is operational.
- Kali Linux is operational.

---

# 🌐 OpenSOC-Lab Network Architecture

The laboratory consists of four virtual machines connected through a dedicated VirtualBox NAT Network.

```text
                         Internet
                             │
                             │
                    VirtualBox NAT Network
                             │
        ┌──────────────┬──────────────┬──────────────┐
        │              │              │              │
        ▼              ▼              ▼              ▼
+----------------+ +----------------+ +----------------+ +----------------+
| Ubuntu Server  | | Windows 11 VM  | | Ubuntu VM      | | Kali Linux     |
| Wazuh Server   | | Wazuh Agent    | | Wazuh Agent    | | Attacker        |
+----------------+ +----------------+ +----------------+ +----------------+
```

---

# 📌 Virtual Machine Roles

| Virtual Machine | Purpose |
|-----------------|---------|
| Ubuntu Server | Wazuh Manager, Indexer, Dashboard |
| Windows 11 | Monitored Endpoint |
| Ubuntu Desktop | Monitored Endpoint |
| Kali Linux | Attack Simulation |

---

# 🌍 Recommended IP Addressing

Example addressing scheme.

| Virtual Machine | Example IP |
|-----------------|------------|
| Ubuntu Server | 10.0.2.4 |
| Windows Endpoint | 10.0.2.x |
| Ubuntu Endpoint | 10.0.2.x |
| Kali Linux | 10.0.2.x |

> **Note**
>
> IP addresses assigned through DHCP may vary depending on your VirtualBox configuration.

---

# ⚙ Configure VirtualBox Network Adapter

For every virtual machine:

1. Open **Settings**.
2. Select **Network**.
3. Enable **Adapter 1**.
4. Choose **Attached to: NAT Network**.
5. Select the configured NAT Network.

Repeat the same configuration for:

- Ubuntu Server
- Windows Endpoint
- Ubuntu Endpoint
- Kali Linux

---

# 🔍 Verify IP Addresses

On Ubuntu Server:

```bash
hostname -I
```

On Ubuntu Endpoint:

```bash
hostname -I
```

On Kali Linux:

```bash
hostname -I
```

On Windows:

```cmd
ipconfig
```

Verify that every virtual machine has received an IP address.

---

# 📡 Verify Connectivity

## Kali → Ubuntu Server

```bash
ping -c 4 10.0.2.4
```

---

## Kali → Windows Endpoint

```bash
ping -c 4 <WINDOWS-IP>
```

---

## Kali → Ubuntu Endpoint

```bash
ping -c 4 <UBUNTU-ENDPOINT-IP>
```

---

## Ubuntu Endpoint → Ubuntu Server

```bash
ping -c 4 10.0.2.4
```

---

## Windows Endpoint → Ubuntu Server

```cmd
ping 10.0.2.4
```

---

Expected Output

```text
64 bytes from ...
```

or

```text
Reply from ...
```

All systems should successfully communicate with one another.

---

# 🌐 Verify Internet Connectivity

Ubuntu Server

```bash
ping -c 4 google.com
```

Ubuntu Endpoint

```bash
ping -c 4 google.com
```

Kali Linux

```bash
ping -c 4 google.com
```

Windows

```cmd
ping google.com
```

---

# 🔎 Verify DNS Resolution

Ubuntu

```bash
nslookup google.com
```

Windows

```cmd
nslookup google.com
```

Successful DNS resolution confirms that the virtual machines can resolve domain names.

---

# 🔐 Verify Wazuh Communication Ports

Verify that the Wazuh Server is listening on the required ports.

```bash
sudo ss -tulnp
```

Important ports include:

| Port | Purpose |
|------:|---------|
| 443 | Wazuh Dashboard |
| 1514 | Agent Communication |
| 1515 | Agent Registration |
| 55000 | Wazuh API |
| 9200 | Wazuh Indexer |

---

# ✅ Network Verification Checklist

Verify the following before proceeding.

- [ ] All virtual machines powered on
- [ ] Same NAT Network configured
- [ ] IP addresses assigned
- [ ] Internet connectivity verified
- [ ] DNS resolution working
- [ ] Ubuntu Server reachable
- [ ] Windows Endpoint reachable
- [ ] Ubuntu Endpoint reachable
- [ ] Kali Linux reachable
- [ ] Wazuh communication ports available

---

# 📸 Screenshot References

Store screenshots in:

```text
images/
└── deployment/
      └── network/
```

Recommended screenshots.

| Figure | Screenshot | Filename |
|---------|------------|----------|
| Figure 9.1 | VirtualBox NAT Network | nat-network.png |
| Figure 9.2 | Ubuntu Server IP Address | server-ip.png |
| Figure 9.3 | Windows IP Configuration | windows-ipconfig.png |
| Figure 9.4 | Ubuntu Endpoint IP Address | ubuntu-ip.png |
| Figure 9.5 | Kali Linux IP Address | kali-ip.png |
| Figure 9.6 | Successful Ping Test | ping-test.png |
| Figure 9.7 | Wazuh Listening Ports | listening-ports.png |

---

# 🛠 Common Issues

## Virtual Machines Cannot Communicate

### Symptoms

- Ping requests fail.
- Agents cannot connect to the Wazuh Manager.
- Dashboard shows disconnected agents.

### Resolution

Verify that every virtual machine is attached to the same VirtualBox NAT Network.

---

## No IP Address Assigned

### Symptoms

`hostname -I` returns no IP address or Windows shows an APIPA address (`169.254.x.x`).

### Resolution

- Restart the virtual machine.
- Verify the network adapter configuration.
- Confirm that the NAT Network DHCP service is enabled.

---

## No Internet Connectivity

### Symptoms

Package installation fails or external websites cannot be reached.

### Resolution

- Verify NAT Network settings.
- Confirm the host machine has internet connectivity.
- Restart the virtual machine.
- Verify DNS configuration.

---

## Unable to Ping Windows Endpoint

### Symptoms

Ping requests from Kali or Ubuntu fail.

### Resolution

Windows Firewall may block ICMP echo requests.

Allow ICMP Echo Requests through Windows Firewall or temporarily disable the firewall for testing purposes.

---

## Wazuh Agents Cannot Connect

### Symptoms

Agents appear as **Disconnected**.

### Resolution

Verify:

- Correct Manager IP address.
- Agent service status.
- Network connectivity.
- Required ports are accessible.

---

# 📌 Summary

The OpenSOC-Lab network has now been successfully configured and verified.

Completed tasks:

- NAT Network configured.
- IP addresses assigned.
- Internet connectivity verified.
- VM-to-VM communication confirmed.
- DNS resolution verified.
- Wazuh communication ports validated.

The environment is now fully prepared for attack simulations and security monitoring.

---

# 🎓 Learning Outcomes

After completing this chapter, you should be able to:

- Configure VirtualBox NAT Networks.
- Verify communication between multiple virtual machines.
- Troubleshoot network connectivity issues.
- Validate Wazuh communication ports.
- Prepare a secure networking environment for SOC operations.

---

## ➡️ Next Guide

**10-troubleshooting.md**

The next chapter documents the real-world deployment issues encountered while building OpenSOC-Lab, along with their root causes, diagnostic steps, and resolutions. This section serves as a practical troubleshooting reference for future deployments.
