
# 🧩 Task: Create a New Image from a Running Container
## Steps
## Switch to App Server 2
```bash
ssh steve@stapp02
```
## Verify the running container
```bash
sudo docker ps
```
## ✅ Ensure the container name is ubuntu_latest.

## Create a new image named blog:xfusion from the running container
```bash
sudo docker commit ubuntu_latest blog:xfusion
```

## Verify that the image has been created
```bash
sudo docker images | grep blog
```

## ✅ Expected Output:

## blog   xfusion   <image_id>   ...

