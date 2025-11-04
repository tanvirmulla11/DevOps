# Day 45: Resolve Dockerfile Issues

### Connect to App Server 3
```bash
ssh banner@stapp03
```

### 🔑 Password (if prompted):
```bash
BigGr33n
```

### Switch to root user
```bash
sudo -i
```
### Navigate to the Dockerfile location
```bash
cd /opt/docker
```

### List files to confirm Dockerfile exists
```bash
ls -l
```

### View and fix the Dockerfile
```bash
cat Dockerfile
vi Dockerfile
```
## ✅ Corrected Dockerfile
```bash
FROM httpd:2.4.43

# Update Apache to listen on port 8080
RUN sed -i "s/Listen 80/Listen 8080/g" /usr/local/apache2/conf/httpd.conf

# Enable SSL modules
RUN sed -i '/LoadModule ssl_module modules\/mod_ssl.so/s/^#//g' /usr/local/apache2/conf/httpd.conf
RUN sed -i '/LoadModule socache_shmcb_module modules\/mod_socache_shmcb.so/s/^#//g' /usr/local/apache2/conf/httpd.conf
RUN sed -i '/Include conf\/extra\/httpd-ssl.conf/s/^#//g' /usr/local/apache2/conf/httpd.conf

# Copy SSL certificates
COPY certs/server.crt /usr/local/apache2/conf/server.crt
COPY certs/server.key /usr/local/apache2/conf/server.key

# Copy website files
COPY html/index.html /usr/local/apache2/htdocs/

🔧 Then build the image:
cd /opt/docker
docker build -t httpd-secure .
````
## ✅ Verify:
### docker images

