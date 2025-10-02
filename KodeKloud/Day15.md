# 🔒 DevOps Day 15: Deploying Secure Nginx with SSL

### This task was about deploying a secure static website with Nginx + SSL on App Server 2.

# 🎯 The Task

### Install and configure Nginx.

### Use provided SSL cert (nautilus.crt) and key (nautilus.key).

### Serve content with index.html showing "Welcome!".

### Ensure website works via HTTPS (curl -k https://stapp02).

# 🛠️ Key Steps
# 1. Install Nginx
sudo yum install -y nginx

# 2. Setup SSL directory and move files
sudo mkdir -p /etc/nginx/ssl
sudo mv /tmp/nautilus.crt /etc/nginx/ssl/
sudo mv /tmp/nautilus.key /etc/nginx/ssl/
sudo chmod 600 /etc/nginx/ssl/nautilus.key

# 3. Configure Nginx SSL server block (in /etc/nginx/nginx.conf)
server {
    listen 443 ssl;
    server_name stapp02.stratos.xfusioncorp.com;
    root /usr/share/nginx/html;

    ssl_certificate "/etc/nginx/ssl/nautilus.crt";
    ssl_certificate_key "/etc/nginx/ssl/nautilus.key";
}

# 4. Test & restart Nginx
sudo nginx -t
sudo systemctl start nginx
sudo systemctl enable nginx

# 5. Add firewall rule for HTTPS
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload

# 6. Deploy content
echo "Welcome!" | sudo tee /usr/share/nginx/html/index.html
---
## ✅ Verification

### Run from jump host:
```bash
curl -k https://stapp02
```
## Expected output:
```bash
 welcome!!
```
## Images
<img width="1919" height="967" alt="Screenshot 2025-10-02 063302" src="https://github.com/user-attachments/assets/3847cf68-1792-4114-9223-34ced6757d36" />
<img width="1919" height="969" alt="Screenshot 2025-10-02 063326" src="https://github.com/user-attachments/assets/bc8fbd12-26d6-4caf-9659-1212b5d8a3f1" />



