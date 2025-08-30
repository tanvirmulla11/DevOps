# 🚀 Day 10: Linux Bash Scripts – KodeKloud 100 Days of DevOps

This repository contains my solution for **Day 10** of the [100 Days of DevOps Challenge](https://kodekloud.com/), focused on **Linux Bash Scripting**.

---

## 📌 Task Description
The production support team of *xFusionCorp Industries* is working on developing some bash scripts to automate different day-to-day tasks.  
One such requirement is to **create a bash script that prints the names of all users on the system**, along with their login shell.

---

## ✅ Solution

### Bash Script (`users_info.sh`)
```bash
#!/bin/bash
# Script to list all system users with their login shell

echo "===== System Users and their Login Shells ====="
awk -F: '{ print $1 " -> " $7 }' /etc/passwd
```
---
## 🔹 Make the script executable
```bash
chmod +x users_info.sh
```
## 🔹 Run the script
```bash
./users_info.sh
```
## 📂 Sample Output
```bash
===== System Users and their Login Shells =====
root -> /bin/bash
daemon -> /usr/sbin/nologin
bin -> /usr/sbin/nologin
sys -> /usr/sbin/nologin
ubuntu -> /bin/bash
```
## 🎯 Key Learnings
### -Basics of Bash scripting in Linux.

### -Using awk with : as a field separator to extract specific fields.

### -Understanding /etc/passwd structure.

### -Granting execute permissions to scripts with chmod.
## 🔗 References

### KodeKloud – 100 Days of DevOps Challenge
---
