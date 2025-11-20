
# 📦 **How to Create Your Own Docker Image (Beginner-Friendly Guide)**
---
## 🔧 **Steps to Create Your Own Docker Image**

### **Step 1: Choose Base OS (Ubuntu)**

Every Docker image must be based on another image.

```dockerfile
FROM ubuntu:latest
```

---

### **Step 2: Update apt Repository**

```dockerfile
RUN apt-get update
```

---

### **Step 3: Install System Dependencies**

```dockerfile
RUN apt-get install -y python3 python3-pip
```

---

### **Step 4: Install Python Dependencies (Flask, MySQL Driver)**

```dockerfile
RUN pip install flask
RUN pip install flask-mysql
```

---

### **Step 5: Copy Source Code to `/opt` Directory**

```dockerfile
COPY ./source-code /opt/source-code
```

---

### **Step 6: Run Web Server (Flask)**

```dockerfile
ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run --host=0.0.0.0
```

---

## 📝 **Complete Dockerfile Example**

```dockerfile
# Base Image
FROM ubuntu:latest

# Update Repository
RUN apt-get update

# Install Dependencies
RUN apt-get install -y python3 python3-pip

# Install Python Packages
RUN pip install flask
RUN pip install flask-mysql

# Copy Application Code
COPY ./source-code /opt/source-code

# Run Flask Web Server
ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run --host=0.0.0.0
```

---

## 🛠️ **Build Your Image**

```bash
docker build . -t tanvir/my-custom-app
```

---

## 📤 **Push Image to Docker Hub**

```bash
docker push tanvir/my-custom-app
```

---

## 📚 **What is a Dockerfile?**

* A Dockerfile is a **text file** with instructions to build a Docker image.
* Instructions are written in **CAPITAL LETTERS** (FROM, RUN, COPY, ENTRYPOINT).
* Each instruction creates a **new image layer**.
* Docker uses **cached layers** to speed up image rebuilds.
* Arguments (right side) tell Docker what to do.

---

## 🧱 **Layered Architecture**

* Docker builds images in layers.
* If a step fails, after fixing it you **don't need to rebuild everything**.
* Docker reuses cached layers → **faster builds**.
* Very useful when your source code changes frequently.

---

## 🧰 **Useful Commands**

### **View Image History**

```bash
docker history tanvir/simple-webapp
```

---

### **Run Container with Environment Variables**

Example: Set color of a web app.

```bash
docker run -p 38282:8080 --name blue-app -e APP_COLOR=blue -d kodekloud/simple-webapp
```

Check environment variables inside container:

```bash
docker exec -it blue-app env
```

---

## 🗄️ **MYSQL Example – Set Root Password**

Task: Set root password to `db_pass123`.

### **Solution**

```bash
docker run -d -e MYSQL_ROOT_PASSWORD=db_pass123 --name mysql-db mysql
```

Check env:

```bash
docker exec -it mysql-db env
```

---

# ⭐ Output Example

```
MYSQL_ROOT_PASSWORD=db_pass123
MYSQL_VERSION=9.5.0
PATH=...
```

---

## 🎯 **What Can You Containerize?**

You can containerize almost everything:

* Databases
* Web apps
* Operating systems
* Development tools
* Browsers
* Utilities (curl)
* Apps like Spotify, Skype, VS Code
* Your own custom applications

---

