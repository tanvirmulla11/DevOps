# 🚀 DevOps Day 14: Multi-Server Troubleshooting & Standardization

### This task was about fixing a down Apache service caused by a port conflict and then standardizing Apache to run on port 3002 across all app servers.

## 🎯 The Task

### Find the faulty server where Apache was down.

### Fix the issue (stop conflicting service).

### Configure Apache to run on port 3002 on all servers.

### Allow port 3002 in firewall using iptables.

### Verify using curl.

# 🛠️ Bash Script (Run on each server)
#!/bin/bash
# DevOps Day 14 - Apache Fix & Standardization

# Stop conflicting service
sudo systemctl stop sendmail 2>/dev/null
sudo systemctl disable sendmail 2>/dev/null

# Set Apache to port 3002
sudo sed -i 's/^Listen .*/Listen 3002/' /etc/httpd/conf/httpd.conf

# Restart & enable Apache
sudo systemctl restart httpd
sudo systemctl enable httpd

# Open firewall for port 3002
sudo iptables -I INPUT 1 -p tcp --dport 3002 -j ACCEPT
sudo service iptables save

# Verify service
curl http://localhost:3002
---
## ✅ Verification

### Run:
```bash
curl http://stapp01:3002
curl http://stapp02:3002
curl http://stapp03:3002
```
### You should see the Apache default page from all servers.

## images
<img width="1919" height="964" alt="Screenshot 2025-10-02 062550" src="https://github.com/user-attachments/assets/1581c69e-772a-4798-8f3d-70e315977113" />
<img width="1919" height="970" alt="Screenshot 2025-10-02 062602" src="https://github.com/user-attachments/assets/b31873fe-5ee7-4b1f-a1da-22ecd4d57f16" />


