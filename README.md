# 📘 DevOps Interview Guide

Welcome to the DevOps Interview Preparation Repository. This guide will help you revise the most commonly asked questions with clear answers, especially designed for freshers and job seekers in cloud and DevOps roles.

---

## 📚 DevOps Table of Contents 🔧

- ### 🐧 [Linux](#linux-🐧)
- ### 🌐 [Networking](#networking-🌐)
- ### 🔧 [Git](#git-🔧)
- ### ☁️ [AWS](#aws-☁️)
- ### ☁️ [Azure](#azure-☁️)
- ### 🧱 [Terraform](#terraform-🧱)
- ### 🐳 [Docker & Kubernetes](#docker--kubernetes-🐳)
- ### 🛠️ [Ansible](#ansible-🛠️)
- ### ⚙️ [CI/CD](#cicd-⚙️)
- ### 📈 [DevOps Methodology, Practices & Agile](#devops-methodology-practices--agile-📈)

---

## Linux 🐧

<details>
<summary>🔹 1. What is Linux?</summary>
<br>
Linux is an open-source, Unix-like operating system based on the Linux kernel. It is widely used for servers, development, networking, and embedded systems.
</details>

<details>
<summary>🔹 2. What is the difference between Linux and Unix?</summary>
<br>
UNIX is a proprietary OS, while Linux is open-source. Linux is widely used for modern infrastructure, and UNIX is typically used in legacy systems.
</details>

<details>
<summary>🔹 3. What is the Linux kernel?</summary>
<br>
The Linux kernel is the core of the operating system that manages hardware, system calls, processes, and resources.
</details>

<details>
<summary>🔹 4. What is a shell in Linux?</summary>
<br>
The shell is a command-line interface (CLI) used to interact with the OS, like Bash, Zsh, or Sh.
</details>

<details>
<summary>🔹 5. What are inodes?</summary>
<br>
Inodes are data structures storing metadata about files (e.g., permissions, ownership, size), but not filenames.
</details>

<details>
<summary>🔹 6. What are runlevels in Linux?</summary>
<br>
Runlevels define the state of the machine: e.g., 0 = halt, 1 = single-user, 3 = multi-user, 5 = GUI, 6 = reboot.
</details>

<details>
<summary>🔹 7. What is the difference between a process and a thread?</summary>
<br>
A process is an independent program in execution, while a thread is a lightweight subprocess sharing the same memory space.
</details>

<details>
<summary>🔹 8. What is the difference between hard link and soft link?</summary>
<br>
Hard links point to inodes directly, soft (symbolic) links point to filenames.
</details>

<details>
<summary>🔹 9. What is a zombie process?</summary>
<br>
A zombie process has completed execution but still has an entry in the process table awaiting parent acknowledgment.
</details>

<details>
<summary>🔹 10. What is swap space?</summary>
<br>
Swap is disk space used as virtual memory when the system runs out of RAM.
</details>

<details>
<summary>🔹 11. What are the types of permissions in Linux?</summary>
<br>
Read (r), Write (w), Execute (x) for User, Group, and Others.
</details>

<details>
<summary>🔹 12. What is chmod?</summary>
<br>
`chmod` changes the permission of files/directories using symbolic or numeric mode.
</details>

<details>
<summary>🔹 13. What does chmod +x file.sh do?</summary>
<br>
It makes the file executable by adding execute permission.
</details>

<details>
<summary>🔹 14. What is chown used for?</summary>
<br>
`chown` changes file ownership (user and group).
</details>

<details>
<summary>🔹 15. What is the difference between `>` and `>>`?</summary>
<br>
`>` overwrites a file, while `>>` appends to it.
</details>

<details>
<summary>🔹 16. How to check system memory usage?</summary>
<br>
Use commands like `free -h`, `top`, `htop`, or `vmstat`.
</details>

<details>
<summary>🔹 17. How to schedule a task in Linux?</summary>
<br>
Use `cron` (for recurring tasks) or `at` (for one-time tasks).
</details>

<details>
<summary>🔹 18. What is crontab?</summary>
<br>
`crontab` is a table used by the cron daemon to schedule jobs at fixed times/dates.
</details>

<details>
<summary>🔹 19. What is the use of grep?</summary>
<br>
`grep` searches text using patterns or regular expressions.
</details>

<details>
<summary>🔹 20. What is the difference between su and sudo?</summary>
<br>
`su` switches to another user (typically root), `sudo` runs a command as another user temporarily.
</details>

<details>
<summary>🔹 21. What is systemd?</summary>
<br>
Systemd is a modern init system used to bootstrap the system and manage services.
</details>

<details>
<summary>🔹 22. What is the `ps` command?</summary>
<br>
`ps` shows currently running processes. Example: `ps aux`.
</details>

<details>
<summary>🔹 23. How to find a file in Linux?</summary>
<br>
Use `find /path -name filename` or `locate filename`.
</details>

<details>
<summary>🔹 24. What does `df -h` show?</summary>
<br>
It shows disk space usage in a human-readable format.
</details>

<details>
<summary>🔹 25. What is the difference between kill and killall?</summary>
<br>
`kill` ends a process by PID; `killall` ends all processes by name.
</details>

---

### 📌 Stay tuned...

Next up:  
🌐 **Networking Interview Questions**  
🔧 **Git Essentials**  
☁️ **AWS Core Services**  
🐳 **Docker & Kubernetes**  
⚙️ **CI/CD Pipelines**  
🧱 **Terraform** and more!
