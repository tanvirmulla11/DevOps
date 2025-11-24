# Day 74 – Jenkins Database Backup Job

**Series:** 100 Days of DevOps (KodeKloud)
**Lab Theme:** Automate a database dump & transfer using Jenkins

---

## 🎯 Objective

* Create a Jenkins job named `database-backup`
* Dump the database `kodekloud_db01` from the database server
* Use DB credentials:

  * **User:** `kodekloud_roy`
  * **Password:** `asdfgdsd`
* Name the dump file as: `db_$(date +%F).sql`
* Transfer the dump file to backup server folder: `/home/clint/db_backups`
* Schedule job to run **every 10 minutes** using cron: `*/10 * * * *`
* Restart Jenkins after plugin installation if required

---

## 🔧 Environment Details

### **Database Server**

* Host: `stdb01.stratos.xfusioncorp.com` (IP: **172.16.239.10**)
* User: `peter`
* Password: `Sp!dy`

### **Backup Server**

* Host: `stbkp01.stratos.xfusioncorp.com` (IP: **172.16.238.16**)
* User: `clint`
* Password: `H@wk3y3`

### **Jenkins Server**

* Host: `jenkins.stratos.xfusioncorp.com` (IP: **172.16.238.19**)
* User: `jenkins`
* Password: `j@rv!s`

---

## ✅ Solution Steps

### **1. Login to Jenkins**

* Open Jenkins in browser
* Credentials: `admin` / `Adm!n321`

---

### **2. Install Required Plugins**

Navigate to: **Manage Jenkins → Manage Plugins → Available**

* Install: **SSH Agent**, **Credentials**, and any related plugins
* Restart Jenkins

---

### **3. Add SSH Credentials in Jenkins**

Navigate to: **Manage Jenkins → Credentials → System → Global → Add Credentials**

Add two credentials:

1. **DB Server Credentials**

   * Username: `peter`
   * Password: `Sp!dy`
   * ID: `db-server-creds`

2. **Backup Server Credentials**

   * Username: `clint`
   * Password: `H@wk3y3`
   * ID: `bkp-server-creds`

---

### **4. Create the Jenkins Job**

* Go to **New Item** → Freestyle Project
* Name: `database-backup`
* Save

---

### **5. Configure Build Step (Execute Shell)**

Add this script:

```bash
#!/bin/bash

DATE=$(date +%F)
DUMP_FILE="db_${DATE}.sql"

# Dump database on DB server
ssh peter@172.16.239.10 "mysqldump -u kodekloud_roy -pasdfgdsd kodekloud_db01 > /tmp/${DUMP_FILE}"

# Copy the dump file to backup server
scp peter@172.16.239.10:/tmp/${DUMP_FILE} clint@172.16.238.16:/home/clint/db_backups/

# Cleanup dump file on DB server
ssh peter@172.16.239.10 "rm -f /tmp/${DUMP_FILE}"
```

⚠️ **Note:** MySQL password is written without space: `-pasdfgdsd`.

---

### **6. Set Build Trigger**

Go to **Build Triggers** → Select **Build periodically**
Enter cron expression:

```
*/10 * * * *
```

Runs the job every 10 minutes.

---

### **7. Save & Run**

* Click **Save**
* Click **Build Now**
* Check console output for:

  * Database dump created
  * File transferred
  * Cleanup done

---

### **8. Verify Backup on Backup Server**

SSH into the backup server:

```bash
ssh clint@172.16.238.16
```

Password: `H@wk3y3`

Check backup directory:

```bash
ls -l /home/clint/db_backups
```

You should see:

```
db_2025-11-15.sql
```

(or today’s date)

---

## 🎉 Final Result

* Jenkins job runs every 10 minutes
* Automatically dumps MySQL DB
* Transfers dump to backup server
* Files stored in `/home/clint/db_backups`
* Reliable automated backup pipeline created!

---

