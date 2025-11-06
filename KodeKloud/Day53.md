# Day 53: Resolve VolumeMounts Issue in Kubernetes
# 🧩 Kubernetes Task — Fix Nginx + PHP-FPM Configuration

## 🧠 Problem Statement
The Nautilus DevOps team encountered an issue with their **Nginx and PHP-FPM** setup running on the Kubernetes cluster.  
The application became non-functional, and the team needed to:
1. Investigate and fix the misconfiguration.
2. Ensure that PHP files execute properly via FastCGI.
3. Copy the `index.php` file from `/home/thor/` into the Nginx document root.
4. Verify accessibility using the “Website” button.

---

## ⚙️ Environment Details
- **Pod Name:** `nginx-phpfpm`
- **ConfigMap Name:** `nginx-config`
- **Service Name:** `nginx-service`
- **Port:** `8099`
- **NodePort:** `30008`
- **Document Root:** `/var/www/html`

---

## 🔍 Root Cause
The **ConfigMap (nginx-config)** contained an incorrect or incomplete FastCGI configuration.  
As a result, Nginx couldn’t communicate with the PHP-FPM container properly, breaking dynamic PHP file handling.

---

## 🛠️ Step-by-Step Fix

### 1. Inspect the current ConfigMap
```bash
kubectl describe configmap nginx-config
```
### 2. Edit the Nginx configuration
```bash
kubectl edit configmap nginx-config
```

## Replace or fix the nginx.conf section to:
```bash
events {}

http {
  server {
    listen 8099 default_server;
    listen [::]:8099 default_server;

    root /var/www/html;
    index index.php index.html index.htm;
    server_name _;

    location / {
      try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
      include fastcgi_params;
      fastcgi_index index.php;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
      fastcgi_pass 127.0.0.1:9000;
    }
  }
}
```

### Apply the updated configuration if edited manually:
```bash
kubectl apply -f /tmp/kubectl-edit-xxxx.yaml
```
### 3. Recreate the pod
```bash
kubectl delete pod nginx-phpfpm
kubectl apply -f nginx-phpfpm.yaml   # or allow Deployment/ReplicaSet to recreate it
```

Wait for it to start:
```bash
kubectl get pods
```
### 4. Verify the pod’s containers
```bash
kubectl get pods -o wide
kubectl describe pod nginx-phpfpm
```

Ensure both containers (nginx-container and phpfpm-container) are running.

### 5. Copy the PHP file to the Nginx container
```bash
kubectl cp /home/thor/index.php nginx-phpfpm:/var/www/html/index.php -c nginx-container
```
### 6. Verify service configuration

Check existing service:
```bash
kubectl get svc nginx-service
```

If the selector is incorrect (e.g., app=php-app), edit it:
```bash
kubectl edit svc nginx-service
```

Ensure the selector matches your pod:
```bash
selector:
  app: nginx-phpfpm
```

Confirm:
```bash
kubectl describe svc nginx-service | grep Endpoints
```

Should show:
```bash
Endpoints: 10.244.x.x:8099
```
### 7. Reload Nginx configuration
```bash
kubectl exec -it nginx-phpfpm -c nginx-container -- nginx -s reload
```

### If netstat is missing, this is expected — no issue.

### 8. Test internal communication
```bash
kubectl exec -it nginx-phpfpm -c nginx-container -- curl localhost:8099
```
### 9. Test external NodePort access
```bash
curl http://172.17.0.2:30008/
```

### ✅ Expected Output:

### A PHP info page

### or your custom “Welcome” message from index.php

