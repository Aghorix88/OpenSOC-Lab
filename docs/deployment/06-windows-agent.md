# 06. Windows Agent Deployment

---

# 📖 Overview

The Wazuh Agent is responsible for collecting endpoint security events and forwarding them securely to the Wazuh Manager for analysis. Once installed, the agent enables centralized monitoring of Windows systems, including event logs, file integrity monitoring, vulnerability detection, and system inventory.

This chapter explains how to install, register, and verify the Wazuh Agent on a Windows endpoint.

---

| Information | Details |
|-------------|---------|
| **Document** | 06-windows-agent.md |
| **Version** | v1.0 |
| **Difficulty** | Beginner |
| **Estimated Time** | 20–30 Minutes |
| **Related Screenshots** | `images/deployment/windows-agent/` |

---

# 🎯 Objectives

After completing this chapter, you will be able to:

- Download the Wazuh Windows Agent.
- Install the agent.
- Register the endpoint with the Wazuh Manager.
- Start the Wazuh Agent service.
- Verify successful communication with the Manager.
- Confirm that the Windows endpoint appears in the Wazuh Dashboard.

---

# 📋 Prerequisites

Before continuing, ensure that:

- Wazuh Manager is installed and running.
- Wazuh Dashboard is accessible.
- Windows 11 virtual machine is operational.
- Windows endpoint can communicate with the Ubuntu Server.
- Both systems are connected to the same VirtualBox NAT Network.

---

# 🌐 Verify Network Connectivity

Determine the IP address of the Wazuh Server.

```bash
hostname -I
```

Example

```text
10.0.2.4
```

From the Windows endpoint, verify connectivity.

Open Command Prompt.

```cmd
ping 10.0.2.4
```

Expected Output

```text
Reply from 10.0.2.4
```

---

# 📥 Download the Wazuh Windows Agent

Download the latest compatible Wazuh Windows Agent from the official Wazuh website.

> **💡 Best Practice**
>
> Ensure that the Windows Agent version matches the Wazuh Manager version whenever possible to maintain compatibility.

---

# 💻 Install the Wazuh Agent

Run the installer with Administrator privileges.

During installation, provide the following information.

| Field | Value |
|--------|-------|
| Manager Address | Ubuntu Server IP Address |
| Agent Name | windows-victim |
| Agent Group | Default |

Complete the installation.

---

# ▶ Start the Wazuh Agent Service

Open Windows Services.

Locate:

```
Wazuh Agent
```

Verify that the service status is:

```text
Running
```

Alternatively, using Command Prompt (Administrator):

```cmd
sc query WazuhSvc
```

Expected Output

```text
STATE : RUNNING
```

---

# 🔍 Verify Agent Registration

On the Ubuntu Server, verify that the agent has been registered.

```bash
sudo /var/ossec/bin/agent_control -l
```

Expected Output

```text
ID    Name              IP Address
001   windows-victim    xxx.xxx.xxx.xxx
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

- Windows endpoint appears.
- Agent status is **Active**.
- Last Keep Alive is updating.
- Version information is displayed.
- Operating System is detected correctly.

---

# 🖥️ Verify Windows Event Collection

Generate normal Windows activity.

Examples:

- Open File Explorer.
- Launch Notepad.
- Log out and log back in.
- Open Windows Security.

Return to the Wazuh Dashboard.

Navigate to:

```
Security Events
```

Verify that Windows events are being collected.

---

# ✅ Deployment Verification Checklist

Before proceeding, verify:

- [ ] Windows Agent Installed
- [ ] Service Running
- [ ] Agent Registered
- [ ] Agent Active
- [ ] Dashboard Communication Verified
- [ ] Windows Events Visible
- [ ] Endpoint Successfully Onboarded

---

# 📸 Screenshot References

Store screenshots in:

```text
images/
└── deployment/
      └── windows-agent/
```

Recommended screenshots.

| Figure | Screenshot | Filename |
|---------|------------|----------|
| Figure 6.1 | Windows Agent Installer | windows-agent-installer.png |
| Figure 6.2 | Installation Wizard | installation-wizard.png |
| Figure 6.3 | Wazuh Agent Service | wazuh-agent-service.png |
| Figure 6.4 | Agent Registration | agent-registration.png |
| Figure 6.5 | Active Agent in Dashboard | active-agent-dashboard.png |
| Figure 6.6 | Windows Security Events | windows-security-events.png |

---

# 🛠️ Common Issues

## Agent Does Not Appear in Dashboard

### Symptoms

The Windows endpoint is not listed under **Endpoints → Agents**.

### Resolution

Verify that:

- The Wazuh Agent service is running.
- The Manager IP address is correct.
- Network connectivity is available.
- Firewall rules allow communication.
- The endpoint can ping the Wazuh Server.

Restart the service if required.

```cmd
net stop WazuhSvc
net start WazuhSvc
```

---

## Agent Status Remains Disconnected

### Symptoms

The agent appears but remains **Disconnected**.

### Resolution

Verify communication with the Manager.

Check the Windows Agent log.

Default log location:

```text
C:\Program Files (x86)\ossec-agent\ossec.log
```

Restart the service.

```cmd
net stop WazuhSvc
net start WazuhSvc
```

---

## Incorrect Manager Address

### Symptoms

The agent cannot register.

### Resolution

Verify that the configured Manager IP address matches the Ubuntu Server IP address.

Update the configuration if necessary and restart the agent.

---

## Windows Firewall Blocking Communication

### Symptoms

The Windows Agent cannot connect to the Wazuh Manager.

### Resolution

Temporarily disable the firewall for testing or create an inbound/outbound rule allowing communication with the Wazuh Manager on the required ports.

---

# 📌 Summary

The Windows endpoint has now been successfully onboarded into the OpenSOC-Lab environment.

Completed tasks:

- Wazuh Windows Agent installed.
- Endpoint registered with the Wazuh Manager.
- Agent service verified.
- Dashboard communication confirmed.
- Windows security events collected successfully.

The Windows endpoint is now actively monitored by the Wazuh platform.

---

# 🎓 Learning Outcomes

After completing this chapter, you should be able to:

- Deploy the Wazuh Windows Agent.
- Register endpoints with the Wazuh Manager.
- Verify agent communication.
- Troubleshoot registration issues.
- Confirm successful log collection from Windows systems.

---

## ➡️ Next Guide

**07-ubuntu-agent.md**

The next chapter explains how to install and configure the Wazuh Agent on an Ubuntu endpoint, register it with the Wazuh Manager, and verify Linux log collection through the Wazuh Dashboard.
