Day 48:Deploy Pods in Kubernetes Cluster
# ☸️ Kubernetes – HTTPD Pod and Service Deployment

This repository documents the steps to deploy and expose an **Apache HTTPD** application inside a Kubernetes cluster using **kubectl**.

---

## 🧩 Task Overview

| Requirement | Description |
|--------------|-------------|
| **Pod Name** | `pod-httpd` |
| **Container Name** | `httpd-container` |
| **Image** | `httpd:latest` |
| **Label** | `app=httpd_app` |
| **Service Name** | `httpd-service` |
| **Service Type** | `NodePort` |
| **Service Port** | `80` |
| **NodePort** | Auto-assigned (e.g. `30162`) |

---

## ⚙️ Step-by-Step Deployment

### 1️⃣ Verify Cluster Access
```bash
kubectl config get-contexts
kubectl get nodes -o wide
```
### 2️⃣ Create the Pod YAML
```bash
vi pod-httpd.yaml
```
```bash
Paste the following:

apiVersion: v1
kind: Pod
metadata:
  name: pod-httpd
  labels:
    app: httpd_app
spec:
  containers:
    - name: httpd-container
      image: httpd:latest
      ports:
        - containerPort: 80
```

### Apply it:
```bash
kubectl apply -f pod-httpd.yaml
```
### 3️⃣ Verify Pod Status
```bash
kubectl get pods --show-labels
```

## ✅ Expected output:
```bash
NAME        READY   STATUS    RESTARTS   AGE   LABELS
pod-httpd   1/1     Running   0          10s   app=httpd_app
```
###  4️⃣ Expose Pod as a Service
```bash
kubectl expose pod pod-httpd --type=NodePort --port=80 --name=httpd-service
```

### Check assigned NodePort:
```bash
kubectl get svc httpd-service
```

### Example:
```bash
NAME            TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
httpd-service   NodePort   10.96.205.83    <none>        80:30162/TCP   10s
```
### 5️⃣ Verify Connectivity Inside the Cluster

### Run a temporary BusyBox pod to test service access:
```bash
kubectl run testpod --image=busybox:latest --restart=Never --command -- wget -qO- httpd-service.default.svc.cluster.local
```

### ✅ Expected output:
```bash
<html><body><h1>It works!</h1></body></html>
 ```
