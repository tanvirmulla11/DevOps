# CMD vs ENTRYPOINT in Docker

Containers are designed to run a **specific task or process** such as hosting a web server, application server, or database. Once the defined task finishes, the container exits.

---

## 🧩 How Containers Work

* A container **lives only as long as the main process inside it is running**.
* If the main process stops (e.g., Nginx/MySQL stops), the container exits.
* So how do we define what process a container should run?
* This is done using **CMD** or **ENTRYPOINT** in the Dockerfile.

---

# 🟦 CMD Instruction

`CMD` defines the **default command** that will run when the container starts.

### ✔ Example

```Dockerfile
CMD ["nginx"]
```

This will start Nginx inside the container.

### ✔ Correct Syntax

```Dockerfile
CMD ["sleep", "5"]   # Correct
CMD ["sleep 5"]       # Incorrect
```

### ✔ Example Usage

```bash
docker build -t ubuntu-sleeper .
docker run ubuntu-sleeper   # sleeps for 5 seconds
```

### ✔ Override CMD at Runtime

```bash
docker run ubuntu-sleeper 10   # sleeps for 10 seconds
```

CMD gets **fully replaced** when parameters are passed.

---

# 🟩 ENTRYPOINT Instruction

`ENTRYPOINT` defines the **main executable** that always runs when the container starts.

### ✔ Example

```Dockerfile
ENTRYPOINT ["sleep"]
```

This forces the container to always run the `sleep` command.

---

# 🔍 CMD vs ENTRYPOINT — Key Difference

| Feature           | CMD                                   | ENTRYPOINT                         |
| ----------------- | ------------------------------------- | ---------------------------------- |
| Purpose           | Default command                       | Main executable command            |
| Runtime Arguments | Replace CMD                           | Appended to ENTRYPOINT             |
| Flexibility       | More flexible                         | More controlled                    |
| Best For          | Default program but can be overridden | Fixed executable + user parameters |

---

# 🛠 Using CMD + ENTRYPOINT Together

To set a **default value** that can still be overridden:

```Dockerfile
FROM ubuntu
ENTRYPOINT ["sleep"]
CMD ["5"]
```

### ✔ Behavior

* If user runs: `docker run image` → sleeps **5 seconds**
* If user runs: `docker run image 10` → sleeps **10 seconds**

This is the **recommended pattern**.

---

# 📘 Summary

* **CMD** → default command (can be replaced entirely).
* **ENTRYPOINT** → fixed command (arguments append).
* **ENTRYPOINT + CMD** → best combination for default values.
---
