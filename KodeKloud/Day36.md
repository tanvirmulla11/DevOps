# Task: Deploy Nginx Container on Application Server 2

## Steps

## Connect to App Server 2  
```bash
ssh steve@stapp02
```
## Pull the nginx image with alpine tag

```bash
sudo docker pull nginx:alpine
```
## Create and run a container named nginx_2

```bash
sudo docker run -d --name nginx_2 nginx:alpine
```
## Verify the container is running

```bash
sudo docker ps
```
---
