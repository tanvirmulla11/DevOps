Introduction to Shell Scripting
What is Shell Scripting?
Shell scripting is writing a series of commands in a text file to automate tasks in a Linux/Unix shell (like bash). Think of it like writing a recipe: Instead of typing commands one-by-one, you save them in a .sh file, and run them all together.

Example: Basic Hello World and Date Script
This is a simple script to print a greeting and the current date.

#!/bin/bash

echo "Hello, Connections!"
date

How to Run it:

Save the code in a file, for example, hello.sh.

Make it executable: chmod +x hello.sh

Run the script: ./hello.sh

Who invented Shell Scripting?
Shell scripting wasn't "invented" by one person like a tool; it evolved with Unix.

Here's the key timeline:

Ken Thompson (1971): Created the first Unix shell called sh.

Stephen Bourne (1979): Wrote the improved Bourne Shell (sh), which made scripting widely possible. He is mostly credited for popularizing shell scripting.

Later came other popular shells like bash (Bourne Again SHell), zsh, ksh, etc.

Why is Shell Scripting important for DevOps?
Shell scripting is super important in DevOps because it helps automate tasks, which is central to DevOps principles.

Here's why it matters:

Automation: Run builds, deployments, tests, cleanups all with one script.

CI/CD Pipelines: Shell scripts are often used in tools like Jenkins, GitHub Actions, GitLab CI to automate pipelines.

Server Management: Start/stop services, backup logs, check disk space easily.

Configuration Management: Automate server setup and software installation with tools like Ansible (which often leverages shell scripts).

Monitoring & Alerting: Write scripts to monitor system health and trigger alerts for issues.

Custom Tools: Create custom scripts for specific project needs, acting as glue code between different tools.

Efficiency: Reduces manual errors and speeds up repetitive tasks.

Portability: Shell scripts are highly portable across different Linux/Unix environments.

Essential Linux Commands & Shell Scripting Concepts
Here are key commands and concepts demonstrated with code examples:

1. Basic File & Directory Commands
These commands help you navigate and manage files and folders.

touch <Filename>: Used to create a new empty file.

# Example: Create a file named my_file.txt
touch my_file.txt

ls: Lists files and directories in the current location.

ls -l: Shows detailed information (permissions, ownership, size, date).

ls -r: Lists files in reverse alphabetical order.

ls -t: Sorts by modification time (newest first).

ls -h: Shows file sizes in human-readable format (e.g., KB, MB).

ls -x: Sorts by file extension.

ls -a: Shows all files, including hidden ones (starting with .).

ls -R <folder_name>: Recursively lists contents of a directory and its subdirectories.

# Example: List files in long format
ls -l

# Example: Show hidden files
ls -a

# Example: Recursively list contents of a folder named 'my_folder'
ls -R my_folder

clear: Clears the terminal screen.

clear

mkdir <dirname>: Creates a new directory (folder).

mkdir -p <dir1/dir2/dir3>: Creates nested directories.

# Example: Create a directory named 'my_directory'
mkdir my_directory

# Example: Create nested directories
mkdir -p project/src/data

cd <directory-name>: Changes the current directory.

cd ..: Moves to the parent directory.

cd ../..: Moves up two directories.

cd ~: Changes to the home directory.

cd -: Changes to the previous working directory.

# Example: Change to 'my_directory'
cd my_directory

# Example: Go up one level
cd ..

# Example: Go to home directory
cd ~

2. File Content Manipulation
Commands to view, write, and modify file contents.

cat <Filename>: Displays the content of a file.

# Assuming 'my_file.txt' exists with content
cat my_file.txt

cat > <Filename>: Creates a new file or overwrites an existing one. Use Ctrl + D to save and exit.

# Create or overwrite my_new_file.txt
cat > my_new_file.txt
# Type your content here...
# Press Ctrl+D when done

cat >> <Filename>: Appends data to an existing file without overwriting.

# Append to my_new_file.txt
cat >> my_new_file.txt
# Type additional content here...
# Press Ctrl+D when done

head -n <lines> <filename>: Displays the first 'n' lines of a file.

