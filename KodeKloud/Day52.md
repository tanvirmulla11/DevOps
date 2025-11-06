# Day 52:☸️ Kubernetes – Deployment Rollback

This guide documents how to perform a **rollback** on an existing Kubernetes Deployment (`nginx-deployment`) to revert it to its **previous stable version** after a buggy release.

---

## 🧩 Task Overview

| Specification | Details |
|----------------|----------|
| **Deployment Name** | `nginx-deployment` |
| **Current Image (buggy)** | `nginx:1.18` |
| **Previous Image (stable)** | `nginx:1.16` |
| **Action** | Rollback to previous revision |
| **Cluster Access** | `kubectl` preconfigured on jump_host |

---

## ⚙️ Step-by-Step Procedure

### 1️⃣ Verify Cluster Access
Ensure the Kubernetes cluster is reachable:
```bash
kubectl get nodes
```
Expected:
```bash
NAME                      STATUS   ROLES           AGE   VERSION
kodekloud-control-plane   Ready    control-plane   XXm   v1.27.x
```
### 2️⃣ Check Current Deployment and Image

Confirm the current deployment and image version:
```bash
kubectl get deployments
kubectl describe deployment nginx-deployment | grep -i image
```

Example output:
```bash
Image:  nginx:1.18
```

## ✅ Confirms that the current (buggy) version is nginx:1.18.
### 3️⃣ View Rollout History

List deployment revisions to identify available versions:
```bash
kubectl rollout history deployment/nginx-deployment
```

Example output:
```bash
deployment.apps/nginx-deployment 
REVISION  CHANGE-CAUSE
1         <none>
2         kubectl set image deployment/nginx-deployment nginx-container=nginx:1.18
```

### ✅ Revision 1 → Old stable version (nginx:1.16)
### ✅ Revision 2 → Latest buggy release (nginx:1.18)

### 4️⃣ Perform Rollback

Revert the deployment to the previous revision:
```bash
kubectl rollout undo deployment/nginx-deployment
```

Expected output:
```bash
deployment.apps/nginx-deployment rolled back
```
### 5️⃣ Verify Rollout Status

Monitor the rollback process:
```bash
kubectl rollout status deployment/nginx-deployment
```

Expected:
```bash
deployment "nginx-deployment" successfully rolled out
```
### 6️⃣ Confirm Image Reversion

Check that the deployment is using the old image:
```bash
kubectl describe deployment nginx-deployment | grep -i image
```

Expected:
```bash
Image:  nginx:1.16
```
### 7️⃣ Verify Pod Health

Ensure all pods are recreated and running correctly:
```bash
kubectl get pods -o wide
```

Expected output:
```bash
NAME                                READY   STATUS    RESTARTS   AGE   IMAGE
nginx-deployment-5fcb8f74c5-xxxx    1/1     Running   0          10s   nginx:1.16
```

## ✅ All pods are up and healthy.
