# Day 59: Troubleshoot Deployment issues in Kubernetes

# 🚀 Redis Deployment Recovery on Kubernetes (Nautilus DevOps Task)

This document outlines the step-by-step process to **identify, fix, and restore** a broken Redis deployment on a Kubernetes cluster.  
It is based on a real incident where the Redis app went down due to a misconfiguration.

---

## 🎯 Objective

- Investigate and fix the non-running Redis deployment named `redis-deployment`
- Ensure the Redis pod is running and accessible
- Verify Redis functionality using `redis-cli ping`

---

## 🧩 Step 1: Check Deployment and Pod Status

Use the following commands to inspect the current status:

```bash
kubectl get deployments
kubectl get pods -l app=redis
```
⚙️ Step 2: Delete the Faulty Deployment

Remove the existing Redis deployment to start fresh:
```bash
kubectl delete deployment redis-deployment --force --grace-period=0
```

Verify deletion:
```bash
kubectl get deployments
```

Expected output:
```bash
No resources found in default namespace.
```
🧱 Step 3: Recreate a Clean Redis Deployment

Create a fresh deployment using the correct Redis image:
```bash
kubectl create deployment redis-deployment --image=redis:alpine
```

✅ The image redis:alpine is lightweight and stable.

🌐 Step 4: Expose Redis Service

Expose Redis internally within the cluster on port 6379:
```bash
kubectl expose deployment redis-deployment --port=6379 --type=ClusterIP
```

If the service already exists, delete it first:
```bash
kubectl delete svc redis-deployment
kubectl expose deployment redis-deployment --port=6379 --type=ClusterIP
```
🔍 Step 5: Verify Deployment, Pods, and Service

Check that everything is running smoothly:
```bash
kubectl get deployments
kubectl get pods -l app=redis -o wide
kubectl get svc redis-deployment
```

Expected output:
```bash
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
redis-deployment   1/1     1            1           30s

NAME                                READY   STATUS    RESTARTS   AGE
redis-deployment-7c656848c5-5jhd7   1/1     Running   0          81s

NAME               TYPE        CLUSTER-IP     PORT(S)    AGE
redis-deployment   ClusterIP   10.96.xx.xx    6379/TCP   1m
```
🧠 Step 6: Test Redis Functionality

Run the redis-cli command inside the pod to verify connectivity:
```bash
kubectl exec -it redis-deployment-7c656848c5-5jhd7 -- redis-cli ping
```

✅ Expected output:
```bash
PONG
```