# Display the first 5 lines of my_file.txt
head -n 5 my_file.txt

tail -n <lines> <filename>: Displays the last 'n' lines of a file.

# Display the last 10 lines of my_file.txt
tail -n 10 my_file.txt

sed (Stream Editor): Powerful for text transformations.

sed -n 'Np' <filename>: Prints the Nth line.

sed -n 'N,Mp' <filename>: Prints a range of lines (N to M).

sed 'Nd' <filename>: Deletes the Nth line.

sed -i 'Nd' <filename>: Deletes the Nth line permanently (-i for in-place edit).

sed -i 'N,Md' <filename>: Deletes a range of lines permanently.

sed 's/old_string/new_string/g' <filename>: Replaces all occurrences of old_string with new_string globally (g).

sed 'N s/old_string/new_string/' <filename>: Replaces old_string with new_string only on the Nth line.

# Example: Print the 3rd line of data.txt
sed -n '3p' data.txt

# Example: Replace "old" with "new" globally in file.txt
sed 's/old/new/g' file.txt

cut: Extracts sections from each line of files.

cut -c N-M <filename>: Extracts characters from position N to M.

cut -d 'delimiter' -f <field_number> <filename>: Extracts specific fields using a delimiter.

# Example: Extract characters from 1 to 5 from a file
cut -c 1-5 data.csv

# Example: Extract the second field (column) using comma as delimiter
cut -d ',' -f 2 data.csv

awk: Powerful for text processing, especially tabular data.

awk '{print $N}' <filename>: Prints the Nth column.

awk 'NR==N {print $M}' <filename>: Prints the Mth column of the Nth row.

awk '/string/' <filename>: Prints lines containing the specified string.

awk '{print length($N)}' <filename>: Prints the length of the Nth column.

# Example: Print the first and third columns of data.log
awk '{print $1, $3}' data.log

# Example: Find lines containing "error"
awk '/error/' application.log

3. System Information & Networking
Commands to check system details and network connectivity.

uname: Shows the operating system name (e.g., Linux).

whoami: Shows the current logged-in username.

which <command>: Shows the binary path of a command (e.g., which ls).

ifconfig: Shows the IP address of a Linux server.

ipconfig: Shows the IP address of a Windows server.

hostname: Shows the hostname (works on both Linux and Windows).

# Get current username
whoami

# Check IP address (Linux)
ifconfig

ping <IPAddress> <Portno>: Checks network connectivity to a host and port. (Port 22 for Linux, 445 for Windows). Use Ctrl + C to stop.

# Ping a server (example IP)
ping 8.8.8.8

cat /etc/os-release: Checks the Kernel version and OS distribution details.

cat /etc/os-release

cat /var/log/syslog: Checks system log files. (Note: The PDF has /var/sys/log which is likely a typo. Correct path is usually /var/log/syslog or similar, depending on Linux distribution).

cat /var/log/syslog

4. Process Management
Commands to view and manage running processes.

top: Displays real-time dynamic view of a system, including running, stopped, zombie, sleeping, and terminated processes. Provides CPU and memory utilization.

Paging (sw): Occurs when the system has high memory utilization, using backup (swap) memory to free up physical memory.

Zombie Process: A process that has terminated but still has an entry in the process table (information is available on the system).

Process State Codes: R (Running/Runnable), D (Uninterruptible Sleep - dangerous state), S (Interruptible Sleep/Sleeping), T (Stopped/Terminated).

# Launch the top command to monitor processes
top
# Press 'q' to quit

ps (Process Stats): Shows a snapshot of current processes in the terminal.

ps -ef: Shows all running processes for all terminals, including kernel processes (indicated by ?).

# Show current processes
ps

# Show all processes with full format
ps -ef

5. User & Permission Management
Commands for controlling file and directory access.

chmod <permissions> <filename>: Changes access permissions of files and directories.

Numeric Notation: Read (4), Write (2), Execute (1).

chmod 777 filename: Grants read, write, execute to User, Group, and Others.

777 = (4+2+1)(4+2+1)(4+2+1)

u=user, g=group, o=others, a=all

+ adds permission, - removes, = sets exactly.

