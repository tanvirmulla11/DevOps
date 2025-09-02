# 🚀 Docker Level 1 – Task 3 (KodeKloud)
## 📌 Task Description

### The Nautilus DevOps team is managing multiple application containers on App Server 1.
### Some unused containers were found running, and the task was to:

### 1.Check running/stopped containers

### 2.Stop the specific container

### 3.Remove the stopped container

### 4.Verify that the container is removed successfully

## 🛠️ Steps to Solve
```bash
# Step 1: SSH into App Server 1
ssh tony@stapp01

# Step 2: List all running and stopped containers
docker ps -a

# Step 3: Stop the unwanted container (replace <container_id> with actual ID)
docker stop <container_id>

# Step 4: Remove the stopped container
docker rm <container_id>

# Step 5: Verify removal
docker ps -a
```
---
## ✅ Expected Outcome

### The specified container should be stopped and removed successfully.

### docker ps -a should not list the removed container anymore.
---
# 📂 screenshots
<img width="1919" height="966" alt="Screenshot 2025-08-27 112310" src="https://github.com/user-attachments/assets/ce193360-080c-490e-922b-81158873903a" />
<img width="1919" height="970" alt="Screenshot 2025-08-27 112333" src="https://github.com/user-attachments/assets/78d97758-e2ea-4c4b-afd3-5c48c8881faf" />

# 👉 Feel free to ⭐ this repo if you find it helpful!
