# 🚀 100 Days of DevOps – Day 9: MariaDB Troubleshooting
## 📌 Task Overview

### In this challenge, I worked on MariaDB troubleshooting to identify and fix issues related to database startup and permissions.
###  The main objective was to bring the MariaDB service back online, validate its status, and confirm database access.

## 🛠️ Steps Performed

### 1.Connected to the Server
```bash
ssh peter@172.16.239.10
password: day09
```
### 2.Tried Accessing MariaDB
```bash
sudo mysql
```

### 3.Started MariaDB Service
```bash
sudo systemctl start mariadb
```

### 4.Checked Logs for Errors
```bash
sudo journalctl -xeu mariadb.service
```

### 5.Checked MariaDB Data Directory
```bash
sudo ls -lah /var/lib/mysql
```

### 6.Created Data Directory (if missing)
```bash
sudo mkdir /var/lib/mysql
sudo ls -lah /var/lib/mysql
```

### 7.Fixed Ownership Permissions
```bash
sudo chown -R mysql:mysql /var/lib/mysql
```

### 8.Restarted MariaDB Service
```bash
sudo systemctl start mariadb
sudo systemctl status mariadb
```

### 9.Verified MariaDB Access
```bash
sudo mysql
```

### 10.Checked Available Databases
```bash
show databases;
```
---
# ✅ Output & Results

## Successfully started MariaDB 10.5 service.

### Verified access to the databases:

### -information_schema

### -mysql

### -performance_schema

# 📷 Screenshots
<img width="1815" height="899" alt="Screenshot 2025-08-20 074925" src="https://github.com/user-attachments/assets/5d49b602-2c45-46a1-ac3c-0120dc22f5ff" />

<img width="1919" height="966" alt="Screenshot 2025-08-20 074946" src="https://github.com/user-attachments/assets/d90f6047-3aaa-4e27-affc-b1b8fbd6a0f5" />

# 📖 Learnings
### -How to debug MariaDB service failures using journalctl.

### -Importance of correct data directory permissions.

### -Steps to bring up a database service from a broken state.
---
# 🔗 Reference
### This is part of my 100 Days of DevOps journey.
### Follow my progress here: 100 Days of DevOps Repository.
---
