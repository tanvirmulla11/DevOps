# 🚀 Day 06: Cron Job Setup in Linux

## 📌 Task  
Today’s task was about **scheduling jobs in Linux using Cron**.  
Cron is a time-based job scheduler in Unix-like operating systems that allows us to automate tasks at specific intervals.

---

## 🛠️ Steps Performed  

```bash
# 1️⃣ Connect to the target server
ssh tony@stapp01

# 2️⃣ Verify the OS details
sudo cat /etc/os-release

# 3️⃣ Install cron service (if not already installed)
sudo yum install cronie -y

# 4️⃣ Check cron service status
sudo systemctl status crond

# 5️⃣ Start cron service
sudo systemctl start crond

# 6️⃣ Verify service is running
sudo systemctl status crond

# 7️⃣ Edit crontab file to add a new scheduled job
sudo crontab -e

```
### Inside the crontab editor, I added the following line to run a command every 5 minutes:
```bash
*/5 * * * * echo hello > /tmp/cron_text
```
### 👉 This means: Every 5 minutes, the word "hello" will be written to /tmp/cron_text.

# 🔎 Verification
```bash
# 8️⃣ Navigate to /tmp directory
cd /tmp

# 9️⃣ List files
ls -l

# 🔟 Check the output file
cat cron_text
```
# ✅ Output:
```bash
hello
```
# 📖 Key Learnings
Cron jobs are powerful for automation and scheduling repetitive tasks.
With just a few lines, you can automate logs, backups, monitoring scripts, or notifications.
Always verify the cron service is running before adding jobs.

# 🌟 Motivation
### “Automation is to DevOps what oxygen is to humans – essential and life-sustaining.”
### “Don’t stop until you’re proud.”
