# Git Stash Restore Task

## Task Summary
The Nautilus application development team stashed some in-progress changes in the `/usr/src/kodekloudrepos/news` repository.  
The goal was to restore the stash with the identifier `stash@{1}`, commit the changes, and push them to the remote repository.

---

## Steps Performed

## Connected to the Storage Server
```bash
   ssh natasha@ststor01
```
## Navigated to the repository
```bash
cd /usr/src/kodekloudrepos/news
```

## Checked available stashes
```bash
sudo git stash list
```

## Applied the stash
```bash
sudo git stash apply stash@{1}
```

## Staged and committed the changes
```bash
sudo git add .
sudo git commit -m "Restore and commit changes from stash@{1}"
```

## Pushed the commit to the remote repository
```bash
sudo git push origin master
```

## Verified the commit
```bash
sudo git log --oneline
```
## Verification

## The new commit message appeared at the top of the log:
```bash
3045552 Restore and commit changes from stash@{1}
95b202b initial commit
```

# ✅ Task completed successfully.
