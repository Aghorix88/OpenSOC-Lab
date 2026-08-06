# 🚀 OpenSOC-Lab Deployment Guide

Welcome to the **OpenSOC-Lab Deployment Guide**.

This section contains the complete deployment documentation for building the OpenSOC-Lab environment from scratch. Every guide is based on the actual implementation of this project and includes the commands, configurations, verification steps, screenshots, and troubleshooting required to successfully reproduce the environment.

Whether you are a student, cybersecurity enthusiast, or Blue Team learner, this documentation is designed to help you deploy a fully functional Wazuh-based Security Operations Center (SOC) home lab.

---

# 📖 Deployment Objectives

The deployment documentation aims to:

- Build a complete Wazuh SIEM infrastructure.
- Configure multiple monitored endpoints.
- Establish secure communication between the Wazuh Manager and agents.
- Create an enterprise-inspired SOC home laboratory.
- Document every deployment step for reproducibility.
- Record real-world troubleshooting encountered during implementation.

---

# 🏗️ Deployment Workflow

The recommended deployment order is shown below.

```text
Host Machine Preparation
        │
        ▼
Oracle VirtualBox Setup
        │
        ▼
Ubuntu Server Installation
        │
        ▼
Wazuh Installation
        │
        ▼
Dashboard Configuration
        │
        ▼
Windows Agent Deployment
        │
        ▼
Ubuntu Agent Deployment
        │
        ▼
Kali Linux Configuration
        │
        ▼
Network Configuration
        │
        ▼
Deployment Verification
```

---

# 📂 Deployment Documentation

| Guide | Description | Status |
|--------|-------------|--------|
| 01. Host Machine Preparation | Prepare the host machine and enable virtualization | 🚧 |
| 02. Oracle VirtualBox Setup | Install Oracle VirtualBox and configure the lab environment | 🚧 |
| 03. Ubuntu Server Installation | Install Ubuntu Server for the SOC infrastructure | 🚧 |
| 04. Wazuh Installation | Install the Wazuh Manager, Indexer, and Dashboard | 🚧 |
| 05. Dashboard Configuration | Verify services and configure the Wazuh Dashboard | 🚧 |
| 06. Windows Agent Deployment | Install and register the Windows endpoint | 🚧 |
| 07. Ubuntu Agent Deployment | Install and register the Ubuntu endpoint | 🚧 |
| 08. Kali Linux Configuration | Configure the attacker machine | 🚧 |
| 09. Network Configuration | Configure networking and verify connectivity | 🚧 |
| 10. Troubleshooting | Common deployment issues and their resolutions | 🚧 |
| 11. Commands Reference | Frequently used deployment commands | 🚧 |

---

# 🖥️ Lab Environment

The deployment documented in this repository was performed using the following virtual machines.

| Virtual Machine | Purpose |
|-----------------|---------|
| Ubuntu Server | Wazuh Manager, Indexer & Dashboard |
| Windows 11 | Monitored Endpoint |
| Ubuntu Desktop | Monitored Endpoint |
| Kali Linux | Attack Simulation |

---

# 📌 Documentation Standards

Every deployment guide follows a consistent structure to make the installation process easy to understand and reproduce.

Each guide contains:

- Overview
- Objectives
- Prerequisites
- Step-by-Step Procedure
- Command Explanations
- Verification Steps
- Expected Results
- Screenshots
- Common Issues
- Troubleshooting
- Summary

---

# ⚠️ Troubleshooting

Unlike many installation guides, this documentation includes real deployment issues encountered during implementation, including:

- Wazuh Indexer memory issues
- Dashboard startup failures
- Agent registration problems
- Authentication key mismatches
- Duplicate agent registration
- Ubuntu agent communication issues
- Service startup verification
- SSH authentication testing
- Network connectivity verification

Each issue is documented together with its root cause and resolution.

---

# 🎯 Expected Result

After completing every deployment guide, the lab should include:

- ✅ Ubuntu Server running Wazuh
- ✅ Wazuh Manager operational
- ✅ Wazuh Indexer operational
- ✅ Wazuh Dashboard accessible
- ✅ Windows endpoint connected
- ✅ Ubuntu endpoint connected
- ✅ Kali Linux configured for attack simulation
- ✅ Functional communication between all virtual machines

The environment will then be ready for attack simulation, threat hunting, detection engineering, and incident response exercises.

---

## 📖 Next Step

Continue with:

**01-host-machine-preparation.md**
