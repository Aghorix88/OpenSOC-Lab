# 10. Troubleshooting Guide

---

# 📖 Overview

During the deployment of OpenSOC-Lab, several configuration, networking, and service-related issues were encountered. This chapter documents the most common deployment problems, explains their root causes, and provides practical solutions based on the actual implementation of this project.

Use this guide whenever the deployment does not behave as expected.

---

| Information | Details |
|-------------|---------|
| **Document** | 10-troubleshooting.md |
| **Version** | v1.0 |
| **Difficulty** | Intermediate |
| **Estimated Time** | Reference Guide |
| **Related Screenshots** | `images/troubleshooting/` |

---

# 🎯 Objectives

After reading this guide, you will be able to:

- Diagnose common Wazuh deployment problems.
- Verify service health.
- Resolve networking issues.
- Restore disconnected agents.
- Troubleshoot Dashboard failures.
- Investigate service logs.
- Recover from common deployment errors.

---

# 🛠 Troubleshooting Workflow

Whenever an issue occurs, follow this workflow.

```text
Problem Identified
        │
        ▼
Read Error Message
        │
        ▼
Check Service Status
        │
        ▼
Review System Logs
        │
        ▼
Identify Root Cause
        │
        ▼
Apply Resolution
        │
        ▼
Verify Fix
```

---

# Issue 1 — Wazuh Dashboard Server is Not Ready Yet

## Symptoms

The browser displays

```text
Wazuh dashboard server is not ready yet
```

---

## Root Cause

The Wazuh Dashboard depends on the Wazuh Indexer.

If the Indexer fails to start, the Dashboard cannot initialize.

---

## Diagnosis

Check the Dashboard.

```bash
sudo systemctl status wazuh-dashboard
```

Check the Indexer.

```bash
sudo systemctl status wazuh-indexer
```

Review logs.

```bash
sudo journalctl -u wazuh-indexer
```

---

## Resolution

Restart the services.

```bash
sudo systemctl restart wazuh-indexer
```

```bash
sudo systemctl restart wazuh-dashboard
```

If the problem persists, check available memory.

```bash
free -h
```

---

# Issue 2 — Linux Out Of Memory (OOM) Killer

## Symptoms

- Dashboard unavailable
- Indexer stops
- Java process terminated

---

## Diagnosis

Check kernel messages.

```bash
dmesg | grep -i "killed process"
```

Example

```text
Out of memory:
Killed process xxxx (java)
```

---

## Root Cause

Insufficient RAM allocated to the virtual machine.

---

## Resolution

Shutdown the virtual machine.

Increase RAM in VirtualBox.

Recommended:

| VM | RAM |
|-----|------|
| Wazuh Server | 8 GB or Higher |

Restart.

```bash
sudo systemctl restart wazuh-indexer
```

```bash
sudo systemctl restart wazuh-dashboard
```

Verify.

```bash
sudo systemctl status wazuh-indexer
```

---

# Issue 3 — Agent Not Appearing in Dashboard

## Symptoms

The endpoint does not appear under

```
Endpoints → Agents
```

---

## Diagnosis

Server

```bash
sudo /var/ossec/bin/agent_control -l
```

Windows

Verify

```
Wazuh Agent
```

service.

Ubuntu

```bash
sudo systemctl status wazuh-agent
```

---

## Resolution

Restart the agent.

Ubuntu

```bash
sudo systemctl restart wazuh-agent
```

Windows

```cmd
net stop WazuhSvc
net start WazuhSvc
```

---

# Issue 4 — Agent Shows Disconnected

## Symptoms

Agent exists.

Status remains

```
Disconnected
```

---

## Resolution

Verify

- Manager IP
- Firewall
- Service

Restart the service.

---

# Issue 5 — Ubuntu Agent Connected but No Logs

## Symptoms

Ubuntu Agent

Status

```
Active
```

No events visible.

---

## Diagnosis

Agent log.

```bash
sudo tail -f /var/ossec/logs/ossec.log
```

Generate activity.

```bash
sudo apt update
```

```bash
sudo ls /root
```

---

## Resolution

Restart the agent.

```bash
sudo systemctl restart wazuh-agent
```

Generate additional monitored activity.

Verify Security Events.

---

# Issue 6 — Windows Agent Installed but No Events

## Resolution

Restart service.

```cmd
net stop WazuhSvc
```

```cmd
net start WazuhSvc
```

Verify Windows Event Logs are enabled.

---

# Issue 7 — Virtual Machines Cannot Communicate

## Symptoms

Ping fails.

---

## Diagnosis

Ubuntu

```bash
hostname -I
```

Windows

```cmd
ipconfig
```

---

## Resolution

Verify

- Same NAT Network
- Correct Adapter
- VM Powered On

---

# Issue 8 — No Internet Access

## Diagnosis

Ubuntu

```bash
ping google.com
```

Windows

```cmd
ping google.com
```

---

## Resolution

Verify

- NAT Network
- Host Internet
- DNS

---

# Issue 9 — Dashboard Cannot Be Accessed

Verify.

```bash
sudo systemctl status wazuh-dashboard
```

Verify listening ports.

```bash
sudo ss -tulnp
```

Verify IP.

```bash
hostname -I
```

---

# Issue 10 — Service Failed to Start

Check

```bash
sudo systemctl status <service-name>
```

Example

```bash
sudo systemctl status wazuh-manager
```

Logs

```bash
sudo journalctl -u wazuh-manager
```

---

# Useful Diagnostic Commands

## System Resources

```bash
free -h
```

```bash
df -h
```

```bash
lscpu
```

---

## Networking

```bash
hostname -I
```

```bash
ip addr
```

```bash
ss -tulnp
```

```bash
ping
```

---

## Services

```bash
sudo systemctl status wazuh-manager
```

```bash
sudo systemctl status wazuh-dashboard
```

```bash
sudo systemctl status wazuh-indexer
```

```bash
sudo systemctl status wazuh-agent
```

---

## Logs

```bash
sudo journalctl -xe
```

```bash
sudo journalctl -u wazuh-indexer
```

```bash
sudo journalctl -u wazuh-dashboard
```

```bash
sudo tail -f /var/ossec/logs/ossec.log
```

---

# 📸 Screenshot References

```text
images/
└── troubleshooting/
```

Recommended screenshots

| Figure | Screenshot |
|----------|-----------------------------|
| 10.1 | Dashboard Error |
| 10.2 | OOM Killer Log |
| 10.3 | Service Status |
| 10.4 | Agent Disconnected |
| 10.5 | Network Failure |
| 10.6 | Successful Resolution |

---

# 📌 Summary

This troubleshooting guide documents the real deployment challenges encountered while building OpenSOC-Lab.

Following the diagnostic procedures in this chapter enables administrators to identify, isolate, and resolve the majority of deployment issues without rebuilding the environment.

---

# 🎓 Learning Outcomes

After completing this chapter you should be able to

- Diagnose deployment failures.
- Investigate Linux services.
- Read system logs.
- Recover disconnected agents.
- Resolve Dashboard failures.
- Troubleshoot networking problems.
- Identify Out Of Memory issues.

---

## ➡️ Next Guide

**11-commands-reference.md**

The final chapter provides a categorized reference of all important Linux, Wazuh, networking, and troubleshooting commands used throughout the OpenSOC-Lab deployment.
