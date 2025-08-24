# 🚀 Day 07 – SSH Key-Based Authentication  

This session demonstrates how to configure **SSH key-based authentication** across multiple servers.  
SSH keys improve security by removing the need for password-based logins and allowing seamless automation.  

---

## 🔑 Steps Performed  

### 1. Generate RSA Key Pair  
```bash
ssh-keygen -t rsa
```
### This creates a public/private RSA key pair inside the ~/.ssh/ directory (id_rsa and id_rsa.pub).
### 2. Configure Key-Based Authentication on Target Servers
### 🔹 stapp01 Server (User: tony)
```bash
ssh-copy-id tony@stapp01
ssh tony@stapp01
exit

```
### 🔹 stapp02 Server (User: steve)
```bash
ssh steve@stapp02
ssh-copy-id steve@stapp02
ssh steve@stapp02
exit
```
### 🔹 stapp03 Server (User: banner)
```bash
ssh-copy-id banner@stapp03
ssh banner@stapp03
exit
```
### 3. Verify Authorized Keys
### On each server:
```bash
cd ~/.ssh/
ls -l
cat authorized_keys
```
### ✅ The copied public keys should be listed inside authorized_keys.
# 📌 Notes

### -This example uses sample usernames (tony, steve, banner) and hostnames (stapp01, stapp02, stapp03).

### -In real-world scenarios, the actual usernames and servers may differ, but the procedure remains the same.

### -Always secure your private key (id_rsa) with proper permissions:
```bash
 chmod 600 ~/.ssh/id_rsa
```

# 🎯 Outcome

### Password-less login enabled across all configured servers.

### Improved security and efficiency for automation and DevOps workflows.

# 🛠️ Use Cases

### -Automated deployments

### -Secure CI/CD pipelines

### -Infrastructure as Code (IaC) workflows
