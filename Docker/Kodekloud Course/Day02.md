# 📘 Docker Course – Day 2 Notes

Professional, structured, and ready for GitHub or writing in your notebook.

---

## 🚀 **1. `docker run` Command**

* The `docker run` command is used to **run a container from an image**.
* Example: `docker run nginx`

  * If the **nginx image exists locally**, Docker uses it.
  * If the **image does not exist**, Docker automatically **pulls it from Docker Hub**.
  * The image is downloaded **only once**. Next time, Docker uses the **cached local copy**.

---

## 🐳 **2. `docker ps` – View Running Containers**

* Shows **all running containers**.
* Displays details like:

  * Container ID
  * Image name used
  * Current status
  * Container name (Docker assigns a random name if not provided)

### ➤ `docker ps -a`

* Shows **all containers**, including:

  * Running
  * Stopped
  * Exited

---

## 🛑 **3. Stopping & Removing Containers**

### ✔ Stop a running container

```
docker stop <container-name>
```

### ✔ Remove a stopped container

```
docker rm silly_sammet
```

(Replace `silly_sammet` with the actual container name.)

---

## 📦 **4. Working With Images**

### ✔ List all available images

```
docker images
```

### ✔ Remove an image

```
docker rmi nginx
```

> Note: You must delete all containers based on this image before removing it.

### ✔ Pull images without running

```
docker pull nginx
docker pull ubuntu
```

---

## 🐧 **5. Running Ubuntu Containers**

* Ubuntu image is a **base OS image**, not an application.
* Running: `docker run ubuntu` → container **starts and exits immediately**.

Why?
Containers **run only as long as the main process is running**.

* Since Ubuntu has **no default long-running process**, it exits.

### Example with a command:

```
docker run ubuntu sleep 5
```

* The container runs `sleep 5` → waits 5 seconds → exits.

---

## 🔧 **6. Running Commands Inside a Running Container**

* Use `docker exec` to run commands **inside a running container**.

Example: View `/etc/hosts` inside a running Ubuntu container:

```
docker exec distracted_mcclintock cat /etc/hosts
```

---

## 🌐 **7. Running a Web Application Container**

Example image: `kodekloud/simple-webapp`
It runs a web server on **port 8080**.

### ▶ Running in **attached mode** (foreground)

```
docker run kodekloud/simple-webapp
```

* Shows container logs/output on your screen.
* Press **CTRL + C** → stops the container.

### ▶ Running in **detached mode** (background)

```
docker run -d kodekloud/simple-webapp
```

* Runs in background.
* Use `docker ps` to check the container.

### ▶ Attach to running container

```
docker attach <container-id>
```

> You can use only the **first few characters** of the container ID.

Example:

```
docker attach a043d
```

---

## 📝 **Summary Table**

| Command                    | Description                        |
| -------------------------- | ---------------------------------- |
| `docker run nginx`         | Run container from nginx image     |
| `docker ps`                | See running containers             |
| `docker ps -a`             | See all containers                 |
| `docker stop <name>`       | Stop a container                   |
| `docker rm <name>`         | Remove a container                 |
| `docker images`            | List images                        |
| `docker rmi <image>`       | Remove image                       |
| `docker pull <image>`      | Download image only                |
| `docker exec <name> <cmd>` | Execute a command inside container |
| `docker run -d <image>`    | Run container in detached mode     |
| `docker attach <id>`       | Attach to running container        |

---

Just tell me!
