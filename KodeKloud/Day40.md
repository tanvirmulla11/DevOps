# Configure Apache on Port 5003 in kkloud Container

##  Connect to App Server 1 and check running containers:
```bash
sudo docker ps
```
## Access kkloud container:

```bash
sudo docker exec -it kkloud /bin/bash
```
## Update and install Apache:

```bash
apt update && apt install apache2 -y
```
## Change Apache port:

```bash
sed -i 's/80/5003/g' /etc/apache2/ports.conf
sed -i 's/*:80/*:5003/g' /etc/apache2/sites-enabled/000-default.conf
```
## Restart and verify:

```bash
service apache2 restart
netstat -tuln | grep 5003
```
## ✅ Apache now runs on port 5003 in the kkloud container.
