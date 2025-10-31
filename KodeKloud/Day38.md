# 🧩 Task: Pull and Retag BusyBox Image (on App Server 2)
## Steps

## Switch to App Server 2
```bash
ssh steve@stapp02
```

## Pull the BusyBox musl image
```bash
sudo docker pull busybox:musl
```

## Retag the image as busybox:blog
```bash
sudo docker tag busybox:musl busybox:blog
```

## Verify both image tags
```bash
sudo docker images | grep busybox
```

## ✅ Expected Output:

## busybox   blog   <image_id>   ...
## busybox   musl   <image_id>   ...

---
