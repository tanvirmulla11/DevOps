
# Day 68: 🚀 Jenkins Server Setup – xFusionCorp Industries

## 📘 Task Overview
The DevOps team at **xFusionCorp Industries** is initiating the setup of CI/CD pipelines using **Jenkins**.  
Your task is to install and configure Jenkins on the **Jenkins server** using the `yum` utility and create an admin user with the provided credentials.

---

## 🧩 Requirements

1. Install Jenkins on the **Jenkins server** using `yum`.
2. Start and enable the Jenkins service.
3. Create the following admin user during initial setup:
   - **Username:** `theadmin`
   - **Password:** `Adm!n321`
   - **Full Name:** `Mariyam`
   - **Email:** `mariyam@jenkins.stratos.xfusioncorp.com`

---

## 🔐 Access Details

- **Server:** `jenkins.stratos.xfusioncorp.com`
- **Login User:** `root`
- **Password:** `S3curePass`
- **Access URL (after setup):** [http://jenkins.stratos.xfusioncorp.com:8080](http://jenkins.stratos.xfusioncorp.com:8080)

---

## ⚙️ Step-by-Step Installation Guide

### 1️⃣ Connect to Jenkins Server
```bash
ssh root@jenkins.stratos.xfusioncorp.com
Password:
```
```bash
S3curePass
```
## 2️⃣ Install Java (Required by Jenkins)
```bash
yum install java-11-openjdk -y
```
## 3️⃣ Add Jenkins Repository
```bash
yum install wget -y
wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
```
## 4️⃣ Install Jenkins
```bash
yum install jenkins -y
```
## 5️⃣ Enable and Start Jenkins Service
```bash
systemctl enable jenkins
systemctl start jenkins
systemctl status jenkins
```

⚠️ If you face a timeout error, make sure Java is correctly configured:
```bash
alternatives --config java
systemctl restart jenkins
```

Check logs if needed:
```bash
journalctl -u jenkins -xe | tail -20
```
## 6️⃣ Unlock Jenkins UI

After installation, open:
```bash
http://jenkins.stratos.xfusioncorp.com:8080
```

Retrieve the initial admin password:
```bash
cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy and paste it into the Unlock Jenkins page.

## 7️⃣ Install Suggested Plugins

Choose Install suggested plugins when prompted.

## 8️⃣ Create Admin User

Fill out the form as below:
```bash
Field	Value
Username	theadmin
Password	Adm!n321
Full Name	Mariyam
Email	mariyam@jenkins.stratos.xfusioncorp.com
```
Click Save and Continue.

## 9️⃣ Confirm Jenkins URL

Use:
```bash
http://jenkins.stratos.xfusioncorp.com:8080/

```
Click Save and Finish → Start using Jenkins.

## ✅ Verification

To confirm Jenkins is running:
```bash
systemctl status jenkins
```

You should now be able to log in using:
```bash
Username: theadmin

Password: Adm!n321
```
