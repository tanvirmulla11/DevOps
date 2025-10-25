# Max Story Merge – Pull Request Workflow

## Step 1: SSH and Verify Repository
```bash
ssh max@ststor01.stratos.xfusioncorp.com
# Password: Max_pass123
cd ~/story-blog
git log --oneline
git branch -a
git push origin story/fox-and-grapes
```
## Step 2: Create Pull Request in Gitea

### Open Gitea UI and log in as Max (Username: max, Password: Max_pass123)

### Navigate to story-blog → New Pull Request

### Set PR details:

### Pull from (source): story/fox-and-grapes

### Merge into (destination): master

### Title: Added fox-and-grapes story

### Assign Tom as reviewer → Click Create Pull Request

## Step 3: Review and Approve PR as Tom

### Log out Max → Log in as Tom (Username: tom, Password: Tom_pass123)

### Open PR → Go to Files Changed → Click Review → Select Approve → Submit Review

## Step 4: Merge Pull Request

### Click Merge Pull Request → Confirm merge

### Verify master branch now contains Max’s story

### Optional: Take screenshots for proof

# ✅ Result: Max’s story is merged into master safely, after proper review. No direct pushes to master were made.
