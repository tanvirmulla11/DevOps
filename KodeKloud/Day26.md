# 🚀 DevOps Day 26: Managing Multiple Git Remotes (Media Repo Task)

### 🗓️ Date
October 25, 2025

---

## 🧠 Overview

Today's task was focused on a practical Git operation — **managing multiple remotes** in the same repository.  
This is a common scenario in real-world DevOps workflows where code needs to be synchronized across multiple environments like **development**, **staging**, and **production** servers.

In this task, I worked on the `media` repository located on the **Storage Server** and successfully added a new remote, committed changes, and pushed updates to it.

---

## 🧾 Task Description

The xFusionCorp development team added updates to the project that is maintained under `/opt/media.git` repo and cloned under `/usr/src/kodekloudrepos/media`.  
Recently, some changes were made on the Git server that is hosted on the Storage Server in Stratos DC.  
The DevOps team added new Git remotes, so I had to update the remote on `/usr/src/kodekloudrepos/media` repository as per the below requirements:

### ✅ Objectives:
1. In `/usr/src/kodekloudrepos/media` repo, add a new remote named **`dev_media`** pointing to `/opt/xfusioncorp_media.git`.
2. Copy the `/tmp/index.html` file into the repo and **commit** it to the `master` branch.
3. Finally, **push the master branch** to this new remote.

---

## 🧩 Server Details

| Server Name | Hostname | User | Password | Purpose |
|--------------|-----------|-------|-----------|-----------|
| ststor01 | ststor01.stratos.xfusioncorp.com | natasha | Bl@kW | Nautilus Storage Server |

---

## ⚙️ Step-by-Step Implementation

### Step 1: SSH into the Storage Server
```bash
ssh natasha@ststor01
# Password: Bl@kW
```

# Step 2: Go to the Git repository
```bash
cd /usr/src/kodekloudrepos/media
```
# Step 3: Add a new Git remote named dev_media
```bash
sudo git remote add dev_media /opt/xfusioncorp_media.git
````
# Step 4: Verify the remote
```bash
sudo git remote -v
```
# Step 5: Copy the index.html file into the repo
```bash
sudo cp /tmp/index.html .
```
# Step 6: Add and commit the new file
```bash
sudo git add index.html
sudo git commit -m "Add index file for dev remote"
```
# Step 7: Push the master branch to the new remote
```bash
sudo git push dev_media master
```
## 🧪 Verification

### To verify the new remote and the successful push:
```bash
sudo git remote -v
```
