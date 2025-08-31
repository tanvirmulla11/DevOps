 # Docker Task 2 – Deploy Nginx Container (KodeKloud Level 1)
## 📌 Task Description
### As part of KodeKloud Docker Level 1 Labs, the objective of this task was to deploy an Nginx container on Application Server 2 (stapp02) using Docker.
## 🛠️ Steps Performed
### 1. Connect to Application Server 2
```bash
ssh steave@stapp02
```
### 2. Verify Existing Containers
```bash
docker ps -a
```
### 3. Run Nginx Container in Detached Mode
```bash
docker run -d --name nginx_2 nginx:alpine
```

### -d → Run container in detached mode (background)

### --name nginx_2 → Assigns a custom container name

### nginx:alpine → Lightweight Alpine-based Nginx image

### 4. Validate Running Container
```bash
docker ps
```

### Expected output should show nginx_2 container in Up status.

# ✅ Outcome

### Successfully deployed an Nginx container on App Server 2.

### Task completed and verified in KodeKloud Level 1 Docker Labs.

# 📸 Proof of Completion
<img width="1864" height="918" alt="Screenshot 2025-08-27 111341" src="https://github.com/user-attachments/assets/34a80c50-387a-43d4-b8fe-7902d33197cd" />
<img width="1919" height="971" alt="Screenshot 2025-08-27 111359" src="https://github.com/user-attachments/assets/98597483-e597-46de-aaa9-697a5b93d9f3" />


## 🔗 References

### KodeKloud Labs

### Docker Official Documentation
