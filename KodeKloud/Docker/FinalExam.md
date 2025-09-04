# 🚀 Nautilus DevOps – Docker Final Exam (App Server 2)

### This repository documents the nine Docker tasks successfully completed on Application Server 2 (stapp02) in the Stratos Datacenter as part of the KodeKloud – Docker Level 1 Final Exam.

### All tasks were executed using standard Docker CLI commands for container, image, network, and file management.

# 📋 Task Summary
| Task No. | Objective                                                      | Status      |
| -------- | -------------------------------------------------------------- | ----------- |
| 1        | Create a Debug Container (`debug_2`)                           | ✅ Completed |
| 2        | Deploy Nginx Container (`nginx_2`)                             | ✅ Completed |
| 3        | Copy File from Container to Host                               | ✅ Completed |
| 4        | Copy File from Host to Container                               | ✅ Completed |
| 5        | Create Image from Container                                    | ✅ Completed |
| 6        | Pull Required Docker Images (`redis`, `memcached`)             | ✅ Completed |
| 7        | Create Docker Network (`mysql-network`)                        | ✅ Completed |
| 8        | Delete Old Docker Network (`php-network`)                      | ✅ Completed |
| 9        | Restart Exited Containers (`lab1_container`, `lab2_container`) | ✅ Completed |
# 📝 Detailed Task Breakdown
## Task 1 – Create a Debug Container

### Objective: Create a container named debug_2 using ubuntu/apache2:latest, overriding CMD to sleep 1000.
```bash
sudo docker pull ubuntu/apache2:latest
sudo docker run -d --name debug_2 ubuntu/apache2:latest sleep 1000
sudo docker ps
```

### ✅ Result: debug_2 is running in detached mode.

## Task 2 – Deploy Nginx Container

### Objective: Create a container named nginx_2 using nginx:alpine.
```bash
sudo docker pull nginx:alpine
sudo docker run -d --name nginx_2 nginx:alpine
sudo docker ps
```

### ✅ Result: nginx_2 is running successfully.
## Task 3 – Copy File from Container to Host

### Objective: Copy /tmp/test.txt.gpg from container development_3 to host /tmp.
```bash
sudo docker cp development_3:/tmp/test.txt.gpg /tmp/
ls -l /tmp/test.txt.gpg
```

### ✅ Result: File successfully copied to host.
## Task 4 – Copy File from Host to Container

### Objective: Copy /tmp/nautilus.txt.gpg from host to container ubuntu_latest at /usr/src/.
```bash
sudo docker exec ubuntu_latest mkdir -p /usr/src/
sudo docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src/
sudo docker exec ubuntu_latest ls -l /usr/src/
```

### ✅ Result: File available inside container.
## Task 5 – Create Image from Container

### Objective: Commit container alpine_nautilus into a new image alpine:nautilus.
```bash
sudo docker commit alpine_nautilus alpine:nautilus
sudo docker images
```

### ✅ Result: Custom image created.

## Task 6 – Pull Required Docker Images

### Objective: Pull redis:alpine and memcached:alpine.
```bash
sudo docker pull redis:alpine
sudo docker pull memcached:alpine
sudo docker images
```

### ✅ Result: Images downloaded successfully.
## Task 7 – Create Docker Network

### Objective: Create bridge network mysql-network with subnet 182.18.0.0/24.
```bash
sudo docker network create \
  --driver bridge \
  --subnet 182.18.0.0/24 \
  --gateway 182.18.0.1 \
  mysql-network

sudo docker network inspect mysql-network
```

### ✅ Result: Network ready for use.
## Task 8 – Delete Old Docker Network

### Objective: Remove unused php-network.
```bash
sudo docker network rm php-network
```

### ✅ Result: Network deleted successfully.
## Task 9 – Restart Exited Containers

### Objective: Restart exited containers lab1_container and lab2_container.
```bash
sudo docker start lab1_container
sudo docker start lab2_container
sudo docker ps
```

### ✅ Result: Both containers restarted.
## 📌 Notes

### All tasks performed on App Server 2 (stapp02).

### Files were copied safely without modification.

### Networking tasks ensured custom subnets and gateways were configured properly.

### This README provides step-by-step commands for replication.

## Images 
<img width="1919" height="969" alt="Screenshot 2025-08-27 114758" src="https://github.com/user-attachments/assets/572de021-c452-4a3c-8f0f-2cfdf1be478d" />
<img width="1919" height="977" alt="Screenshot 2025-08-27 113405" src="https://github.com/user-attachments/assets/95d66478-ac2d-4361-a8b7-f9a1ae9ebe2e" />

## ✅ Final Result:
## All 9 Docker tasks were completed successfully, demonstrating skills in container management, image creation, file operations, and networking.

