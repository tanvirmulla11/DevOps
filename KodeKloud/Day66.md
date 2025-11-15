# 🧠 Day 66: Deploy MySQL on Kubernetes


## 🎯 Objective
Deploy a **MySQL server** on Kubernetes with persistent storage, secrets for credentials, and NodePort exposure for accessibility.

---

## ⚙️ Task Details

| Resource | Required Configuration |
|-----------|------------------------|
| **PersistentVolume** | Name: `mysql-pv`, Capacity: `250Mi`, AccessMode: `ReadWriteOnce` |
| **PersistentVolumeClaim** | Name: `mysql-pv-claim`, Request: `250Mi` |
| **Deployment** | Name: `mysql-deployment`, Image: `mysql:5.7`, Volume mount at `/var/lib/mysql` |
| **Secrets** | 3 Secrets (`mysql-root-pass`, `mysql-user-pass`, `mysql-db-url`) |
| **Service** | Name: `mysql`, Type: `NodePort`, Port: `3306`, NodePort: `30007` |
| **Environment Variables** | Loaded via secrets (root password, user, password, DB name) |

---

## 🧱 Step 1 — Create Persistent Volume

**File:** `mysql-pv.yaml`

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mysql-pv
spec:
  capacity:
    storage: 250Mi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: /mnt/mysql-data
```
## 🧱 Step 2 — Create Persistent Volume Claim

File: mysql-pvc.yaml
```bash
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pv-claim
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 250Mi

kubectl apply -f mysql-pvc.yaml
kubectl get pvc

```
✅ Expected:
```bash
mysql-pv-claim   Bound   mysql-pv   250Mi   RWO
```
## 🔐 Step 3 — Create Secrets
```bash
kubectl create secret generic mysql-root-pass --from-literal=password=YUIidhb667
kubectl create secret generic mysql-user-pass --from-literal=username=kodekloud_top --from-literal=password=YchZHRcLkL
kubectl create secret generic mysql-db-url --from-literal=database=kodekloud_db7
```

✅ Verify:
```bash
kubectl get secrets
```

Expected:
```bash
mysql-root-pass
mysql-user-pass
mysql-db-url
```
## 🧩 Step 4 — Create MySQL Deployment
```bash
File: mysql-deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: mysql-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: mysql
  template:
    metadata:
      labels:
        app: mysql
    spec:
      containers:
        - name: mysql
          image: mysql:5.7
          ports:
            - containerPort: 3306
          env:
            - name: MYSQL_ROOT_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: mysql-root-pass
                  key: password
            - name: MYSQL_DATABASE
              valueFrom:
                secretKeyRef:
                  name: mysql-db-url
                  key: database
            - name: MYSQL_USER
              valueFrom:
                secretKeyRef:
                  name: mysql-user-pass
                  key: username
            - name: MYSQL_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: mysql-user-pass
                  key: password
          volumeMounts:
            - name: mysql-storage
              mountPath: /var/lib/mysql
      volumes:
        - name: mysql-storage
          persistentVolumeClaim:
            claimName: mysql-pv-claim

kubectl apply -f mysql-deployment.yaml
kubectl get pods -l app=mysql -w
```

✅ Expected:
```bash
mysql-deployment-xxxxx   1/1   Running   0   20s
```
## 🌐 Step 5 — Expose MySQL via NodePort Service
```bash
File: mysql-service.yaml

apiVersion: v1
kind: Service
metadata:
  name: mysql
spec:
  type: NodePort
  selector:
    app: mysql
  ports:
    - protocol: TCP
      port: 3306
      targetPort: 3306
      nodePort: 30007
```
```bash
kubectl apply -f mysql-service.yaml
kubectl get svc mysql
```

✅ Expected:
```bash
mysql   NodePort   10.96.x.x   <none>   3306:30007/TCP
```
## 🧠 Step 6 — Verify Environment Variables
```bash
kubectl exec -it $(kubectl get pods -l app=mysql -o jsonpath='{.items[0].metadata.name}') -- env | grep MYSQL
```

✅ Output:
```bash

MYSQL_ROOT_PASSWORD=YUIidhb667
MYSQL_DATABASE=kodekloud_db7
MYSQL_USER=kodekloud_top
MYSQL_PASSWORD=YchZHRcLkL
```
📦 Step 7 — Validate Storage Mount
```bash
kubectl exec -it $(kubectl get pods -l app=mysql -o jsonpath='{.items[0].metadata.name}') -- df -h | grep /var/lib/mysql
```

✅ Output:
```bash
/dev/...   250Mi   ...   /var/lib/mysql
```
