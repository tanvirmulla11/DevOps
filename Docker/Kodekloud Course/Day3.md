
# 📘 Docker Course – Day 3 

## 🏷️ 1. TAG — Using Specific Versions

* If you want to run a **specific version** of an image, you need to specify its **tag**.
* Example:

  ```bash
  docker run redis:4.0
  ```
* If no tag is provided → Docker uses the **latest** tag by default.
* Tags help run **older**, **stable**, or **custom** versions of images.

---

## 📌 2. Interactive vs Non-Interactive Shells

### 🔹 Docker containers **do not** have a console by default

→ They print output directly but **cannot take input** unless enabled.

### ✨ Use `-i` and `-t`:

* `-i` → Interactive mode (allows input)
* `-t` → Allocates pseudo-terminal (TTY)
* Combined:

  ```bash
  -it
  ```

  This gives interactive + terminal access.

### 🧪 Examples

```bash
docker run kodekloud/simple-prompt-docker
```

→ Only prints message (no input).

```bash
docker run -i kodekloud/simple-prompt-docker
```

→ Asks for input but does not show proper prompt.

```bash
docker run -it kodekloud/simple-prompt-docker
```

→ Shows:

```
Enter your name:
```

→ Accepts input and prints message.

---

# 🌐 3. Port Mapping (Publishing Ports)

When running apps inside containers:

### ❓ How do we access the application?

Two ways:

### **1. Access using Container IP**

* Every container gets an internal IP
* Only accessible **inside the Docker host**
* Not useful for external users

---

### **2. Map Container Port to Host Port**

Use `-p HostPort:ContainerPort`.

Example:

```bash
docker run -p 80:5000 kodekloud/webapp
```

Meaning:

* Host machine port **80**
* Mapped to container's internal port **5000**
* External users access: `http://<host-ip>:80`

### ❗ Important Rule

* You **cannot** map the same host port twice.

  * Example: You cannot run two containers both using `-p 80:5000`.

---

# 📦 4. Data Persistence (Volume Mapping)

### ❗ Problem

* Docker containers have **isolated file systems**
* If container is deleted → **data is lost**

  * Example: MySQL database inside a container

### ✅ Solution: Volume Mapping

Use the `-v` option to map external folder to container folder.

Example:

```bash
docker run -v /opt/datadir:/var/lib/mysql mysql
```

What this does:

* `/opt/datadir` = folder on your Docker host
* `/var/lib/mysql` = MySQL database location inside container
* MySQL stores all data in `/opt/datadir` on host
  → Even if container is deleted **data remains safe**.

---

# 🔍 5. Inspecting Containers (`docker inspect`)

Use `docker inspect` to view **detailed information** about a container.

Example:

```bash
docker inspect blissful_hopper
```

It returns JSON with:

* State (running, exited)
* Mounts (volumes)
* Network details
* Internal IP address
* Configuration
* Storage details

### Find Internal IP Address

Inside JSON:

```
NetworkSettings → Bridge → IPAddress
```

---

# 📜 6. Viewing Logs of a Detached Container

If a container is running in **detached mode** (`-d`), use:

```bash
docker logs <id_or_name>
```

Useful for:

* Debugging
* Checking server output
* Viewing app logs

---

# 📄 7. Show OS Version of a Container

```bash
docker run ubuntu cat /etc/*release*
```

Prints:

* Ubuntu version
* Build details
* OS information

---

# 📌 Final Summary Table

| Feature                | Command                                        | Explanation                   |
| ---------------------- | ---------------------------------------------- | ----------------------------- |
| Specific image version | `docker run redis:4.0`                         | Run older/specific version    |
| Interactive input      | `docker run -i IMAGE`                          | Allows input                  |
| Terminal access        | `docker run -t IMAGE`                          | Adds TTY                      |
| Full interactive mode  | `docker run -it IMAGE`                         | Input + Terminal              |
| Port mapping           | `docker run -p 80:5000 IMAGE`                  | Host Port 80 → Container 5000 |
| Volume mapping         | `docker run -v /host:/container IMAGE`         | Persistent data               |
| Inspect container      | `docker inspect <id>`                          | See detailed JSON info        |
| View logs              | `docker logs <id>`                             | Read container logs           |
| Internal IP            | `docker inspect` → `NetworkSettings.IPAddress` | Shows container IP            |

---



