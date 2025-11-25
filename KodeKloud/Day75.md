
# Day 75: Jenkins Slave Nodes

# Jenkins SSH Build Agents Configuration  
**Project:** Stratos Datacenter – Application Server Integration  
**Task:** Configure App Servers as SSH Build Agents in Jenkins  
**Prepared By:** Tanvir Mulla  
**Date:** 15 November 2025  

---

## 📌 Overview  
This document details the configuration of three application servers in the Stratos Datacenter as SSH-based Jenkins build agents. The objective is to enable Jenkins to perform CI/CD and automation tasks remotely on each app server using secure SSH communication.

---

## 🛠️ Environment Details  

### **Jenkins Controller**
- **UI Access:** Jenkins button (top navigation bar)  
- **Login:**  
```

Username: admin
Password: Adm!n321

````

---

### **Application Servers (to be configured as Jenkins Agents)**

| Node Name       | Hostname                           | IP Address      | Username | Password  | Remote Root Directory        | Label    |
|-----------------|-------------------------------------|------------------|----------|-----------|-------------------------------|----------|
| App_server_1    | stapp01.stratos.xfusioncorp.com     | 172.16.238.10    | tony     | Ir0nM@n   | /home/tony/jenkins            | stapp01  |
| App_server_2    | stapp02.stratos.xfusioncorp.com     | 172.16.238.11    | steve    | Am3ric@   | /home/steve/jenkins           | stapp02  |
| App_server_3    | stapp03.stratos.xfusioncorp.com     | 172.16.238.12    | banner   | BigGr33n  | /home/banner/jenkins          | stapp03  |

---

## 🔧 Step 1 — Install Required Jenkins Plugins  

Navigate to:  
**Manage Jenkins → Manage Plugins → Available**

Install the following plugins:

- **SSH Build Agents Plugin**  
- **SSH Agent Plugin**  
- **Credentials Plugin**

After installation:  
✔ Restart Jenkins  
✔ Refresh UI if needed  

These plugins allow Jenkins to connect to agents using SSH.

---

## 🔐 Step 2 — Add SSH Credentials  

Path:  
**Manage Jenkins → Credentials → System → Global → Add Credentials**

Create the following credentials:

| Credential ID   | Username | Password | Associated Server |
|-----------------|----------|----------|--------------------|
| stapp01-creds   | tony     | Ir0nM@n  | App Server 1       |
| stapp02-creds   | steve    | Am3ric@  | App Server 2       |
| stapp03-creds   | banner   | BigGr33n | App Server 3       |

---

## 📁 Step 3 — Prepare App Servers  

Each agent requires a Jenkins working directory and Java runtime.

### **Create Jenkins Directories**

Run these commands on each server:

#### App Server 1
```bash
sudo mkdir -p /home/tony/jenkins
sudo chown -R tony:tony /home/tony/jenkins
````

#### App Server 2

```bash
sudo mkdir -p /home/steve/jenkins
sudo chown -R steve:steve /home/steve/jenkins
```

#### App Server 3

```bash
sudo mkdir -p /home/banner/jenkins
sudo chown -R banner:banner /home/banner/jenkins
```

---

## ☕ Step 4 — Install Java 17 (Required for Jenkins Remoting)

The installed Jenkins version requires **Java 17**.

Run on each app server:

```bash
sudo yum remove -y java-11-openjdk
sudo yum install -y java-17-openjdk
java -version
```

Expected output:

```
openjdk version "17.x.x"
```

---

## 🖥️ Step 5 — Configure Jenkins Agent Nodes

Navigate to:
**Manage Jenkins → Nodes → New Node**

### Example Configuration (App_server_1)

```yml
Node Name: App_server_1
Type: Permanent Agent
# of Executors: 1
Remote Root Directory: /home/tony/jenkins
Label: stapp01
Launch Method: Launch agent via SSH
Host: 172.16.238.10
Credentials: stapp01-creds
Host Key Strategy: Non verifying strategy
```

Repeat this configuration for:

* **App_server_2**
* **App_server_3**

using their respective directories, hosts, and credentials.

---

## 🟢 Step 6 — Validate Agent Status

After Java installation and correct configuration, Jenkins will deploy `remoting.jar` to each server.

Check status:

**Manage Jenkins → Nodes**

| Node Name    | Expected Status |
| ------------ | --------------- |
| App_server_1 | 🟢 ONLINE       |
| App_server_2 | 🟢 ONLINE       |
| App_server_3 | 🟢 ONLINE       |

Each agent should show:

* Architecture
* Clock synchronization
* Disk usage
* Response time
* No class version or connection errors

---

## ✅ Completion

Your Jenkins controller is now connected to three secure SSH-based application server agents, ready for CI/CD automation.

---


