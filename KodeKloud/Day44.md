
# Day:44

```bash
SSH into App Server 2
ssh steve@stapp02
```


### Switch to root user (if needed)
```bash
sudo -i
```


### Create the required directory (if not exists)
```bash
mkdir -p /opt/docker
cd /opt/docker
```


### Create the docker-compose.yml file
```bash
vi /opt/docker/docker-compose.yml
```

```bash
### Add the following content exactly:
version: '3'
services:
  webserver:
    image: httpd:latest
    container_name: httpd
    ports:
      - "8082:80"
    volumes:
      - /opt/devops:/usr/local/apache2/htdocs
```


### Save and exit (:wq in vi)


### Start the container using docker compose
```bash
sudo docker compose -f /opt/docker/docker-compose.yml up -d
```


### Verify the container is running
```bash
sudo docker ps
```
## ✅ Expected output example:
### CONTAINER ID   IMAGE          COMMAND              STATUS         PORTS                  NAMES
### abcd1234efgh   httpd:latest   "httpd-foreground"   Up X seconds   0.0.0.0:8082->80/tcp   httpd



### (Optional) Test the web server
```bash
curl -I http://localhost:8082
```
### You should see:
### HTTP/1.1 200 OK
### Server: Apache/2.4.x (Unix)




## ✅ Task Completed Summary


### Container name: httpd


### Image: httpd:latest


### Host port 8082 → container port 80


### Volume mapped: /opt/devops → /usr/local/apache2/htdocs


### Deployed via /opt/docker/docker-compose.yml
