# Day 61: Init Containers in Kubernetes
# 🧩 Init Container Deployment on Kubernetes

This guide demonstrates how to deploy a web application using **Init Containers** to perform pre-start setup tasks on Kubernetes.

---

## 🎯 Objective

- Create a **Deployment** named `ic-deploy-xfusion`
- Use an **init container** to create a message file
- Use a **main container** to read that file continuously
- Share data using an **emptyDir** volume

---

## ⚙️ Deployment YAML

Create file `ic-deploy-xfusion.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ic-deploy-xfusion
spec:
  replicas: 1
  selector:
    matchLabels:
      app: ic-xfusion
  template:
    metadata:
      labels:
        app: ic-xfusion
    spec:
      initContainers:
        - name: ic-msg-xfusion
          image: ubuntu:latest
          command: ["/bin/bash", "-c", "echo Init Done - Welcome to xFusionCorp Industries > /ic/blog"]
          volumeMounts:
            - name: ic-volume-xfusion
              mountPath: /ic
      containers:
        - name: ic-main-xfusion
          image: ubuntu:latest
          command: ["/bin/bash", "-c", "while true; do cat /ic/blog; sleep 5; done"]
          volumeMounts:
            - name: ic-volume-xfusion
              mountPath: /ic
      volumes:
        - name: ic-volume-xfusion
          emptyDir: {}
```
## Apply it:
```bash
kubectl apply -f ic-deploy-xfusion.yaml
```
## 🔍 Verify Deployment

Check deployment and pods:
```bash
kubectl get deployments
kubectl get pods -l app=ic-xfusion
```

Example:
```bash
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
ic-deploy-xfusion   1/1     1            1           20s
```
📄 Check Logs
Main container logs:
```bash
kubectl logs -f $(kubectl get pods -l app=ic-xfusion -o jsonpath='{.items[0].metadata.name}')
```

## Expected output:
```bash
Init Done - Welcome to xFusionCorp Industries
Init Done - Welcome to xFusionCorp Industries
...
```
