# 🐳 Docker Engine, Storage & Containerization 

## ✅ Docker Engine Overview
When Docker is installed on a Linux host, it actually includes **three major components**:

### 1. Docker Daemon
- A background service that manages Docker objects such as:
  - Images
  - Containers
  - Volumes
  - Networks

### 2. REST API Server
- An API interface used by programs and tools to communicate with the Docker Daemon.
- Developers can build their own tools using Docker’s REST API.

### 3. Docker CLI
- A command-line interface to interact with the Docker Daemon.
- Performs actions such as:
  - Running containers
  - Stopping containers
  - Deleting images
- Uses the REST API internally.
- CLI can work on a **remote host** using the `-H` option:

```bash
docker -H=remote-docker-engine:2375
docker -H=10.123.2.1:2375 run nginx
```

---

## 🧱 How Applications Are Containerized
Docker uses **namespaces** to isolate processes and resources.

### Namespaces Used:
- **PID namespace** → Isolated process IDs  
- **Network namespace** → Independent network stack  
- **IPC namespace** → Inter-process communication isolation  
- **Mount namespace** → Separate filesystem mounts  
- **UTS namespace** → Hostname isolation

Even though all processes run on the same host, they are **separated logically** inside containers.

---

## ⚙️ Control Groups (cgroups)
Docker uses **cgroups** to limit hardware resources per container.

### CPU Limit Example
```bash
docker run --cpus=.5 ubuntu
```
➡️ Limits container to **50% CPU**.

### Memory Limit Example
```bash
docker run --memory=100m ubuntu
```
➡️ Container cannot exceed **100 MB RAM**.

---

# 📦 Docker Storage

## 📁 Where Docker Stores Data
Docker maintains all its data under:

```
/var/lib/docker
```

Contains directories like:
- `aufs/`
- `containers/`
- `images/`
- `volumes/`

---

## 🧱 Layered Architecture
Each instruction in a Dockerfile creates a new **image layer**.

If two Dockerfiles share the first few steps, Docker **reuses cached layers**, improving build speed.

### Image Layers
- Read-only  
- Cannot be modified after creation  

### Container Layer
- Writable  
- Stores:
  - User-generated files  
  - Logs  
  - Temporary data  
- Deleted when the container is removed  

---

## 📝 Copy-on-Write Mechanism
If a container modifies a file that exists in a **read-only image layer**, Docker:
1. Copies the file to the writable container layer  
2. Modifies it there  

Image layers remain unchanged.

---

# 🗄️ Persistent Storage

## 🔹 Why Use Volumes?
Container data is **lost** when the container is deleted.  
Volumes allow data to persist.

### Create a Volume
```bash
docker volume create data_volume
```

### Run a container with a volume
```bash
docker run -v data_volume:/var/lib/mysql mysql
```

Even if the container is destroyed, the volume remains.

### Anonymous Volume
```bash
docker run -v /var/lib/mysql mysql
```
Docker creates a random volume under `/var/lib/docker/volumes`.

---

# 📚 Volume Mounts vs Bind Mounts

| Type | Source | Target | Use Case |
|------|--------|--------|----------|
| **Volume Mount** | `/var/lib/docker/volumes` | Container directory | Persistent container data |
| **Bind Mount** | Any host directory | Container directory | Use host filesystem directly |

### New Syntax (`--mount`)
```bash
docker run \
  --mount type=bind,source=/opt/data,target=/var/lib/mysql \
  mysql
```

---

# 🗄️ Storage Drivers
Docker uses storage drivers to enable layered filesystems.

Common drivers:
- AUFS  
- BTRFS  
- VFS  
- Device Mapper  
- Overlay  
- Overlay2 (recommended)

Docker selects the best available driver automatically based on OS.

Example:
- **Ubuntu** → AUFS or Overlay2  
- **CentOS/Fedora** → Device Mapper or Overlay2  

---

# 🧪 Task: Run a MySQL Container with Volume Mapping

### Requirement
- Container name: `mysql-db`  
- Root password: `db_pass123`  
- MySQL data path: `/var/lib/mysql`  
- Data should persist at: `/opt/data` on host  

### ✅ Solution Command
```bash
docker run -v /opt/data:/var/lib/mysql \
  -d --name mysql-db \
  -e MYSQL_ROOT_PASSWORD=db_pass123 \
  mysql
```

---

