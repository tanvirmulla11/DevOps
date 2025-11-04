
# Task: Create a Custom Apache Image on Port 8082 (App Server 2)
```bash
SSH to App Server 2
ssh steve@stapp02
```

### Become root (or use sudo for each command)
```bash
sudo -i
```

### Create the docker build directory and open Dockerfile (capital D)
```bash
mkdir -p /opt/docker
cd /opt/docker
sudo vi /opt/docker/Dockerfile
```

### Put the following exact content into /opt/docker/Dockerfile (save & exit):
```bash
# /opt/docker/Dockerfile
FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

# Install apache2
RUN apt-get update && \
    apt-get install -y apache2 && \
    # change Apache listen port from 80 to 8082 (ports.conf)
    sed -i 's/^Listen 80$/Listen 8082/' /etc/apache2/ports.conf && \
    # update default virtual host to use 8082
    if [ -f /etc/apache2/sites-available/000-default.conf ]; then \
      sed -i 's/<VirtualHost \\*:80>/<VirtualHost *:8082>/' /etc/apache2/sites-available/000-default.conf; \
    fi && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

EXPOSE 8082

# run Apache in foreground
CMD ["apachectl", "-D", "FOREGROUND"]
```

### Build the image (from /opt/docker)
```bash
cd /opt/docker
sudo docker build -t blog-apache:8082 .
```

### Verify image created
```bash
sudo docker images | grep blog-apache
```

### (Optional) Run a container from the image and map host port 8082 → container 8082 to test
```bash
sudo docker run -d --name blog_test -p 8082:8082 blog-apache:8082
```

### Verify container is running
```bash
sudo docker ps --filter name=blog_test
```

### Test Apache on the host (from App Server 2)
```bash
curl -I http://localhost:8082
# or
curl http://localhost:8082

```
### When satisfied, stop/remove test container (optional)
```bash
sudo docker stop blog_test
sudo docker rm blog_test
```
