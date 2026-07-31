# Wazuh Installation

## Overview

This document describes the deployment of the Wazuh All-in-One Security Information and Event Management (SIEM) platform for OpenSOC-Lab.

The deployment includes:

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard

---

## Objective

Deploy a fully functional enterprise-style open-source SIEM that will serve as the central monitoring platform for OpenSOC-Lab.

---

## Lab Environment

| Component | Specification |
|------------|--------------|
| Host OS | Windows 11 |
| Hypervisor | Oracle VirtualBox |
| VM Name | soc-server |
| Operating System | Ubuntu Server 26.04 LTS |
| CPU | 5 vCPU |
| Memory | 8 GB |
| Disk | 40 GB |
| Network | NAT Network |

---

## Pre-deployment Checklist

- Ubuntu Server installed
- Internet connectivity verified
- System updated
- Time synchronization verified
- VM snapshot created

---

## Installation

Downloaded the official Wazuh installation script.

Made the script executable.

Installed Wazuh using the All-in-One deployment.

The deployment installed:

- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer

---

## Verification

Verified the following services:

- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer

Verified successful dashboard login.

---

## Result

The Wazuh platform was successfully deployed and is operational.

Current Status:

✅ Wazuh Manager Running

✅ Wazuh Dashboard Running

✅ Wazuh Indexer Running

✅ Dashboard Accessible

---

## Next Phase

Deploy Windows Endpoint

Install Wazuh Agent

Install Sysmon

Begin Detection Engineering
