# Docker Networking Complete Notes & Commands

## 📌 Overview

When Docker is installed, it automatically creates **three default networks**:

* **bridge** (default)
* **host**
* **none**

### 🔹 Bridge Network

* Default network for all containers.
* Private internal network on the host.
* Usually uses IP range: `172.17.0.0/16`.
* Containers can communicate internally using these IPs.
* To access containers from outside, use **port mapping**.

### 🔹 Host Network

* Removes network isolation between host and container.
* Container uses the **host’s network stack**.
* No need for port mapping.
* Example: If a container runs on port 5000 → it's directly accessible on port 5000 of the host.

### 🔹 None Network

* No network assigned.
* No access to external networks or other containers.

---

## 📌 Docker Network Commands

### 👉 Check default networks

```bash
docker network ls
```

### 👉 Inspect bridge network

```bash
docker network inspect bridge
```

### 👉 Run a container with different networks

```bash
docker run ubuntu
```

```bash
docker run --network=none ubuntu
```

```bash
docker run --network=host ubuntu
```

---

## 📌 Create a Custom Docker Network

Use **bridge driver** and define your own **subnet**.

```bash
docker network create \
  --driver bridge \
  --subnet 182.18.0.0/16 \
  custom-isolated-network
```

### 👉 List all networks

```bash
docker network ls
```

### 👉 Inspect a network

```bash
docker network inspect custom-isolated-network
```

---

## 📌 Docker Networking Internals

* Docker uses **network namespaces** to isolate containers.
* Uses **virtual ethernet pairs (veth)** to connect containers.
* Docker has a built-in **DNS server** at `127.0.0.11` which resolves container names.
* Containers on the same network can reach each other using their **container names** (e.g., `mysql-db`).

---

# 🚀 Hands-on Lab Commands

Use these commands directly in your practice environment.

## 1️⃣ Check subnet configured on bridge network

```bash
docker network inspect bridge
```

---

## 2️⃣ Run a container in `none` network

Create a container named **alpine-2**:

```bash
docker run --name alpine-2 --network=none alpine
```

---

## 3️⃣ Create a custom network `wp-mysql-network`

Subnet: `182.18.0.0/24`
Gateway: `182.18.0.1`

```bash
docker network create \
  --driver bridge \
  --subnet 182.18.0.0/24 \
  --gateway 182.18.0.1 \
  wp-mysql-network
```

### 👉 Inspect the network

```bash
docker network inspect wp-mysql-network
```

---

## 4️⃣ Deploy MySQL Container

Image: `mysql:5.7`
Name: `mysql-db`
Root Password: `db_pass123`

```bash
docker run -d \
  -e MYSQL_ROOT_PASSWORD=db_pass123 \
  --name mysql-db \
  --network wp-mysql-network \
  mysql:5.7
```

---

## 5️⃣ Deploy Web Application

Image: `kodekloud/simple-webapp-mysql`
Name: `webapp`
Expose port: `8080 → 38080` on host

Environment variables:

* `DB_Host=mysql-db`
* `DB_Password=db_pass123`

```bash
docker run \
  --network=wp-mysql-network \
  -e DB_Host=mysql-db \
  -e DB_Password=db_pass123 \
  -p 38080:8080 \
  --name webapp \
  --link mysql-db:mysql-db \
  -d kodekloud/simple-webapp-mysql
```
You can use this for:

* GitHub repository documentation
* Writing in your notebook
* Docker learning & interview preparat

