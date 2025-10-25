# Git Tasks – Step-by-Step Commands

This document provides the commands to complete the Git tasks: reverting commits in two repositories and cherry-picking a commit from a feature branch to master.

---

## 1. Revert Latest Commit in `/usr/src/kodekloudrepos/news`
**Task:** Undo the most recent commit in the `news` repository and create a revert commit.

```bash
cd /usr/src/kodekloudrepos/news      # Go to the news repository
sudo git log --oneline               # View commit history
sudo git revert --no-commit HEAD     # Revert latest commit without committing
sudo git commit -m "revert news"     # Commit the revert with custom message
sudo git log --oneline               # Verify the new revert commit
```
### 2. Revert Latest Commit in /usr/src/kodekloudrepos/official

### Task: Undo the most recent commit in the official repository and create a revert commit.
```bash
cd /usr/src/kodekloudrepos/official  # Go to the official repository
sudo git log --oneline               # View commit history
sudo git revert --no-commit HEAD     # Revert latest commit without committing
sudo git commit -m "revert official" # Commit the revert with custom message
sudo git log --oneline               # Verify the new revert commit
```
### 3. Cherry-Pick Commit from feature to master in /usr/src/kodekloudrepos/cluster

### Task: Merge a specific commit (Update info.txt) from the feature branch into master.
```bash
cd /usr/src/kodekloudrepos/cluster  # Go to the cluster repository
sudo git checkout master            # Switch to master branch
sudo git log feature --oneline      # Find the commit hash on feature branch
sudo git cherry-pick 195f5ca        # Apply the specific commit to master
sudo git push origin master         # Push the updated master branch
sudo git log --oneline              # Verify the new commit on master
```

