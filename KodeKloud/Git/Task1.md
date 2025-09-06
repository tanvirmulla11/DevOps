# 📌 KodeKloud – Git Level 2

## This repository documents the solution for Git Level 2 task 1 from KodeKloud.
# 📖 What is Git?
### Git is a distributed version control system (VCS) that allows developers to track changes in their code, collaborate with teams, and manage different versions of projects.
### It provides a workflow where you can move code between:

### Working Directory → Staging Area → Repository

# 📝 Task Objective

### Set up and initialize a Git repository under /opt/games.git.

# ⚙️ Steps Performed
### 1. SSH into the server
```bash
ssh natasha@ststor01
```
### 2. Switch to superuser
```bash
sudo su
```
### 3. Install Git
```bash
yum install git -y
```
### 4. Create project directory
```bash
mkdir /opt/games.git
cd /opt/games.git
```
### 5. Initialize Git repository
```bash
git init
```
# ✅ Result

### Git was successfully installed on the server.

### An empty repository was created in /opt/games.git.

### The default branch created is master (can be renamed to main).

# 📌 Notes

### This task validates the ability to install Git, create a new project folder, and initialize it as a Git repository.

### The setup can now be used to commit, push, and manage source code.

#image
<img width="1919" height="973" alt="Screenshot 2025-09-05 111409" src="https://github.com/user-attachments/assets/124d2a90-e8e3-4d43-a086-88a173509ed5" />
