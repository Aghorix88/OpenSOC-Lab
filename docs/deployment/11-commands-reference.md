# 11. Commands Reference

---

# 📖 Overview

This chapter provides a categorized reference of the commands used throughout the OpenSOC-Lab deployment. It serves as a quick lookup guide for system administration, networking, Wazuh management, agent administration, troubleshooting, and verification.

Rather than searching through each deployment chapter, administrators can use this document as a central command reference.

---

| Information | Details |
|-------------|---------|
| **Document** | 11-commands-reference.md |
| **Version** | v1.0 |
| **Difficulty** | Reference Guide |
| **Estimated Time** | As Required |
| **Related Screenshots** | N/A |

---

# 🎯 Objectives

This reference enables you to quickly locate commands for:

- Linux administration
- System updates
- Network verification
- Service management
- Wazuh administration
- Agent management
- Log analysis
- Troubleshooting

---

# 🐧 Linux System Commands

## Update Package Repository

```bash
sudo apt update
```

---

## Upgrade Installed Packages

```bash
sudo apt upgrade -y
```

---

## Remove Unused Packages

```bash
sudo apt autoremove -y
```

---

## Reboot the System

```bash
sudo reboot
```

---

## Shutdown the System

```bash
sudo shutdown now
```

---

## Display Operating System Information

```bash
lsb_release -a
```

---

## Display Kernel Version

```bash
uname -r
```

---

## Display CPU Information

```bash
lscpu
```

---

## Display Memory Information

```bash
free -h
```

---

## Display Disk Usage

```bash
df -h
```

---

# 🌐 Network Commands

## Display IP Address

```bash
hostname -I
```

---

## Display Network Interfaces

```bash
ip addr
```

---

## Test Connectivity

```bash
ping -c 4 <IP-ADDRESS>
```

Example

```bash
ping -c 4 10.0.2.4
```

---

## Verify Internet Connectivity

```bash
ping -c 4 google.com
```

---

## DNS Lookup

```bash
nslookup google.com
```

---

## Display Listening Ports

```bash
sudo ss -tulnp
```

---

# ⚙ Service Management

## Check Service Status

```bash
sudo systemctl status <service-name>
```

Example

```bash
sudo systemctl status wazuh-manager
```

---

## Start Service

```bash
sudo systemctl start <service-name>
```

---

## Stop Service

```bash
sudo systemctl stop <service-name>
```

---

## Restart Service

```bash
sudo systemctl restart <service-name>
```

---

## Enable Service at Boot

```bash
sudo systemctl enable <service-name>
```

---

## Disable Service

```bash
sudo systemctl disable <service-name>
```

---

# 🛡 Wazuh Manager Commands

## Verify Wazuh Manager

```bash
sudo systemctl status wazuh-manager
```

---

## Verify Wazuh Indexer

```bash
sudo systemctl status wazuh-indexer
```

---

## Verify Wazuh Dashboard

```bash
sudo systemctl status wazuh-dashboard
```

---

## Restart Manager

```bash
sudo systemctl restart wazuh-manager
```

---

## Restart Indexer

```bash
sudo systemctl restart wazuh-indexer
```

---

## Restart Dashboard

```bash
sudo systemctl restart wazuh-dashboard
```

---

# 👥 Agent Management

## List Registered Agents

```bash
sudo /var/ossec/bin/agent_control -l
```

---

## List Connected Agents

```bash
sudo /var/ossec/bin/agent_control -lc
```

---

## Restart Ubuntu Agent

```bash
sudo systemctl restart wazuh-agent
```

---

## Check Ubuntu Agent Status

```bash
sudo systemctl status wazuh-agent
```

---

## Windows Agent Service

Check Status

```cmd
sc query WazuhSvc
```

Start

```cmd
net start WazuhSvc
```

Stop

```cmd
net stop WazuhSvc
```

Restart

```cmd
net stop WazuhSvc
net start WazuhSvc
```

---

# 📜 Log Analysis Commands

## View Ubuntu Agent Log

```bash
sudo tail -f /var/ossec/logs/ossec.log
```

---

## View Manager Log

```bash
sudo journalctl -u wazuh-manager
```

---

## View Dashboard Log

```bash
sudo journalctl -u wazuh-dashboard
```

---

## View Indexer Log

```bash
sudo journalctl -u wazuh-indexer
```

---

## View Complete System Log

```bash
sudo journalctl -xe
```

---

# 🔍 Resource Monitoring

## Memory Usage

```bash
free -h
```

---

## Disk Usage

```bash
df -h
```

---

## Running Processes

```bash
top
```

or

```bash
htop
```

---

## Running Services

```bash
systemctl --type=service
```

---

# ⚔ Kali Linux Commands

## Verify Nmap

```bash
nmap --version
```

---

## Verify Hydra

```bash
hydra -h
```

---

## Verify Nikto

```bash
nikto -Version
```

---

## Verify Metasploit

```bash
msfconsole --version
```

---

## Update Kali

```bash
sudo apt update
sudo apt upgrade -y
```

---

# 🚨 Troubleshooting Commands

## Verify Listening Ports

```bash
sudo ss -tulnp
```

---

## Verify Internet

```bash
ping google.com
```

---

## Check OOM Messages

```bash
dmesg | grep -i "killed process"
```

---

## View Service Logs

```bash
sudo journalctl -u <service-name>
```

---

## Restart All Wazuh Services

```bash
sudo systemctl restart wazuh-manager
sudo systemctl restart wazuh-indexer
sudo systemctl restart wazuh-dashboard
```

---

# 📋 Deployment Verification Commands

## Verify Server IP

```bash
hostname -I
```

---

## Verify Wazuh Services

```bash
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard
```

---

## Verify Registered Agents

```bash
sudo /var/ossec/bin/agent_control -l
```

---

## Verify Dashboard

Open

```text
https://<SERVER-IP>
```

Example

```text
https://10.0.2.4
```

---

# 📌 Summary

This reference consolidates the most frequently used commands required to deploy, verify, administer, and troubleshoot the OpenSOC-Lab environment.

Administrators can use this guide as a quick reference during installation, maintenance, and future lab expansion.

---

# 🎓 Learning Outcomes

After completing this deployment guide, you should be able to:

- Deploy the OpenSOC-Lab environment from scratch.
- Configure VirtualBox networking.
- Install Ubuntu Server.
- Deploy the complete Wazuh platform.
- Configure the Wazuh Dashboard.
- Register Windows and Ubuntu agents.
- Configure Kali Linux for attack simulation.
- Troubleshoot common deployment issues.
- Use Linux and Wazuh administrative commands effectively.

---

# 🎉 Deployment Guide Completed

Congratulations!

You have successfully completed the deployment phase of **OpenSOC-Lab**.

The environment is now ready for:

- Attack Simulation
- Detection Engineering
- Threat Hunting
- Incident Response
- Digital Forensics (DFIR)
- Malware Analysis
- Active Response
- Blue Team Exercises

---

## ➡ Next Documentation

The next stage of the project focuses on documenting attack scenarios, detection rules, alert analysis, and incident response workflows generated within the OpenSOC-Lab environment.
