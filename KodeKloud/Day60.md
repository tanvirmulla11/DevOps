# Day 60: Persistent Volumes in Kubernetes
# 🌐 Web Application Deployment with Persistent Storage on Kubernetes

This guide details how the **Nautilus DevOps Team** deployed a web application on Kubernetes using **Persistent Volumes (PV)** and **Persistent Volume Claims (PVC)** to store application data.  
The web app is exposed using a **NodePort Service** on port **30008**.

---

## 🎯 Objective

- Create a **PersistentVolume (PV)** with hostPath storage.
- Create a **PersistentVolumeClaim (PVC)** bound to that PV.
- Deploy a **Pod** running an `httpd:latest` container, mounting the PVC.
- Expose the web server using a **NodePort Service (30008)**.

---

## ⚙️ Step 1: Create the PersistentVolume (PV)

Create a file named `pv-datacenter.yaml`:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-datacenter
spec:
  storageClassName: manual
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /mnt/itadmin
```
Apply it:
```bash
kubectl apply -f pv-datacenter.yaml
```

Verify:
```bash
kubectl get pv
```

Expected:
```bash
NAME            CAPACITY   ACCESS MODES   STATUS   CLAIM   STORAGECLASS   AGE
pv-datacenter   5Gi        RWO            Available           manual         5s
```
## ⚙️ Step 2: Create the PersistentVolumeClaim (PVC)

Create a file named pvc-datacenter.yaml:
```bash
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-datacenter
spec:
  storageClassName: manual
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 2Gi

```
Apply it:
```bash
kubectl apply -f pvc-datacenter.yaml
```

Verify:
```bash
kubectl get pvc
```

Expected:
```bash
NAME             STATUS   VOLUME          CAPACITY   ACCESS MODES   STORAGECLASS   AGE
pvc-datacenter   Bound    pv-datacenter   5Gi        RWO            manual         5s
```
## 🧱 Step 3: Create the Pod (with PVC Mount)
```bash
Create a file named pod-datacenter.yaml:

apiVersion: v1
kind: Pod
metadata:
  name: pod-datacenter
  labels:
    app: httpd
spec:
  containers:
    - name: container-datacenter
      image: httpd:latest
      ports:
        - containerPort: 80
      volumeMounts:
        - name: datacenter-storage
          mountPath: /usr/local/apache2/htdocs
  volumes:
    - name: datacenter-storage
      persistentVolumeClaim:
        claimName: pvc-datacenter
```

Apply it:
```bash
kubectl apply -f pod-datacenter.yaml
```

Verify:
```bash
kubectl get pods
```

Expected:
```bash
NAME             READY   STATUS    RESTARTS   AGE
pod-datacenter   1/1     Running   0          30s
```
## 🌍 Step 4: Create the NodePort Service

Create a file named web-datacenter.yaml:
```bash
apiVersion: v1
kind: Service
metadata:
  name: web-datacenter
spec:
  type: NodePort
  selector:
    app: httpd
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30008
```

Apply it:
```bash
kubectl apply -f web-datacenter.yaml
```

Verify:
```bash
kubectl get svc web-datacenter
```

Expected:
```bash
NAME              TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
web-datacenter    NodePort   10.96.x.x       <none>        80:30008/TCP     10s
```
## 🔍 Step 5: Verify All Resources
```bash
kubectl get pv,pvc,pods,svc
```

Expected output:
```bash
NAME                         CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                   STORAGECLASS   AGE
persistentvolume/pv-datacenter   5Gi        RWO            Retain           Bound    default/pvc-datacenter   manual         2m

NAME                         STATUS   VOLUME          CAPACITY   ACCESS MODES   STORAGECLASS   AGE
persistentvolumeclaim/pvc-datacenter   Bound    pv-datacenter   5Gi        RWO            manual         2m

NAME               READY   STATUS    RESTARTS   AGE
pod/pod-datacenter 1/1     Running   0          30s

NAME               TYPE       CLUSTER-IP     PORT(S)        AGE
service/web-datacenter   NodePort   10.96.x.x      80:30008/TCP   10s
```
## 🌐 Step 6: Access the Web Application

Get the node IP:
```bash
kubectl get nodes -o wide
```

Example:
```bash
NAME                      STATUS   ROLES           AGE   VERSION   INTERNAL-IP   EXTERNAL-IP
kodekloud-control-plane   Ready    control-plane   15m   v1.27.16  172.17.0.2    <none>
```

Access the web page:
```bash
curl http://172.17.0.2:30008
```

## ✅ Expected:
```bash
<html><body><h1>It works!</h1></body></html>
```


