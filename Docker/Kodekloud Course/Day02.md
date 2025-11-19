


# 📘 Docker Course – Day 2 Notes

## 📌 1. `docker run`

* The `docker run` command is used to **run a container from an image**.
* Example:

  ```bash
  docker run nginx
  ```

  * If the image exists locally → container starts.
  * If not, Docker pulls the image from Docker Hub automatically (only first time).

---

## 📌 2. `docker ps`

* Shows **all running containers**.
* Displays:

  * Container ID
  * Image name
  * Status
  * Container name (randomly generated)
* Command:

  ```bash
  docker ps
  ```

### Show **all** containers (running + stopped/exited)

```bash
docker ps -a
```

---

## 📌 3. Stop & Remove Containers

### Stop a running container

```bash
docker stop <container_name>
```

### Remove a stopped container

```bash
docker rm silly_sammet
```

### Remove multiple containers

```bash
docker rm <id1> <id2> <id3>
```

---

## 📌 4. Docker Images

### Show images

```bash
docker images
```

### Remove image

```bash
docker rmi nginx
```

⚠️ You must delete all containers based on that image before removing it.

### Only pull (download) an image

```bash
docker pull nginx
docker pull ubuntu
```

---

## 📌 5. Why Ubuntu Container Exits Immediately?

* Containers are **not full OS** → they run **a single process**.
* They stop when the main process exits.
* Running ubuntu:

  ```bash
  docker run ubuntu
  ```

  → It exits immediately because it has **no task to run**.

### Example with a command

```bash
docker run ubuntu sleep 5
```

Container runs for 5 seconds → stops.

---

## 📌 6. `docker exec` – Run Commands in a Running Container

Used when you want to **run a command inside a running container**.

Example:

```bash
docker exec distracted_mcclintock cat /etc/hosts
```

---

## 📌 7. Foreground vs Detached Mode

### Foreground (attached mode)

```bash
docker run kodekloud/simple-webapp
```

* Shows logs/output on screen.
* `Ctrl + C` stops container.

### Detached mode (background)

```bash
docker run -d kodekloud/simple-webapp
```

* Runs in background.
* Use `docker ps` to check status.

### Attach to running container

```bash
docker attach <container_id>
```

---

## 📌 8. Interactive Terminal (`-it`)

```bash
docker run -it centos bash
```

* Opens terminal **inside the container**.

---

## 📌 9. Troubleshooting

If you try to remove an image in use:

```
Error: unable to remove repository reference "ubuntu"
Reason: container exists using this image
```

Solution:

1. Stop container
2. Remove container
3. Remove image

---

## 📌 10. `docker exec` OS Info Example

```bash
docker exec <id_or_name> cat /etc/*release*
```

Shows OS version inside container.

---

## 📌 11. Assign Custom Container Name

```bash
docker run -d --name webapp nginx:1.14-alpine
```

---

# ✅ Summary Table

| Command                     | Purpose                        |
| --------------------------- | ------------------------------ |
| `docker run IMAGE`          | Run a container from image     |
| `docker pull IMAGE`         | Only download image            |
| `docker ps`                 | List running containers        |
| `docker ps -a`              | List all containers            |
| `docker stop CONTAINER`     | Stop running container         |
| `docker rm CONTAINER`       | Remove stopped container       |
| `docker rmi IMAGE`          | Remove image                   |
| `docker exec CONTAINER CMD` | Run command in container       |
| `docker run -d IMAGE`       | Run container in background    |
| `docker run -it IMAGE bash` | Open terminal inside container |

---


