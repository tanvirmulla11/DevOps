# 🚀 Docker Compose Deployment – PHP + MariaDB Stack

This project deploys a two-container stack (`php_host` + `mysql_host`) on App Server 3 using Docker Compose.

---

## 🧩 Requirements

- **Web Service**
  - Container Name: `php_host`
  - Image: `php:apache`
  - Ports: `8082:80`
  - Volume: `/var/www/html:/var/www/html`

- **Database Service**
  - Container Name: `mysql_host`
  - Image: `mariadb:latest`
  - Ports: `3306:3306`
  - Volume: `/var/lib/mysql:/var/lib/mysql`
  - Environment:
    - `MYSQL_DATABASE=database_host`
    - `MYSQL_USER=nautilus_user`
    - `MYSQL_PASSWORD=ComplexPass@123`
    - `MYSQL_ROOT_PASSWORD=Root@123`

---

## ⚙️ Steps to Deploy

## 1️⃣ Connect to App Server 3
```bash
ssh banner@stapp03
# Password: BigGr33n
```
## 2️⃣ Create Required Directories
```bash
sudo mkdir -p /opt/security /var/www/html /var/lib/mysql
```
## 3️⃣ Create Docker Compose File
```bash
sudo vi /opt/security/docker-compose.yml

version: '3.8'

services:
  web:
    image: php:apache
    container_name: php_host
    ports:
      - "8082:80"
    volumes:
      - /var/www/html:/var/www/html

  db:
    image: mariadb:latest
    container_name: mysql_host
    ports:
      - "3306:3306"
    volumes:
      - /var/lib/mysql:/var/lib/mysql
    environment:
      MYSQL_DATABASE: database_host
      MYSQL_USER: nautilus_user
      MYSQL_PASSWORD: ComplexPass@123
      MYSQL_ROOT_PASSWORD: Root@123
```
## 4️⃣ Launch Containers
```bash
cd /opt/security
sudo docker compose up -d
```
## 5️⃣ Verify
```bash
sudo docker ps
```

### You should see:
```bash

php_host     Up  (0.0.0.0:8082->80/tcp)
mysql_host   Up  (0.0.0.0:3306->3306/tcp)
```
## 6️⃣ Test Web Access
```bash
curl http://stapp03:8082/
````

### Output:
```bash
Welcome to xFusionCorp Industries!
```
