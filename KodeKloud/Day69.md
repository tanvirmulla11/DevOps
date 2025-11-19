# Day 69: Install Jenkins Plugins
# 🔧 Jenkins Plugin Installation — Nautilus DevOps

## 📘 Overview
Install the **Git** and **GitLab** plugins on the Nautilus Jenkins server, then restart Jenkins if required.

**Jenkins Credentials**
- Username: `admin`
- Password: `Adm!n321`

---

## 🪜 Steps to Complete

### 1) Access Jenkins UI
1. Click the **Jenkins** button on the lab’s top bar.
2. Log in with:
Username: admin
Password: Adm!n321


### 2) Open Plugin Manager
- Navigate:
- Newer UI: **Manage Jenkins → Plugins → Available plugins**
- Older UI: **Manage Jenkins → Manage Plugins → Available**

### 3) Install Required Plugins
1. In **Available** tab, search **Git** → check **Git plugin** → click **Install without restart**.
2. Search **GitLab** → check **GitLab Plugin** → click **Install without restart**.

> During installation you’ll see status messages. Wait until each shows **Success**.

### 4) Restart Jenkins (if prompted)
- On the installer page, click **“Restart Jenkins when installation is complete and no jobs are running.”**
- Wait for Jenkins to shut down and come back to the login screen.
- Log in again with `admin` / `Adm!n321`.

### 5) Verify Installation
1. Go to **Manage Jenkins → Plugins → Installed**.
2. Confirm both appear:
- **Git plugin**
- **GitLab Plugin**

---


## 🧰 (Optional) CLI Verification
If you have shell access to the controller:
```bash
# List installed plugins (names may include versions)
ls /var/lib/jenkins/plugins | grep -Ei 'git|gitlab'
```

