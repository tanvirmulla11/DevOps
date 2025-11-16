Day 67: Deploy Guest Book App on Kubernetes
# 🧠 Kubernetes Guestbook Application Deployment — Nautilus DevOps Task

## 🎯 Objective
Deploy a **Guestbook application** on a Kubernetes cluster with a **multi-tier architecture** using Redis as the backend and PHP as the frontend.

---

## ⚙️ Task Breakdown

| Tier | Resource Name | Replicas | Image | Port | Type |
|------|----------------|-----------|--------|------|------|
| **Redis Master** | redis-master | 1 | redis | 6379 | ClusterIP |
| **Redis Slave** | redis-slave | 2 | gcr.io/google_samples/gb-redisslave:v3 | 6379 | ClusterIP |
| **Frontend (PHP)** | frontend | 3 | gcr.io/google-samples/gb-frontend@sha256:a908df8486ff66f2c4daa0d3d8a2fa09846a1fc8efd65649c0109695c7c5cbff | 80 | NodePort (30009) |

---

## 🧩 Step 1 — Redis Master Deployment

**File:** `redis-master-deployment.yaml`

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-master
spec:
  replicas: 1
  selector:
    matchLabels:
      app: redis-master
  template:
    metadata:
      labels:
        app: redis-master
    spec:
      containers:
        - name: master-redis-xfusion
          image: redis
          resources:
            requests:
              cpu: "100m"
              memory: "100Mi"
          ports:
            - containerPort: 6379
Service: redis-master-service.yaml

apiVersion: v1
kind: Service
metadata:
  name: redis-master
spec:
  selector:
    app: redis-master
  ports:
    - port: 6379
      targetPort: 6379

```
Apply:
```bash
kubectl apply -f redis-master-deployment.yaml
kubectl apply -f redis-master-service.yaml
```
🧩 Step 2 — Redis Slave Deployment
```bash
File: redis-slave-deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-slave
spec:
  replicas: 2
  selector:
    matchLabels:
      app: redis-slave
  template:
    metadata:
      labels:
        app: redis-slave
    spec:
      containers:
        - name: slave-redis-xfusion
          image: gcr.io/google_samples/gb-redisslave:v3
          resources:
            requests:
              cpu: "100m"
              memory: "100Mi"
          env:
            - name: GET_HOSTS_FROM
              value: dns
          ports:
            - containerPort: 6379


Service: redis-slave-service.yaml

apiVersion: v1
kind: Service
metadata:
  name: redis-slave
spec:
  selector:
    app: redis-slave
  ports:
    - port: 6379
      targetPort: 6379

```
Apply:
```bash
kubectl apply -f redis-slave-deployment.yaml
kubectl apply -f redis-slave-service.yaml
```
🧩 Step 3 — Frontend (PHP) Deployment
```bash
File: frontend-deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend
spec:
  replicas: 3
  selector:
    matchLabels:
      app: frontend
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
        - name: php-redis-xfusion
          image: gcr.io/google-samples/gb-frontend@sha256:a908df8486ff66f2c4daa0d3d8a2fa09846a1fc8efd65649c0109695c7c5cbff
          resources:
            requests:
              cpu: "100m"
              memory: "100Mi"
          env:
            - name: GET_HOSTS_FROM
              value: dns
          ports:
            - containerPort: 80


Service: frontend-service.yaml

apiVersion: v1
kind: Service
metadata:
  name: frontend
spec:
  type: NodePort
  selector:
    app: frontend
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30009

```
Apply:
```bash
kubectl apply -f frontend-deployment.yaml
kubectl apply -f frontend-service.yaml
```
🔍 Step 4 — Verification

Check deployments, pods, and services:
```bash
kubectl get deployments
kubectl get pods
kubectl get svc
```

✅ Expected:
```bash
NAME           READY   UP-TO-DATE   AVAILABLE   AGE
frontend       3/3     3            3           2m
redis-master   1/1     1            1           3m
redis-slave    2/2     2            2           2m
```
```bash
NAME           TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
frontend       NodePort    10.96.x.x       <none>        80:30009/TCP   2m
redis-master   ClusterIP   10.96.x.x       <none>        6379/TCP       3m
redis-slave    ClusterIP   10.96.x.x       <none>        6379/TCP       2m
```
🌍 Step 5 — Access the Application

Get node IP:
```bash
kubectl get nodes -o wide
```

✅ Example:
```bash
INTERNAL-IP: 172.17.0.2
```

Access from browser or via curl:
```bash
curl http://172.17.0.2:30009
```

✅ Expected:
```bash
Guestbook App HTML Response
```
