# 🛡️ OpenSOC-Lab

> **Learn. Detect. Investigate. Respond. Improve.**

An enterprise-inspired open-source **Security Operations Center (SOC)** home lab built to develop practical Blue Team skills using **Wazuh SIEM**. OpenSOC-Lab simulates a real-world SOC environment for security monitoring, attack detection, incident response, threat hunting, and digital forensics.

---

# 📖 Project Overview

OpenSOC-Lab is a self-hosted SOC environment running inside **Oracle VirtualBox**. It consists of multiple virtual machines communicating over a private network where attacks can be safely simulated and detected.

The lab currently includes:

- Ubuntu Server (Wazuh Manager, Indexer & Dashboard)
- Windows 11 Endpoint (Wazuh Agent)
- Ubuntu Endpoint (Wazuh Agent)
- Kali Linux (Attacker Machine)

The objective is to build a practical portfolio project that demonstrates enterprise SOC workflows using open-source technologies.

---

# 🎯 Mission

Develop a production-inspired Security Operations Center using open-source tools to gain hands-on experience in:

- Security Monitoring
- Detection Engineering
- Threat Hunting
- Incident Response
- Digital Forensics (DFIR)
- Threat Intelligence
- Security Automation

---

# 🌟 Vision

Bridge the gap between academic learning and real-world SOC operations by building a fully documented, continuously evolving Blue Team laboratory.

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

# 🛠️ Technology Stack (Current)

| Category | Technology |
|-----------|------------|
| Virtualization | Oracle VirtualBox |
| Operating Systems | Ubuntu Server 22.04 LTS, Ubuntu Desktop 22.04 LTS, Windows 11, Kali Linux |
| SIEM | Wazuh 4.12 |
| Search Engine | OpenSearch |
| Dashboard | Wazuh Dashboard |
| Endpoint Monitoring | Wazuh Agents |
| Networking | VirtualBox NAT Network |
| Attack Simulation | Kali Linux |

---

# 🚀 Future Roadmap (Phase 2)

The following technologies will be integrated as OpenSOC-Lab evolves:

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
| Forensics | Autopsy |
| Detection Rules | Sigma |
| Malware Detection | YARA |
| SOAR | Shuffle |

---

# 🏗️ Lab Architecture

The complete architecture documentation is available in:

```
images/architecture/
```

Includes:

- OpenSOC-Lab Architecture
- Network Topology
- Data Flow
- Wazuh Components
- VM Layout
- Attack & Detection Flow

---

# 📂 Repository Structure

```text
OpenSOC-Lab
│
├── assets/
├── docs/
├── images/
│   ├── architecture/
│   ├── deployment/
│   ├── dashboard/
│   ├── agents/
│   ├── alerts/
│   └── troubleshooting/
│
├── scripts/
├── rules/
├── tools/
└── README.md
```

---

# 📊 Current Project Status

| Milestone | Status |
|------------|---------|
| Repository Setup | ✅ Completed |
| Project Documentation | ✅ Completed |
| Architecture Diagrams | ✅ Completed |
| Virtual Lab Setup | ✅ Completed |
| Wazuh Installation | ✅ Completed |
| Wazuh Dashboard | ✅ Completed |
| Windows Agent Deployment | ✅ Completed |
| Ubuntu Agent Deployment | 🔄 In Progress |
| Dashboard Documentation | 🔄 In Progress |
| Attack Simulations | ⏳ Pending |
| Detection Rules | ⏳ Pending |
| Active Response | ⏳ Pending |
| Threat Hunting | ⏳ Pending |
| Digital Forensics | ⏳ Pending |
| ELK Integration (Phase 2) | 📅 Planned |

---

# 🚀 Current Release

## **v0.5 — Wazuh Infrastructure Operational**

Successfully implemented:

- ✅ Ubuntu SOC Server
- ✅ Wazuh Manager
- ✅ Wazuh Indexer
- ✅ Wazuh Dashboard
- ✅ Windows Agent
- ✅ Virtual Network
- ✅ Architecture Documentation
- ✅ Deployment Documentation

Current capabilities:

- Centralized Log Collection
- Endpoint Monitoring
- Security Event Monitoring
- Dashboard Visualization
- Agent Management
- OpenSearch Indexing

---

# 📸 Documentation

The repository includes:

- Architecture Diagrams
- Deployment Screenshots
- Dashboard Screenshots
- Agent Configuration
- Troubleshooting Guide
- Future Roadmap

---

# 🎯 Upcoming Features

The next milestones include:

- Attack Simulations (Nmap, Hydra, Nikto, Metasploit)
- Detection Engineering
- Custom Wazuh Rules
- MITRE ATT&CK Mapping
- Alert Analysis
- Incident Response Playbooks
- Threat Hunting Scenarios
- Active Response
- ELK Stack Integration
- Blue Team Exercises

---

# 🤝 Contributing

This project is currently under active development.

Suggestions, ideas, and contributions are always welcome.

---

# 📜 License

This project is licensed under the **MIT License**.

---

## ⭐ If you found this project useful, consider giving it a Star.

**OpenSOC-Lab** is being built as a long-term learning project to demonstrate practical SOC, Blue Team, Detection Engineering, and Incident Response skills using enterprise-inspired open-source technologies.
