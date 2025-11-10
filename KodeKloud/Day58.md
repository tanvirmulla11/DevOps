
## Day 58: Deploy Grafana on Kubernetes Cluster

# 📊 Grafana Deployment on Kubernetes (Nautilus DevOps Task)

This document explains how to deploy the **Grafana** monitoring tool on a Kubernetes cluster and expose it externally using a **NodePort Service** on port **32000**.

---

## 🎯 Objective

- Deploy Grafana with a Kubernetes **Deployment** named `grafana-deployment-xfusion`
- Expose it externally using a **NodePort Service** named `grafana-service` on **port 32000**
- Verify access to the **Grafana login page**

---

## ⚙️ Step 1: Create Deployment Manifest

Create a file named **`grafana-deployment-xfusion.yaml`**:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: grafana-deployment-xfusion
  labels:
    app: grafana
spec:
  replicas: 1
  selector:
    matchLabels:
      app: grafana
  template:
    metadata:
      labels:
        app: grafana
    spec:
      containers:
        - name: grafana
          image: grafana/grafana:latest
          ports:
            - containerPort: 3000
```
## 🚀 Step 2: Deploy Grafana

Apply the deployment:
```base
kubectl apply -f grafana-deployment-xfusion.yaml
```

Expected output:
```base
deployment.apps/grafana-deployment-xfusion created
```

Check the pod status:
```base
kubectl get pods -l app=grafana -o wide
```

Example output:
```base
NAME                                         READY   STATUS    RESTARTS   AGE
grafana-deployment-xfusion-77648df4c-sqvtf   1/1     Running   0          1m
```

If the pod is in ContainerCreating for a while, check details:
```base
kubectl describe pod <pod-name>
```

Wait until the status becomes Running.

## ⚙️ Step 3: Create Service Manifest

Create a file named grafana-service.yaml:
```base
apiVersion: v1
kind: Service
metadata:
  name: grafana-service
spec:
  type: NodePort
  selector:
    app: grafana
  ports:
    - port: 3000
      targetPort: 3000
      nodePort: 32000
```
## 🚀 Step 4: Apply the Service

Apply the service manifest:
```base
kubectl apply -f grafana-service.yaml
```

Expected output:
```base
service/grafana-service created
```

Verify the service:
```base
kubectl get svc grafana-service
```

Expected:
```base
NAME              TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
grafana-service   NodePort   10.96.x.x       <none>        3000:32000/TCP   10s
```
## 🔍 Step 5: Verify Deployment and Service

Check both pods and services:
```base
kubectl get deployments
kubectl get pods -l app=grafana -o wide
kubectl get svc grafana-service
```

You should see one Grafana pod running and the service exposing port 32000.

## 🌐 Step 6: Access Grafana Web UI

Find the node IP:
```base
kubectl get nodes -o wide
```

Example:
```base
NAME                      STATUS   ROLES           AGE   VERSION   INTERNAL-IP   EXTERNAL-IP
kodekloud-control-plane   Ready    control-plane   15m   v1.27.16  172.17.0.2    <none>
```

Access Grafana in a browser or curl command:
```base
http://172.17.0.2:32000
```

## ✅ You should see the Grafana login page.
