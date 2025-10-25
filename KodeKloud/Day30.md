# Git Reset Task – Clean Repository History

**Goal:** Reset the `cluster` repository so that only the initial commit and `add data.txt file` commit remain, and push changes to the remote.

---

## Step 1: Connect to Storage Server
```bash
ssh natasha@ststor01.stratos.xfusioncorp.com
# Password: Bl@kW
cd /usr/src/kodekloudrepos/cluster
```
## Step 2: Inspect Commit History
```bash
sudo git log --oneline
```

## Identify the target commit hash for add data.txt file.

## In this case, the hash is 029ac38.

## Step 3: Reset Repository to Target Commit
```bash
sudo git reset --hard 029ac38
```

## This resets both commit history and working directory to this commit.

## Step 4: Force Push to Remote
```bash
sudo git push origin master --force
```

## Necessary to overwrite remote history.

## Step 5: Verification
```bash
sudo git log --oneline
```

## Expected output:
```bash
029ac38 add data.txt file
66b17cd initial commit
```
## Confirms that unwanted test commits are removed and only the desired commits remain.

## ✅ Result:
## The repository now has a clean history with only the initial commit and the add data.txt file commit. The remote is updated accordingly.
