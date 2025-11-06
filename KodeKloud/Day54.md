## Day 54: Kubernetes Shared Volumes
# 🧩 Kubernetes Multi-Container Pod with Shared Volume

## 📘 Task Description
The Nautilus DevOps team needed to create an application setup running on **multiple containers within the same Pod** in a Kubernetes cluster.  
The goal was to **share a temporary volume** between these containers using the **`emptyDir`** volume type.

---

## ⚙️ Requirements

| Component | Specification |
|------------|----------------|
| **Pod Name** | `volume-share-datacenter` |
| **Container 1** | Image: `ubuntu:latest` |
| **Container 2** | Image: `ubuntu:latest` |
| **Volume Name** | `volume-share` |
| **Volume Type** | `emptyDir` |
| **Mount Path (Container 1)** | `/tmp/official` |
| **Mount Path (Container 2)** | `/tmp/apps` |
| **Command (both containers)** | `sleep 3600` (to keep containers running) |

---

## 🛠️ Step-by-Step Implementation

### 🧾 Step 1: Create Pod Manifest
Create a YAML file named **`volume-share-datacenter.yaml`**:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: volume-share-datacenter
spec:
  containers:
    - name: volume-container-datacenter-1
      image: ubuntu:latest
      command: ["/bin/bash", "-c", "sleep 3600"]
      volumeMounts:
        - name: volume-share
          mountPath: /tmp/official

    - name: volume-container-datacenter-2
      image: ubuntu:latest
      command: ["/bin/bash", "-c", "sleep 3600"]
      volumeMounts:
        - name: volume-share
          mountPath: /tmp/apps

  volumes:
    - name: volume-share
      emptyDir: {}
```
🚀 Step 2: Deploy the Pod

Apply the manifest:
```bash
kubectl apply -f volume-share-datacenter.yaml
```

Verify the Pod status:
```bash
kubectl get pods
```

Expected output:
```bash
volume-share-datacenter   2/2   Running   0   XXs
```
🧪 Step 3: Test Shared Volume
Enter Container 1:
```bash
kubectl exec -it volume-share-datacenter -c volume-container-datacenter-1 -- bash


Create a test file:

echo "Shared file from container 1" > /tmp/official/official.txt
exit
```
Enter Container 2:
```bash
kubectl exec -it volume-share-datacenter -c volume-container-datacenter-2 -- bash
```

Check the file:
```bash
cat /tmp/apps/official.txt
```

## ✅ Expected Output:

### Shared file from container 1
