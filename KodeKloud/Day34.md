# Task34: Git Hook - Auto Release Tag Creation



## Steps to Complete

1. Switch to user `natasha`.
2. Go to the bare repository directory:
```bash
   cd /opt/ecommerce.git/hooks
```
## Create a post-update hook file:

```bash
sudo vi post-update
```
## Add the following script inside:

```bash

#!/bin/bash
BRANCH=$(git rev-parse --symbolic --abbrev-ref HEAD)
if [ "$BRANCH" == "master" ]; then
    DATE=$(date +%F)
    git tag "release-$DATE"
fi
```
##Make the hook executable:

```bash

sudo chmod +x /opt/ecommerce.git/hooks/post-update
```
##Navigate to the working repo:
```bash
cd /usr/src/kodekloudrepos/ecommerce
```
## Checkout master branch and merge feature branch:

```bash
sudo git checkout master
sudo git merge feature
```
## Push changes to master to trigger the hook:

``` bash
sudo git push origin master
```
## Fetch tags to verify the release tag creation:
```bash
sudo git fetch origin --tags
sudo git tag
```

## ✅ Result:
## A tag like release-2025-10-30 is automatically created after pushing to the master branch.


