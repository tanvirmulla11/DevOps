# DevOps Day 23: Collaborative Git Workflows with Forks

Today’s task shifted focus from the command line to the **web interface of Git (Gitea)** — an essential environment for collaborative development.  
I explored the concept of **forking**, one of the core ideas behind modern open-source and team collaboration workflows.  

This exercise clarified the difference between a **clone** (a local copy of a repository) and a **fork** (a new, server-side copy that I own).  
It was my first hands-on experience with the famous **“Fork and Pull Request”** workflow.

---

## 📋 Task Overview
**Objective:** Perform a repository fork using the Gitea web interface as user `jon`.  

**Requirements:**
- Log into the Gitea server as user **jon**.  
- Locate the repository **sarah/story-blog**.  
- Fork it to create a new copy under **jon’s** account.

---

## ⚙️ My Step-by-Step Solution

### Step 1: Access and Login
I opened the **Gitea UI** from the lab environment.  
On the login screen, I entered the credentials:

```bash
Username: jon
Password: Jon_pass123
```

After logging in, I landed on the Gitea dashboard.

---

### Step 2: Locate the Repository
Using the **search bar** at the top of the dashboard, I searched for the repository named:

```bash
sarah/story-blog
```

I clicked the repository name in the search results to open its main page.

---

### Step 3: Fork the Repository
In the top-right corner of the repository page, I found the **“Fork”** button and clicked it.

This opened the **New Fork** screen. The **Owner** field was automatically set to my account (`jon`).

---

### Step 4: Confirm the Fork
I clicked the **“Fork Repository”** button to finalize the action.

After a short moment, Gitea redirected me to my new repository’s page.

---

### Step 5: Verification
On the new repository page, the header displayed:

```bash
jon/story-blog
```

This confirmed that the fork was successful and that I now owned my own copy of the repository.

---

## 🧠 Why This Matters
Forking is a crucial part of collaborative software development because it:
- Allows contributors to work safely on their own copies without affecting the original repository.
- Enables open-source contributions through the **Pull Request (PR)** workflow.
- Promotes experimentation and learning in isolated environments.

---

## 🔄 The Fork and Pull Request Workflow

The standard workflow goes like this:

1. **Fork** a repository → creates your own copy.  
2. **Clone** your fork locally → make changes on your machine.  
3. **Commit & Push** updates to your forked repo.  
4. **Create a Pull Request (PR)** → propose changes back to the original repository.

This model encourages clean collaboration and version control across multiple contributors.

---

## 💻 Exploring the UI Used
The Gitea web interface provides a friendly and visual way to manage Git repositories:
- **Search Bar:** Quickly locate repositories.
- **Fork Button:** Instantly create your own server-side copy.
- **Pull Requests Tab:** View, create, and manage collaboration requests.
- **User Dashboard:** Track repositories you own or have contributed to.

---

✅ **Outcome:**  
Successfully forked the `sarah/story-blog` repository into `jon/story-blog` using the Gitea web interface, completing the foundation of the **Fork and Pull Request** workflow.

