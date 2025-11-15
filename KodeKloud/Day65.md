Day 65: Deploy Redis Deployment on Kubernetes
# 🚀 Kubernetes Redis Deployment — Nautilus DevOps Task

## 🎯 Objective
The Nautilus DevOps team needs to deploy Redis on a Kubernetes cluster for testing performance improvements.  
This setup must use **ConfigMap-based configuration**, proper **volume mounts**, and CPU resource requests.

---

## ⚙️ Task Requirements

| Parameter | Value |
|------------|--------|
| **ConfigMap Name** | `my-redis-config` |
| **Config Key** | `maxmemory=2mb` |
| **Deployment Name** | `redis-deployment` |
| **Container Name** | `redis-container` |
| **Image** | `redis:alpine` |
| **Replicas** | 1 |
| **CPU Request** | 1 CPU |
| **EmptyDir Volume** | `/redis-master-data` |
| **ConfigMap Volume** | `/redis-master` |
| **Container Port** | 6379 |

---

## 🧩 Step 1 — Create ConfigMap

```bash
kubectl create configmap my-redis-config --from-literal=maxmemory=2mb
```
✅ Verify:
```bash
kubectl get configmap my-redis-config -o yaml
```

Expected:
```bash
data:
  maxmemory: 2mb
```
🧱 Step 2 — Create Redis Deployment
```bash
File: redis-deployment.yaml
```
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: redis
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
        - name: redis-container
          image: redis:alpine
          ports:
            - containerPort: 6379
          resources:
            requests:
              cpu: "1"
          volumeMounts:
            - name: data
              mountPath: /redis-master-data
            - name: redis-config
              mountPath: /redis-master
      volumes:
        - name: data
          emptyDir: {}
        - name: redis-config
          configMap:
            name: my-redis-config
```

Apply it:
```bash
kubectl apply -f redis-deployment.yaml
```
🔍 Step 3 — Verify Deployment & Pods
```bash
kubectl get deployments
kubectl get pods -l app=redis -o wide
```

✅ Expected:
```bash
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
redis-deployment   1/1     1            1           30s
```
🧠 Step 4 — Validate Volumes and Mounts
```bash
Check volume mounts:

kubectl describe pod -l app=redis | grep -A3 "Mounts"

```
✅ Expected:
```bash
Mounts:
  /redis-master-data from data (rw)
  /redis-master from redis-config (rw)
```
⚙️ Step 5 — Confirm ConfigMap Value Inside Pod
```bash
kubectl exec -it $(kubectl get pods -l app=redis -o jsonpath='{.items[0].metadata.name}') -- cat /redis-master/maxmemory
```

✅ Output:
```bash
2mb
```
🧾 Step 6 — Verify CPU Request
```bash
kubectl get pod -l app=redis -o yaml | grep -A2 "resources:"
```

✅ Output:
```bash
resources:
  requests:
    cpu: "1"
```

