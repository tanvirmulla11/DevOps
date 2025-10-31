# Task: Copy Encrypted File into Running Container on App Server 2

## Steps
Connect to App Server 2  
```bash
ssh steve@stapp02
```
## Verify the running container

```bash
sudo docker ps
```
## Ensure a container named ubuntu_latest is running.

## Copy the encrypted file from host to container

```bash
sudo docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src/
```
## Verify the file inside the container

```bash
sudo docker exec -it ubuntu_latest ls -l /usr/src/
```
## Confirm that nautilus.txt.gpg exists and is unmodified.
---


