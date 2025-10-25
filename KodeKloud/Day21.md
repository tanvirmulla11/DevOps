# DevOps Day 21: Creating a Central Git Repository

Today’s task focused on building the foundation for collaboration in software development — setting up a **central Git repository**.  
This repository serves as the **single source of truth** where all developers can push and pull their code securely.

---

## 📋 Task Overview
**Goal:** Configure the Storage Server to act as a Git server by creating a bare repository.  
**Requirements:**
- Install Git using the `yum` package manager.  
- Create a bare Git repository named `/opt/official.git`.

---

## ⚙️ Step-by-Step Solution

### Step 1: Install Git
First, I connected to the Storage Server and ensured Git was installed.

```bash
ssh natasha@ststor01
sudo yum install -y git
```
## Step 2: Create a Bare Repository

### A bare repository is used as a central remote repo — it does not contain a working directory.
```bash
sudo git init --bare /opt/official.git
```
## Step 3: Verify Repository Creation

### After initialization, I verified that the repository was successfully created.
```bash
ls -l /opt/official.git
```
### The output displayed files such as:
```bash
HEAD  config  description  hooks/  info/  objects/  refs/
```
# 🧠 Why This Matters

## A central Git repository enables:

## Collaborative development for teams.

## Version control consistency.

## A reliable backup of all source code changes.
