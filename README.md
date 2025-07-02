# 📘 DevOps Interview Guide

Welcome to the DevOps Interview Preparation Repository. This guide helps you revise the most commonly asked questions with clear answers — specially designed for freshers and job seekers in Cloud and DevOps roles.

---

## 📚 Table of Contents

- [Linux](#linux-🐧)
- [Networking](#networking-🌐)
- [Git](#git-🔧)
- [AWS](#aws-☁️)
- [Azure](#azure-☁️)
- [Terraform](#terraform-🧱)
- [Docker & Kubernetes](#docker--kubernetes-🐳)
- [Ansible](#ansible-🛠️)
- [CI/CD](#cicd-⚙️)
- [DevOps Methodology, Practices & Agile](#devops-methodology-practices--agile-📈)

---

## Linux 🐧

<details>
<summary>🔹 1. What is Linux?</summary>
<br>
Linux is an open-source, Unix-like operating system based on the Linux kernel. It is widely used in servers, development, and embedded systems.
</details>

<details>
<summary>🔹 2. What is the difference between Linux and Unix?</summary>
<br>
Unix is proprietary, while Linux is open-source. Linux is more commonly used in modern systems.
</details>

<details>
<summary>🔹 3. What is the Linux kernel?</summary>
<br>
The kernel is the core of Linux, managing hardware, memory, and processes.
</details>

<details>
<summary>🔹 4. What is a shell in Linux?</summary>
<br>
The shell is a command-line interface to interact with the OS (e.g., Bash).
</details>

<details>
<summary>🔹 5. What are inodes?</summary>
<br>
Inodes store metadata about files, like permissions and timestamps, not filenames.
</details>

<details>
<summary>🔹 6. What are runlevels in Linux?</summary>
<br>
Runlevels define the system state (e.g., 0 = halt, 3 = multi-user, 5 = GUI, 6 = reboot).
</details>

<details>
<summary>🔹 7. What is the difference between a process and a thread?</summary>
<br>
A process is an independent program; a thread is a lightweight subprocess within it.
</details>

<details>
<summary>🔹 8. What is the difference between hard and soft links?</summary>
<br>
Hard links point to file data (inode), soft links point to filenames (symbolic links).
</details>

<details>
<summary>🔹 9. What is a zombie process?</summary>
<br>
A zombie process has finished execution but still exists in the process table.
</details>

<details>
<summary>🔹 10. What is swap space?</summary>
<br>
Swap is disk space used as virtual memory when RAM is full.
</details>

<details>
<summary>🔹 11. What are the types of permissions in Linux?</summary>
<br>
Read (r), Write (w), Execute (x) for User, Group, and Others.
</details>

<details>
<summary>🔹 12. What is chmod?</summary>
<br>
`chmod` is used to change file or directory permissions.
</details>

<details>
<summary>🔹 13. What does chmod +x file.sh do?</summary>
<br>
It makes the shell script file executable.
</details>

<details>
<summary>🔹 14. What is chown used for?</summary>
<br>
`chown` changes file ownership (user and/or group).
</details>

<details>
<summary>🔹 15. What is the difference between > and >>?</summary>
<br>
`>` overwrites a file, `>>` appends to it.
</details>

<details>
<summary>🔹 16. How to check system memory usage?</summary>
<br>
Use `free -h`, `top`, `htop`, or `vmstat`.
</details>

<details>
<summary>🔹 17. How to schedule a task in Linux?</summary>
<br>
Use `cron` for recurring tasks, `at` for one-time tasks.
</details>

<details>
<summary>🔹 18. What is crontab?</summary>
<br>
`crontab` defines jobs for cron to run at specific times.
</details>

<details>
<summary>🔹 19. What is the use of grep?</summary>
<br>
`grep` searches text using patterns or regular expressions.
</details>

<details>
<summary>🔹 20. What is the difference between su and sudo?</summary>
<br>
`su` switches to another user; `sudo` runs a command as another user (typically root).
</details>

<details>
<summary>🔹 21. What is systemd?</summary>
<br>
Systemd is a system and service manager used to bootstrap and manage services.
</details>

<details>
<summary>🔹 22. What is the ps command?</summary>
<br>
`ps` displays running processes. Example: `ps aux`.
</details>

<details>
<summary>🔹 23. How to find a file in Linux?</summary>
<br>
Use `find /path -name filename` or `locate filename`.
</details>

<details>
<summary>🔹 24. What does df -h show?</summary>
<br>
Shows disk space usage in a human-readable format.
</details>

<details>
<summary>🔹 25. What is the difference between kill and killall?</summary>
<br>
`kill` ends a process by PID; `killall` ends all processes by name.
</details>

---
## Networking 🌐

<details>
<summary>🔹 1. What is a network?</summary>
<br>
A network is a group of interconnected devices that communicate and share resources.
</details>

<details>
<summary>🔹 2. What is an IP address?</summary>
<br>
An IP address is a unique identifier for a device on a network, used for routing traffic.
</details>

<details>
<summary>🔹 3. What is the difference between IPv4 and IPv6?</summary>
<br>
IPv4 uses 32-bit addresses (e.g., 192.168.1.1), while IPv6 uses 128-bit (e.g., fe80::1).
</details>

<details>
<summary>🔹 4. What is a subnet mask?</summary>
<br>
It determines the network and host portions of an IP address.
</details>

<details>
<summary>🔹 5. What is DNS?</summary>
<br>
DNS (Domain Name System) translates domain names into IP addresses.
</details>

<details>
<summary>🔹 6. What is DHCP?</summary>
<br>
DHCP (Dynamic Host Configuration Protocol) automatically assigns IP addresses to devices.
</details>

<details>
<summary>🔹 7. What is the difference between TCP and UDP?</summary>
<br>
TCP is connection-oriented and reliable; UDP is connectionless and faster but less reliable.
</details>

<details>
<summary>🔹 8. What is NAT?</summary>
<br>
NAT (Network Address Translation) maps private IP addresses to public ones.
</details>

<details>
<summary>🔹 9. What is a firewall?</summary>
<br>
A firewall filters incoming and outgoing traffic based on security rules.
</details>

<details>
<summary>🔹 10. What is the OSI model?</summary>
<br>
The OSI model is a conceptual framework with 7 layers that describe network communication.
</details>

<details>
<summary>🔹 11. What layer is DNS in the OSI model?</summary>
<br>
DNS operates at the Application layer (Layer 7).
</details>

<details>
<summary>🔹 12. What is a port number?</summary>
<br>
Ports identify specific processes/services on a device (e.g., HTTP = 80, SSH = 22).
</details>

<details>
<summary>🔹 13. What is ping used for?</summary>
<br>
`ping` checks network connectivity by sending ICMP echo requests.
</details>

<details>
<summary>🔹 14. What is traceroute?</summary>
<br>
`traceroute` shows the path packets take to reach a destination.
</details>

<details>
<summary>🔹 15. What is localhost?</summary>
<br>
Localhost (127.0.0.1) refers to the local computer's network interface.
</details>

<details>
<summary>🔹 16. What is a VPN?</summary>
<br>
A VPN (Virtual Private Network) securely connects remote users to a private network.
</details>

<details>
<summary>🔹 17. What is latency?</summary>
<br>
Latency is the delay between sending and receiving data, usually measured in milliseconds.
</details>

<details>
<summary>🔹 18. What is bandwidth?</summary>
<br>
Bandwidth is the maximum data transfer rate over a network path.
</details>

<details>
<summary>🔹 19. What is the default gateway?</summary>
<br>
It is the IP address that routes traffic from a local network to other networks.
</details>

<details>
<summary>🔹 20. What is ARP?</summary>
<br>
ARP (Address Resolution Protocol) maps IP addresses to MAC addresses on a local network.
</details>

---

## Git 🔧

<details>
<summary>🔹 1. What is Git?</summary>
<br>
Git is a distributed version control system used to track changes in source code during software development.
</details>

<details>
<summary>🔹 2. What is the difference between Git and GitHub?</summary>
<br>
Git is a version control system, while GitHub is a cloud-based platform that hosts Git repositories.
</details>

<details>
<summary>🔹 3. What is a repository in Git?</summary>
<br>
A repository (repo) is a storage space where your project’s code and its history are stored.
</details>

<details>
<summary>🔹 4. What is the difference between a local and remote repository?</summary>
<br>
A local repository exists on your machine; a remote repository is hosted on a server like GitHub or GitLab.
</details>

<details>
<summary>🔹 5. What is a branch in Git?</summary>
<br>
A branch is a separate line of development. The default branch is usually `main` or `master`.
</details>

<details>
<summary>🔹 6. How do you create a new branch?</summary>
<br>
Use `git branch branch-name` to create and `git checkout branch-name` to switch.
</details>

<details>
<summary>🔹 7. What is the difference between `git merge` and `git rebase`?</summary>
<br>
`git merge` combines branches and creates a merge commit.  
`git rebase` moves or reapplies commits on top of another base branch.
</details>

<details>
<summary>🔹 8. What is a commit in Git?</summary>
<br>
A commit is a snapshot of the repository at a specific point in time.
</details>

<details>
<summary>🔹 9. What does `git status` do?</summary>
<br>
It shows the current status of your working directory and staging area.
</details>

<details>
<summary>🔹 10. What is the staging area in Git?</summary>
<br>
It's a place where changes are kept before committing them with `git commit`.
</details>

<details>
<summary>🔹 11. What does `git add` do?</summary>
<br>
It adds changes to the staging area, preparing them for a commit.
</details>

<details>
<summary>🔹 12. What is the difference between `git pull` and `git fetch`?</summary>
<br>
`git pull` fetches changes and merges them into your local branch.  
`git fetch` only downloads changes, not merging them.
</details>

<details>
<summary>🔹 13. What does `git clone` do?</summary>
<br>
It copies a remote repository to your local machine.
</details>

<details>
<summary>🔹 14. What is a conflict in Git, and how do you resolve it?</summary>
<br>
A conflict occurs when changes in two branches clash. You resolve it manually and then commit the fix.
</details>

<details>
<summary>🔹 15. How do you undo a commit?</summary>
<br>
Use `git revert` to create a new commit that undoes changes, or `git reset` for local history changes.
</details>

<details>
<summary>🔹 16. What is `.gitignore`?</summary>
<br>
A file that tells Git which files or directories to ignore in a project.
</details>

<details>
<summary>🔹 17. What is a detached HEAD in Git?</summary>
<br>
It means you're not on any branch but on a specific commit. Commits made here won’t belong to any branch.
</details>

<details>
<summary>🔹 18. What is `git stash`?</summary>
<br>
It temporarily saves changes that are not ready to be committed so you can work on something else.
</details>

<details>
<summary>🔹 19. How do you see the commit history?</summary>
<br>
Use `git log` to view the commit history.
</details>

<details>
<summary>🔹 20. How do you contribute to an open-source project using Git?</summary>
<br>
1. Fork the repo  
2. Clone your fork  
3. Create a branch  
4. Make changes  
5. Commit and push  
6. Open a pull request (PR)
</details>

---
# ☁️ AWS – DevOps Interview Questions

<details>
<summary>🔹 1. What is AWS?</summary>
<br>
Amazon Web Services (AWS) is a comprehensive cloud computing platform offering IaaS, PaaS, and SaaS services such as compute, storage, databases, networking, machine learning, and more.
</details>

<details>
<summary>🔹 2. What is EC2?</summary>
<br>
Amazon EC2 (Elastic Compute Cloud) provides scalable virtual servers in the cloud.
</details>

<details>
<summary>🔹 3. What is S3?</summary>
<br>
Amazon S3 (Simple Storage Service) is an object storage service with high scalability, durability, and availability.
</details>

<details>
<summary>🔹 4. What are IAM roles and policies?</summary>
<br>
IAM (Identity and Access Management) allows you to define permissions using users, roles, and policies to securely control access to AWS resources.
</details>

<details>
<summary>🔹 5. What is an AMI?</summary>
<br>
An AMI (Amazon Machine Image) is a pre-configured template used to launch EC2 instances.
</details>

<details>
<summary>🔹 6. What is the difference between a Security Group and NACL?</summary>
<br>
Security Groups act as virtual firewalls for instances, while NACLs (Network Access Control Lists) control traffic at the subnet level.
</details>

<details>
<summary>🔹 7. What is an Elastic Load Balancer (ELB)?</summary>
<br>
ELB automatically distributes incoming traffic across multiple targets (EC2 instances, containers, etc.) to ensure high availability.
</details>

<details>
<summary>🔹 8. What is Auto Scaling?</summary>
<br>
Auto Scaling automatically adjusts the number of EC2 instances to handle traffic changes based on defined policies.
</details>

<details>
<summary>🔹 9. What is VPC?</summary>
<br>
Amazon VPC (Virtual Private Cloud) lets you provision a logically isolated network in AWS where you can launch resources.
</details>

<details>
<summary>🔹 10. What are subnets?</summary>
<br>
Subnets divide a VPC into smaller IP ranges, enabling isolation and routing of resources across different availability zones.
</details>

<details>
<summary>🔹 11. What is the difference between Public and Private subnets?</summary>
<br>
Public subnets have internet access via an Internet Gateway; private subnets do not.
</details>

<details>
<summary>🔹 12. What is CloudWatch?</summary>
<br>
Amazon CloudWatch monitors AWS resources and applications, providing logs, metrics, and alarms.
</details>

<details>
<summary>🔹 13. What is the difference between CloudFormation and Terraform?</summary>
<br>
CloudFormation is AWS's native Infrastructure as Code (IaC) service, while Terraform is cloud-agnostic and supports multiple providers.
</details>

<details>
<summary>🔹 14. What is Route 53?</summary>
<br>
Amazon Route 53 is a scalable DNS and domain name management service.
</details>

<details>
<summary>🔹 15. What is EBS?</summary>
<br>
Amazon EBS (Elastic Block Store) provides persistent block storage for EC2 instances.
</details>

<details>
<summary>🔹 16. What is EFS?</summary>
<br>
Amazon EFS (Elastic File System) is a scalable, shared file storage for use with EC2 instances.
</details>

<details>
<summary>🔹 17. What is an AWS Region and Availability Zone?</summary>
<br>
A Region is a geographic area; an Availability Zone is an isolated data center within a region.
</details>

<details>
<summary>🔹 18. What is Lambda?</summary>
<br>
AWS Lambda is a serverless compute service that lets you run code in response to events without provisioning or managing servers.
</details>

<details>
<summary>🔹 19. What is S3 Versioning?</summary>
<br>
S3 Versioning allows you to keep multiple versions of an object in the same bucket to prevent accidental deletions or overwrites.
</details>

<details>
<summary>🔹 20. What is the Shared Responsibility Model?</summary>
<br>
AWS secures the infrastructure; customers are responsible for securing their data, applications, and configurations.
</details>

---

## ✅ Coming Up Next

➡️ **Terraform 🧱**  
➡️ **Docker & Kubernetes 🐳**  
➡️ **CI/CD ⚙️**  

> 📘 _Keep building your cloud confidence — one concept at a time!_






