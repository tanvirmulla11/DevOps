day 50:
# ☸️ Kubernetes – Pod with Resource Limits

This repository documents how to create a **Kubernetes Pod** that runs an Apache HTTPD container with defined **CPU and Memory resource requests and limits** to ensure controlled utilization.

---

## 🧩 Task Overview

| Specification | Details |
|----------------|----------|
| **Pod Name** | `httpd-pod` |
| **Container Name** | `httpd-container` |
| **Image** | `httpd:latest` |
| **Memory Request** | `15Mi` |
| **CPU Request** | `100m` |
| **Memory Limit** | `20Mi` |
| **CPU Limit** | `100m` |
| **QoS Class** | `Burstable` |
| **Cluster Tool** | `kubectl` (pre-configured on jump host) |

---

## ⚙️ Step-by-Step Guide

### 1️⃣ Verify Cluster Connectivity
Check that your cluster is accessible and the node is ready:
```bash
kubectl get nodes
Expected output:

NAME                      STATUS   ROLES           AGE   VERSION
kodekloud-control-plane   Ready    control-plane   XXm   v1.27.x
```
### 2️⃣ Create Pod Definition YAML

Create a file named httpd-pod.yaml:
```bash
vi httpd-pod.yaml
```
```bash

Paste the following YAML:

apiVersion: v1
kind: Pod
metadata:
  name: httpd-pod
spec:
  containers:
    - name: httpd-container
      image: httpd:latest
      resources:
        requests:
          memory: "15Mi"
          cpu: "100m"
        limits:
          memory: "20Mi"
          cpu: "100m"


Save and exit (:wq).
```
### 3️⃣ Deploy the Pod

Apply the YAML configuration:
```bash
kubectl apply -f httpd-pod.yaml
```

Expected:
```bash
pod/httpd-pod created
```
### 4️⃣ Verify Pod Status

Check that the Pod is running:
```bash
kubectl get pods
```

Expected:
```bash
NAME         READY   STATUS    RESTARTS   AGE
httpd-pod    1/1     Running   0          10s
```
### 5️⃣ Validate Resource Limits

Describe the Pod to confirm that limits and requests are applied:
```bash
kubectl describe pod httpd-pod
```

Expected section:
```bash
Limits:
  cpu:     100m
  memory:  20Mi
Requests:
  cpu:     100m
  memory:  15Mi
QoS Class: Burstable
```
### 6️⃣ Verify Pod Internals (Optional)

To ensure the container is serving correctly:
```bash
kubectl exec -it httpd-pod -- curl localhost
```

###Expected output:
```bash
<html><body><h1>It works!</h1></body></html>
```
## 🧠 Explanation

### Requests: Minimum guaranteed resources (Pod will always get at least 15Mi memory & 100m CPU).

### Limits: Maximum resources the Pod can consume (capped at 20Mi memory & 100m CPU).

### QoS Class = Burstable: Because requests < limits for memory. 


