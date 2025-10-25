# Git Revert Task – Step-by-Step

This document provides the steps to safely revert the latest commit in the `news` and `official` repositories located on the Storage Server.

---

## Reverting Latest Commit in `/usr/src/kodekloudrepos/news`

### Phase 1: Investigation
1. Connect to the storage server:
```bash
   ssh natasha@ststor01
```
2.Navigate to the repository:
```bash
cd /usr/src/kodekloudrepos/news
```

3.View the commit history:
```bash
sudo git log --oneline
```
### Phase 2: Revert the Latest Commit

### Revert without committing:
```bash
sudo git revert --no-commit HEAD
```

### Commit with a custom message:
```bash
sudo git commit -m "revert news"
```
### Phase 3: Verification

### Verify the new commit:
```bash
sudo git log --oneline
```
