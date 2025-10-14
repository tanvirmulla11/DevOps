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
