# 📘 Day 02 – KodeKloud Practice
# 🎯 Task

### Create a temporary user named john on App Server 1 in Stratos Datacenter.

### The account must expire on 2024-01-28.

### Ensure the username is in lowercase as per standard protocol.
# 🛠️ Steps Performed
### 1. Connect to the App Server
```bash
ssh tony@stapp01
```
### 2. Create the User with Expiry Date
```bash
sudo useradd -e 2024-01-28 john
```
### 3. Verify User Account Details
```bash
sudo chage -l john
```
### ✅ Output confirms:

Last password change: Aug 17, 2025

Account expires: Jan 28, 2024

### 4. (Additional Checks from Lab)

Checked expiry for existing user:
```bash
sudo chage -l devopswithus
```
Modified expiry date for existing user:
```bash
sudo usermod -e 2024-01-28 devopswithus
sudo chage -E 2024-01-28 john
```
### ✅ Result

User john was successfully created with an expiry date of 2024-01-28.

Task completed and validated in KodeKloud Lab.


