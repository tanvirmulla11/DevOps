# Day 05 - SELinux Configuration on CentOS Stream 9

## 📌 Task  
Check SELinux status on `stapp01`, install SELinux policies if required, and configure SELinux.

---

## 🛠️ Steps Performed  
### Step 1: SSH into stapp01
```bash
ssh tony@stapp01
```
### Step 2: Check OS details
```bash
cat /etc/os-release
# Output: CentOS Stream 9
```

### Step 3: Check current SELinux status
```bash
sestatus
```
### Output:
### SELinux status: disabled

### Step 3.1: Install SELinux package (if not installed)
```bash
sudo yum install selinux -y
```

### Step 4: Install SELinux policies
```bash
sudo yum install selinux-policy selinux-policy-targeted -y
```

### Step 5: Edit SELinux config file
```bash
sudo vi /etc/selinux/config
```

### Inside the file, update the line:
### SELINUX=disabled   →   SELINUX=permissive (or enforcing)

### Step 6: Verify SELinux status again
```bash
sestatus
```
### Output still shows:
### SELinux status: disabled
### (Reboot required to apply the new policy)

### ✅ Result

### -Installed SELinux package and required policies (selinux-policy, selinux-policy-targeted).

### -Updated /etc/selinux/config to change mode from disabled → permissive (or enforcing).

### -Current session still shows disabled (reboot required to activate changes).

# 📌 Notes

After reboot, SELinux will start in the configured mode (permissive/enforcing).

permissive mode is recommended initially to avoid accidental service blockage.

Use getenforce to quickly check current mode.

# 🌟 Motivation

### "Small progress each day adds up to big results."
### "Don’t watch the clock; do what it does. Keep going."
