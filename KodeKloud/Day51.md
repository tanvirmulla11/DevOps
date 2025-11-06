# Day 51:Execute Rolling Updates in Kubernetes
# ☸️ Kubernetes – Rolling Update (nginx:1.18)

This guide documents how to perform a **Rolling Update** on an existing Kubernetes deployment named `nginx-deployment`, upgrading the container image from `nginx:1.16` to `nginx:1.18`.  
The process ensures **zero downtime** while new pods replace the old ones gradually.

---

## 🧩 Task Overview

| Specification | Details |
|----------------|----------|
| **Deployment Name** | `nginx-deployment` |
| **Container Name** | `nginx-container` |
| **Old Image** | `nginx:1.16` |
| **New Image** | `nginx:1.18` |
| **Update Type** | Rolling Update |
| **Tool Used** | `kubectl` (preconfigured on jump_host) |

---

## ⚙️ Step-by-Step Deployment Update

### 1️⃣ Verify Cluster Access
Ensure the Kubernetes cluster is running and accessible:
```bash
kubectl get nodes
Expected output:
```
```bash
NAME                      STATUS   ROLES           AGE   VERSION
kodekloud-control-plane   Ready    control-plane   XXm   v1.27.x
```
### 2️⃣ Check Current Deployment Status

List all running deployments:
```bash
kubectl get deployments
```

Expected output:
```bash
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   3/3     3            3           5m
```
### 3️⃣ Identify Current Image and Container Name

Describe the deployment to find container details:
```bash
kubectl describe deployment nginx-deployment | grep -A5 "Containers:"
```

Example output:
```bash
Containers:
   nginx-container:
    Image:         nginx:1.16
    Port:          <none>
```

✅ Container name is nginx-container
✅ Current image is nginx:1.16

### 4️⃣ Perform the Rolling Update

Use the correct container name in the update command:
```bash
kubectl set image deployment/nginx-deployment nginx-container=nginx:1.18
```

Expected output:
```bash
deployment.apps/nginx-deployment image updated
```
### 5️⃣ Monitor Rollout Progress

Check if the rolling update completes successfully:
```bash
kubectl rollout status deployment/nginx-deployment
```

Expected:
```bash
deployment "nginx-deployment" successfully rolled out
```
### 6️⃣ Verify Image Update

Confirm that the new image version is applied:
```bash
kubectl describe deployment nginx-deployment | grep -i image
```

Expected:
```bash
Image:  nginx:1.18
```
### 7️⃣ Verify Pods

List the pods and ensure all are running with the updated image:
```bash
kubectl get pods -o wide
```

### Expected output:
```bash
NAME                                READY   STATUS    RESTARTS   AGE   IMAGE
nginx-deployment-75dbdcb886-xxxx    1/1     Running   0          20s   nginx:1.18
```
