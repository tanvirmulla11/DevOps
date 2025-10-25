# DevOps Day 22: Mastering the `git clone` Command

Today’s task focused on one of the most fundamental parts of any developer’s workflow — **cloning a repository**.  
While `git clone` seems simple at first glance, this exercise taught me the subtleties of how it determines the **destination path** and why small mistakes can cause big issues.  

After a few failed attempts, I finally understood how to interpret the task correctly and clone the repository exactly where required.

---

## 📋 Task Overview
**Objective:** Create a local working copy of a central Git repository on the Storage Server.  

**Requirements:**
- Connect to the server as user `natasha`.
- The central repository was located at `/opt/games.git`.
- Clone the repository inside the `/usr/src/kodekloudrepos` directory.

---

## ⚙️ My Step-by-Step Solution (The One That Worked)

### Step 1: Connect to the Server
I logged into the Storage Server using SSH.

```bash
ssh natasha@ststor01
```
## Step 2: Navigate to the Parent Directory

### This step was critical. Instead of specifying the full target path in the clone command,
### I first changed my current working directory to the parent folder where the repository should reside.
```bash
cd /usr/src/kodekloudrepos/
```
### Step 3: Clone the Repository

### Once inside the correct directory, I ran the git clone command using only the source repository path.
```bash
git clone /opt/media.git
```
### Git automatically created a new subdirectory named media (derived from the source name).
### The output confirmed success, even though the repository was empty — which was expected.
## Step 4: Verify the Clone

### To confirm everything worked, I listed the contents of the directory.
```bash
ls -la
```
# 🧠 Why This Matters

## Understanding how git clone interprets paths ensures you:

## Avoid overwriting existing files.

## Maintain proper directory structures in collaborative environments.

## Follow CI/CD or lab validation expectations precisely.
