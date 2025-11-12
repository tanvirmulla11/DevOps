# Day 62: Manage Secrets in Kubernetes

# 🔐 Kubernetes Secret Deployment — Nautilus DevOps Task

This document explains how to securely store and mount sensitive data (like license keys) in Kubernetes using **Secrets**.

---

## 🎯 Objective

- Create a **Secret** named `news` from an existing file `/opt/news.txt`.
- Deploy a **Pod** named `secret-nautilus` using the secret.
- Mount the secret under `/opt/demo` inside the container.
- Keep the container running using the `sleep` command.

---

## ⚙️ Step 1: Create Secret from File

```bash
kubectl create secret generic news --from-file=/opt/news.txt
```
Verify:
```bash
kubectl get secrets
```

Expected:
```bash
NAME   TYPE     DATA   AGE
news   Opaque   1      5s
```
## ⚙️ Step 2: Create Pod Using the Secret

Create file secret-nautilus.yaml:
```bash
apiVersion: v1
kind: Pod
metadata:
  name: secret-nautilus
spec:
  containers:
    - name: secret-container-nautilus
      image: debian:latest
      command: ["/bin/bash", "-c", "sleep infinity"]
      volumeMounts:
        - name: secret-volume
          mountPath: /opt/demo
  volumes:
    - name: secret-volume
      secret:
        secretName: news

```
Apply:
```bash
kubectl apply -f secret-nautilus.yaml
```
## 🔍 Step 3: Verify Pod and Secret Mount

Check pod:
```bash
kubectl get pods
```

Expected:
```bash
NAME               READY   STATUS    RESTARTS   AGE
secret-nautilus    1/1     Running   0          15s
```

Enter container:
```bash
kubectl exec -it secret-nautilus -- /bin/bash
```

Inside container:
```bash
ls /opt/demo
cat /opt/demo/news.txt
```

## ✅ Output:
```bash
news.txt
<your-license-key-or-password>
```

Exit:
```bash
exit
```
