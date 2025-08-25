# Day 8 – Ansible Installation on Jump Host

## Overview
As part of the Nautilus DevOps team's weekly meeting, the decision was made to adopt **Ansible** for automation and configuration management due to its simple setup and minimal prerequisites.  

The team will begin testing by configuring the **Jump Host** as the Ansible controller, which will be used to execute tasks on the rest of the servers.

---

## Objective
- Install **Ansible v4.9.0** on the Jump Host.  
- Installation must be performed using **pip3 only**.  
- The Ansible binary should be **globally available** so that all users on the system can run Ansible commands.

---

## Implementation Steps
```bash
# Install Ansible version 4.9.0
sudo pip3 install ansible==4.9.0

# Verify Ansible installation and version
ansible --version

# Confirm binary availability
ls -l $(which ansible)
```
---
# Verification

### ansible --version should display ansible [core 2.11.6], which corresponds to Ansible v4.9.0.

### The binary should be located under /usr/local/bin/ansible, confirming global availability.
---
# Key Takeaways

### -Installing via pip3 allows precise version control.

### -Ensures Ansible is accessible system-wide for multiple users.

### -Sets the foundation for using Jump Host as an Ansible controller in future tasks.
---
# images
<img width="1919" height="968" alt="Screenshot 2025-08-20 072318" src="https://github.com/user-attachments/assets/a60b0465-095a-453b-8733-6c0fe18d29c1" />

<img width="1919" height="909" alt="Screenshot 2025-08-20 072342" src="https://github.com/user-attachments/assets/313524f6-d781-4461-bca5-c82ca874a5ee" />

