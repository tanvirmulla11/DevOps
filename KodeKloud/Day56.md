Day 56: Deploy Nginx Web Server on Kubernetes Cluster
# 🚀 Nginx Deployment on Kubernetes (Highly Available & Scalable)

This guide demonstrates how to deploy a **highly available and scalable Nginx web server** on a Kubernetes cluster using **Deployments** and **NodePort Services**.

---

## 🧩 Objective

Create:
- A **Deployment** named `nginx-deployment`
- Running the **nginx:latest** image
- With **3 replicas**
- A **NodePort Service** named `nginx-service` exposing the app on **port 30011**

---

## ⚙️ Step 1: Create Deployment Manifest

Create a file named **`nginx-deployment.yaml`**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx-container
          image: nginx:latest
          ports:
            - containerPort: 80
```
## ⚙️ Step 2: Create Service Manifest

Create a file named nginx-service.yaml
```base
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30011
```
## 🚀 Step 3: Apply the Manifests
```bash
kubectl apply -f nginx-deployment.yaml
kubectl apply -f nginx-service.yaml
```

Expected Output:
```bash
deployment.apps/nginx-deployment created
service/nginx-service created
```
## 🔍 Step 4: Verify the Setup
### Check Deployment
```bash
kubectl get deployments
```

Expected:
```bash
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   3/3     3            3           20s
```
Check Pods
```bash
kubectl get pods -l app=nginx -o wide
```
Check Service
```bash
kubectl get svc nginx-service
```

Expected:
```bash
NAME            TYPE       CLUSTER-IP      PORT(S)        AGE
nginx-service   NodePort   10.96.106.34    80:30011/TCP   25s
```
## 🌐 Step 5: Access the Nginx Website

Find the node’s IP:
```bash
kubectl get nodes -o wide
```

Example Output:
```bash
NAME                      STATUS   ROLES           AGE   VERSION   INTERNAL-IP   EXTERNAL-IP
kodekloud-control-plane   Ready    control-plane   10m   v1.27.16  172.17.0.2    <none>

```
Access the app:
```bash
curl http://172.17.0.2:30011
```

Expected:
```bash
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
...
```

## ✅ You’ve successfully deployed Nginx on Kubernetes!
