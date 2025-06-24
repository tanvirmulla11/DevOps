# 🐧 Useful Linux Commands for Shell Scripting & DevOps 🚀

Welcome to your ultimate cheat sheet of essential Linux commands that every DevOps enthusiast and shell scripter should know! These are commands you’ll use daily in automation, server setup, system debugging, and CI/CD pipelines.

---

## 📁 File & Directory Management

| Command           | Description                                     | Syntax Example                     |
|-------------------|-------------------------------------------------|------------------------------------|
| `touch`           | Create an empty file                            | `touch file.txt`                   |
| `mkdir`           | Create a directory                              | `mkdir folder`                     |
| `mkdir -p`        | Create nested directories                       | `mkdir -p dir1/dir2/dir3`          |
| `cd`              | Change directory                                | `cd myfolder`                      |
| `cd ..`           | Go back one level                               | `cd ..`                            |
| `cd ../..`        | Go back two levels                              | `cd ../..`                         |
| `cd ~`            | Go to home directory                            | `cd ~`                             |
| `cd -`            | Switch to previous directory                    | `cd -`                             |
| `pwd`             | Show current directory path                     | `pwd`                              |
| `clear`           | Clear terminal screen                           | `clear`                            |

---

## 📄 File Content Commands

| Command        | Description                                         |
|----------------|-----------------------------------------------------|
| `cat file.txt` | View contents of a file                             |
| `cat > file`   | Write (overwrite) contents into a file              |
| `cat >> file`  | Append contents to an existing file                 |
| `Ctrl + D`     | Use to exit writing mode in `cat`                   |

---

## 📂 Listing Files

| Command       | Description                                              |
|---------------|----------------------------------------------------------|
| `ls`          | List files/folders in directory                          |
| `ls -l`       | Long listing format (with permissions, size, owner, etc) |
| `ls -a`       | Show hidden files (starting with dot `.`)                |
| `ls -t`       | Sort by modification time                                |
| `ls -r`       | Reverse order                                            |
| `ls -x`       | Sort alphabetically by extension                         |
| `ls -R`       | List directories recursively                             |
| `ls -h`       | Show sizes in human-readable format (e.g., KB, MB)       |

---

## 🌐 Networking & System Info

| Command                 | Description                                |
|--------------------------|--------------------------------------------|
| `uname`                 | Show system name                           |
| `whoami`                | Show current user                          |
| `which <command>`       | Show path of a command (e.g., `which ls`)  |
| `ifconfig`              | Show Linux IP address                      |
| `ipconfig`              | Show Windows IP address                    |
| `hostname`              | Display hostname/IP                        |
| `ping <ip>`             | Check connection with a server             |
| `cat /etc/os-release`   | Show OS & kernel info                      |
| `cat /var/log/syslog`   | View system logs                           |

---

## 💡 Tip: Shell Script to Display System Info

```bash
#!/bin/bash

echo "Welcome, $USER 👋"
echo "Today is: $(date)"
echo "System Info:"
uname -a

echo "IP Address:"
ifconfig | grep inet
