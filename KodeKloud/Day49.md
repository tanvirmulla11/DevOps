day 49:
# ☸️ Kubernetes – NGINX Deployment

This repository documents how to create and expose a **Deployment** in Kubernetes to run the **NGINX web server** using the image `nginx:latest`.

---

## 🧩 Task Overview

| Specification | Details |
|----------------|----------|
| **Deployment Name** | `nginx` |
| **Container Name** | `nginx` |
| **Image** | `nginx:latest` |
| **Replicas** | 1 |
| **Service Name** | `nginx-service` |
| **Service Type** | `NodePort` |
| **Port** | 80 |

---

## ⚙️ Step-by-Step Deployment

### 1️⃣ Verify Cluster Connection
Check that your cluster is reachable and nodes are ready:
```bash
kubectl get nodes
```
### 2️⃣ Create Deployment
### Run the command below to deploy NGINX:
```bash
kubectl create deployment nginx --image=nginx:latest
```

### Verify:
```bash
kubectl get deployments
```

### Expected:
```bash
NAME    READY   UP-TO-DATE   AVAILABLE   AGE
nginx   1/1     1            1           Xs
```
### 3️⃣ Confirm Pod Status
```bash
kubectl get pods -o wide
```

### Example output:
```bash
NAME                     READY   STATUS    RESTARTS   AGE   IP           NODE
nginx-7bf8c77b5b-m8ck2   1/1     Running   0          20s   10.244.0.5   kodekloud-control-plane
```
### 4️⃣ Expose Deployment as a Service

### Create a NodePort service to access NGINX:
```bash
kubectl expose deployment nginx --type=NodePort --port=80 --name=nginx-service
```

### Check service details:
```bash
kubectl get svc nginx-service
```

### Expected output:
```bash
NAME             TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
nginx-service    NodePort   10.96.xxx.xxx   <none>        80:30xxx/TCP   Xs
```
### 5️⃣ Test the Application Inside the Cluster

### Use a temporary pod (BusyBox) to verify connectivity:
```bash
kubectl run testpod --image=busybox:latest --restart=Never --command -- wget -qO- nginx-service.default.svc.cluster.local
```

## ✅ Expected output:
```bash
<html>
<head><title>Welcome to nginx!</title></head>
```
<body><h1>Welcome to nginx!</h1></body>
</html>
