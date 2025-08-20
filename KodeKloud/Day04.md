# Day 04 - File Permission Fix and Script Execution
# 🎯 Task

A script tmp/xfusioncorp.sh exists on stapp01, but it did not have the proper execution permission.
We had to fix the file permission and run the script successfully.
# 🛠️ Steps Performed
```bash
# Step 1: SSH into stapp01 as tony
ssh tony@stapp01

# Step 2: Verify file permission (no read/execute for user)
ls -l /tmp/xfusioncorp.sh
# Output:
# ---------- 1 root root 40 Aug 17 05:26 /tmp/xfusioncorp.sh

# Step 3: Add execute permission for the script
sudo chmod +x /tmp/xfusioncorp.sh

# Step 4: Confirm new permissions
ls -l /tmp/xfusioncorp.sh
# Output:
# -r-xr-xr-x 1 root root 40 Aug 17 05:26 /tmp/xfusioncorp.sh

# Step 5: Execute the script
bash /tmp/xfusioncorp.sh
# Output:
# Welcome To KodeKloud

```
# ✅ Result

Script permissions were fixed.

Script executed successfully and displayed the message.

# images 
<img width="1919" height="970" alt="Screenshot 2025-08-17 110033" src="https://github.com/user-attachments/assets/d30eab03-6922-4793-b7c8-676e8d92f105" />
<img width="1919" height="966" alt="Screenshot 2025-08-17 110229" src="https://github.com/user-attachments/assets/254ec20f-624a-4f37-aad0-d62b4684d036" />



# 📌 Author: Tanvir Mulla
