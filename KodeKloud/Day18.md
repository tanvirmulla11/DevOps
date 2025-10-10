# DevOps Day 18: Graduating to Automation with Ansible for a LAMP Stack Deployment

Today's task marked a turning point in my DevOps journey — the moment I stopped fighting configuration fires manually and embraced automation through **Ansible**. After multiple failed manual attempts, I successfully deployed a complete **LAMP stack** for a WordPress-style setup across multiple servers using a single playbook.

---

## 🧠 Table of Contents
- [The Task](#the-task)
- [My Solution: The Ansible Automation Approach](#my-solution-the-ansible-automation-approach)
  - [1️⃣ The Inventory (inventory.ini)](#1️⃣-the-inventory-inventoryini)
  - [2️⃣ The Playbook (playbookyaml)](#2️⃣-the-playbook-playbookyaml)
  - [3️⃣ The Execution](#3️⃣-the-execution)
- [💥 Post-Mortem: Why My Manual Attempts Failed](#💥-post-mortem-why-my-manual-attempts-failed)
- [⚙️ Why Did I Do This? (The "What & Why" of Ansible)](#⚙️-why-did-i-do-this-the-what--why-of-ansible)
- [🔍 Deep Dive: Line-by-Line Explanation](#🔍-deep-dive-line-by-line-explanation)
- [📜 Commands Used](#📜-commands-used)

---

## 🧩 The Task
**Objective:** Deploy the full infrastructure for a WordPress-like web application using automation.

### ✅ Requirements
- **DB Server**
  - Install MariaDB
  - Create database: `kodekloud_db1`
  - Create user: `kodekloud_cap` with password `GyQkFRVNr3`
  - Grant privileges to the user

- **App Servers (x3)**
  - Install Apache (httpd), PHP, and dependencies
  - Configure Apache to run on **port 8087**
  - Connect to the DB and display a success message

- **Final Goal:**  
  Accessible through a Load Balancer showing a success message.

---

## 🧰 My Solution: The Ansible Automation Approach
Instead of manually logging into each server, I automated the setup using **Ansible** from a **jump host**.

### 1️⃣ The Inventory (`inventory.ini`)
```ini
[app_servers]
stapp01 ansible_host=172.16.238.10 ansible_user=tony ansible_ssh_pass=Ir0nM@n ansible_become_pass=Ir0nM@n
stapp02 ansible_host=172.16.238.11 ansible_user=steve ansible_ssh_pass=Am3ric@ ansible_become_pass=Am3ric@
stapp03 ansible_host=172.16.238.12 ansible_user=banner ansible_ssh_pass=BigGr33n ansible_become_pass=BigGr33n

[db_server]
stdb01 ansible_host=172.16.239.10 ansible_user=peter ansible_ssh_pass=Sp!dy ansible_become_pass=Sp!dy

