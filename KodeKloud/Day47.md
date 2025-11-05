Day 47 :
# 🐍 Dockerized Python Application – Nautilus Project

This project Dockerizes a Python web application and deploys it on **App Server 3** in the Nautilus Datacenter.

---

## ⚙️ Requirements

- **Base Image:** Any official Python image
- **App Directory:** `/python_app/src/`
- **Dependencies File:** `requirements.txt`
- **App Script:** `server.py`
- **Exposed Container Port:** `8084`
- **Host Port Mapping:** `8095`
- **Image Name:** `nautilus/python-app`
- **Container Name:** `pythonapp_nautilus`

---

## 🚀 Deployment Steps

### 1️⃣ Connect to App Server 3
```bash
ssh banner@stapp03
# Password: BigGr33n
### 2️⃣ Navigate to the App Directory
cd /python_app

### 3️⃣ Create the Dockerfile
sudo vi Dockerfile


### Paste the following content:

# Use an official Python base image
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Copy source code
COPY src/ /app/

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose the application port
EXPOSE 8084
```
# Run the Python server
```bash
CMD ["python", "server.py"]
```

### Save and exit (:wq).

### 4️⃣ Build the Docker Image
```bash
sudo docker build -t nautilus/python-app /python_app
```
### 5️⃣ Run the Container
```bash
sudo docker run -d --name pythonapp_nautilus -p 8095:8084 nautilus/python-app
```
### 6️⃣ Verify the Container
```bash
sudo docker ps
```

### Expected output:
```bash
CONTAINER ID   IMAGE                 PORTS                    NAMES
abcd12345678   nautilus/python-app   0.0.0.0:8095->8084/tcp   pythonapp_nautilus
```
### 7️⃣ Test the Application
```bash
curl http://localhost:8095/
```

### Expected output:
```bash
Hello from Nautilus Python App!
```
