# 🐳 Docker Level 1 – Task 4 (KodeKloud Engineer)
## 📌 Task Description

### The Nautilus DevOps team has a file (/tmp/nautilus.txt.gpg) on the host system that needs to be copied into a running ### Docker container named ubuntu_latest. Your job is to use basic Docker commands to locate the file and copy it into ### the container.

### ✅ Steps to Solve
### 1. Connect to App Server
```bash
ssh tony@stapp01
```
### 2. Check Running & Exited Containers
```bash
docker ps -a
```

### 👉 This lists all containers (running + stopped). Identify the container ubuntu_latest.

### 3. Verify File on Host
```bash
ls -l /tmp/nautilus.txt.gpg
```

### 👉 Confirms that the file exists in /tmp directory.

### 4. Copy File into Container
```bash
docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/tmp/
```

### 👉 This command copies the file from the host into the container’s /tmp/ directory.

### 5. Verify Inside Container (Optional)
```bash
docker exec -it ubuntu_latest ls -l /tmp/
```

### 👉 Confirms the file has been successfully copied.

# 🎯 Outcome

## File nautilus.txt.gpg is successfully copied into /tmp directory inside the ubuntu_latest container.

### Task completed ✅

# images
<img width="1919" height="971" alt="Screenshot 2025-08-27 112914" src="https://github.com/user-attachments/assets/4b465ede-afa7-458c-b4fb-2c00dde7beb5" />
<img width="1919" height="974" alt="Screenshot 2025-08-27 112933" src="https://github.com/user-attachments/assets/0aad26a8-9aee-4ffd-96b5-a5e974c52f14" />



### ✨ Author: Tanvir Mulla
### 🔗 GitHub: tanvirmulla11
