# 🚀 DevOps Project Tasks – Kubernetes, GitHub Actions & Jira Integration

This document provides a detailed, structured approach to managing and deploying the **Wanderlust Web Application** using **Docker, Kubernetes, GitHub Actions, and Jira**.  
It is suitable for **college projects, DevOps practice, and professional documentation**.

---

## ✅ Task 1: Review Existing Code and Dockerfile

### 🎯 Objective
Ensure that the application source code and Dockerfile are properly configured for deployment.

### 📝 Steps Performed
1. Reviewed the existing source code in the GitHub repository to:
   - Validate project structure
   - Check dependencies and configuration files
   - Ensure no environment-specific values are hardcoded

2. Verified the `Dockerfile` to ensure:
   - Correct base image is used
   - Build and runtime steps are properly defined
   - Required ports are exposed
   - The image builds successfully without errors

3. Confirmed that the Docker image can be built and run correctly.

### 📌 Status
- ✅ Task completed  
- 🔄 Moved to **REVIEW**

---

## ✅ Task 2: Validate Kubernetes YAML Files

### 🎯 Objective
Validate Kubernetes configuration files to ensure correct deployment behavior.

### 📝 Steps Performed
1. Reviewed `deployment.yaml` to verify:
   - Correct API version and resource kind
   - Container image name and tag
   - Replica count
   - Port configuration
   - Environment variables
   - Resource requests and limits

2. Reviewed `service.yaml` to verify:
   - Service type (ClusterIP / NodePort / LoadBalancer)
   - Port and targetPort configuration
   - Selector labels matching the deployment

3. Ensured the configurations align with the expected Kubernetes deployment environment.

### 📌 Status
- ✅ Task completed  
- 🔄 Moved to **REVIEW**

---

## ✅ Task 3: Set Up GitHub Actions Workflow

### 🎯 Objective
Automate build and deployment using GitHub Actions.

### 📝 Steps Performed
1. Checked for an existing workflow file in:
## .github/workflows/
2. Verified the existing workflow configuration.
3. Created a new workflow file (`deploy.yaml`) if none was present.
4. Ensured the workflow includes:
- Code checkout
- Build steps
- Deployment steps (Docker / Kubernetes)

### 📄 Example Workflow (`.github/workflows/deploy.yaml`)
```yaml
name: Deploy Application

on:
push:
 branches:
   - main

jobs:
deploy:
 runs-on: ubuntu-latest

 steps:
   - name: Checkout code
     uses: actions/checkout@v3

   - name: Build Application
     run: echo "Build step here"

   - name: Deploy to Kubernetes
     run: echo "Deploy step here"
```
## 📌 Status

✅ Workflow verified / created

🔄 Moved to REVIEW

## ✅ Task 4: Install GitHub for Jira App
## 🎯 Objective

Enable GitHub–Jira integration for issue tracking and development visibility.

## 📝 Steps Performed

Navigated to Jira Settings.

Selected Apps → Find new apps.

Searched for GitHub for Jira.

Clicked Get it now.

Followed the prompts to complete installation.

## 📌 Status

✅ App installed successfully

🔄 Moved to REVIEW

## ✅ Task 5: Connect Jira to GitHub Repository
## 🎯 Objective

Link Jira with the GitHub repository to track commits, pull requests, and deployments.

## 📝 Steps Performed

Navigated to Apps → Manage your apps in Jira.

Located GitHub for Jira and clicked Configure.

Linked the GitHub account.

Selected the GitHub repository for the Wanderlust Web App.

Verified the connection between Jira and GitHub.

## 📌 Status

✅ Jira connected to GitHub repository

## 🔁 Project Management Practices

Daily Standups

Regular updates on task progress and blockers.

Review Sessions

Review all tasks moved to the REVIEW column.

Retrospectives

Conducted after project completion to analyze:

What went well

What can be improved

## ✅ Conclusion

By following this structured approach, the project ensures:

Clean and deployable codebase

Valid Kubernetes configurations

Automated CI/CD using GitHub Actions

Seamless GitHub–Jira integration

Effective project tracking and review process
