# Linux Command Line

## Basic Commands

```
date = current date
cal = current months calendar
cal 1999 = calendar for 1999
cal -3 = calendar (last month, current and next month)
cal -y = all year calendar
clear = clear console text
exit = exits de terminal
```

## Navigate Directories

### Linux File System Tree:

![Screenshot](./Linux%20File%20System.png)

- **bin** = binary (commands and utilities that all users can run)
- **sbin** = this directory contains programs that performs vital system tasks (network management, disk partitioning). Only the superuser has access to these programs.
- **home** = each user is given a directory under the home directory. A user can store anything in his home directory
- **opt** = optional (additional software)
- **tmp** = temporary files, files created by various programs (**Generally cleared on reboot**)
- **var** = variable data, data that frequently changes over time.
  - Log files
  - Data bases
  - User mail
  - Spools -> temporary storage location
    - /var/spool is traditionally used for machine-local data being spooled to or from UNIX subsystems. For example, print jobs are spooled here for delivery to the lineprinter daemon, out-bound mail is spooled for delivery to remote systems, and UUCP files are spooled for transmission to UUCP neighbors. In-bound mail and news are spooled here for delivery to users, and at and cron jobs are spooled for delayed execution by the cron daemon.
  home = the directory with the users and user data

![Screenshot](./Linux%20Relative%20and%20Absolute%20paths.png)


### Commands

```
pwd = print work directory

ls = list directory

cd = change directory

cd / = take you to the root directory

cd ~ = take you to the user home directory

cd ./another_folder = navigate from current directory to another_folder

cd .. = navigate from current directory to parent directory

cd - = go back to the previous working directory
  $ cd / = going to the root directory
  $ cd ~/ = going to the home directory
  $ cd - = going back to the root directory

ls / = display your root directory

ls ~ = display your home directory

ls .. = display the content of my parent directory

[DOES NOT WORK] ls - = should display you the content of your previous working directory
```

![Screenshot](./LS%20-L%20OUTPUT.png)

## Linux Links

- Every file in the system has an inode (Index node)
  - Contains all file information except the file content and name  
  - A database of a file
  - They contain:
    - Inode number
    - File size
    - Owner information
    - Permission
    - File type
    - Number of links
      - Soft Link
      - Hard Link
    - etc...

### Soft Link
- A soft link is the same as a shortcut in Windows
- Aka Symbolic link
- It is a pointer to the original file
- It is a file pointing to another file
  - Different inode number
- Small file size
- In case the original file gets deleted, the soft link will no longer work
- You can create soft links for directories

![Screenshot](./Linux%20Soft%20Links.png)

### Hard Link
- Different name of the same file
- Same file size
- Same inode number
- You cannot differentiate between a real file and a hard link
- They are kind of a copy of the file
- If I change a hard link file content, it will reflect on the other files (the original and other hard links)
- In case I delete the original file, the hard link file will still work
- **Be careful**: You should not create hard links for directories. Normally they are not even allowed because they break the file system structure.
![Screenshot](./Linux%20Hard%20Links.png)

### Commands

```
ls -i = show inode of files

ls -l = show files information (size in bytes, permission, etc.)

ln = link

ln file_name hard_link1 = Create a hard link for a file (same inode)

ln -s file_name soft_link1 = Create a soft link for a file

ln -s .. c = Create a soft link C for the parent directory you are currently located in
```
## LS Options

```
ls -i = This will list the index node number of each file

ls -a = This will show all the files in your current directory, including hidden files

ls -l = Long listing of all files in the directory and some important information.

ls -t = Sort files by modification date

ls -r = List the files in reverse fashion

ls -li = Long listing + show inode ids

ls -lia = Long listing + show inode ids + hidden files

ls -R = Show current directory content plus any children/sub directory content as well

ls -Ra = Show current directory content plus any children/sub directory content as well + including hidden files



```
