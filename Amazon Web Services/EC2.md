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

## 🔐 Security Group Configuration

📍 Go to **AWS Console → EC2 → Security Groups → Inbound Rules → Edit**

Add the following inbound rules to allow public web traffic:

- **HTTP (port 80)** → Source: Anywhere (IPv4)  
- **HTTPS (port 443)** → Source: Anywhere (IPv4)  

---

## 📺 Watch the Full Deployment

🎬 **Watch on Google Drive**  
I’ve recorded the **entire deployment process** as part of my DevOps learning and documentation journey. [https://drive.google.com/file/d/1zJMHM2_GMpx4xsiV7qOcegPvdhGowcDk/view?usp=sharing]

---

## 🧠 What I Learned

- 🌍 How to host a static site on **AWS EC2**
- 💻 Working with essential **Linux commands** (`wget`, `mv`, `unzip`)
- ⚙️ Setting up and managing the **Apache HTTP Server**
- 🔐 Configuring **AWS Security Groups**
- 📦 Manual deployment of a GitHub project to a live web server

---

## 🌱 What's Next?

- ✅ Add a **custom domain** via Route 53  
- 🔐 Configure **HTTPS with SSL** using Let’s Encrypt  
- 🔄 Automate deployment using **Shell scripts** or **Terraform**  
- ⚙️ Implement **CI/CD pipeline** using GitHub Actions  

---

## 🤝 Let’s Connect

If you're also passionate about **cloud**, **DevOps**, or **web deployment**, let’s learn and grow together!  

- 🔗 [LinkedIn](https://www.linkedin.com/in/tanvir-mulla-198309251/)  
- 🐙 [GitHub](https://github.com/tanvirmulla11)

---

Thanks for checking out my work! ⭐  
**Keep building. Keep learning. ☁️**
