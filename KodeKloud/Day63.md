# Day 63: Deploy Iron Gallery App on Kubernetes

# 🏗️ Iron Gallery App Deployment — Nautilus DevOps Task

This guide explains how to deploy the **Iron Gallery app** and **Iron DB** on Kubernetes with proper namespace, volumes, and services.

---

## 🎯 Objective

- Create a namespace `iron-namespace-xfusion`
- Deploy **Iron Gallery (Frontend)** and **Iron DB (Backend)**
- Expose both apps with proper services

---

## ⚙️ Step 1: Create Namespace

```bash
kubectl create namespace iron-namespace-xfusion
```
## ⚙️ Step 2: Create Iron Gallery Deployment

Create file iron-gallery-deployment.yaml:
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: iron-gallery-deployment-xfusion
  namespace: iron-namespace-xfusion
  labels:
    run: iron-gallery
spec:
  replicas: 1
  selector:
    matchLabels:
      run: iron-gallery
  template:
    metadata:
      labels:
        run: iron-gallery
    spec:
      containers:
        - name: iron-gallery-container-xfusion
          image: kodekloud/irongallery:2.0
          resources:
            limits:
              memory: "100Mi"
              cpu: "50m"
          volumeMounts:
            - name: config
              mountPath: /usr/share/nginx/html/data
            - name: images
              mountPath: /usr/share/nginx/html/uploads
      volumes:
        - name: config
          emptyDir: {}
        - name: images
          emptyDir: {}
```

Apply:
```bash
kubectl apply -f iron-gallery-deployment.yaml
```
## ⚙️ Step 3: Create Iron DB Deployment

Create file iron-db-deployment.yaml:
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: iron-db-deployment-xfusion
  namespace: iron-namespace-xfusion
  labels:
    db: mariadb
spec:
  replicas: 1
  selector:
    matchLabels:
      db: mariadb
  template:
    metadata:
      labels:
        db: mariadb
    spec:
      containers:
        - name: iron-db-container-xfusion
          image: kodekloud/irondb:2.0
          env:
            - name: MYSQL_DATABASE
              value: database_blog
            - name: MYSQL_ROOT_PASSWORD
              value: "R00t@1234!"
            - name: MYSQL_PASSWORD
              value: "DbPass@2024"
            - name: MYSQL_USER
              value: "ironuser"
          volumeMounts:
            - name: db
              mountPath: /var/lib/mysql
      volumes:
        - name: db
          emptyDir: {}

```
Apply:
```bash
kubectl apply -f iron-db-deployment.yaml
```
## ⚙️ Step 4: Create Services
Iron DB Service
```bash
apiVersion: v1
kind: Service
metadata:
  name: iron-db-service-xfusion
  namespace: iron-namespace-xfusion
spec:
  selector:
    db: mariadb
  ports:
    - protocol: TCP
      port: 3306
      targetPort: 3306
  type: ClusterIP

```
Apply:
```bash
kubectl apply -f iron-db-service.yaml
```
## Iron Gallery Service
```bash
apiVersion: v1
kind: Service
metadata:
  name: iron-gallery-service-xfusion
  namespace: iron-namespace-xfusion
spec:
  selector:
    run: iron-gallery
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 32678
  type: NodePort
```

Apply:
```bash
kubectl apply -f iron-gallery-service.yaml
```
## 🔍 Step 5: Verify Resources
```bash
kubectl get all -n iron-namespace-xfusion
```

You should see:
```bash
Pods → Running
Deployments → Available
Services → Active
```
## 🌐 Step 6: Access the App

Get node IP:
```bash
kubectl get nodes -o wide
```