# Example: Give read, write, execute permissions to everyone for script.sh
chmod 777 script.sh

# Example: Add write permission for the user
chmod u+w my_file.txt

# Example: Remove execute permission from the group
chmod g-x my_script.sh

sudo <command>: Allows users to run commands with elevated (superuser) privileges.

# Example: Run a command as root
sudo apt update

sudo bash: Switches to the root directory/user shell.

sudo bash

exit: Exits the current shell session (e.g., exits root shell).

exit

sudo chown <new_owner> <filename>: Changes the owner of a file or directory.

# Example: Change owner of my_file.txt to 'yasmin'
sudo chown yasmin my_file.txt

sudo useradd <username>: Adds a new user to the system.

# Example: Add a new user named 'devuser'
sudo useradd devuser

sudo groupadd <groupname>: Adds a new group to the system.

# Example: Add a new group named 'devops_team'
sudo groupadd devops_team

sudo chgrp <new_group> <filename>: Changes the group ownership of a file or directory.

# Example: Change group of my_file.txt to 'devops_team'
sudo chgrp devops_team my_file.txt

passwd <username>: Sets or resets the password for a user.

# Example: Set password for 'devuser'
sudo passwd devuser

passwd -l <username>: Locks a user account.

passwd -u <username>: Unlocks a user account.

# Example: Lock 'devuser' account
sudo passwd -l devuser

userdel <username>: Deletes a user account.

# Example: Delete user 'olduser'
sudo userdel olduser

groupdel <groupname>: Deletes a group.

# Example: Delete group 'old_team'
sudo groupdel old_team

usermod -l <new_username> <old_username>: Renames an existing user account.

# Example: Rename user 'johndoe' to 'john_new'
sudo usermod -l john_new johndoe

6. Search & Filter Commands
Commands to find files and text patterns.

find: Used to search for files and directories based on various criteria.

find -type f -name <filename>: Finds files by name.

find -type d -name <dirname>: Finds directories by name.

find -type f -name <filename> -exec chmod 777 {} \;: Finds files and applies permissions.

find -type f -perm 777: Finds files with specific permissions.

find -type f -size 0 or find -type f -empty: Finds empty files.

find -type f -mmin -10: Finds files modified within the last 10 minutes.

find -type d -mmin -10: Finds directories modified within the last 10 minutes.

find -type f -mmin +10: Finds files modified more than 10 minutes ago.

find -type f -mtime -10: Finds files modified within the last 10 days.

find -type f -mtime +1: Finds files modified more than 1 day ago.

# Example: Find all .txt files in the current directory and its subdirectories
find . -type f -name "*.txt"

# Example: Find empty files
find . -type f -empty

grep (Global Regular Expression Print): Used for pattern matching within text files.

grep 'string' <filename>: Finds lines containing 'string'.

grep -i 'string' <filename>: Case-insensitive search.

grep -n 'string' <filename>: Shows line numbers with matches.

grep -c 'string' <filename>: Counts matching lines.

grep -o 'string' <filename>: Shows only the matched string, not the whole line.

grep -l 'string' *: Lists filenames containing the string.

grep '^string' <filename>: Finds lines starting with 'string'.

grep 'string$' <filename>: Finds lines ending with 'string'.

grep -A2 'string' <filename>: Shows matched line and 2 lines after.

grep -B2 'string' <filename>: Shows matched line and 2 lines before.

grep -C2 'string' <filename>: Shows matched line and 2 lines before/after.

# Example: Search for "error" in application.log
grep 'error' application.log

# Example: Count occurrences of "WARNING" (case-insensitive)
grep -ic 'warning' server.log

egrep or grep -E: Searches for multiple patterns using extended regular expressions.

# Example: Search for "error" or "fail" in log.txt
egrep 'error|fail' log.txt

fgrep or grep -F: Searches for fixed strings (no regular expressions) in multiple files.

# Example: Search for "specific_text" in file1.txt and file2.txt
fgrep 'specific_text' file1.txt file2.txt

7. Disk Usage
Commands to check disk space usage and availability.

du: Shows disk space used by files and directories.

