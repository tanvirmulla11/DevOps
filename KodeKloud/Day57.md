## Day 57: Print Environment Variables
# 🧩 Kubernetes Pod: print-envars-greeting

This guide demonstrates how to create a **Kubernetes Pod** that prints greeting messages using **environment variables**.  
It is a simple example of how to pass and use environment variables inside a container.

---

## 🎯 Objective

Create a pod named **`print-envars-greeting`** that:

- Uses the **bash** image
- Runs the command to print environment variables:
  ```bash
  echo "$(GREETING) $(COMPANY) $(GROUP)"
## ⚙️ Step 1: Create Pod Manifest

Create a YAML file named print-envars-greeting.yaml
```bash
apiVersion: v1
kind: Pod
metadata:
  name: print-envars-greeting
spec:
  containers:
    - name: print-env-container
      image: bash
      command: ["/bin/sh", "-c", 'echo "$(GREETING) $(COMPANY) $(GROUP)"']
      env:
        - name: GREETING
          value: "Welcome to"
        - name: COMPANY
          value: "xFusionCorp"
        - name: GROUP
          value: "Ltd"
  restartPolicy: Never
```
## 🚀 Step 2: Deploy the Pod

Apply the manifest using kubectl:
```bash
kubectl apply -f print-envars-greeting.yaml
```

Expected output:
```bash
pod/print-envars-greeting created
```
## 🔍 Step 3: Verify Pod Status

Check if the pod completed successfully:
```bash
kubectl get pods
```

Example output:
```bash
NAME                    READY   STATUS      RESTARTS   AGE
print-envars-greeting   0/1     Completed   0          8s
```
## 🧾 Step 4: View the Output

Use logs to check what the pod printed:
```bash
kubectl logs -f print-envars-greeting
```

Expected output:
```bash
Welcome to xFusionCorp Ltd
```
---
