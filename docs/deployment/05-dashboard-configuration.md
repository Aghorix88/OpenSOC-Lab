# 05. Dashboard Configuration

---

# 📖 Overview

The Wazuh Dashboard provides a centralized web interface for monitoring security events, managing agents, analyzing alerts, and investigating incidents. After installing the Wazuh platform, it is important to verify that the Dashboard is operating correctly before connecting endpoint agents.

This chapter covers the initial verification and configuration of the Wazuh Dashboard, ensuring that all backend services are communicating correctly and that the web interface is accessible.

---

| Information | Details |
|-------------|---------|
| **Document** | 05-dashboard-configuration.md |
| **Version** | v1.0 |
| **Difficulty** | Beginner |
| **Estimated Time** | 20–30 Minutes |
| **Related Screenshots** | `images/deployment/dashboard/` |

---

# 🎯 Objectives

After completing this chapter, you will be able to:

- Access the Wazuh Dashboard.
- Verify Dashboard functionality.
- Authenticate using administrator credentials.
- Verify communication between Dashboard, Manager, and Indexer.
- Perform an initial health check.
- Prepare the Dashboard for agent onboarding.

---

# 📋 Prerequisites

Before continuing, ensure that:

- Ubuntu Server is running.
- Wazuh Manager is installed.
- Wazuh Indexer is running.
- Wazuh Dashboard is installed.
- Internet connectivity is available.
- All Wazuh services are active.

---

# 🌐 Verify Server IP Address

Determine the IP address assigned to the Ubuntu Server.

```bash
hostname -I
```

Example Output

```text
10.0.2.4
```

This IP address will be used to access the Dashboard.

---

# 🌍 Access the Dashboard

Open any modern web browser.

Navigate to:

```text
https://<SERVER-IP>
```

Example

```text
https://10.0.2.4
```

Because the Dashboard uses a self-signed SSL certificate, your browser may display a security warning.

Select:

```
Advanced
↓

Proceed to Website
```

This warning is expected in a lab environment.

---

# 🔐 Login to the Dashboard

Enter the administrator credentials generated during the Wazuh installation.

Example

```text
Username : admin
Password : <generated-password>
```

After successful authentication, the Dashboard home page should appear.

---

# 🔍 Verify Wazuh Services

Verify that every Wazuh component is running correctly.

## Wazuh Manager

```bash
sudo systemctl status wazuh-manager
```

Expected

```text
Active: active (running)
```

---

## Wazuh Indexer

```bash
sudo systemctl status wazuh-indexer
```

Expected

```text
Active: active (running)
```

---

## Wazuh Dashboard

```bash
sudo systemctl status wazuh-dashboard
```

Expected

```text
Active: active (running)
```

---

# 📊 Verify Dashboard Health

After logging in, verify the following:

- Dashboard loads successfully.
- No initialization errors appear.
- Wazuh Manager status is healthy.
- Wazuh Indexer status is healthy.
- Dashboard menus load correctly.
- No warning banners are displayed.

---

# 🖥️ Explore the Dashboard

Verify that the following sections are accessible.

- Dashboard
- Endpoints
- Security Events
- Inventory
- Vulnerabilities
- Integrity Monitoring
- MITRE ATT&CK
- Server Management

At this stage, some pages may not display data because no endpoint agents have been registered yet.

This is expected.

---

# 🔎 Verify Manager Communication

Open:

```
Server Management
↓

Status
```

Verify that:

- Wazuh Manager is connected.
- Wazuh API is reachable.
- Indexer is healthy.

---

# 🌐 Verify Listening Ports

Run:

```bash
sudo ss -tulnp
```

Verify that the following ports are listening.

| Port | Service |
|-------|----------|
| 443 | Wazuh Dashboard |
| 1514 | Wazuh Manager |
| 1515 | Agent Registration |
| 55000 | Wazuh API |
| 9200 | Wazuh Indexer |

---

# 🔍 Verify the Wazuh API

Test API availability.

```bash
curl -k https://localhost:55000
```

If authentication is enabled, receiving an authentication response confirms that the API is operational.

---

# ✅ Dashboard Verification Checklist

Verify the following before continuing.

- [ ] Dashboard Login Successful
- [ ] HTTPS Accessible
- [ ] Wazuh Manager Running
- [ ] Wazuh Indexer Running
- [ ] Wazuh Dashboard Running
- [ ] API Reachable
- [ ] Dashboard Fully Loaded
- [ ] Ready for Agent Deployment

---

# 📸 Screenshot References

Store screenshots in:

```text
images/
└── deployment/
      └── dashboard/
```

Recommended screenshots.

| Figure | Screenshot | Filename |
|---------|------------|----------|
| Figure 5.1 | Dashboard Login Page | dashboard-login.png |
| Figure 5.2 | Dashboard Home | dashboard-home.png |
| Figure 5.3 | Manager Status | manager-status.png |
| Figure 5.4 | Server Management | server-management.png |
| Figure 5.5 | Running Services | running-services.png |
| Figure 5.6 | Dashboard Overview | dashboard-overview.png |

---

# 🛠️ Common Issues

## Dashboard Not Accessible

### Symptoms

The browser cannot open the Dashboard.

### Resolution

Verify that the Dashboard service is running.

```bash
sudo systemctl status wazuh-dashboard
```

Restart the service if necessary.

```bash
sudo systemctl restart wazuh-dashboard
```

---

## Login Failure

### Symptoms

Authentication fails even with the correct username.

### Resolution

Verify that the credentials generated during installation are being used.

If necessary, regenerate or reset the administrator password according to the Wazuh documentation.

---

## Dashboard Shows "Server is Not Ready Yet"

### Symptoms

Dashboard initialization never completes.

### Resolution

Verify the Wazuh Indexer.

```bash
sudo systemctl status wazuh-indexer
```

Inspect the logs.

```bash
sudo journalctl -u wazuh-indexer
```

Restart the affected services.

```bash
sudo systemctl restart wazuh-indexer
sudo systemctl restart wazuh-dashboard
```

If the Indexer repeatedly stops, refer to the Out Of Memory (OOM) troubleshooting described in the previous chapter.

---

# 📌 Summary

At this stage, the Wazuh Dashboard has been successfully verified.

Completed tasks:

- Dashboard accessible.
- Administrator login verified.
- Manager communication verified.
- Indexer communication verified.
- API availability confirmed.
- Platform ready for endpoint onboarding.

---

# 🎓 Learning Outcomes

After completing this chapter, you should be able to:

- Access the Wazuh Dashboard.
- Authenticate successfully.
- Verify core Wazuh services.
- Perform basic Dashboard health checks.
- Confirm Manager and Indexer communication.
- Prepare the environment for agent deployment.

---

## ➡️ Next Guide

**06-windows-agent.md**

In the next chapter, you will deploy the Wazuh Agent on a Windows endpoint, register it with the Wazuh Manager, and verify that the endpoint appears successfully in the Dashboard.
