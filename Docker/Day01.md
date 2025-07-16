# 🚀 Day 1: Docker In One Shot – Kickstarting Container Mastery

Welcome to **Day 1** of my Docker learning journey! Today, I started exploring Docker — one of the most powerful tools in modern DevOps and cloud-native development.  
This session is part of a deep-dive series covering Docker from scratch to real-world projects.

---

## 🎯 Topics Covered

1. ### 📦 Introduction to Docker
   - What is Docker?
   - Why use containers over virtual machines?
   - Use cases and benefits in development & deployment.

2. ### 🏗 Docker Architecture
   - Client–Server model
   - Docker Daemon, REST API, and CLI
   - Docker Objects: Images, Containers, Volumes, Networks

3. ### 🛠 Installing Docker
   - Installing Docker Engine on Ubuntu
   - Verifying installation with `docker --version`
   - First command: `docker run hello-world`

4. ### 🖼 Docker Images
   - What are Docker Images?
   - Pulling from Docker Hub: `docker pull nginx`
   - Creating custom images with Dockerfile

5. ### 📦 Docker Containers
   - Running containers: `docker run -d -p 80:80 nginx`
   - Lifecycle commands: start, stop, restart, remove
   - Inspecting with `docker ps`, `docker inspect`

6. ### 🌐 Docker Networking
   - Bridge, Host, and Overlay networks
   - Port binding and container-to-container communication

7. ### 💾 Docker Volumes and Storage
   - Difference between Volumes, Bind Mounts, tmpfs
   - Persisting data in containers using `docker volume create`

8. ### 🧩 Docker Compose
   - Defining multi-container applications using `docker-compose.yml`
   - Commands: `docker-compose up`, `docker-compose down`

9. ### 🗃 Docker Registry
   - Docker Hub and private registries
   - Pushing images to Docker Hub with `docker push`

10. ### 🏗 Multi-Stage Docker Builds
   - Building optimized and lightweight images
   - Writing efficient Dockerfiles for production

11. ### 📈 Monitoring and Logging in Docker
   - Logs with `docker logs <container>`
   - Monitoring with `docker stats`

12. ### ☸ Orchestrating Docker with Kubernetes (Intro)
   - Why Docker + Kubernetes?
   - Overview of Pods, Nodes, and Clusters

---

## 💻 Projects Covered

### ✅ Project 1: 3-Tier Application with Docker Compose
- Frontend, Backend, and Database in one stack
- All managed with `docker-compose`

### ✅ Project 2: Deploying a Web Application with Nginx & MySQL
- Web server using Nginx
- Persistent MySQL database
- Custom app container

---

## 🧠 Key Learnings

- Docker makes app deployment seamless and reproducible.
- Containers are fast, portable, and ideal for microservices.
- Compose helps manage multi-container environments efficiently.
- Multi-stage builds = smaller images, better performance.
- Registry integration enables easy CI/CD workflows.

---

## 🔗 Resources

- [Docker Docs](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Play With Docker (Online Lab)](https://labs.play-with-docker.com/)
- [Install Docker on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

---


🎯 Stay tuned for more hands-on Docker & DevOps practice in upcoming days!

