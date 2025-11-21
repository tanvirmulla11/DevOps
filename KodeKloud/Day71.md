
# Day 71 🧩 Configure Jenkins Job for Package Installation

## 📘 Objective
Create a Jenkins job named **install-packages** that installs a package on the storage server based on a parameter input.

---

## ⚙️ Steps

### 1️⃣ Access Jenkins
- Click the **Jenkins** button on the top bar.  
- Login with:
Username: admin
Password: Adm!n321


---

### 2️⃣ Create a New Job
1. Click **New Item**.  
2. Enter name: `install-packages`.  
3. Select **Freestyle project** → Click **OK**.

---

### 3️⃣ Add Parameter
1. In the job configuration, check **This project is parameterized**.  
2. Click **Add Parameter → String Parameter**.  
3. Enter:
 - **Name:** `PACKAGE`  
 - **Default Value:** `httpd`  
 - **Description:** Package name to install on the storage server.

---

### 4️⃣ Configure Build
1. Scroll to **Build → Execute Shell**.  
2. Add this script:
 ```bash
 sshpass -p 'S3curePass' ssh -o StrictHostKeyChecking=no root@ststor01.stratos.xfusioncorp.com "yum install -y ${PACKAGE}"
```
### 5️⃣ Save and Build

Click Save.

On the left, click Build with Parameters.
 ```bash
Enter a package name (e.g., git, wget, curl).
```
Click Build.

### 6️⃣ Verify
 ```bash
Check Console Output to confirm successful installation.

Run multiple builds to test reliability.
```
### 7️⃣ Notes
 ```bash
Install SSH Agent or Matrix Authorization plugin if missing.

Restart Jenkins when prompted and refresh the UI.

Capture screenshots or record steps using loom.com
```

### ✅ Result
 ```bash
You have successfully:

Created the install-packages Jenkins job

Added a parameter for package installation

Automated package setup on the storage server

Verified repeated successful executions`
```
