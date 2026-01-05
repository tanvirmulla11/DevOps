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
