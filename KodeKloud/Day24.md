# DevOps Day 24: Managing Development with Git Branches

Today’s task focused on one of the **core practices of collaborative software development** — creating and managing branches in Git.  
Branching is a fundamental concept that allows developers to **work on new features or bug fixes in isolation**, without affecting the stability of the main project.

I learned how to create a new branch from the existing `master` branch and understood how Linux file permissions can impact Git operations when working in system-owned directories.  
This document is my first-person guide to that process.

---

## 🧾 Table of Contents
- [The Task](#-the-task)
- [My Step-by-Step Solution](#-my-step-by-step-solution)
- [Why Did I Do This? (The "What & Why")](#-why-did-i-do-this-the-what--why)
- [Deep Dive: git branch vs. git checkout -b](#-deep-dive-git-branch-vs-git-checkout--b)
- [Exploring the Commands Used](#-exploring-the-commands-used)

---

## 🧠 The Task

**Objective:**  
Create a new Git branch on the **Storage Server**.

**Requirements:**
- Navigate to the `/usr/src/kodekloudrepos/games` Git repository.  
- Create a new branch named **xfusioncorp_games** from the `master` branch.  
- Do **not** switch to the new branch or make any code changes.

---

## ⚙️ My Step-by-Step Solution

This process was completed entirely on the **command line** of the Storage Server.

---

### **Step 1: Connect to the Server**

### I first logged into the Storage Server as user **natasha**.

```bash
ssh natasha@ststor01
```
### Step 2: Navigate to the Repository

### All Git operations must be performed inside the repository directory, so I navigated to the path:
```bash
cd /usr/src/kodekloudrepos/games
```
### Step 3: Create the Branch

### Because the repository was stored under /usr/src (a system directory owned by root), I used sudo to ensure the command had proper permissions to write to the .git directory.
```bash
sudo git branch xfusioncorp_games
```

### This command created a new branch named xfusioncorp_games from the current branch (master).

### Step 4: Verification

### To confirm the branch was created successfully, I listed all the local branches.
```bash
sudo git branch
```

### The output displayed:
```bash
  * master
    xfusioncorp_games
```

### The asterisk (*) indicates that I was still on the master branch — exactly as required by the task.

## ✅ Result: New branch created successfully without switching branches.

## 💡 Why Did I Do This? (The "What & Why")

### Creating branches is essential for collaborative development because it:

### Keeps the main (production) branch stable.

### Allows safe experimentation and isolated feature development.

### Makes it easy to review and merge changes later using pull requests.

### Supports parallel development, enabling multiple team members to work on different features simultaneously.

## 🔍 Deep Dive: git branch vs. git checkout -b
### Command	Description
### git branch <branch-name>	Creates a new branch, but does not switch to it.
### git checkout -b <branch-name>	Creates a new branch and switches to it immediately.

### In this task, I used git branch because the instructions explicitly said not to switch to the new branch.

## 🧰 Exploring the Commands Used
```bash
git branch
```
### Displays, creates, or deletes branches.
```bash
git branch          # Lists all local branches
git branch <name>   # Creates a new branch
git branch -d <name> # Deletes a branch
```
### sudo

### Used to execute commands with root privileges — necessary in directories owned by the system, like /usr/src.
```bash
sudo <command>
```
```bash
cd
```
### Changes the current working directory to the specified path. Essential for navigating into the Git repo before executing any Git commands.
```bash
cd /usr/src/kodekloudrepos/games
```
## ✅ Final Output
```bash
* master
  xfusioncorp_games
```

### This confirmed that:

### The new branch xfusioncorp_games was successfully created.

### I remained on the master branch, as required.

## 🏁 Summary

### In this task, I successfully:

### Connected to the Storage Server as natasha.

### Navigated to /usr/src/kodekloudrepos/games.

### Created a new branch xfusioncorp_games using sudo git branch.

### Verified that the branch was created correctly.
