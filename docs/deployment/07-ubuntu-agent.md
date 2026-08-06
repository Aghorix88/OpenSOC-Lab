# 07. Ubuntu Agent Deployment

---

# 📖 Overview

The Wazuh Agent enables continuous monitoring of Linux endpoints by collecting security events, system logs, file integrity changes, vulnerability information, and system inventory data. Once connected to the Wazuh Manager, the Ubuntu endpoint becomes part of the centralized Security Operations Center (SOC) environment.

This chapter covers the complete deployment of the Wazuh Agent on an Ubuntu endpoint, including installation, registration, service verification, connectivity testing, and troubleshooting.

---

| Information | Details |
|-------------|---------|
| **Document** | 07-ubuntu-agent.md |
| **Version** | v1.0 |
| **Difficulty** | Beginner |
| **Estimated Time** | 20–30 Minutes |
| **Related Screenshots** | `images/deployment/ubuntu-agent/` |

---

# 🎯 Objectives

After completing this chapter, you will be able to:

- Install the Wazuh Agent on Ubuntu.
- Register the endpoint with the Wazuh Manager.
- Configure the Manager IP address.
- Start and enable the Wazuh Agent service.
- Verify successful communication with the Wazuh Manager.
- Confirm that the Ubuntu endpoint appears in the Wazuh Dashboard.

---

# 📋 Prerequisites

Before continuing, ensure that:

- Wazuh Manager is installed and operational.
- Ubuntu Desktop virtual machine is running.
- Both Ubuntu Server and Ubuntu Desktop are connected to the same NAT Network.
- Internet connectivity is available.
- SSH access is available (optional).

---

# 🌐 Verify Network Connectivity

Determine the IP address of the Wazuh Manager.

```bash
hostname -I
```

Example

```text
10.0.2.4
```

From the Ubuntu endpoint, verify connectivity.

```bash
ping -c 4 10.0.2.4
```

Expected Output

```text
64 bytes from 10.0.2.4
```

---

# 🔄 Update the Ubuntu Endpoint

Update the package repository.

```bash
sudo apt update
```

Upgrade installed packages.

```bash
sudo apt upgrade -y
```

Remove unused packages.

```bash
sudo apt autoremove -y
```

---

# 📥 Install the Wazuh Agent

Download and install the Wazuh Agent package.

```bash
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo gpg --dearmor -o /usr/share/keyrings/wazuh.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
```

Update the repository.

```bash
sudo apt update
```

Install the agent.

```bash
sudo WAZUH_MANAGER="10.0.2.4" apt install wazuh-agent -y
```

> **Note**
>
> Replace `10.0.2.4` with the IP address of your Wazuh Manager if different.

---

# ⚙ Configure the Wazuh Agent

Verify the Manager IP address.

```bash
sudo nano /var/ossec/etc/ossec.conf
```

Locate the following section.

```xml
<server>
    <address>10.0.2.4</address>
</server>
```

Ensure that the Manager IP address is correct.

Save the configuration.

---

# ▶ Start the Agent Service

Enable the service.

```bash
sudo systemctl enable wazuh-agent
```

Start the service.

```bash
sudo systemctl start wazuh-agent
```

Verify its status.

```bash
sudo systemctl status wazuh-agent
```

Expected Output

```text
Active: active (running)
```

---

# 🔍 Verify Agent Registration

On the Wazuh Server.

```bash
sudo /var/ossec/bin/agent_control -l
```

Expected Output

```text
ID    Name            IP Address
002   ubuntu-victim   xxx.xxx.xxx.xxx
```

---

# 📊 Verify in the Wazuh Dashboard

Navigate to:

```
Endpoints
↓

Agents
```

Verify that:

- Ubuntu endpoint appears.
- Status is **Active**.
- Last Keep Alive updates regularly.
- Operating System is detected correctly.

---

# 🧪 Generate Test Activity

Generate simple Linux activity.

```bash
sudo apt update
```

```bash
sudo ls /root
```

```bash
cat /etc/passwd
```

```bash
whoami
```

Return to the Dashboard.

Navigate to:

```
Security Events
```

Verify that Linux events are being collected.

---

# ✅ Deployment Verification Checklist

Before proceeding, verify:

- [ ] Ubuntu Agent Installed
- [ ] Manager IP Configured
- [ ] Agent Service Running
- [ ] Agent Registered
- [ ] Dashboard Status Active
- [ ] Security Events Received
- [ ] Endpoint Successfully Onboarded

---

# 📸 Screenshot References

Store screenshots in:

```text
images/
└── deployment/
      └── ubuntu-agent/
```

Recommended screenshots.

| Figure | Screenshot | Filename |
|---------|------------|----------|
| Figure 7.1 | Ubuntu Agent Installation | ubuntu-agent-install.png |
| Figure 7.2 | Agent Service Running | ubuntu-agent-service.png |
| Figure 7.3 | Agent Registration | ubuntu-agent-registration.png |
| Figure 7.4 | Ubuntu Endpoint Active | ubuntu-agent-dashboard.png |
| Figure 7.5 | Linux Security Events | ubuntu-security-events.png |

---

# 🛠 Common Issues

## Agent Not Appearing in Dashboard

### Symptoms

The Ubuntu endpoint does not appear in the Wazuh Dashboard.

### Resolution

Verify the service.

```bash
sudo systemctl status wazuh-agent
```

Restart the service.

```bash
sudo systemctl restart wazuh-agent
```

Verify network connectivity.

```bash
ping -c 4 10.0.2.4
```

---

## Agent Status Shows Disconnected

### Symptoms

The endpoint appears but remains disconnected.

### Resolution

Verify the Manager IP address.

```bash
sudo nano /var/ossec/etc/ossec.conf
```

Restart the service.

```bash
sudo systemctl restart wazuh-agent
```

---

## Linux Logs Not Appearing

### Symptoms

The agent is active, but expected Linux activity is not visible in the Dashboard.

### Possible Causes

- Log sources are not configured.
- Syscheck has not completed its first scan.
- Test activity does not generate monitored events.
- Dashboard filters exclude the events.

### Resolution

Verify the agent log.

```bash
sudo tail -f /var/ossec/logs/ossec.log
```

Force Syscheck.

```bash
sudo systemctl restart wazuh-agent
```

Generate additional activity such as:

```bash
sudo apt update
```

```bash
sudo cat /etc/shadow
```

Verify that events appear under **Security Events** in the Dashboard.

> **Deployment Note**
>
> During the OpenSOC-Lab deployment, the Ubuntu Agent successfully connected to the Wazuh Manager before all expected Linux events became visible. Additional log collection configuration and monitored activity were required to generate meaningful events.

---

# 📌 Summary

The Ubuntu endpoint has now been successfully integrated into the OpenSOC-Lab environment.

Completed tasks:

- Wazuh Agent installed.
- Manager communication established.
- Agent service verified.
- Ubuntu endpoint visible in the Dashboard.
- Linux security event collection validated.

The Ubuntu endpoint is now actively monitored by the Wazuh platform.

---

# 🎓 Learning Outcomes

After completing this chapter, you should be able to:

- Deploy the Wazuh Agent on Ubuntu.
- Configure Manager communication.
- Verify agent registration.
- Troubleshoot Linux agent issues.
- Confirm endpoint monitoring through the Dashboard.

---

## ➡️ Next Guide

**08-kali-attacker.md**

In the next chapter, you will configure the Kali Linux attacker machine used to simulate reconnaissance, exploitation, and post-exploitation activities for testing Wazuh detections within the OpenSOC-Lab environment.
