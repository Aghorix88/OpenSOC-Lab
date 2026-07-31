# Wazuh Indexer OOM Issue

## Overview

During the initial deployment of Wazuh, the dashboard failed to load correctly even though all services appeared to be running.

The browser displayed:

> Wazuh dashboard server is not ready yet

---

## Symptoms

- Dashboard unavailable
- Dashboard reported "server not ready"
- Login unsuccessful
- Dashboard logs showed connection errors

---

## Investigation

### Step 1

Verified Wazuh Manager.

Status:

✅ Running

---

### Step 2

Verified Wazuh Dashboard.

Status:

✅ Running

---

### Step 3

Verified Wazuh Indexer.

Initially appeared to be running.

---

### Step 4

Checked Dashboard logs.

Observed:

Connection refused on port 9200.

---

### Step 5

Verified listening ports.

Result:

Port 9200 was not listening.

---

### Step 6

Reviewed Indexer logs.

Observed:

The Linux Out Of Memory (OOM) Killer terminated the Java process running the Wazuh Indexer.

---

## Root Cause

The virtual machine had only 4 GB RAM allocated.

The Wazuh Indexer (OpenSearch) exhausted available memory.

Linux terminated the process to protect the operating system.

---

## Resolution

Increased VM memory:

Before

4 GB

After

8 GB

Restarted the virtual machine.

Verified:

- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer

Verified port 9200 was listening.

Successfully accessed the Wazuh Dashboard.

---

## Lessons Learned

Never assume a running service is healthy.

Always verify:

- Service status
- Listening ports
- Application logs
- System logs

Logs identify the root cause faster than reinstalling software.

---

## Status

✅ Issue Resolved
