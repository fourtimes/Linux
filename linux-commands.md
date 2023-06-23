### CPU(processor), RAM(memory), Storage(Hard Disk) informations:-


– To see memory status, type: **free**

– To see more options, type: **free –help**

– To see all processes running, type: **top**; 
– Type ‘q‘ to quit top

– To get processor speed and other CPU information, type: **cat /proc/cpuinfo**

– To get hard disk space and information, type: **df**

– To get a list of drives, type: **sudo fdisk -l**
## LINUX COMMANDS DETAILS:-

| Commands| Descriptions                                                             | Examples |
| ------- | ------------------------------------------------------------------------ |-------------------|
| ls      | Use the "ls" command to know what files are in the directory you are in. |
| ls -la|List out the items one by one. You can see all the hidden files|
|cd|Change directory.|
|pwd|Print working directory (exact directory).|
|mkdir|When you need to create a folder or a directory.| mkdir (filename)|
|rmdir|Can only be used to delete an empty directory.| rmdir (filename)|
|rm| rm command to delete files and directories.| 
|rm -r|delete just the directory. It deletes both the folder and the files it contains when using only the rm command.|rm -r (folder name)|
|touch|The touch command is used to create a file.| 
|man & --help|To know more about a command and how to use it, use the man command. It shows the manual pages of the command.|
|cp (copy)|Use the cp command to copy files through the command line. It takes two arguments: The first is the location of the to be copied, the second is where to copy.| cp (filename1) (filename2)|
|mv (move)|Use the mv command to move files through the command line. We can also use the mv command to rename a file. For example, if we want to rename the file “text” to “new”, we can use “mv text new”.|mv (filename1) (filename2)|
|locate|The locate command is used to locate a file in a Linux system, just like the search command in Windows. This command is useful when you don't know where a file is saved or the actual name of the file.| **~/Desktop$ locate test.txt**|
|echo|The "echo" command helps us insert some data into a file. |**~/Desktop$ echo ashli, joe >> test.txt**|
|cat|Use the cat command to display the contents of a file. It is usually used to easily view programs. |**~/Desktop$ cat test.txt**|
|cat (filename) I grep (selected word)|Highlighted a selected word in selected file.|
|Kill -9 PID|The most common command to terminate a process is kill command. You need to know the PID of the process you want to terminate.|
|nano, vi, jed|nano and vi are already installed text editors in the Linux command line. The nano command is a good text editor that denotes keywords with color and can recognize most languages|
|sudo| A widely used command in the Linux command line, sudo stands for "SuperUser Do". So, if you want any command to be done with administrative or root privileges, you can use the sudo command.|
|sudo bash|You can enter the root line |**root@HP-EliteBook-8570w:/home/crash#**|
|su -|open up the new shell of directory.| **ashli**@Hp-EliteBook-8570w:~$|
|ssh crash@(ip address)|To Change root user to normal user.|
|sudo su|To change normal user to root user.|
|crash@HP-EliteBook-8570w:~**$**|Normal User.|
|root@HP-EliteBook-8570w:/home/crash/**#**|Root User.|
|sudo passwd|Change in the new root password.|
|df|Use the df command to see the available disk space in each of the partitions in your system. You can just type in df in the command line and you can see each mounted partition and their used/available space in % and in Kbs.|
|df -m| Disk file system want it shown in megabytes.|
|du|Use du to know the disk usage of a file in your system. If you want to know the disk usage for a particular folder or file in Linux, you can type in the command df and the name of the folder or file.|
|ls -lh|To view the file sizes of all the files in a folder.|
|zip, unzip|Use zip to compress files into a zip archive, and unzip to extract files from a zip archive.|
|uname|To show the information about the system.|
|uname -a|prints most of the information about the system. This prints the kernel release date, version, processor type, etc.|
|uname -s|Print the kernal name.|
|uname -p|Print the processor.|
|uname -n|Print the network node hostname.|
|uname -o|Print the operating system.|
|hostname|To show your name of your host or network.|
|hostname -I|To show IP address in your network.|
|ip a| find the ip address.|
|lscpu|To display information about the CPU on Linux.|
|sudo apt-get update && upgrade| To update and upgrade the system;|
|sudo apt install package_name|To install the new packeages.|
|sudo apt-get remove package_name| To remove the packages using this commands.|
|apt list|Let us list all software packages on Ubuntu Linux.|
| apt list --installed|List all installed packages only.|
|apt list -a pkgNameHere|Find a specified package.|
|service --status-all| List all services in Ubuntu.|
|sudo systemctl stop service_name|Stop the service.|
|sudo systemctl start service_name|Start the service.|
|sudo systemctl restart service_name|Restart the service.|
|sudo systemctl status service_name|Status of the service details.|
|df -h|Shows disk space in human-readable format.|
|df -i|shows used and free inodes.|
|getfacl (filename)|getfacl displays the file name, owner, the group, and the Access Control List (ACL). If a directory has a default ACL, getfacl also displays the default ACL.|
|setfacl -m group::rwx or rw- or --- (filename) (manual ACL)| We can add ACL to these files using setfacl. ACL – Access Control List.|
|shutdown -r (time)|With option r, system will shutdown immediately and automatically reboot. |**sudo shutdown -r 3**|
|shutdown -P (time)|To power-off the system option P is used.|
|sudo mount /dev/sdd1 /mnt|To mount into the disk.|
|sudo umount /mnt|To unmount the disk.|
|lsblk|To see all the disks and partitions on your system.|
|blkid|To gather UUID of the partition. UUID- Univeresal Unique Identification.|
|chmod g+x (filename)|Execute(x) permission **group** in test.txt(your filename) filename.|
|chmod o-r (filename)|Remove read permission **others** in text.txt(your filename) filename.|
|chmod u-x (filename)|Remove execute permission on **user** in test.test.txt(your filename) filename.|
|chmod 777 filename| To give a permission read(4), write(2), execute(1).|
|vi (filename)|vim file created.|
|:q!|Exit the vim file.|
|:wq!|Save and exit the vim file.|
|alias -p|Listing all alias name|
|lt --port (port-number)| to get the url and use this url to operate the another person|
|sudo lsof -i -P|What are the instance are running|
|telnet serverIP port|Telnet can also be used to check if a specific port is open on a server.|For example, to check if port 22 is open on a server, run `telnet 38.76.11.19  22`|
