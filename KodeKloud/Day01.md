# 🚀 100 Days of DevOps – Day 1  

## 📌 Linux User Setup with Non-Interactive Shell  

I’ve officially started my **100 Days of DevOps Challenge** with [KodeKloud](https://kodekloud.com)! 🎉  
Today’s task was about creating a **Linux user with a non-interactive shell** on **App Server 1**.  

---

### 🛠️ Steps  

```bash
# 1. Connect to App Server
ssh tony@stapp01  

# 2. Switch to root
sudo su -  

# 3. Create user 'john' with /sbin/nologin shell
sudo useradd john --shell /sbin/nologin  

# 4. Verify user entry in /etc/passwd
cat /etc/passwd | grep john
```
### Output:

```bash
john:x:1002:1002::/home/john:/sbin/nologin
```
### 📸 Screenshot
### 📝 Note: The screenshot shows my KodeKloud lab run.
In real challenges, the task name or server might differ, but the steps remain the same.

<img width="1919" height="1029" alt="Screenshot 2025-08-17 093720" src="https://github.com/user-attachments/assets/f50032a3-cf76-4783-a0d3-8212b4b09af2" />

# ✨ Motivation

“Small progress each day adds up to big results.”

Day 1 ✅ | 99 more to go 🚀

# 🔖 Tags

#100DaysOfDevOps #Linux #KodeKloud #DevOps #Security #LearningByDoing