du -h: Shows human-readable sizes.

du -ah: Shows human-readable sizes recursively for all files and directories.

# Example: Show disk usage of current directory in human-readable format
du -h .

df: Shows disk space free on file systems. Displays size, used, available size in KB blocks, and where files are mounted.

# Example: Show free disk space
df -h

8. Compression Commands
Commands for zipping, gzipping, and archiving files.

zip <archive_name> <files/directories>: Compresses files and directories into a .zip archive.

zip -m: Moves (deletes original) files/directories into the zip archive.

zip -u: Updates the zip archive (adds new/modified files).

zip -d <archive_name> <file_to_delete>: Deletes a specific file from the archive.

zip -v: Shows compression percentage.

# Example: Create a zip archive of my_folder and my_file.txt
zip my_archive.zip my_folder my_file.txt

unzip <archive_name>: Extracts files from a .zip archive.

unzip my_archive.zip

gzip <filename>: Compresses a file into a .gz archive. The original file is typically deleted.

gzip -k <filename>: Keeps the original file after compression.

# Example: Compress log.txt (log.txt will be replaced by log.txt.gz)
gzip log.txt

gunzip <filename.gz>: Extracts files from a .gz archive.

gunzip log.txt.gz

tar: Archives multiple files into a single .tar (tape archive) file, often used for bundling. Not primarily for compression itself, but often combined with gzip (e.g., .tar.gz).

tar -cvf <archive.tar> <files/directories>: Creates (c), Verbose (v), File (f) archive.

tar -tvf <archive.tar>: Lists (t) contents of a tar archive.

tar -uvf <archive.tar> <files/directories>: Updates (u) existing tar archive.

tar -xvf <archive.tar>: Extracts (x) contents from a tar archive.

# Example: Create a tar archive of multiple files
tar -cvf my_bundle.tar file1.txt folder1/ report.pdf

# Example: Extract contents of the tar archive
tar -xvf my_bundle.tar

9. Linking Files
Commands to create shortcuts or alternative names for files.

ln -s <Source_Path> <Destination_Path> (Softlink / Symlink): Creates a symbolic link (shortcut). If the original file is deleted, the softlink becomes broken.

# Example: Create a softlink 'short_cut' to 'original_file.txt'
ln -s original_file.txt short_cut

ln <Source_Path> <Destination_Path> (Hardlink): Creates a hard link. Both the original file and the hardlink point to the same inode (data on disk). If the original file is deleted, the hardlink still works.

# Example: Create a hardlink 'permanent_link' to 'original_file.txt'
ln original_file.txt permanent_link

10. Scheduling Tasks
Automating tasks with crontab.

crontab: A Linux utility to schedule jobs (commands or scripts) to run automatically at specified intervals.

Syntax: min hour day_of_month month day_of_week command

min: (0-59)

hour: (0-23)

day_of_month: (1-31)

month: (1-12 or Jan-Dec)

day_of_week: (0-7, 0 or 7 is Sunday)

crontab -l: Lists cron entries for the current user.

crontab -u <username> -l: Lists cron entries for another user.

# Example: Edit crontab entries for the current user
crontab -e
# Add a line like:
# 0 2 * * * /path/to/my_backup_script.sh
# This runs my_backup_script.sh every day at 2:00 AM

# Example: List current user's crontab entries
crontab -l

11. Text Editing (Vi Editor)
A powerful, command-line text editor.

vi <filename>: Opens a file in the Vi editor.

Modes:

Command Mode: Default mode. Interprets typed characters as commands (e.g., navigation, copy, paste, delete).

Insert Mode: To enter, press i (insert), a (append), o (open new line). Everything typed is inserted as text. Press ESC to return to Command Mode.

Escape (Last Line) Mode: To enter, press : (colon) from Command Mode. Allows saving, quitting, and running external commands.

Common Commands in Command Mode:

l: Move cursor right.

h: Move cursor left.

j: Move cursor down.

k: Move cursor up.

:wq: Save and exit the file (from Escape Mode).

:q!: Quit without saving (from Escape Mode).

# Example: Open a file in Vi
vi my_document.txt
