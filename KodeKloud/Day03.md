# KodeKloud - Day 03 Task
### SSH Root Login Restriction Across App Servers
### In this task, we connected to all 3 application servers (***stapp01, stapp02, stapp03***) from the jump host and ensured that root login via SSH is disabled by modifying the sshd_config file.

# 🎯 Objective

Disable direct root SSH login on all application servers.

Verify that PermitRootLogin is set to no.

# 🛠️ Steps Performed
🔹 Step 1: Connect to stapp01 as tony
```bash
thor@jumphost ~$ ssh tony@stapp01
tony@stapp01's password:
```

### 👉 Switched to root and verified:

```bash
[tony@stapp01 ~]$ sudo su -
[root@stapp01 ~]# exit
```
### 👉 Edited sshd_config file and restarted SSH service:
```bash
[tony@stapp01 ~]$ sudo vi /etc/ssh/sshd_config
[tony@stapp01 ~]$ sudo systemctl restart sshd
```
### 👉 Verified PermitRootLogin setting:
```bash
[tony@stapp01 ~]$ sudo cat /etc/ssh/sshd_config | grep -i "permitRootLogin"
PermitRootLogin no
# the setting of "PermitRootLogin without-password".
```
### 👉 Exited session:
```bash
[tony@stapp01 ~]$ exit
logout
Connection to stapp01 closed.
```
✅ Root login disabled successfully on stapp01.
# 🔹 Step 2: Connect to stapp02 as steve
```bash
thor@jumphost ~$ ssh steve@stapp02
steve@stapp02's password:
```
### 👉 Edited sshd_config file and restarted SSH service:
```bash
[steve@stapp02 ~]$ sudo vi /etc/ssh/sshd_config
[steve@stapp02 ~]$ sudo systemctl restart sshd
```
### 👉 Verified PermitRootLogin setting:
```bash
[steve@stapp02 ~]$ sudo cat /etc/ssh/sshd_config | grep -i "permitRootLogin"
PermitRootLogin no
# the setting of "PermitRootLogin without-password".
```
### 👉 Exited session:
```bash
[steve@stapp02 ~]$ exit
logout
Connection to stapp02 closed.
```
✅ Root login disabled successfully on stapp02.
# 🔹 Step 3: Connect to stapp03 as banner
```bash
thor@jumphost ~$ ssh banner@stapp03
banner@stapp03's password:
```
### 👉 Edited sshd_config file and restarted SSH service:
```bash
[banner@stapp03 ~]$ sudo vi /etc/ssh/sshd_config
[banner@stapp03 ~]$ sudo systemctl restart sshd
```
### 👉 Verified PermitRootLogin setting:
```bash
[banner@stapp03 ~]$ sudo cat /etc/ssh/sshd_config | grep -i "permitRootLogin"
PermitRootLogin no
# the setting of "PermitRootLogin without-password".
```
### 👉 Exited session:
```bash
[banner@stapp03 ~]$ exit
logout
Connection to stapp03 closed.
```
✅ Root login disabled successfully on stapp03.
# ✅ Final Verification

On all three servers, the configuration shows:
```bash
PermitRootLogin no
```
This confirms that direct root login via SSH is disabled across all app servers.

# 📝 Notes

Initial attempts to SSH as root were denied (expected).

Restarted SSH service using:
```bash
sudo systemctl restart sshd
```


Confirmed configuration using:
```bash
grep -i "permitRootLogin" /etc/ssh/sshd_config
```
# images

<img width="1919" height="972" alt="Screenshot 2025-08-17 102958" src="https://github.com/user-attachments/assets/df46a656-2daa-4d9e-93fd-eaf517abd670" />

<img width="1919" height="962" alt="Screenshot 2025-08-17 103042" src="https://github.com/user-attachments/assets/f2bb583e-453b-4101-8525-bbfacb50a370" />


📌 Author: Tanvir Mulla


