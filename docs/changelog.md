# 📜 OpenSOC-Lab Changelog

All notable changes to this project will be documented in this file.

This project follows the principles of **Keep a Changelog** and **Semantic Versioning**.

---

# 🚀 v0.6 — OpenSOC-Lab Core Infrastructure Complete

**Release Date:** 04 August 2026

---

## 🎉 Added

### Infrastructure

- Ubuntu SOC Server
- Wazuh Manager 4.12
- Wazuh Dashboard
- Wazuh Indexer
- Oracle VirtualBox Lab Environment
- VirtualBox NAT Network

### Endpoint Monitoring

- Windows 11 Endpoint
- Ubuntu Endpoint
- Wazuh Windows Agent
- Wazuh Ubuntu Agent
- Multi-endpoint monitoring

### Documentation

- Complete Architecture Documentation
- Deployment Guides
- Troubleshooting Documentation
- Detection Engineering Structure
- Incident Response Documentation Structure
- Threat Hunting Documentation Structure
- MITRE ATT&CK Documentation Structure

### Architecture

Created six professional architecture diagrams:

- OpenSOC-Lab Architecture
- Network Topology
- Data Flow
- Wazuh Components
- Virtual Machine Layout
- Attack & Detection Flow

---

## 🔧 Fixed

- Wazuh Agent version compatibility
- Ubuntu repository configuration
- GPG key installation
- Package version pinning
- Ubuntu agent authentication
- Multi-endpoint registration
- Agent enrollment issues
- Dashboard synchronization
- Documentation consistency

---

## 🛡️ Infrastructure

| Component | Status |
|-----------|--------|
| Ubuntu SOC Server | ✅ Running |
| Wazuh Manager | ✅ Running |
| Wazuh Dashboard | ✅ Running |
| Wazuh Indexer | ✅ Running |
| Windows Endpoint | ✅ Connected |
| Ubuntu Endpoint | ✅ Connected |
| Multi-Endpoint Monitoring | ✅ Operational |

---

## 📊 Current Capabilities

- Centralized Log Collection
- Windows Monitoring
- Linux Monitoring
- Endpoint Visibility
- Dashboard Monitoring
- Agent Management
- OpenSearch Indexing

---

## 🎯 Next Release (v0.7)

- Detection Engineering
- Attack Simulation
- Alert Investigation
- MITRE ATT&CK Mapping
- Nmap Detection
- Hydra Detection
- File Integrity Monitoring
- Custom Detection Rules

---

# 🖥️ v0.4 — First Windows Endpoint Connected

**Release Date:** 01 August 2026

---

## 🎉 Added

- Windows 11 endpoint deployment
- Wazuh Windows Agent v4.12
- First endpoint connected to Wazuh Manager
- Secure agent-manager communication
- Real-time endpoint monitoring

---

## 🔧 Fixed

- Duplicate agent registration
- Authentication key mismatch
- Agent ID conflicts
- Agent communication verification

---

## 🛡️ Infrastructure

- Ubuntu Server 24.04 LTS
- Oracle VirtualBox
- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer
- Windows 11 Endpoint
- NAT Network

---

## 📊 Status

- ✅ Wazuh Manager Running
- ✅ Wazuh Dashboard Running
- ✅ Wazuh Indexer Running
- ✅ Windows Agent Connected

---

# 🚀 v0.3 — Wazuh Core Operational

**Release Date:** 31 July 2026

---

## 🎉 Added

- Initial GitHub repository
- Documentation structure
- Deployment documentation
- Troubleshooting documentation
- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer

---

## 🔧 Fixed

### Wazuh Indexer Memory Issue

**Problem**

```
Wazuh dashboard server is not ready yet
```

**Root Cause**

Linux Out Of Memory (OOM) Killer terminated the Wazuh Indexer.

**Resolution**

- Increased VM RAM from 4 GB to 8 GB
- Restarted Wazuh services
- Verified port 9200
- Confirmed dashboard accessibility

---

## 🛡️ Infrastructure

- Ubuntu Server 24.04 LTS
- Oracle VirtualBox
- NAT Network
- 8 GB RAM
- 5 vCPU

---

## 📊 Status

- ✅ Wazuh Manager Running
- ✅ Wazuh Dashboard Running
- ✅ Wazuh Indexer Running
- ✅ Dashboard Accessible
