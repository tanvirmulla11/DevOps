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

```
### 2️⃣ The Playbook (playbook.yaml)
---
```bash
- name: Configure DB Server
  hosts: db_server
  become: yes
  tasks:
    - name: Install MariaDB dependencies
      yum:
        name:
          - mariadb-server
          - python3-PyMySQL
        state: present

    - name: Start and enable MariaDB service
      service:
        name: mariadb
        state: started
        enabled: yes

    - name: Create database
      community.mysql.mysql_db:
        name: kodekloud_db1
        state: present
        login_unix_socket: /var/lib/mysql/mysql.sock

    - name: Create user with privileges
      community.mysql.mysql_user:
        name: kodekloud_cap
        password: GyQkFRVNr3
        priv: "kodekloud_db1.*:ALL"
        host: '%'
        state: present
        login_unix_socket: /var/lib/mysql/mysql.sock

    - name: Install firewalld
      yum:
        name: firewalld
        state: present

    - name: Start and enable firewalld
      service:
        name: firewalld
        state: started
        enabled: yes

    - name: Ensure firewall allows MySQL connections
      firewalld:
        service: mysql
        state: enabled
        permanent: yes
        immediate: yes

- name: Configure App Servers
  hosts: app_servers
  become: yes
  tasks:
    - name: Install required packages
      yum:
        name:
          - httpd
          - php
          - php-mysqlnd
        state: present

    - name: Configure Apache to listen on the correct port
      lineinfile:
        path: /etc/httpd/conf/httpd.conf
        regexp: '^Listen '
        line: 'Listen 8087'
      notify: restart httpd

    - name: Install firewalld
      yum:
        name: firewalld
        state: present

    - name: Start and enable firewalld
      service:
        name: firewalld
        state: started
        enabled: yes

    - name: Ensure firewall allows the correct port
      firewalld:
        port: 8087/tcp
        state: enabled
        permanent: yes
        immediate: yes

    - name: Create the test PHP page
      copy:
        content: |
          <?php
          $link = mysqli_connect('stdb01', 'kodekloud_cap', 'GyQkFRVNr3', 'kodekloud_db1');
          if (!$link) {
              die('Could not connect: ' . mysqli_connect_error());
          }
          echo 'App is able to connect to the database using user kodekloud_cap';
          mysqli_close($link);
          ?>
        dest: /var/www/html/index.php
        mode: 0644

    - name: Start and enable httpd service
      service:
        name: httpd
        state: started
        enabled: yes

  handlers:
    - name: restart httpd
      service:
        name: httpd
        state: restarted
```
