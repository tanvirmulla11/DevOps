# 🌐 Portfolio Website Deployment on AWS EC2
<!--  -->
Hello and welcome! 👋  
This repository documents the step-by-step deployment of my **personal portfolio website** on an **Amazon EC2 instance** using Apache web server.

---

## 🚀 Why This Project?

As part of my **DevOps learning journey**, I wanted to explore real-world cloud deployment. Hosting my portfolio on **AWS EC2** gave me hands-on experience with:

- Linux terminal operations  
- Apache HTTP server setup  
- Manual deployment process  
- Security Group configuration  
- Static website hosting  

This project gave me a practical understanding of server setup and cloud hosting from scratch!

---

## 🛠️ Technologies Used

- **Amazon EC2** (Amazon Linux 2)  
- **Apache HTTP Server (httpd)**  
- **Bash / Shell scripting**  
- **GitHub** (for source code)  
- **Security Groups** (inbound rules)

---

## 📋 What You'll Find in This Repo

- ✅ Step-by-step deployment instructions  
- 🔐 AWS EC2 and Security Group configuration  
- 🌍 Static site hosted from GitHub ZIP file  
- 🎥 [Recording of the full deployment](https://drive.google.com/file/d/1zJMHM2_GMpx4xsiV7qOcegPvdhGowcDk/view?usp=sharing)  
- ✍️ Key commands and Linux tricks I learned  

---

## 🧪 Project Steps & Commands

```bash
# 1️⃣ Become root user
sudo su

# 2️⃣ Update the system
yum update -y

# 3️⃣ Create project folder and navigate into it
mkdir tech
cd tech

# 4️⃣ Download Your portfolio ZIP from GitHub
wget https://github.com/yourusername/your-portfolio-repo/archive/refs/heads/main.zip

# 5️⃣ List files to confirm download
ls -l

# 6️⃣ Unzip downloaded file
unzip main.zip

# 7️⃣ Navigate into unzipped folder
cd your-portfolio-repo-main

# 8️⃣ List files
ls -l

# 9️⃣ Move all files to Apache web root
mv * /var/www/html

# 🔟 Navigate to web root to verify
cd /var/www/html
ls -l

# 1️⃣1️⃣ Enable and start Apache server
systemctl enable httpd
systemctl start httpd

