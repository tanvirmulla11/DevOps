
# 🚀 Day 73: Jenkins Scheduled Jobs 

### 🎯 Objective  
Automate Apache log collection from **App Server 1** to the **Storage Server** using a Jenkins job scheduled to run **every 3 minutes**.

This automation helps xFusionCorp’s DevOps team **centralize Apache logs** (both `access_log` and `error_log`) for analysis and troubleshooting.

---

# ⚙️ Environment Details

| Component | Description |
|----------|-------------|
| **Jenkins Server** | Main automation server (login: `admin` / `Adm!n321`) |
| **App Server 1** | Source server containing Apache logs |
| **Storage Server** | Destination server for centralized logs |
| **Log Source Path** | `/var/log/httpd/` |
| **Log Destination Path** | `/usr/src/itadmin/` |

---

# 🚀 Solution Steps

## **Step 1: Login to Jenkins**
Access Jenkins UI:  
```
http://<jenkins-server-ip>:8080
```

Login credentials:  
- **Username:** admin  
- **Password:** Adm!n321  

Wait for the dashboard to load.

---

## **Step 2: Install Required Plugins**

Ensure the following plugins are installed:

| Plugin | Purpose |
|--------|---------|
| **SSH Agent Plugin** | For Jenkins to connect to remote servers |
| **Publish Over SSH Plugin** | Securely copy files between servers |

### To install:
- Go to **Manage Jenkins → Manage Plugins → Available**
- Search and install:
  - SSH Agent Plugin  
  - Publish Over SSH Plugin  
- Click **Restart Jenkins when installation is complete**

---

## **Step 3: Configure SSH Access**

### 🔹 For App Server 1 (Source)

Generate SSH key (if not available):
```bash
ssh-keygen -t rsa -b 4096
```

Copy key to App Server 1:
```bash
ssh-copy-id root@appserver1
```

Test connection:
```bash
ssh root@appserver1
```

---

### 🔹 For Storage Server (Destination)

Copy same key:
```bash
ssh-copy-id root@storageserver
```

Test connection:
```bash
ssh root@storageserver
```

---

## **Step 4: Configure “Publish over SSH” in Jenkins**

Go to:  
**Manage Jenkins → Configure System → Publish over SSH**

Add configuration:

- **Name:** StorageServer  
- **Hostname:** `<Storage_Server_IP>`  
- **Username:** root  
- **Remote Directory:** `/usr/src/itadmin/`  

Click **Test Configuration → Success**  
Click **Save**

---

## **Step 5: Create a New Jenkins Job**

Dashboard → **New Item**

Enter job name:  
```
copy-logs
```

Select **Freestyle project** → OK

---

## **Step 6: Configure the Job**

### 🔸 General Section
Description:
```
This job collects Apache access and error logs from App Server 1 every 3 minutes and stores them in /usr/src/itadmin on the Storage Server.
```

---

### 🔸 Build Triggers Section

Enable:
```
Build periodically
```

Schedule:
```
*/3 * * * *
```

(Runs every 3 minutes)

---

### 🔸 Build Environment
Enable:
- ✅ Use secret text(s) or file(s)  
- ✅ Use SSH agent credentials  

---

### 🔸 Build Step (Execute Shell)

Add script:

```bash
#!/bin/bash
# Source and destination
SRC_USER=root
SRC_HOST=appserver1
SRC_LOG_PATH=/var/log/httpd/
DEST_PATH=/usr/src/itadmin/

# Copy access_log and error_log from App Server 1 to Jenkins server temp directory
scp ${SRC_USER}@${SRC_HOST}:${SRC_LOG_PATH}access_log /tmp/access_log
scp ${SRC_USER}@${SRC_HOST}:${SRC_LOG_PATH}error_log /tmp/error_log

# Send logs to Storage Server
scp /tmp/access_log /tmp/error_log root@storageserver:${DEST_PATH}

# Confirmation message
echo "Apache logs copied successfully to ${DEST_PATH} on Storage Server"
```

Click **Save**.

---

## **Step 7: Run and Verify**

Click **Build Now**.

Check **Console Output** — It should show:
```
Apache logs copied successfully to /usr/src/itadmin on Storage Server
```

On Storage Server:
```bash
ls -l /usr/src/itadmin/
```

You should see:
```
access_log
error_log
```

---

## **Step 8: Verify Automatic Schedule**

Wait for 3 minutes → The job should run automatically.

Check if logs update every 3 minutes in:
```
/usr/src/itadmin/
```

---


