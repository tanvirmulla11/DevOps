# Day 42: Create a Docker Network

## ✅ Steps to Create Docker Network (App Server 3)

### Connect to App Server 3
```bash
ssh banner@stapp03
```

### Switch to root user (if needed)
```bash
sudo -i
```

### Create the docker network using bridge driver
```bash
sudo docker network create --driver bridge --subnet 172.28.0.0/24 --ip-range 172.28.0.0/24 blog
```

### Verify the network creation
```bash
sudo docker network ls
```

### Inspect the network details
```bash
sudo docker network inspect blog
```

## ✅ Expected Output:

### Network blog appears in the list.

### Driver = bridge

### Subnet = 172.28.0.0/24

### IPRange = 172.28.0.0/24

### Task completed successfully!

