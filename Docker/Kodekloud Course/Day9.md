
# Docker Registry – Complete Notes 

## 🌧️ Introduction: What Is a Docker Registry?

If **containers were rain**, then the **Docker Registry would be the cloud** where all Docker images are stored.  
A Docker Registry is a **central repository** that stores, manages, and distributes Docker images.

Whenever you run:

```bash
docker run nginx
````

Docker pulls the `nginx` image from the **Docker Hub** registry (public registry), unless another registry is specified.

---

## 🔐 Private Docker Registry

A **private registry** is used when organizations need to store images securely within their network.

Before pulling or pushing images to a private registry, you MUST authenticate:

```bash
docker login private-registry.io
```

After successful login, you can:

* Push images
* Pull images
* Manage private stored containers

---

## 🏗️ Deploying Your Own Private Docker Registry

Docker Registry itself is available as a **Docker image**.

To run your own private registry on port **5000**, use:

```bash
docker run -d -p 5000:5000 --name registry registry:2
```

This command:

* Runs the registry container in background
* Exposes API on port `5000`
* Makes your machine act as a Docker image server

---

## 🏷️ Tagging Docker Images for Your Private Registry

Before pushing your image to the private registry, you must **tag** it with your registry address.

Example:

```bash
docker image tag my-image localhost:5000/my-image
```

Explanation:

* `my-image` → your local image name
* `localhost:5000/my-image` → new tag pointing to your private registry

---

## 📤 Pushing an Image to Your Private Registry

Once tagged correctly, push the image using:

```bash
docker push localhost:5000/my-image
```

This uploads the image to the custom registry running on your host.

---

## 📥 Pulling Images From Your Private Registry

To pull an image stored in your private registry:

```bash
docker pull localhost:5000/my-image
```

If pulling from **another server** inside the same network, use the host’s IP instead of `localhost`:

```bash
docker pull 192.168.56.100:5000/my-image
```

This method allows you to distribute images across multiple servers in a secure environment.

---

## 🧠 Summary (Book Style)

### ✔ Docker Registry

A centralized storage location for Docker images.

### ✔ Public Registry

* Docker Hub

### ✔ Private Registry

* Self-hosted
* Requires authentication
* Stores internal images securely

### ✔ Run a Private Registry

```bash
docker run -d -p 5000:5000 --name registry registry:2
```

### ✔ Tag an Image

```bash
docker tag my-image localhost:5000/my-image
```

### ✔ Push an Image

```bash
docker push localhost:5000/my-image
```

### ✔ Pull an Image

```bash
docker pull localhost:5000/my-image
```

### ✔ Pull from Another Host

```bash
docker pull 192.168.56.100:5000/my-image
```

---

## 📦 Complete Workflow

```bash
# 1. Run Private Registry
docker run -d -p 5000:5000 --name registry registry:2

# 2. Tag Image
docker tag my-image localhost:5000/my-image

# 3. Push Image
docker push localhost:5000/my-image

# 4. Pull Image
docker pull localhost:5000/my-image

# 5. Pull from another host
docker pull 192.168.56.100:5000/my-image
```

---



