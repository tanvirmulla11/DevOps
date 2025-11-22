# Docker Compose – Complete Notes

Docker Compose helps us run **multi-container applications** using a single YAML configuration file. It simplifies container creation, dependency management, networking, and environment configuration.

---

# 📌 What is Docker Compose?

* Docker Compose uses a **YAML file (`docker-compose.yaml`)** to define and run multiple services together.
* After defining all services, we can start everything using:

```bash
docker compose up
```

---

# 🧱 Example: Voting Application Stack

A voting application consists of:

* Python Voting App
* Redis
* PostgreSQL Database
* Worker Service
* Result App

### Without Docker Compose (manual commands)

```bash
docker run --name=redis redis

docker run --name=db postgres:9.4

docker run --name=vote -p 5000:80 voting-app

docker run --name=result -p 5001:80 result-app

docker run --name=worker worker
```

These containers start, but they **cannot talk to each other**, because links/networks are missing.

---

# 🔗 Linking Containers (older method)

To link containers manually:

```bash
docker run --name=vote -p 5000:80 --link redis:redis voting-app
```

```bash
docker run --name=result -p 5001:80 --link db:db result-app
```

Links are now deprecated. Docker Compose with networks is the modern solution.

---

# 📝 Creating a Docker Compose File (Version 1)

Version 1 does not require `version:` keyword.

```yaml
redis:
  image: redis

postgres:
  image: postgres:9.4

vote:
  image: voting-app
  ports:
    - "5000:80"
  links:
    - redis

result:
  image: result-app
  ports:
    - "5001:80"
  links:
    - db

worker:
  image: worker
```

---

# 📝 Docker Compose Version 2

Version 2 requires the **version** keyword and introduces `services:`.

```yaml
version: "2"
services:
  redis:
    image: redis

  postgres:
    image: postgres:9.4

  vote:
    image: voting-app
    ports:
      - "5000:80"
    depends_on:
      - redis

  result:
    image: result-app
    ports:
      - "5001:80"
    depends_on:
      - postgres

  worker:
    image: worker
```

### ✔ Improvements in Version 2

* Automatic **bridge network** created.
* Containers communicate using service names.
* `links` not required.
* `depends_on` introduced to specify **startup order**.

---

# 📝 Docker Compose Version 3

* Latest commonly used version.
* Designed for **Docker Swarm mode**.
* Introduces and removes some options for orchestration.
* Most commonly used in modern production apps.

---

# 🌐 Docker Compose Networks

We can create custom networks such as **frontend** and **backend**.

```yaml
services:
  redis:
    image: redis
    networks:
      - back-end

  postgres:
    image: postgres:9.4
    networks:
      - back-end

  vote:
    image: voting-app
    ports:
      - "5000:80"
    networks:
      - front-end
      - back-end

  result:
    image: result-app
    ports:
      - "5001:80"
    networks:
      - front-end
      - back-end

  worker:
    image: worker
    networks:
      - back-end

networks:
  front-end:
  back-end:
```

---

# 🔐 Environment Variables in Compose

Used for setting things like database username & password.

```yaml
postgres:
  image: postgres:9.4
  networks:
    - back-end
  environment:
    POSTGRES_USER: postgres
    POSTGRES_PASS: postgres
```

---

# 🧪 Task Example: Create Click Counter App

Run a Redis container first, then link a Click Counter app.

### Click Counter runs on port **5000**.

```bash
docker run -d --name=clickcounter --link redis:redis -p 8085:5000 kodekloud/click-counter
```

Now the Click Counter app is accessible at:

```
http://localhost:8085
```

---

# 📘 Summary

* Docker Compose simplifies multi-container deployments.
* YAML used to define services, networks, volumes, dependencies.
* Version 1 → basic
* Version 2 → introduces `services`, networks, `depends_on`
* Version 3 → used for Docker Swarm
* Compose auto-creates networks enabling easy communication.
* Environment variables allow secure configuration.

---
