# DevOps Day 20: Mastering the Nginx + PHP-FPM Stack

Today's task was to configure a modern, high-performance **web stack using Nginx and PHP-FPM** — a setup widely used for PHP applications because of its **speed, scalability, and efficiency** compared to traditional Apache setups.

This README documents the full working setup — including installation, configuration, and verification — all in one place.

---

## 🧭 The Task

Deploy a PHP-based web application using:
- **Nginx** (listening on a custom port, e.g., 8097)
- **PHP-FPM 8.2**
- **Unix socket communication** between Nginx and PHP-FPM
- Serve content from `/var/www/html`

---

## 🧱 Step-by-Step Solution

### **Phase 1: Installing PHP 8.2**

By default, PHP 8.2 isn’t available in system repositories, so we’ll use the **Remi repository**.

```bash
# Connect to App Server 3
ssh banner@stapp03

# Install EPEL and Remi repositories
sudo dnf install epel-release -y
sudo dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm -y

# Enable PHP 8.2 module
sudo dnf module enable php:remi-8.2 -y

# Install PHP-FPM and extensions
sudo dnf install php-fpm php-cli php-mysqlnd php-gd php-xml php-mbstring php-opcache -y

# Verify PHP version
php -v
```
## ✅ Expected Output:
### PHP 8.2.x (cli) confirming the correct version is installed.
### Phase 2: Configuring PHP-FPM

### We’ll now configure PHP-FPM to use a Unix socket and run as the nginx user for security and performance.
```bash
sudo vi /etc/php-fpm.d/www.conf
```

### Update or add these lines:
```bash
listen = /var/run/php-fpm/default.sock
listen.owner = nginx
listen.group = nginx
listen.mode = 0660
user = nginx
group = nginx
```

### Start and enable PHP-FPM service:
```bash
sudo systemctl start php-fpm
sudo systemctl enable php-fpm
```

## ✅ Check Status:
```bash
systemctl status php-fpm
```

### If it’s running without errors, the PHP-FPM service is ready.

### Phase 3: Configuring Nginx

### Instead of editing the main nginx.conf, create a separate configuration file for our PHP application (a best practice).
```bash
sudo vi /etc/nginx/conf.d/phpapp.conf
```

### Add this configuration:
```bash
server {
    listen 8097;
    server_name stapp03;
    root /var/www/html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass unix:/var/run/php-fpm/default.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}

```
### Test and restart Nginx:
```bash
sudo nginx -t
sudo systemctl restart nginx
sudo systemctl enable nginx
```

### ✅ Expected Output:
```bash
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
### Phase 4: Final Verification

### To confirm the setup works:
```bash
curl http://stapp03:8097/index.php
curl http://stapp03:8097/info.php
```

### If you see PHP info or “Hello World” output, the Nginx + PHP-FPM stack is working perfectly!
 
### 🧠 Deep Dive: Why This Setup?
### Component	Purpose
### Nginx	Handles static content and forwards PHP requests to PHP-FPM
### PHP-FPM	Manages PHP processes efficiently using FastCGI
### Unix Socket	Enables secure and fast local communication between Nginx and PHP-FPM
### Custom Config File	Keeps main Nginx config clean and modular

### This approach is faster and more scalable than traditional Apache with mod_php because:

### Nginx is event-driven and handles concurrency efficiently.

### PHP-FPM runs separately, improving fault isolation and performance.

### Unix sockets are faster and more secure than TCP for local communicati
---
