# 🖼 Docker Images

Welcome to **Day X** of your Docker journey! Today we explore one of the core components of Docker: **Docker Images**. Understanding how to use and create images is essential for containerized development.

---

## 📦 What are Docker Images?

A **Docker Image** is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software:
- Code
- Runtime
- Libraries
- Environment variables
- Configuration files

💡 **Think of an image as a blueprint for a container.**

---

## 📥 Pulling Images from Docker Hub

Docker Hub is the default registry from where Docker pulls images.

### 🔧 Example: Pulling the official NGINX image
```bash
docker pull nginx
```
## You can now run it:
```bash
docker run -d -p 8080:80 nginx
```
Visit http://localhost:8080 in your browser.

## 🛠 Creating Custom Docker Images with Dockerfile
```bash
# Use official Python base image
FROM python:3.9

# Set working directory
WORKDIR /app

# Copy current directory to /app in container
COPY . /app

# Install dependencies
RUN pip install -r requirements.txt

# Run the application
CMD ["python", "app.py"]

```
## 🚀 Build your image
```bash
docker build -t my-python-app .

```
##  🧪 Run your image
```bash
docker run -d -p 5000:5000 my-python-app

```
##  🗂 Best Practices

Use small base images (like alpine) to reduce image size.

Combine RUN commands to minimize image layers.

Use .dockerignore to exclude unnecessary files during build.



## 📚 Resources
🔗 Docker Hub

📘 Official Dockerfile Reference

📕 Docker Image Best Practices



## 🔚 Final Notes

Docker images are foundational to building and sharing containerized applications. Mastering image creation and optimization will make your development more efficient and scalable.

## ✅ Next Up:

👉 Learn about Docker Containers and how to manage them using commands like docker run, docker ps, docker stop.


