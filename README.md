# 📘 DevOps Interview Guide
Welcome to the DevOps Interview Preparation Repository. This guide helps you revise the most commonly asked questions with clear answers  specially designed for job seekers in Cloud and DevOps roles.
---
## 📚 Table of Contents
- [Linux](#linux-🐧)
- [Networking](#networking-🌐)
- [Git](#git-🔧)
- [KodeKloud](#KodeKloud)
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
# ☁️ GCP Interview Questions & Answers
<details>
<summary>1️⃣ What is Google Cloud Platform (GCP)?</summary>
GCP is a suite of cloud computing services provided by Google. It offers IaaS, PaaS, and SaaS solutions, including compute, storage, networking, Big Data, and AI/ML services.
</details>

<details>
<summary>2️⃣ What is Google Compute Engine?</summary>
Google Compute Engine (GCE) is GCP’s IaaS component, allowing users to create and manage virtual machines (VMs) on Google’s infrastructure.
</details>

<details>
<summary>3️⃣ What are GCP Projects?</summary>
A GCP Project is a logical container that groups together resources like VMs, APIs, billing, and IAM. Projects provide isolation and billing boundaries.
</details>

<details>
<summary>4️⃣ What is the role of IAM in GCP?</summary>
IAM (Identity and Access Management) controls who can access what in a GCP project. It assigns roles to users and service accounts to manage permissions.
</details>

<details>
<summary>5️⃣ What is a Service Account?</summary>
A service account is a special type of Google account used by applications or VMs to interact with GCP APIs securely.
</details>

<details>
<summary>6️⃣ Difference between Preemptible and Standard VM instances?</summary>
Preemptible VMs are short-lived, cost-effective instances that can be terminated by GCP anytime (after 24h max). Standard VMs are stable, long-running instances.
</details>

<details>
<summary>7️⃣ What is Google Cloud Storage?</summary>
It’s a globally unified object storage service for unstructured data like files, images, backups, and logs.
</details>

<details>
<summary>8️⃣ Explain GCP’s networking components.</summary>
Key components include:
- VPC (Virtual Private Cloud)
- Subnets
- Firewalls
- Routes
- Cloud Load Balancing
</details>

<details>
<summary>9️⃣ What is GKE?</summary>
Google Kubernetes Engine (GKE) is a managed Kubernetes service for running containerized applications in production.
</details>

<details>
<summary>🔟 What is Cloud Pub/Sub?</summary>
It’s a messaging service that enables asynchronous communication between services using a publisher-subscriber model.
</details>

<details>
<summary>🔢 11. What is the use of Cloud Functions?</summary>
Cloud Functions is a serverless compute service for running event-driven functions without managing infrastructure.
</details>

<details>
<summary>🔢 12. What is BigQuery?</summary>
BigQuery is GCP’s fully managed data warehouse designed for fast SQL analytics over large datasets.
</details>

<details>
<summary>🔢 13. How does GCP handle regions and zones?</summary>
Regions are specific geographical locations; each region has multiple zones. Zones are isolated locations within a region.
</details>

<details>
<summary>🔢 14. Difference between GCP roles: Owner, Editor, and Viewer?</summary>
- Owner: Full access to all resources
- Editor: Modify existing resources
- Viewer: Read-only access
</details>

<details>
<summary>🔢 15. What is Cloud Run?</summary>
Cloud Run is a fully managed compute platform that automatically scales containers in response to HTTP requests.
</details>

<details>
<summary>🔢 16. What is GCP Marketplace?</summary>
It is a platform to deploy third-party solutions, like WordPress, Jenkins, and MongoDB, directly to GCP.
</details>

<details>
<summary>🔢 17. What is Stackdriver (now called Cloud Operations)?</summary>
It is a suite of tools for monitoring, logging, tracing, and diagnostics of applications and infrastructure.
</details>

<details>
<summary>🔢 18. How is billing handled in GCP?</summary>
Billing is linked to GCP projects and can be managed via budgets, alerts, and cost analysis tools in the Billing Console.
</details>

<details>
<summary>🔢 19. What is Cloud Spanner?</summary>
A globally distributed, horizontally scalable, and strongly consistent relational database service.
</details>

<details>
<summary>🔢 20. What is the Shared VPC in GCP?</summary>
It allows multiple projects to share a common Virtual Private Cloud network, simplifying policy enforcement and connectivity.
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

## ☁️ Azure – DevOps Interview Questions

<details>
<summary>🔹 1. What is Microsoft Azure?</summary>
<br>
Microsoft Azure is a cloud computing platform offering a wide range of services including computing, analytics, storage, and networking.
</details>

<details>
<summary>🔹 2. What is the difference between Azure and AWS?</summary>
<br>
Both are cloud providers, but Azure integrates better with Microsoft services like Active Directory and Windows Server. AWS offers broader service availability.
</details>

<details>
<summary>🔹 3. What is an Azure Resource Group?</summary>
<br>
A Resource Group is a container that holds related resources for an Azure solution. It allows for management of those resources as a group.
</details>

<details>
<summary>🔹 4. What is Azure Virtual Machine?</summary>
<br>
Azure VM provides Infrastructure-as-a-Service (IaaS) that allows you to run virtualized Windows or Linux machines in the cloud.
</details>

<details>
<summary>🔹 5. What is Azure DevOps?</summary>
<br>
Azure DevOps is a set of development tools for software development teams including pipelines, boards, repos, test plans, and artifacts.
</details>

<details>
<summary>🔹 6. What is the difference between Azure DevOps and GitHub Actions?</summary>
<br>
Azure DevOps offers a comprehensive suite of services, while GitHub Actions is CI/CD for GitHub repositories, integrated directly into GitHub.
</details>

<details>
<summary>🔹 7. What is Azure Active Directory (AAD)?</summary>
<br>
Azure AD is Microsoft's cloud-based identity and access management service, used for employee sign-in and access control.
</details>

<details>
<summary>🔹 8. What is an Azure Subscription?</summary>
<br>
A subscription is an agreement with Azure to use cloud services. It links to billing and provides access to Azure products.
</details>

<details>
<summary>🔹 9. What are Availability Sets and Availability Zones?</summary>
<br>
Availability Sets protect against hardware failures within a data center. Availability Zones protect against data center-level failures.
</details>

<details>
<summary>🔹 10. What is Azure Blob Storage?</summary>
<br>
Blob Storage is Azure's object storage solution for unstructured data like images, videos, and documents.
</details>

<details>
<summary>🔹 11. What is Azure Kubernetes Service (AKS)?</summary>
<br>
AKS is a managed Kubernetes service that simplifies container orchestration in Azure.
</details>

<details>
<summary>🔹 12. What is the difference between Azure Functions and Logic Apps?</summary>
<br>
Azure Functions are serverless compute services for custom code. Logic Apps are workflow automation tools that use connectors and triggers.
</details>

<details>
<summary>🔹 13. What is the Azure CLI?</summary>
<br>
Azure CLI is a command-line tool used to manage Azure resources directly from the terminal or command prompt.
</details>

<details>
<summary>🔹 14. What is Azure ARM Template?</summary>
<br>
ARM (Azure Resource Manager) Templates are JSON files that define infrastructure and configuration for automated deployments.
</details>

<details>
<summary>🔹 15. What is Azure Policy?</summary>
<br>
Azure Policy helps enforce organizational standards and assess compliance at scale across your Azure environment.
</details>

<details>
<summary>🔹 16. What is Azure Monitor?</summary>
<br>
Azure Monitor collects and analyzes telemetry data from your Azure and on-premises resources for observability and diagnostics.
</details>

<details>
<summary>🔹 17. What is Azure Application Gateway?</summary>
<br>
It is a web traffic load balancer that enables you to manage traffic to your web applications using layer 7 routing.
</details>

<details>
<summary>🔹 18. What is Azure Key Vault?</summary>
<br>
Azure Key Vault is used to securely store secrets, keys, and certificates.
</details>

<details>
<summary>🔹 19. What is the use of Azure Pipelines?</summary>
<br>
Azure Pipelines provides CI/CD automation to build, test, and deploy applications across environments.
</details>

<details>
<summary>🔹 20. What is the Shared Responsibility Model in Azure?</summary>
<br>
Azure is responsible for the cloud infrastructure; users are responsible for securing data, applications, and configurations within it.
</details>

## 🧱 Terraform – DevOps Interview Questions

<details>
<summary>🔹 1. What is Terraform?</summary>
<br>
Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp that allows you to define and provision infrastructure using a declarative configuration language (HCL).
</details>

<details>
<summary>🔹 2. What are the key components of Terraform?</summary>
<br>
- Providers (e.g., AWS, Azure, GCP)  
- Resources  
- Variables  
- Modules  
- State  
- Outputs
</details>

<details>
<summary>🔹 3. What is a Terraform provider?</summary>
<br>
A provider is a plugin that Terraform uses to interact with cloud platforms (e.g., AWS, Azure) and other APIs.
</details>

<details>
<summary>🔹 4. What is a Terraform state file?</summary>
<br>
The state file (`terraform.tfstate`) stores information about the deployed infrastructure and is used to track changes and manage updates.
</details>

<details>
<summary>🔹 5. What is the use of `terraform init`?</summary>
<br>
Initializes the working directory, downloads providers, and sets up the backend.
</details>

<details>
<summary>🔹 6. What does `terraform plan` do?</summary>
<br>
It shows what changes will be made to the infrastructure before applying them, serving as a dry-run.
</details>

<details>
<summary>🔹 7. What is the command to apply a configuration in Terraform?</summary>
<br>
`terraform apply` — it executes the plan and provisions the defined resources.
</details>

<details>
<summary>🔹 8. What is the difference between `terraform apply` and `terraform destroy`?</summary>
<br>
- `apply` provisions infrastructure  
- `destroy` tears down infrastructure defined in your configuration
</details>

<details>
<summary>🔹 9. What are Terraform modules?</summary>
<br>
Modules are reusable Terraform configurations that group related resources together to promote code reusability.
</details>

<details>
<summary>🔹 10. What are the benefits of using Terraform?</summary>
<br>
- Infrastructure as Code  
- Multi-cloud support  
- Version control  
- Modular and reusable code  
- Automation and consistency
</details>

<details>
<summary>🔹 11. How do you manage secrets in Terraform?</summary>
<br>
Avoid storing secrets in code; use tools like AWS Secrets Manager, Vault, or environment variables.
</details>

<details>
<summary>🔹 12. What is Terraform backend?</summary>
<br>
A backend in Terraform determines how state is loaded and how an operation such as `apply` is executed — e.g., local, remote, S3 with DynamoDB locking.
</details>

<details>
<summary>🔹 13. How can you lock Terraform state?</summary>
<br>
By using a remote backend like AWS S3 with DynamoDB for state locking and consistency.
</details>

<details>
<summary>🔹 14. What is the difference between `terraform refresh` and `terraform plan`?</summary>
<br>
- `refresh`: Updates state file with real-world infrastructure  
- `plan`: Shows proposed changes based on the current state
</details>

<details>
<summary>🔹 15. What is a data source in Terraform?</summary>
<br>
Data sources allow you to fetch or compute data from existing resources outside Terraform's management.
</details>

<details>
<summary>🔹 16. How do you use variables in Terraform?</summary>
<br>
Define them in `variables.tf`, pass them via CLI, environment, or `terraform.tfvars` file.
</details>

<details>
<summary>🔹 17. What is output in Terraform?</summary>
<br>
Outputs display the values of resources after `apply`, useful for sharing values like IPs or URLs.
</details>

<details>
<summary>🔹 18. What is the purpose of `.terraform.lock.hcl`?</summary>
<br>
It ensures consistent provider versions across different environments or team members.
</details>

<details>
<summary>🔹 19. Can Terraform be used with CI/CD?</summary>
<br>
Yes, Terraform can be integrated with CI/CD pipelines (e.g., GitHub Actions, Jenkins, GitLab CI) for automated deployments.
</details>

<details>
<summary>🔹 20. What is the difference between Terraform and CloudFormation?</summary>
<br>
Terraform is multi-cloud and open-source. CloudFormation is AWS-specific. Terraform has better modularity and state management flexibility.
</details>

## 🐳 Docker – DevOps Interview Questions

<details>
<summary>🔹 1. What is Docker?</summary>
<br>
Docker is a platform for developing, shipping, and running applications in lightweight containers that include everything needed to run the application.
</details>

<details>
<summary>🔹 2. What is a Docker container?</summary>
<br>
A Docker container is a lightweight, standalone, and executable package of software that includes the application and its dependencies.
</details>

<details>
<summary>🔹 3. What is the difference between a Docker image and a container?</summary>
<br>
An image is a snapshot of a container, while a container is a running instance of an image.
</details>

<details>
<summary>🔹 4. What is Dockerfile?</summary>
<br>
A Dockerfile is a script containing instructions to build a Docker image.
</details>

<details>
<summary>🔹 5. What is the purpose of the `docker-compose` tool?</summary>
<br>
`docker-compose` is used to define and manage multi-container Docker applications using a `docker-compose.yml` file.
</details>

<details>
<summary>🔹 6. What command is used to build a Docker image?</summary>
<br>
`docker build -t image-name .`
</details>

<details>
<summary>🔹 7. How do you run a container from an image?</summary>
<br>
`docker run image-name`  
Or with more options: `docker run -d -p 80:80 --name container-name image-name`
</details>

<details>
<summary>🔹 8. What is the difference between `COPY` and `ADD` in Dockerfile?</summary>
<br>
`COPY` only copies files/directories. `ADD` can also extract tar files and supports URLs.
</details>

<details>
<summary>🔹 9. What is a Docker volume?</summary>
<br>
Volumes are used for persisting data generated and used by Docker containers.
</details>

<details>
<summary>🔹 10. What is the default network driver in Docker?</summary>
<br>
The default driver is `bridge` for standalone containers.
</details>

<details>
<summary>🔹 11. How do you list running containers?</summary>
<br>
`docker ps` – shows running containers.  
`docker ps -a` – shows all containers.
</details>

<details>
<summary>🔹 12. How do you stop a running container?</summary>
<br>
`docker stop container_id_or_name`
</details>

<details>
<summary>🔹 13. How do you remove a container?</summary>
<br>
`docker rm container_id_or_name`
</details>

<details>
<summary>🔹 14. How do you remove an image?</summary>
<br>
`docker rmi image_name`
</details>

<details>
<summary>🔹 15. What is the use of `.dockerignore` file?</summary>
<br>
It works like `.gitignore`, telling Docker which files/folders to ignore when building an image.
</details>

<details>
<summary>🔹 16. What is the difference between `CMD` and `ENTRYPOINT` in Dockerfile?</summary>
<br>
Both define container execution, but `ENTRYPOINT` is preferred for fixed execution commands; `CMD` provides default arguments.
</details>

<details>
<summary>🔹 17. How do you check logs of a container?</summary>
<br>
`docker logs container_name`
</details>

<details>
<summary>🔹 18. What are Docker namespaces?</summary>
<br>
Namespaces isolate containers, allowing them to have their own network, PID, user, mount points, etc.
</details>

<details>
<summary>🔹 19. What is Docker Swarm?</summary>
<br>
Docker Swarm is Docker’s native orchestration tool to manage a cluster of Docker Engines as a single virtual system.
</details>

<details>
<summary>🔹 20. What is the difference between Docker and a Virtual Machine?</summary>
<br>
Containers share the host OS kernel and are lightweight, while VMs include full guest OS and are heavier in resource usage.
</details>


## 🐳 Kubernetes – DevOps Interview Questions

This section contains 20 essential Kubernetes interview questions and answers — designed for DevOps, SRE, and Cloud Engineer interviews in 2025.

---
<details>
<summary>🔹 1. What is Kubernetes?</summary>
<br>
Kubernetes is an open-source container orchestration platform used to automate the deployment, scaling, and management of containerized applications.
</details>

<details>
<summary>🔹 2. What is a Pod in Kubernetes?</summary>
<br>
A Pod is the smallest deployable unit in Kubernetes. It can host one or more containers that share the same network namespace and storage.
</details>

<details>
<summary>🔹 3. What is etcd?</summary>
<br>
etcd is a distributed key-value store used to persist all cluster configuration and state in Kubernetes.
</details>

<details>
<summary>🔹 4. What is the difference between Deployment and StatefulSet?</summary>
<br>
- **Deployment**: Used for stateless apps. Supports rolling updates and replicas.  
- **StatefulSet**: Used for stateful apps. Maintains stable pod identity and persistent storage.
</details>

<details>
<summary>🔹 5. What are Kubernetes Services?</summary>
<br>
A Kubernetes Service is an abstraction that defines a logical set of Pods and a policy by which to access them. Types include ClusterIP, NodePort, and LoadBalancer.
</details>

<details>
<summary>🔹 6. What is kube-apiserver?</summary>
<br>
kube-apiserver is the front-end for the Kubernetes control plane. It validates and configures data for the API objects.
</details>

<details>
<summary>🔹 7. What are taints and tolerations?</summary>
<br>
- **Taints**: Prevent Pods from being scheduled on certain nodes.  
- **Tolerations**: Allow Pods to be scheduled on nodes with matching taints.
</details>

<details>
<summary>🔹 8. What is a Namespace in Kubernetes?</summary>
<br>
Namespaces provide a mechanism for isolating groups of resources within a single cluster.
</details>

<details>
<summary>🔹 9. What is kube-proxy?</summary>
<br>
kube-proxy maintains network rules on nodes and handles communication to Pods across the cluster.
</details>

<details>
<summary>🔹 10. What is ConfigMap vs Secret?</summary>
<br>
- **ConfigMap**: Stores non-sensitive configuration data.  
- **Secret**: Stores sensitive information like passwords and API keys in base64 encoded form.
</details>

<details>
<summary>🔹 11. What is HPA (Horizontal Pod Autoscaler)?</summary>
<br>
HPA automatically scales the number of Pods based on CPU utilization or custom metrics.
</details>

<details>
<summary>🔹 12. What is a DaemonSet?</summary>
<br>
A DaemonSet ensures that a copy of a Pod runs on all (or selected) nodes in the cluster.
</details>

<details>
<summary>🔹 13. What is a Headless Service?</summary>
<br>
A Headless Service is a Service without a ClusterIP. It enables direct access to the Pod's IP addresses.
</details>

<details>
<summary>🔹 14. How does Kubernetes do service discovery?</summary>
<br>
Kubernetes uses DNS and environment variables to enable Pods to discover each other and access Services.
</details>

<details>
<summary>🔹 15. What is a Helm Chart?</summary>
<br>
A Helm Chart is a collection of YAML templates used to define, install, and upgrade complex Kubernetes applications.
</details>

<details>
<summary>🔹 16. What is the difference between a Node and a Cluster?</summary>
<br>
- **Node**: A physical or virtual machine that runs Pods.  
- **Cluster**: A set of nodes managed by the Kubernetes control plane.
</details>

<details>
<summary>🔹 17. What is a ReplicaSet?</summary>
<br>
A ReplicaSet ensures that a specified number of Pod replicas are running at any time.
</details>

<details>
<summary>🔹 18. Types of Services in Kubernetes?</summary>
<br>
- **ClusterIP** (default) – internal-only access  
- **NodePort** – exposes the service on each node's IP at a static port  
- **LoadBalancer** – provisioned with external load balancer  
- **ExternalName** – maps service to a DNS name
</details>

<details>
<summary>🔹 19. How to troubleshoot a Pod in Pending state?</summary>
<br>
- Check node resources using `kubectl describe node`.  
- Check events using `kubectl describe pod <pod-name>`.  
- Ensure correct storage class, tolerations, and affinity rules.
</details>

<details>
<summary>🔹 20. How do you secure a Kubernetes cluster?</summary>
<br>
- Enable RBAC (Role-Based Access Control)  
- Use Network Policies  
- Regularly update cluster components  
- Limit container privileges  
- Use Secrets for sensitive data  
- Enable audit logging and monitoring
</details>

---
# 🛠️ Ansible – DevOps Interview Questions
<details>
<summary>1. What is Ansible?</summary>

Ansible is an open-source automation tool for configuration management, application deployment, and task automation. It uses YAML for playbooks and SSH for agentless communication.

</details>

<details>
<summary>2. How does Ansible work?</summary>

Ansible connects to target nodes over SSH, pushes modules to execute tasks, and removes them after execution, ensuring agentless automation.

</details>

<details>
<summary>3. What is an Ansible Playbook?</summary>

Playbooks are YAML files that define a set of tasks to be executed on managed hosts. They are reusable and used for multi-step automation.

</details>

<details>
<summary>4. What are Ansible modules?</summary>

Modules are reusable scripts used to perform specific tasks like installing packages, copying files, restarting services, etc.

</details>

<details>
<summary>5. What is an inventory file in Ansible?</summary>

It lists the hosts or groups of hosts on which Ansible performs tasks. It can be static (INI/YAML) or dynamic (scripts or plugins).

</details>

<details>
<summary>6. What are roles in Ansible?</summary>

Roles help in structuring playbooks by organizing tasks, variables, handlers, and templates into reusable directories.

</details>

<details>
<summary>7. Difference between ad-hoc commands and playbooks?</summary>

- **Ad-hoc commands** are one-liners for quick tasks.
- **Playbooks** are YAML-based scripts used for long-term automation.

</details>

<details>
<summary>8. What is the use of Ansible Galaxy?</summary>

Ansible Galaxy is a repository for finding, sharing, and reusing Ansible roles created by the community.

</details>

<details>
<summary>9. What are facts in Ansible?</summary>

Facts are system properties (e.g., IP, OS) gathered using the `setup` module and can be used in playbooks as variables.

</details>

<details>
<summary>10. What is Ansible Vault?</summary>

Ansible Vault is used to encrypt secrets like passwords or keys.  
</details>

# 🐳 Docker Interview Questions and Answers

<details>
<summary><strong>1. What is Docker?</strong></summary>

Docker is an open-source platform that allows developers to automate the deployment of applications inside lightweight, portable containers. It packages code along with its dependencies and environment for consistency across environments.

</details>

<details>
<summary><strong>2. What is the difference between a Docker image and a Docker container?</strong></summary>

- A **Docker image** is a read-only template with instructions for creating a container.
- A **Docker container** is a runnable instance of an image that includes the application and its dependencies.

</details>

<details>
<summary><strong>3. What is a Dockerfile?</strong></summary>

A Dockerfile is a text file containing instructions used by Docker to automate the building of an image. It specifies the base image, commands to install packages, copy files, and define startup behavior.

</details>

<details>
<summary><strong>4. What is Docker Compose?</strong></summary>

Docker Compose is a tool that allows you to define and manage multi-container Docker applications using a `docker-compose.yml` file. It simplifies the process of setting up services, networks, and volumes.

</details>

<details>
<summary><strong>5. What is Docker Hub?</strong></summary>

Docker Hub is Docker’s public registry where users can share, distribute, and pull container images. It offers official images and supports public and private repositories.

</details>

<details>
<summary><strong>6. How does Docker architecture work?</strong></summary>

Docker uses a client-server architecture:
- The **Docker Client** sends commands to the **Docker Daemon**, which builds, runs, and manages containers.
- Docker uses **Images**, stored in **Registries**, to create **Containers**.

</details>

<details>
<summary><strong>7. How to persist data in Docker?</strong></summary>

To persist data in Docker, you can use:
- **Volumes** (managed by Docker)
- **Bind mounts** (host directory mounted inside container)

These methods ensure data is not lost when the container stops.

</details>

<details>
<summary><strong>8. What are Docker volumes?</strong></summary>

Docker volumes are directories managed by Docker and stored on the host machine to persist and share data between containers.

</details>

<details>
<summary><strong>9. What is the difference between bind mounts and volumes?</strong></summary>

- **Bind Mount**: You specify the exact path on the host.
- **Volume**: Managed by Docker in `/var/lib/docker/volumes/`.

Volumes are preferred for better management and portability.

</details>

<details>
<summary><strong>10. How do you expose ports in Docker?</strong></summary>

Use the `-p` or `--publish` flag:
</details>
---

# 🚀 CI/CD Interview Questions & Answers

This document contains **20 commonly asked CI/CD interview questions and answers** designed for Cloud & DevOps Engineers. Ideal for anyone preparing for DevOps roles.

---

<details>
<summary><strong>1. What is CI/CD?</strong></summary>

CI/CD stands for **Continuous Integration** and **Continuous Deployment/Delivery**. CI focuses on automating code integration, while CD automates the release process. Together, they ensure faster and safer software delivery.
</details>

---

<details>
<summary><strong>2. What are the benefits of CI/CD?</strong></summary>

- Faster release cycles  
- Reduced manual effort  
- Higher code quality  
- Easier debugging  
- Immediate feedback loops  
</details>

---

<details>
<summary><strong>3. What tools are commonly used in CI/CD pipelines?</strong></summary>

Popular tools include:
- **Jenkins**
- **GitHub Actions**
- **GitLab CI/CD**
- **CircleCI**
- **Travis CI**
- **AWS CodePipeline**
</details>

---

<details>
<summary><strong>4. What is a pipeline in CI/CD?</strong></summary>

A pipeline is a set of automated steps for building, testing, and deploying applications.
</details>

---

<details>
<summary><strong>5. What is the difference between Continuous Delivery and Continuous Deployment?</strong></summary>

- **Continuous Delivery**: Code is deployed to staging or production only after manual approval.  
- **Continuous Deployment**: Every change passes all stages and is automatically deployed to production.
</details>

---

<details>
<summary><strong>6. What is a build?</strong></summary>

A build is the process of converting source code into an executable format.
</details>

---

<details>
<summary><strong>7. What is artifact in CI/CD?</strong></summary>

An artifact is a compiled binary or package (e.g., `.jar`, `.zip`, `.deb`) generated during a build process.
</details>

---

<details>
<summary><strong>8. What is version control, and how does it relate to CI?</strong></summary>

Version control (like Git) manages code changes. CI relies on it to trigger pipelines upon code commits.
</details>

---

<details>
<summary><strong>9. How do you trigger a CI/CD pipeline?</strong></summary>

Pipelines are triggered by:
- Code commits or pull requests  
- Scheduled jobs  
- Manual triggers  
- Webhooks
</details>

---

<details>
<summary><strong>10. What is a webhook in CI/CD?</strong></summary>

A webhook notifies the CI/CD system of an event, like a Git push, to trigger automated processes.
</details>

---

<details>
<summary><strong>11. What is a self-hosted runner?</strong></summary>

A self-hosted runner is a machine you configure to run your pipeline jobs (as opposed to cloud-hosted runners).
</details>

---

<details>
<summary><strong>12. What are stages and jobs in a pipeline?</strong></summary>

- **Stages** are logical groups of tasks (e.g., Build, Test, Deploy).  
- **Jobs** are tasks within those stages.
</details>

---

<details>
<summary><strong>13. What is the role of Docker in CI/CD?</strong></summary>

Docker provides consistent environments for builds and deployments. It enables container-based CI/CD.
</details>

---

<details>
<summary><strong>14. What is Canary Deployment?</strong></summary>

Canary deployment releases an update to a small portion of users to verify before full rollout.
</details>

---

<details>
<summary><strong>15. What is Blue-Green Deployment?</strong></summary>

It involves two environments (Blue & Green). One is live, and the other is prepared with updates. Switching happens after testing.
</details>

---

<details>
<summary><strong>16. What is rollback in deployment?</strong></summary>

Rollback is reverting to the previous stable version after a failed deployment.
</details>

---

<details>
<summary><strong>17. How can you ensure pipeline security?</strong></summary>

- Secure secrets (use vaults)  
- Scan for vulnerabilities  
- Implement role-based access  
- Avoid hardcoding credentials
</details>

---

<details>
<summary><strong>18. What is Infrastructure as Code in CI/CD?</strong></summary>

IaC tools like Terraform or CloudFormation automate infra setup as part of CI/CD workflows.
</details>

---

<details>
<summary><strong>19. How to monitor CI/CD pipelines?</strong></summary>

Use built-in dashboards (Jenkins, GitHub Actions), logs, and integrations with monitoring tools like Prometheus, Grafana.
</details>

---

<details>
<summary><strong>20. What is the difference between CI and DevOps?</strong></summary>

CI is a practice within DevOps focused on integration. DevOps is a broader culture promoting collaboration, automation, and monitoring.
</details>

---

# 📈 DevOps Methodology, Practices & Agile – Interview Questions
## 📘 Interview Questions & Answers

<details>
<summary>🔹 1. What is DevOps?</summary>
DevOps is a cultural and technical movement that aims to unify software development (Dev) and IT operations (Ops). It emphasizes collaboration, automation, continuous integration & delivery (CI/CD), and monitoring to deliver software faster and more reliably.
</details>

<details>
<summary>🔹 2. What are the core principles of DevOps?</summary>
- Culture of collaboration  
- Automation  
- Continuous feedback  
- Shared responsibility  
- Iterative improvement  
- Monitoring and observability
</details>

<details>
<summary>🔹 3. How does DevOps differ from Agile?</summary>
Agile focuses on software development practices (sprints, scrum, iterations). DevOps expands on Agile by including operations — emphasizing deployment, automation, and system reliability post-development.
</details>

<details>
<summary>🔹 4. What are the stages in a DevOps lifecycle?</summary>
- Plan  
- Develop  
- Build  
- Test  
- Release  
- Deploy  
- Operate  
- Monitor
</details>

<details>
<summary>🔹 5. What is CI/CD?</summary>
CI/CD stands for Continuous Integration and Continuous Delivery/Deployment. It involves automatically building, testing, and deploying code changes, ensuring faster and reliable software delivery.
</details>

<details>
<summary>🔹 6. What is Shift Left Testing?</summary>
Shift Left Testing refers to testing earlier in the software development lifecycle, enabling faster bug detection, reducing cost, and improving quality.
</details>

<details>
<summary>🔹 7. What is Infrastructure as Code (IaC)?</summary>
IaC is the practice of managing and provisioning infrastructure using code (e.g., Terraform, CloudFormation). It helps automate deployments and ensures consistent environments.
</details>

<details>
<summary>🔹 8. What are some popular DevOps tools?</summary>
- Version Control: Git  
- CI/CD: Jenkins, GitHub Actions, GitLab CI  
- Configuration Management: Ansible, Chef  
- Containerization: Docker, Kubernetes  
- Monitoring: Prometheus, Grafana  
- IaC: Terraform, Pulumi
</details>

<details>
<summary>🔹 9. What is the role of a DevOps Engineer?</summary>
A DevOps Engineer builds and maintains CI/CD pipelines, manages infrastructure automation, ensures system reliability, integrates monitoring, and fosters collaboration between teams.
</details>

<details>
<summary>🔹 10. What is a feedback loop in DevOps?</summary>
A feedback loop provides real-time insights between development, testing, and operations, helping teams rapidly detect and correct issues throughout the delivery lifecycle.
</details>

<details>
<summary>🔹 11. What are Agile ceremonies?</summary>
- Daily stand-ups  
- Sprint planning  
- Sprint review  
- Retrospective  
These promote transparency, collaboration, and iterative delivery.
</details>

<details>
<summary>🔹 12. What is the difference between Continuous Delivery and Continuous Deployment?</summary>
- **Continuous Delivery**: Ensures every code change is deployable; manual approval may be needed.  
- **Continuous Deployment**: Automatically deploys every change after passing tests, no manual step.
</details>

<details>
<summary>🔹 13. What are Microservices in DevOps?</summary>
Microservices are small, loosely coupled services that work independently and are deployed separately. DevOps pipelines often manage and scale them efficiently.
</details>

<details>
<summary>🔹 14. What is Mean Time to Recovery (MTTR)?</summary>
MTTR measures how quickly a system can recover from a failure. Lower MTTR indicates better resilience.
</details>

<details>
<summary>🔹 15. What is Trunk-Based Development?</summary>
It is a source control strategy where all developers commit to a single branch (trunk), enabling faster integration and fewer merge conflicts.
</details>

<details>
<summary>🔹 16. What are some DevOps anti-patterns?</summary>
- Treating DevOps as a team, not a culture  
- Siloed Dev and Ops roles  
- Lack of automation  
- Manual deployments  
- Ignoring security (no DevSecOps)
</details>

<details>
<summary>🔹 17. What is a value stream in DevOps?</summary>
A value stream is the series of steps an organization uses to deliver value to the customer, from idea to production.
</details>

<details>
<summary>🔹 18. What is DevSecOps?</summary>
DevSecOps integrates security into the DevOps process, ensuring secure code practices, scanning, and policy enforcement throughout the pipeline.
</details>

<details>
<summary>🔹 19. What metrics are used to measure DevOps success?</summary>
- Deployment Frequency  
- Lead Time for Changes  
- Change Failure Rate  
- Mean Time to Recovery (MTTR)  
- Customer satisfaction (CSAT)
</details>

<details>
<summary>🔹 20. What is the CALMS model in DevOps?</summary>
**CALMS** stands for:
- **Culture**
- **Automation**
- **Lean**
- **Measurement**
- **Sharing**  
It’s a framework for evaluating DevOps maturity and adoption.
</details>

---
📂 Add this to your DevOps Interview Guide or CI/CD Project Repo.


> 📘 _Keep building your cloud confidence — one concept at a time!_






