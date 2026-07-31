# OpenSOC-Lab Changelog

All notable changes to this project will be documented in this file.

The format is inspired by Keep a Changelog.

---

# v0.3 - Wazuh Core Operational

Release Date: 31 July 2026

## Added

- Project repository
- Documentation structure
- Deployment documentation
- Troubleshooting documentation
- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer

## Infrastructure

- Ubuntu Server 26.04
- Oracle VirtualBox
- NAT Network
- 8 GB RAM
- 5 vCPU

## Fixed

### Wazuh Indexer Memory Issue

Problem:

Dashboard displayed:

> Wazuh dashboard server is not ready yet

Root Cause:

Linux Out Of Memory (OOM) Killer terminated the Wazuh Indexer.

Resolution:

- Increased VM RAM from 4 GB to 8 GB
- Restarted services
- Verified port 9200
- Dashboard operational

## Current Status

✅ Wazuh Manager Running

✅ Wazuh Dashboard Running

✅ Wazuh Indexer Running

✅ Dashboard Accessible

---

## Next Release (v0.4)

Planned Features

- Windows 11 Endpoint
- Wazuh Agent
- Sysmon
- Endpoint Monitoring
- Live Alerts
- Initial Detection Rules
