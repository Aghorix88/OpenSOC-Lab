# OpenSOC-Lab Changelog

All notable changes to this project will be documented in this file.

The format is inspired by Keep a Changelog.

---

# v0.4 - First Windows Endpoint Connected

Release Date: 01 August 2026

## Added

- Windows 11 endpoint deployment
- Wazuh Windows Agent 4.12
- First endpoint successfully connected to Wazuh Manager
- Secure agent-manager communication established
- Real-time endpoint monitoring enabled

## Fixed

- Resolved duplicate agent registration
- Corrected authentication key mismatch
- Resolved agent ID conflicts
- Verified secure agent communication

## Infrastructure

- Ubuntu Server 24.04
- Oracle VirtualBox
- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer
- Windows 11 Endpoint
- NAT Network

## Current Status

✅ Wazuh Manager Running

✅ Wazuh Dashboard Running

✅ Wazuh Indexer Running

✅ Windows Agent Connected

✅ Endpoint Visible in Dashboard

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
