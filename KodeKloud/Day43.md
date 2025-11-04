# Day 43: Docker Ports Mapping

### Connect to App Server 3
```bash
ssh banner@stapp03
```

### Switch to root (if needed)
```bash
sudo -i
```

### Pull the required nginx image
```bash
sudo docker pull nginx:alpine-perl
```

### Create and run the container
```bash
sudo docker run -d --name media -p 3000:80 nginx:alpine-perl
```

### Verify the container is running
```bash
sudo docker ps
```

### (Optional) Test the setup
```bash
curl -I http://localhost:3000
```

### ✅ Expected Output:

### Container name: media

### Image: nginx:alpine-perl

### Status: Up

### Port mapping: 0.0.0.0:3000->80/tcp

### Task successfully completed!
---
