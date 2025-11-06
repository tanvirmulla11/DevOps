## Day 55: Kubernetes Sidecar Containers
# 🧩 Kubernetes Sidecar Logging Pattern — Webserver Pod

## 🎯 Objective
The Nautilus DevOps team needed to separate concerns in a multi-container pod setup — one container serving web traffic using **Nginx**, and another responsible for **log shipping**.  
Both containers share logs through a common **emptyDir** volume.

---

## ⚙️ Task Details

| Component | Specification |
|------------|----------------|
| **Pod Name** | `webserver` |
| **Container 1** | Name: `nginx-container`, Image: `nginx:latest` |
| **Container 2** | Name: `sidecar-container`, Image: `ubuntu:latest` |
| **Volume Name** | `shared-logs` |
| **Volume Type** | `emptyDir` |
| **Mount Path** | `/var/log/nginx` (for both containers) |
| **Sidecar Command** | `sh -c "while true; do cat /var/log/nginx/access.log /var/log/nginx/error.log; sleep 30; done"` |

---

## 🧾 Step 1: Create the Pod Definition File

Create a file named **`webserver.yaml`** and add the following content:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: webserver
spec:
  volumes:
    - name: shared-logs
      emptyDir: {}

  containers:
    - name: nginx-container
      image: nginx:latest
      volumeMounts:
        - name: shared-logs
          mountPath: /var/log/nginx

    - name: sidecar-container
      image: ubuntu:latest
      command: ["sh", "-c", "while true; do cat /var/log/nginx/access.log /var/log/nginx/error.log; sleep 30; done"]
      volumeMounts:
        - name: shared-logs
          mountPath: /var/log/nginx
```
## 🧩 Step 2: Deploy the Pod

Apply the manifest:
```bash
kubectl apply -f webserver.yaml
```

Verify the pod status:
```bash
kubectl get pods
```

Expected Output:
```bash
webserver   2/2   Running   0   10s
```
## 🧠 Step 3: Validate Setup
✅ Check Nginx is Running
```bash
kubectl exec -it webserver -c nginx-container -- curl localhost
```

Expected Output:
```bash
<html>
<head><title>Welcome to nginx!</title></head>
<body>
<h1>Welcome to nginx!</h1>
</body>
</html>
```
✅ Verify Logs are Being Shared

View logs from the sidecar container:
```bash
kubectl logs webserver -c sidecar-container --tail=10
```

Expected Output:
```bash
127.0.0.1 - - [05/Nov/2025:11:40:22 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.68.0"
2025/11/05 11:40:22 [notice] 1#1: start worker processes
```
## 🧾 Step 4: Verify Shared Volume
```bash
To confirm both containers use the same volume:

kubectl exec -it webserver -c nginx-container -- ls /var/log/nginx
kubectl exec -it webserver -c sidecar-container -- ls /var/log/nginx
Both should list:

lua
Copy code
access.log  error.log
```
## ✅ Step 5: Verification Summary
Checkpoint	Status
Pod created	✅
Both containers running	✅
Shared volume mounted	✅
Nginx logs written	✅
Sidecar reading logs	✅
Log output verified	✅
