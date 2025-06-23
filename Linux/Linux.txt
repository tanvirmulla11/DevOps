Usefull Linux Commands and Descriptions:

1.  `touch`
    Description: Used to create a file. 
    Syntax: `touch File_name` 

2.  `ls`
    Description: Used to list out the files and directories (folders) in your system. 
    Syntax: `ls` 

3.  `ls -l`
    Description: Used to show the access permissions of files and directories (read, write, or execute). [cite: 63, 64]
    Syntax: `ls -l` 

4.  `ls -r`
     Description: Used to show the files and directories in reverse order. 
     Syntax: `ls -r` 

5.  `ls -t`
    Description: Used to show the timestamp of files and directories, meaning when the file was created or modified (displays date and time). [cite: 64, 65]
    Syntax: `ls -t` 

6.  `ls -h`
    Description:Shows the files and directory size in a human-readable format. 
    Syntax: `ls -h` 

7.  `ls -x`
    Description: Used to sort the files and directories alphabetically after the file extension. 
    Syntax: `ls -x` 

8.  `ls -a`
    Description: Used to show hidden files and directories in your system.Hidden files and directories start with a "`.`" (dot) extension. [cite: 69]
    Syntax: `ls -a` 

9.  `ls -R`
    Description: Used to recursively describe the directory with its sub-files and sub-directories. 
    Syntax: `ls -R` or `ls -R folder_name` 

10. `clear`
    Description:** Used to clear the screen in Linux. 

11. `mkdir`
    Description:** Used to create a directory (folder) in Linux. 
    Syntax:** `mkdir dir-name` 

12. `mkdir -p`
    Description: Used for creating a child directory under the main directory. 
    Syntax: `mkdir -p dir1/dir2/dir3/Filename` (Note: the example shows a filename, but `mkdir -p` is for directories) [cite: 72]

13. cd`
    Description: Used to change directories. 
    Syntax: `cd directory-name` 

14. `pwd`
    Description: Used to show the whole path of the present working directory. 
    Syntax: `pwd` 

15. cd ..`
    Description: Will redirect you to the previous one directory. 
    Syntax: `cd ..` 

16. `cd ../..`
    Description: Will redirect you to the previous two directories. 
    Syntax: `cd ../..` 

17. `cd ~`
    Description: Will redirect you to the home directory. 
    Syntax: `cd ~` 

18. `cd -`
    Description: Will redirect you to the previous working directory. 
    Syntax: `cd -` 

19. `cat`
    Description: Used to read the content of a file. 
    Syntax: `cat Filename` 

20. `cat >`
    Description: Used to put data into a file. It can also be used to create a new file from scratch. However, if the file already exists, it will flush (overwrite) all previous data. 
    Syntax: `cat > Filename` 
    Note: Use `Ctrl + D` to save and exit from the file. 

21. `cat >>`
    Description: Used to append data to a file without removing previous data. 

22. `uname`
    Description: Used to show the operating system name. 
    Example: `uname` (Output: Linux) 

23. `whoami`
    Description: Used to show the username currently logged into the system. 
    Example: `whoami` 

24. `which`
    Description: Used to show the binary path of a command. 
    Example: `which ls` 

25. `ifconfig
    Description: Used to show the IP address of a Linux Server. 

26. `ipconfig`
    Description: Used to show the IP address of a Windows Server. 

27. `hostname`
    Description: Used for both Linux and Windows servers to check the IP address. 

28. `ping`
    Description: Used to check the network connectivity between a host machine and a remote machine. 
    Syntax: `ping iPaddress Portno` 
    Note: Port 22 is for Linux Server, Port 445 is for Windows Server. Use `Ctrl + C` to stop the ping command. 

29. `cat /etc/os-release`
    Description: Used to check the Kernel version of your system. 

30. `cat /var/log/syslog` (The PDF states `/var/sys/log` but this is likely a typo for `/var/log/syslog`)
    Description: Used to check the system log files. 