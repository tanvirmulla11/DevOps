# DevOps Day 25: The Complete Git Feature Branch Workflow

Today's task demonstrated the complete Git feature branch workflow — from creating a new branch to merging and pushing changes to the remote repository.  
This is the standard method used by teams worldwide to safely and collaboratively manage codebases.

---

## 🧠 The Task

**Objective:** Perform a full feature development cycle in Git.

**Repository Path:** `/usr/src/kodekloudrepos/official`

**Requirements:**
1. Create a new branch `datacenter` from `master`.  
2. Copy `/tmp/index.html` into the repository.  
3. Add and commit the file on `datacenter`.  
4. Merge `datacenter` into `master`.  
5. Push both branches to the remote (`origin`).

---

## ⚙️ Step-by-Step Solution

### **Step 1: Connect to Server and Navigate**
```bash
ssh natasha@ststor01
cd /usr/src/kodekloudrepos/official
```
Markdown

# DevOps Day 25: The Complete Git Feature Branch Workflow

Today's task demonstrated the complete Git feature branch workflow — from creating a new branch to merging and pushing changes to the remote repository.  
This is the standard method used by teams worldwide to safely and collaboratively manage codebases.

---

## 🧠 The Task

**Objective:** Perform a full feature development cycle in Git.

**Repository Path:** `/usr/src/kodekloudrepos/official`

**Requirements:**
1. Create a new branch `datacenter` from `master`.  
2. Copy `/tmp/index.html` into the repository.  
3. Add and commit the file on `datacenter`.  
4. Merge `datacenter` into `master`.  
5. Push both branches to the remote (`origin`).

---

## ⚙️ Step-by-Step Solution

### **Step 1: Connect to Server and Navigate**
```bash
ssh natasha@ststor01
cd /usr/src/kodekloudrepos/official
```
### Step 2: Create and Switch to New Branch
Bash

sudo git checkout -b datacenter
### Step 3: Copy File and Commit Changes
```Bash
sudo cp /tmp/index.html .
sudo git add index.html
sudo git commit -m "Add datacenter index file"
```
### Step 4: Switch Back to Master
```Bash
sudo git checkout master
```
### Step 5: Merge the datacenter Branch
```Bash
sudo git merge datacenter
```
### Step 6: Push Both Branches to Remote
```Bash
sudo git push origin master datacenter
```
### ✅ Result:

### New branch datacenter created and merged into master.

### Both branches successfully pushed to the remote repository.

### Complete Git feature branch workflow achieved.
