# 📥 Download the Wazuh Installation Assistant

Before installing Wazuh, create a dedicated working directory to keep all installation files organized.

Create a working directory.

```bash
mkdir ~/wazuh-installation
```

Move into the directory.

```bash
cd ~/wazuh-installation
```

Download the official Wazuh installation assistant.

```bash
curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh
```

Grant execute permission to the installation script.

```bash
chmod +x wazuh-install.sh
```

Verify that the installer has been downloaded successfully.

```bash
ls -lh
```

Expected Output

```text
-rwxr-xr-x 1 user user ... wazuh-install.sh
```

> **💡 Best Practice**
>
> This guide has been validated using **Wazuh 4.12**. If a newer version of Wazuh is available, download the latest installation assistant from the official Wazuh repository or update the version number in the download URL.

---

# 🚀 Install the Wazuh Platform

Deploy the complete Wazuh platform.

```bash
sudo bash wazuh-install.sh -a
```

The installation assistant automatically performs the following tasks:

- Installs the Wazuh Manager
- Installs the Wazuh Indexer
- Installs the Wazuh Dashboard
- Generates SSL/TLS certificates
- Configures secure communication between components
- Starts all required Wazuh services
- Generates the administrator credentials

> **⚠️ Note**
>
> Depending on the available hardware resources and internet speed, the installation may take between **20 and 45 minutes**.

---

# 🔐 Retrieve Dashboard Credentials

After the installation finishes successfully, the installer displays the default administrator credentials.

Save these credentials securely.

If required, they can also be viewed later.

Example:

```text
Username : admin
Password : <generated-password>
```

Store these credentials securely because they are required to log in to the Wazuh Dashboard.

---

# 🔍 Verify Wazuh Services

Verify that all Wazuh services are running.

### Verify Wazuh Manager

```bash
sudo systemctl status wazuh-manager
```

### Verify Wazuh Indexer

```bash
sudo systemctl status wazuh-indexer
```

### Verify Wazuh Dashboard

```bash
sudo systemctl status wazuh-dashboard
```

Expected Output

```text
Active: active (running)
```

---

# 📊 Verify Running Services

Display all Wazuh services.

```bash
sudo systemctl list-units --type=service | grep wazuh
```

Expected Output

```text
wazuh-dashboard.service
wazuh-indexer.service
wazuh-manager.service
```

---

# 🌐 Access the Wazuh Dashboard

Determine the server IP address.

```bash
hostname -I
```

Example

```text
10.0.2.4
```

Open a web browser and navigate to:

```text
https://<SERVER-IP>
```

Example

```text
https://10.0.2.4
```

Log in using the administrator credentials generated during installation.

---

# 🛠️ Common Issues

## Issue 1 — Wazuh Dashboard Displays "Server is not Ready Yet"

### Symptoms

The browser displays:

```text
Wazuh dashboard server is not ready yet
```

### Cause

The Wazuh Dashboard depends on the Wazuh Indexer. If the Indexer fails to start, the Dashboard cannot initialize.

### Diagnosis

Check the Indexer status.

```bash
sudo systemctl status wazuh-indexer
```

View the service logs.

```bash
sudo journalctl -u wazuh-indexer
```

### Resolution

Restart the Indexer.

```bash
sudo systemctl restart wazuh-indexer
```

Wait a few moments and refresh the Dashboard.

If the service still fails, refer to the Out Of Memory (OOM) issue below.

---

## Issue 2 — Out Of Memory (OOM) Killer Terminates the Wazuh Indexer

### Background

During the deployment of OpenSOC-Lab, the Wazuh Dashboard failed to load and displayed:

```text
Wazuh dashboard server is not ready yet
```

After investigating the system logs, it was discovered that the Linux **Out Of Memory (OOM) Killer** had terminated the Wazuh Indexer because the virtual machine did not have sufficient RAM.

This prevented the Dashboard from connecting to the Indexer.

---

### Symptoms

- Wazuh Dashboard does not load.
- Dashboard remains stuck on initialization.
- Wazuh Indexer service stops unexpectedly.
- `systemctl status wazuh-indexer` reports the service as failed or inactive.

---

### Diagnosis

Check the Indexer status.

```bash
sudo systemctl status wazuh-indexer
```

Inspect the system logs.

```bash
sudo journalctl -u wazuh-indexer
```

Check for Out Of Memory messages.

```bash
dmesg | grep -i "killed process"
```

Example Output

```text
Out of memory: Killed process xxxx (java)
```

---

### Root Cause

The virtual machine was configured with insufficient RAM for the Wazuh Indexer.

Since the Indexer is Java-based, it requires a significant amount of memory. When available memory becomes exhausted, the Linux kernel automatically invokes the **Out Of Memory (OOM) Killer** and terminates memory-intensive processes to protect system stability.

---

### Resolution

Power off the virtual machine.

Increase the allocated RAM in Oracle VirtualBox.

Recommended memory allocation:

| Environment | Recommended RAM |
|-------------|-----------------|
| Wazuh Server | **8 GB or higher** |

Start the virtual machine.

Restart the affected services.

```bash
sudo systemctl restart wazuh-indexer
```

```bash
sudo systemctl restart wazuh-dashboard
```

Verify the services.

```bash
sudo systemctl status wazuh-indexer
```

```bash
sudo systemctl status wazuh-dashboard
```

Both services should display:

```text
Active: active (running)
```

Refresh the Dashboard in your web browser.

The Dashboard should now load successfully.

---

### Lessons Learned

For a single-node Wazuh deployment, allocating **8 GB of RAM or more** significantly improves system stability and prevents the Linux OOM Killer from terminating the Wazuh Indexer.

This issue was encountered and successfully resolved during the deployment of the OpenSOC-Lab environment.
