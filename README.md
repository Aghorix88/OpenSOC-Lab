# 🛡️ OpenSOC-Lab

![Status](https://img.shields.io/badge/Status-Active%20Development-success)
![Version](https://img.shields.io/badge/Release-v0.6-blue)
![Wazuh](https://img.shields.io/badge/Wazuh-4.12-blueviolet)
![Platform](https://img.shields.io/badge/Platform-VirtualBox-orange)
![License](https://img.shields.io/badge/License-MIT-green)
![Focus](https://img.shields.io/badge/Focus-Blue%20Team-red)

> **Learn. Detect. Investigate. Respond. Improve.**

An enterprise-inspired open-source **Security Operations Center (SOC)** home lab built to develop practical Blue Team skills using **Wazuh SIEM**. OpenSOC-Lab simulates a real-world SOC environment for security monitoring, attack detection, incident response, threat hunting, and digital forensics.

---

# 📖 Project Overview

OpenSOC-Lab is a self-hosted SOC environment running inside **Oracle VirtualBox**.

The project is designed to simulate a real-world enterprise SOC where security analysts monitor endpoints, investigate alerts, detect attacks, perform incident response, and continuously improve security posture using open-source technologies.

Current virtual machines:

- 🖥️ Ubuntu SOC Server (Wazuh Manager, Indexer & Dashboard)
- 💻 Windows 11 Endpoint (Wazuh Agent)
- 🐧 Ubuntu Endpoint (Wazuh Agent)
- ⚔️ Kali Linux (Attack Simulation)

The objective is to create a professional Blue Team portfolio project while gaining practical SOC experience.

---

# ✨ Features

- Enterprise-inspired SOC architecture
- Multi-endpoint monitoring
- Windows & Linux endpoint visibility
- Centralized log collection
- Security event monitoring
- Detection Engineering
- Threat Hunting
- Incident Response
- MITRE ATT&CK Mapping
- Attack Simulation
- Future ELK Stack Integration

---

# 🎯 Mission

Develop a production-inspired Security Operations Center using open-source technologies to gain hands-on experience in:

- Security Monitoring
- Detection Engineering
- Threat Hunting
- Incident Response
- Digital Forensics (DFIR)
- Threat Intelligence
- Security Automation

---
# 🎯 Project Philosophy

OpenSOC-Lab is not intended to be just another Wazuh installation guide.

The project is being developed as a production-inspired Blue Team laboratory where every deployed component is actively used to simulate attacks, generate telemetry, engineer detections, investigate security events, perform threat hunting, and document incident response activities.

Each phase of development emphasizes understanding the technology, validating detections, and continuously improving defensive capabilities rather than simply deploying infrastructure.
# 🌟 Vision

Bridge the gap between academic learning and real-world SOC operations by building a fully documented, enterprise-inspired Blue Team laboratory.

---

# 🎓 Learning Objectives

- Security Operations Center (SOC)
- SIEM Engineering
- Detection Engineering
- Threat Hunting
- Incident Response
- Malware Detection
- Digital Forensics (DFIR)
- Threat Intelligence
- Active Response
- Blue Team Operations
- BTL1 Preparation

---

# 🏗️ Architecture

The complete OpenSOC-Lab architecture is available inside:

```text
images/architecture/
```

Architecture includes:

- OpenSOC-Lab Architecture
- Network Topology
- Data Flow
- Wazuh Components
- Virtual Machine Layout
- Attack & Detection Flow

---

# 🛠️ Technology Stack

| Category | Technology |
|-----------|------------|
| Virtualization | Oracle VirtualBox |
| Operating Systems | Ubuntu Server 22.04 LTS, Ubuntu Desktop 26.04 LTS, Windows 11, Kali Linux |
| SIEM | Wazuh 4.12 |
| Search Engine | OpenSearch |
| Dashboard | Wazuh Dashboard |
| Endpoint Monitoring | Wazuh Agents |
| Networking | VirtualBox NAT Network |
| Attack Platform | Kali Linux |

---

# 🚀 Future Roadmap (Phase 2)

The following technologies will be integrated as OpenSOC-Lab evolves.

| Category | Technology |
|-----------|------------|
| Log Analytics | Elasticsearch |
| Log Pipeline | Logstash |
| Visualization | Kibana |
| IDS | Suricata |
| Network Monitoring | Zeek |
| Endpoint Telemetry | Sysmon |
| Linux Auditing | Auditd |
| Vulnerability Management | OpenVAS |
| Threat Intelligence | MISP |
| DFIR | Velociraptor |
| Memory Analysis | Volatility 3 |
| Digital Forensics | Autopsy |
| Detection Rules | Sigma |
| Malware Detection | YARA |
| SOAR | Shuffle |

---

# 📂 Repository Structure

```text
OpenSOC-Lab
│
├── assets/
│
├── docs/
│   ├── architecture/
│   ├── deployment/
│   ├── detections/
│   ├── incident-response/
│   ├── mitre/
│   ├── threat-hunting/
│   ├── troubleshooting/
│   ├── README.md
│   └── changelog.md
│
├── images/
│   ├── agents/
│   ├── alerts/
│   ├── architecture/
│   ├── attacks/
│   ├── dashboard/
│   ├── deployment/
│   ├── detections/
│   ├── investigation/
│   ├── mitre/
│   ├── troubleshooting/
│   └── README.md
│
├── LICENSE
└── README.md
```

---

# 📊 Project Progress

| Milestone | Status |
|------------|---------|
| Repository Setup | ✅ Completed |
| Documentation | ✅ Completed |
| Architecture Design | ✅ Completed |
| Virtual Network Setup | ✅ Completed |
| Wazuh Deployment | ✅ Completed |
| Windows Agent Integration | ✅ Completed |
| Ubuntu Agent Integration | ✅ Completed |
| Multi-Endpoint Monitoring | ✅ Completed |
| Detection Engineering | 🚧 In Progress |
| Attack Simulation | ⏳ Pending |
| Threat Hunting | ⏳ Pending |
| Incident Response | ⏳ Pending |
| Digital Forensics | ⏳ Pending |
| ELK Stack Integration (Phase 2) | 📅 Planned |

---

# 🚀 Current Release

## **v0.6 — OpenSOC-Lab Core Infrastructure Complete**

### Successfully implemented

- ✅ Ubuntu SOC Server
- ✅ Wazuh Manager
- ✅ Wazuh Indexer
- ✅ Wazuh Dashboard
- ✅ Windows Agent
- ✅ Ubuntu Agent
- ✅ Multi-Endpoint Monitoring
- ✅ Virtual Network
- ✅ Architecture Documentation
- ✅ Deployment Documentation

### Current capabilities

- Centralized Log Collection
- Endpoint Monitoring
- Security Event Monitoring
- Dashboard Visualization
- Agent Management
- OpenSearch Indexing
- Windows & Linux Endpoint Visibility

---

# 📸 Documentation

The repository currently includes:

- Architecture Diagrams
- Deployment Documentation
- Agent Deployment
- Dashboard Screenshots
- Troubleshooting Guides
- Detection Engineering Structure
- MITRE ATT&CK Documentation
- Threat Hunting Documentation
- Incident Response Documentation

---

# 🗺️ Roadmap

## ✅ Phase 1 — Infrastructure

- Virtual Environment
- Wazuh Deployment
- Windows Agent
- Ubuntu Agent
- Documentation

## 🚧 Phase 2 — Detection Engineering

- Attack Simulation
- Wazuh Alert Analysis
- Detection Rules
- Custom Rules
- MITRE ATT&CK Mapping

## ⏳ Phase 3 — Threat Hunting

- IOC Hunting
- Log Analysis
- Lateral Movement Detection
- Behavioral Analysis

## ⏳ Phase 4 — Incident Response

- Investigation
- Containment
- Eradication
- Recovery

## 📅 Phase 5 — ELK Stack Integration

- Elasticsearch
- Logstash
- Kibana
- Advanced Analytics
- Threat Intelligence Dashboards

---

# 🎯 Upcoming Attack Simulations

The next phase of OpenSOC-Lab includes:

- Nmap Scanning
- Hydra Brute Force
- Nikto Web Scanning
- Metasploit Exploitation
- File Integrity Monitoring
- Linux Audit Events
- Windows Security Events
- Sysmon Telemetry
- Malware Detection
- Custom Detection Rules
- Active Response

---

# 🤝 Contributing

This project is currently under active development.

Suggestions, improvements, and contributions are always welcome.

---

# 📜 License

This project is licensed under the **MIT License**.

---

# ⭐ Support the Project

If you find this project useful or interesting, consider giving it a ⭐ on GitHub.

It motivates continued development and helps others discover the project.

---

> **OpenSOC-Lab** is a continuously evolving Blue Team home lab focused on practical Security Operations, Detection Engineering, Threat Hunting, Incident Response, and Digital Forensics using enterprise-inspired open-source technologies.
