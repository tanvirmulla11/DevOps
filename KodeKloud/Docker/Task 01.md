# 🐳 Task 1 – Install and Run Docker (KodeKloud – Docker Level 1)
## 📌 Task Description

### The Nautilus DevOps team aims to containerize applications. As part of this process, Docker needs to be installed and tested on App Server 2.

### Your task is to:

### 1.Install Docker on CentOS.

### 2.Start and enable the Docker service.

### 3.Run a test container (hello-world) to verify the setup.

# ✅ Step-by-Step Solution

### 1️⃣ Install Required Dependencies
```bash
sudo dnf -y install dnf-plugins-core
```

### 2️⃣ Add Docker Repository
```bash
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```
### 3️⃣ Install Docker Packages
```bash
sudo dnf install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
### 4️⃣ Enable and Start Docker Service
```bash
sudo systemctl enable --now docker
```
### 5️⃣ Verify Docker Installation by Running Test Container
```bash
sudo docker run hello-world
```
# 📊 Verification

### The hello-world container should output a message confirming successful installation.

## Run the following command to check Docker version:
```bash
docker --version
```
---
# 🎯 Outcome

### Docker successfully installed.

### Docker service running and enabled at startup.

### Verified by running the hello-world container.

# images
<img width="1919" height="825" alt="Screenshot 2025-08-27 110618" src="https://github.com/user-attachments/assets/f8bfa9aa-c862-4837-93e4-99f95c007848" />
<img width="1919" height="973" alt="Screenshot 2025-08-27 110639" src="https://github.com/user-attachments/assets/25b61cd0-a08a-46be-9f7b-6f60f77d3bf1" />



### ⚡ Task Completed – Docker Level 1 (Task 1) in KodeKloud
