# 🚀 DevOps Day 16 – Building a High-Availability Stack with Nginx Load Balancer
## 📘 Overview

### Today’s task focused on improving scalability and availability by configuring Nginx as a load balancer in front of multiple backend web servers. This setup ensures better traffic distribution, improved performance, and fault tolerance — essential traits of modern infrastructure.

## 🧠 The Task

### Install and configure Nginx on the Load Balancer (LBR) server.

### Distribute traffic across three Apache app servers.

### Identify backend ports without modifying existing Apache configurations.

## ⚙️ Step-by-Step Implementation
### 1️⃣ Investigation Phase

### Before setting up Nginx, I verified the backend ports and service status:
```bash
sudo yum install -y net-tools
sudo netstat -tulpn | grep httpd
```

### ✅ Found Apache running on port 6200 across all app servers.

### 2️⃣ Load Balancer Setup

On the LBR server:
```bash
sudo yum install -y nginx
sudo vi /etc/nginx/nginx.conf

Add inside the http {} block:
upstream my_app_servers {
    server 172.16.238.10:6200;
    server 172.16.238.11:6200;
    server 172.16.238.12:6200;
}

Modify the location / block:
location / {
    proxy_pass http://my_app_servers;
}
```

## Validate and start the service:
```bash
sudo nginx -t
sudo systemctl start nginx
sudo systemctl enable nginx
```
## 3️⃣ Verification

### Accessed the app via the lab UI (StaticApp button) — successful response confirmed proper load balancing between backend servers.

## 💡 Key Takeaways

### Always investigate before configuring — never assume defaults.

### Use net-tools to diagnose missing commands or port issues.

### Load balancing is a core step toward high availability and scalability.

## 🧩 Tech Stack

### Nginx – Load Balancer

### Apache (httpd) – Backend Servers

### CentOS / RHEL – OS Environment

## 🏁 Outcome

### ✅ Successfully implemented a high-availability setup using Nginx load balancing over three backend servers running Apache on port 6200.
