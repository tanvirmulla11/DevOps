# 📌 Task Description

## The production support team of xFusionCorp Industries is developing automation scripts for daily tasks.
## One of the requirements is to create a bash script to take backups of a static website hosted on App Server 2.

### The script must:

### Create a zip archive of /var/www/html/media.

### Save the archive in /backup/ (temporary storage).

### Copy the archive to the Nautilus Backup Server in /backup/.

### Ensure no password prompt during backup copy (passwordless SSH).

### Be located under /scripts/ and be executable.

# ✅ Steps to Implement
## 1. Connect to App Server 
```bash
ssh steve@stapp02
```
## 2. Create the /scripts directory
```bash
 sudo mkdir -p /scripts
```
## 3. Install zip package
```bash
sudo yum install -y zip     # For RHEL/CentOS
# OR
sudo apt-get install -y zip # For Ubuntu/Debian
```
## 4. Create the backup script
```bash
sudo vi /scripts/media_backup.sh
```
## Paste the following content:
```bash
#!/bin/bash

# Variables
SOURCE_DIR="/var/www/html/media"
BACKUP_DIR="/backup"
ARCHIVE_NAME="xfusioncorp_media.zip"
NAUT_BACKUP_USER="clint"        # Nautilus Backup Server username
NAUT_BACKUP_HOST="stbkp01"      # Nautilus Backup Server hostname
NAUT_BACKUP_DIR="/backup"

# Ensure zip is installed
if ! command -v zip &> /dev/null
then
    echo "zip not installed. Installing..."
    sudo yum install -y zip || sudo apt-get install -y zip
fi

# Create backup directory if not exists
mkdir -p $BACKUP_DIR

# Create zip archive
zip -r $BACKUP_DIR/$ARCHIVE_NAME $SOURCE_DIR

# Copy archive to Nautilus Backup Server
scp $BACKUP_DIR/$ARCHIVE_NAME ${NAUT_BACKUP_USER}@${NAUT_BACKUP_HOST}:${NAUT_BACKUP_DIR}/
```
## Save & exit (:wq).
## 5. Make script executable
```bash
sudo chmod +x /scripts/media_backup.sh
```
## 6. Setup passwordless SSH to Backup Server
```bash
ssh-keygen -t rsa
ssh-copy-id clint@stbkp01
```
## 7. Run the script
```bash
/scripts/media_backup.sh
```
## This will:

### Zip media/ into /backup/xfusioncorp_media.zip

### Copy the archive to Backup Server → /backup/

## 8. Verify Backup
### On Nautilus Backup Server:
```bash
ls -lh /backup/
```
### You should see:
```bash
xfusioncorp_media.zip
```
# 📌 Notes

### Place script only in /scripts/ directory.

### Ensure passwordless SSH is configured.

### /backup/ is temporary storage (cleaned weekly).

# Images
<img width="1919" height="961" alt="Screenshot 2025-08-25 125420" src="https://github.com/user-attachments/assets/9dceebf3-7a8f-4de5-962e-b1f7fc0b8d5b" />
<img width="1919" height="963" alt="Screenshot 2025-08-25 125501" src="https://github.com/user-attachments/assets/de3ca1f9-578f-4f58-93f9-e3a5b346f32f" />

# ✅ Successfully automated media backup with passwordless transfer!







