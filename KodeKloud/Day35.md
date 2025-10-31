# Task: Install Docker CE and Docker Compose on App Server 2

## Steps
## Connect to App Server 2  
```bash
ssh steve@stapp02
```
## Install required dependencies
```bash
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```
## Add Docker CE repository
bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
## Install Docker CE and Docker Compose
```bash
sudo yum install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
## Enable and start Docker service

```bash
sudo systemctl enable docker
sudo systemctl start docker
```
## Verify Docker and Compose installation

```bash
docker --version
docker compose version
```
## Test Docker installation

```bash
sudo docker run --rm hello-world
```
---
