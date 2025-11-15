# Day 64: Fix Python App Deployed on Kubernetes Cluster

# 🐍 Kubernetes Python App Fix – DevOps Task

## 🎯 Task Objective
Fix the misconfiguration of a Python Flask app deployed on the Kubernetes cluster.  
Ensure the app is running and accessible on the specified **NodePort (32345)**.

---

## ⚙️ Requirements

- **Deployment Name:** `python-deployment-devops`  
- **Container Name:** `python-container-devops`  
- **Image:** `poroko/flask-demo-appimage`  
- **App Label:** `app=python_app`  
- **Container Port:** `5000` (Flask default)  
- **Service Name:** `python-service-devops`  
- **Service Type:** `NodePort`  
- **TargetPort:** `5000`  
- **NodePort:** `32345`  

---

## 🧱 Step 1 — Delete Old Resources

```bash
kubectl delete deployment python-deployment-devops
kubectl delete svc python-service-devops
🧩 Step 2 — Create Deployment
apiVersion: apps/v1
kind: Deployment
metadata:
  name: python-deployment-devops
spec:
  replicas: 1
  selector:
    matchLabels:
      app: python_app
  template:
    metadata:
      labels:
        app: python_app
    spec:
      containers:
        - name: python-container-devops
          image: poroko/flask-demo-appimage
          ports:
            - containerPort: 5000

```
Apply it:
```bash
kubectl apply -f python-deployment.yaml
```

Verify pod status:
```bash
kubectl get pods -l app=python_app -w

✅ Must show 1/1 Running.
```
## 🌐 Step 3 — Create NodePort Service
```bash
apiVersion: v1
kind: Service
metadata:
  name: python-service-devops
spec:
  type: NodePort
  selector:
    app: python_app
  ports:
    - protocol: TCP
      port: 5000
      targetPort: 5000
      nodePort: 32345
```

Apply it:
```bash
kubectl apply -f python-service.yaml
```
## 🔍 Step 4 — Verify Everything
```bash
kubectl get all
kubectl logs -l app=python_app
```

Expected logs:
```bash
* Running on http://0.0.0.0:5000/
```
## 🌍 Step 5 — Access Flask App via NodePort

Get the node IP:
```bash
kubectl get nodes -o wide
```

Example:
```bash
INTERNAL-IP: 172.17.0.2
```

Access the app:
```bash
curl http://172.17.0.2:32345
```

✅ Expected output:
```bash
Hello from Flask!
```
