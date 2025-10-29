# Git Rebase Task

## Task Summary
The Nautilus application development team has been working on a project repository `/opt/demo.git`.  
A developer was working on the `feature` branch while new commits were pushed to the `master` branch.  
The requirement was to rebase the `feature` branch with `master` **without losing any data** and **without creating a merge commit**.

---

## Steps Performed
## Connected to the Storage Server
 ```bash
   ssh natasha@ststor01
```
## Navigated to the repository
 ```bash
cd /usr/src/kodekloudrepos/demo
```

## Checked existing branches
 ```bash
sudo git branch
```

## Fetched latest updates from origin
 ```bash
sudo git fetch origin
```

## Rebased the feature branch with master
```bash
sudo git rebase master
```

## Verified commit history
 ```bash
sudo git log --oneline --graph --all
```

## Pushed updated feature branch
 ```bash
sudo git push origin feature --force
```
## Verification

### The rebase was successful:

### No merge commits were created

### The feature branch now includes all latest changes from master

### Commit history is clean and linear

## ✅ Task completed successfully.
