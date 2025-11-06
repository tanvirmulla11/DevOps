# 🐳 KodeKloud Docker Course — Day 1 Notes

## 📘 Objectives
- Understand **what containers are**
- Learn **what Docker is** and **why it’s needed**
- Explore **what Docker can do**
- Learn to **run Docker containers**
- Understand **Docker images**
- Explore **networking in Docker**
- Learn **Docker Compose**
- Understand **core Docker concepts**
- Explore **Docker for Mac/Windows**
- Introduction to **Docker Swarm**
- Compare **Docker vs Kubernetes**

---

## ⚙️ What Can Docker Do?
Docker allows us to run each component of an application in **separate containers**, each with its **own dependencies and libraries** — all on the **same OS and VM** but within **isolated environments**.

Once Docker is installed and configured, developers can launch applications quickly using:
```bash
docker run <image_name>
```
## 📦 What Are Containers?

Containers are lightweight, isolated environments that run processes or services independently.
They have:

- Their own process or service

- Their own network interface

- Their own mounts

They are similar to virtual machines but share the same OS kernel, making them much more efficient.

## 🧱 Example Container Technologies

- LXC

- LXD

- LXCFS

### Docker utilizes LXC containers internally.

## Main Purpose:
Docker is designed to package, containerize, and ship applications — so they can run anywhere, anytime, and as many times as needed.

## 🖥️ Docker vs Virtual Machines
| Feature     | Docker Containers    | Virtual Machines           |
| ----------- | -------------------- | -------------------------- |
| OS          | Share Host OS Kernel | Each has its own OS        |
| Size        | Lightweight (MBs)    | Heavy (GBs)                |
| Boot Time   | Seconds              | Minutes                    |
| Isolation   | Process-level        | Hardware-level             |
| Performance | Near Native          | Overhead due to hypervisor |
| Portability | High                 | Limited                    |

## 🌐 Public Docker Registry — Docker Hub

Docker Hub is the default public registry for storing and retrieving Docker images.

Using the command:
```bash
docker run <image_name>
```

Docker pulls the image from Docker Hub and runs it as a container.

## Example:

We can pull multiple instances like MongoDB, Redis, or Node.js.
A load balancer can manage these instances — if one fails, a new one is automatically started.
