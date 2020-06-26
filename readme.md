# What is Linux ?

- Linux is OS, like Microsoft has windows, Apple has MACOS
- Linux is an OS which sits in the middle of your hardware and users
- Unix operating system was created more than 30 years ago by a group of researchers at AT&T's Bell Labs

---

# difference b/w unix vs linux

- unix was first developed for multi-user and multi-tasking in mid-1970 in Bell labs
- linux was born in 1991 by Linus Torvalds
- Linux is mostly free OS (Redhost distro of linux is paid OS) and Open source
- Unix is mostly used by SunMicrosystem (now bought by Oracle) as Solaris, Hp-UX, AIX, etc
- Linux is mostly used by many developers community or companies (Redhat)
- Unix supports very few file system
- Linux can be installed on a wide variety of computer hardwares -> ranging from mobile phones, tables, video games console to mainframes and supercomputers
- Unix can only be installed in limited hardwares unlike linux OS

---

# Virtual Box

- VirtualBox is a free and open-source hypervisor for x86 computers currently developed by Orcale and VM-ware
- It extends the capabilities of computer to virtually multiple run different operating systems on one hardware at the same time.
-


    (Linux) or (Windows) or (Mac)
    Orcale VirtualBox
        |
    Operating System (windows or Mac)
        |
    Hardware

---

# Downloading iso image of centos in Oracle VMBox

- Download and install Orcale VMBox in your ubuntu host OS
- In Oracle VMBox, If you only see 32bit OS listing then-> Need to enable virtualization in your hardware. Restart > Press F2 > virtualization Enabled
- Create a virtual machine for Centos -> RAM : 2GB, Memory : 10GB
- Download Centos-7 ISO Image (minimal image version)
- Install CentOs ISO image in your virtual machine created in VirtualBox

---

# Different Linux Distro (Distribution) [Flavours of Linux's] :

- Redhat (Not open source)
- Centos [Supported by red-hat]
- Fedora [Supported by red-hat]
- suse [used by vm-ware]
- debian
- ubuntu
- khali

---

# Linux v/s windows

- linux is not user-friendly, but windows is
- linux is very reliable but windows requires tuesday patched and reboot
- linux is enterprise level software, windows is for games, office, utilites, etc
- linux is best for multi-tasking, but windows can also do multitasking but uses very high cpu and memory resources
- Linux is secure but windows is not secure
- Windows is open source OS but windows is liscened under Microsoft Corps

---

# Linux Users

- US Government and Agencies (FBI)
- NASA
- Health Care, Scientist
- Bullet Train in Japan runs at speed at 150-215 m/h
- Traffic Controls
- Financial Institutes ex- Newyork stock exchange
- Entertainment industries (Cinemas, Production houses etc)
- World e-commerce leaders like- Amazon, eBay, PayPal and walmart run their platform on linux
- Other forutne 500 Companies lilke - McDonalds, Google, FB, etc

---

# Command Prompt

root@tejas]#

- root ==> User name
- tejas ==> host name
- \$ ==> prompt symbol logged in as user, # ==> Prompt Symbol logged in as root

- hostname ==> Gives you the host name
- whoami ==> Gives you the username

---

# Access to Linux System

- Each OS has different protocol or client that is used to access the system
- ex :
- Windows ==> Remote Desktop Connection (RDP)
- VMWare ESX ==> vSphere Client
- Linux ==> Putty, SecureCRT, SSH from Linux to Linux

- To install putty in Linux :
- \$ sudo apt-get install -y putty
- \$ putty

---

# Accessing from Ubuntu Host to CentOs VitualMachine using putty

- Network Command : ipconfig (deprecated), ip addr (latest)
- \$ yum install net-tools
- \$ sudo apt install net-tools
- Network Settings
  - Host-only adapter: Allows communication b/w your PC and the VM
  - Bridged Adapter: Allows communication b/w your PC and VM puls allows communication to the internet
- ## Steps to Set the Bridge Adapter to CentOS Virtual Machine :
  - Oracle VMBox > Centos7 Virtual Machine > Settings > Network > Adapter1
  - Attached to : Bridge Adapter
  - Name: wlsp3s0 (network Name, Can be anything but remeber this)
  - Advanced : Promiscuous Mode => Allow All > OK
  - Go to CentOS Virtual Machine > Device (Top-menu) > Network > Connect Network Adapter
  - Virtual Machine Terminal : Login as root
    - \$ su
    - \# ifup wlsp3s0 ( To up the newtowkr ==> ifup <network-name-assigned> )
    - \# ifconfig (inet 192.168.0.106)
- Now Get to know the ip address of the Virtual Machine (Centos) and Host Machine(Ubuntu)
  - ifconfig
  - ping 192.168.0.106 (start ping from both the terminals from VM and Host)
  - If all packets recieved succesfully then, Bridge Adapter is connected successfully
- After Installing putty for linux : sudo apt-get install -y putty
- Session > Host Name : 192.168.0.106, PORT : 22 > Open > Login with user/root

NOTE :

- Linux has a super admin account : 'root'
- 'root' is the most powerful account that can create, modify, delete account and make changes to system configuration files
- Linux is a case-sensitive system
- Avoid using file names with spaces
- '/' ==> Slash Directory is parent of all directory ==> \$ cd /

---

# Linux File System

- OS Store data on disk drive using a structure called filesystem, consisting of files, directories, and the information needed to access and locate them.
- There are many different types of filesystem. In general improvement have been made to filesystem with new releases of OS, and each new filesystem has been given different names ex- ext3, rx4, XFS, NTFS, FAT, etc
- Linux filesystem store information in a hirearchy of directories and files
- C drive in windows <==> '/' (root) in Linux
- ## File System Structure and its description :
  - /boot : Contains file that is used by the boot loader (grub.cfg)
  - /root : root user HOME directory. It is not same as /
  - /dev : System devices (ex- disk, cdrom, speakers, flashdrive, keyboard, keyboard, etc)
  - /etc : Configuration files
  - /bin -> /usr/bin : Everyday user commands
  - /sbin -> /usr/sbin : System/filesystem commands
  - /opt : Optional add-on applications (Not part of OS apps)
  - /proc : Running processes (Only exist in Memory)
  - /lib -> /usr/lib : C programming library files needed by commands and apps
    \$ strace -e open pwd
  - /tmp : Directory for temporary files
  - /home : Directory for users account
  - /var : System logs
  - /run : System daemons that start very early (ex- systemd and udev) to store temporary runtime files like PID(processID) files
  - /mnt : To mount external filesystem (ex: NFS)
  - /media : For cdrom mounts.

---

# Navigating File System

- When navigating a UNIX filesystem, there are a few important commands
  - cd : Change directive
  - pwd : print working directory (Current working directory ur in)
  - ls : list content of directory

---

# File System Path

- There are 2 types to navigate to a filesystem
  - Absolute Path
  - Relative Path
- An absolute path always begins with a '/'. This indicates that the path starts at the root directory.
  ex : \$ cd /var/log/apt
- A relative path does not begin with a '/'. It identifies a location relative to your current position.
  ex : \$ cd /var
  \$ cd log
  \$ cd apt

---

# Directory Listing Attributes

- \$ ls -l (List all the directories in the alphabetical order)
- \$ ls -lt (list all the directories/files which are last modified in Asc order [t -> Time])
- \$ ls -ltr (list all the directories/files which are last modified in Desc order [tr -> Time, Reverse])
- Type of file :
  - drwxr-xr-x ==> Directory
  - lrwxrwxrwx ==> link
  - -rw-rx ==> Regular files

---

# Creating files and directories

- Creating a file
  - touch : \$ touch <file_name> (create an empty file)
  - cp: \$ cp <src_file_name> <dest_file_name>
    - \$ cp <src_file> <dest_file_1> <dest_file_2> .....
  - vi :(using VIM Editor) : \$ vi homer
- Creating Directories
  - mkdir : \$ mkdir <directory_name>
    - mkdir <dir_name_1> <dir_name_2> ...

---

# Linux File Types :

- File Symbol : -, d, l, c, s, p, b

- - ==> Regular file (No character/letter is assoicated then its regular file)
- d ==> Directory
- l ==> link
- c ==> Special file or device file (keyboard, Mouse, Disk, etc are recognized as Special file)
- s ==> socket
- p ==> Named pipe
- b ==> Block device

- NOTE : When we execute \$ ls -l command then first column's first character defines the file Type

---

# Finding Files and Directories

- Two commands are used to find files/directories :

  - find
  - locate

- \$ find . -name "<file_name>" ==> . represent from current directory start searching the <file_name> mentioned
- \$ find / -name "<fiel_name>" ==> from root direcotry start searching the <file_name> mentioned
- \$ locate <file_name>

- NOTE : To know the documentation of any command and how to use ==> man (ex : \$ man find)
- Difference b/w find and locate :
  - locate uses a prebuilt database, which should be regularly updated, while find itreates over a filesystem to locate files. Thus, locate is much faster than find, butcan be inaccurate if the db (can be seen as a cache) is not updated.
  - To update local db run updatedb (This will be updated automatically by OS) ==> updatedb (to run this command become root)
    NOTE : ERROR: updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db', Then you should login as root ==> sudo su

---

# Change Password of particualr user logged in

- \$ passwd userid
  (It will ask following details : old password, new password, re-type new password)

---

# WildCards

- We use wildcard to search for file-name in generic way ex- superheroes1, superheroes2, .. then we write wildcards as : superheroes*, ?perheroes*, etc...
- A wildcard is a character that can be used as a subsitute for any of a class of characters in a search
- \*astreic ==> represents zero or more characters
- ? ==> represents a single characters
- [] ==> represents a range of characters
- \ ==> represents an escape character
- ^ (caret) ==> represents the beginning of the line
- \$ (dollar) ==> The end of the line

- TASK : To create 10 files tejas1-xyz, tejas2-xyz, ....
- touch tejas{1..10}-xyz.js
- ls -l tejas\*
- rm tejas\*
- rm \*.js

- ls -l ?ejas\* ==> Give all the files, but we don't know the first character (first character can be anything)

- ls -l astreic[es]astreic ==> Give me all the files which has e or s character in it
- ls -l astreic[es]astreic | more

---

# Links

- Two types of links : Soft Links and Hards Links
- inode ==> Pointer or number of a file on the hard disk
- If we create a file called index.htmnl, we as human understand this is a file but the computer does not understand the file names so it recognize a file name by assigning the number to it called inode
- Soft link ==> Link will be removed if file is removed or rename (link b/w filename and pointer/inode)
- Hard link ==> Deleting, renaming or moving the original file will not affect the hard link
- To create a hard link : \$ ln
- To create a soft link : \$ ln -s
- If file is created by hardlink then this link will be directly referencing to the inode, whereas if file is created by softlink then the file created will be directly referencing to the inode. (Check this fig in assests)
- TASK : Creating soft links
- \$ cd ~
- \$ cd tejas/test
- \$ touch hulk
- \$ echo "hulk is a superhero" > hulk
- \$ cat hulk
- \$ pwd (u will get the path)
- Now create another link of this hulk file inside temp folder(by referencing using soft link) as:
- \$ mkdir temp
- \$ cd temp (Come inside temp directory)
- \$ ln -s /home/tejas/test/hulk
- \$ ls -li ( i ==> indicates all the inodes)
  [20845343 lrwxrwxrwx 1 tejas tejas 21 Mar 8 12:43 hulk -> /home/tejas/test/hulk]
  (NOTE: You can see, that hulk is referencing to '/home/tejas/test/hulk' file)
- (You can see the hulk created in "/test/hulk" and "/test/temp/hulk" have different node ids)

- TASK : Creating hard links
- \$ cd ~
- \$ cd tejas/test
- \$ touch thor
- \$ echo "thor is a superhero" > thor
- \$ cat thor
- \$ mkdir temp
- \$ cd temp
- \$ ln /home/tejas/test/thor
- \$ ls -li

---

# Different type of Shell avaliable in Unix

- Bourne shell (sh)
- Bourne Again Shell (bash) (/bin/bash)
- C shell (csh)
- TC shell (tcsh)
- rbash
- dash

- Comand to know which shell you are using in the terminal : echo \$SHELL or echo \$0

---

# Command Syntax :

- Command options and arguments[syntax] : command option(s) argument(s)
- Options :
  - Modify the way that a command works
  - Usually consist of hyphen or dash followed by a single letter
  - Some commands accept multiple options which can usually be grouped together after a single hypen
  - ex:
    - \$ ls -l
    - \$ ls -ltr
- Arguments :
  - Most commands are used together with one or more arguments
  - Some commands assume a default argument if none is supplied
  - Arguments are optional for some commands and required by others
  - ex:
    - \$ ls -l workspace
    - \$ rm -f hulk (remove file)
    - \$ rm -r temp (remove directory)
- man ls (man stand for ==> manual) to check all the argumens and options of ls

---

# File Permission

- UNIX is a multi-user system. Every file and directory in your account can be protected from or made accessible to other users by changing its access permissions. Every user has responsibility for controlling access to their files only.
- Permission for a file or directory may be restricted to by types of operation to be performed
- 3 types of permissions are :
  - r ==> read
  - w ==> write
  - x ==> execute = running a program
- Each permission (rwx) can be controlled at 3 levels :
  - u ==> user (yourself)
  - g ==> group (people in the same project)
  - o ==> other (every one on the system/organization)
- File or Directory permission can be displayed by running \$ ls -l command
- Command to change permission ==> chmod (ch - change, mod - mode)
- -rw-r--r-- ==> initial (-) indicates its file, first (rw-) indicates user has read and write permission, Second (r--) indicates group has read permissions and last (r--) indicates others has read permissions.

## Permission assigned using Numeric Mode

- SYNTAX TO ADD PERMISSION: cmod ugo+rwx <file_name/direcotry>
- SYNTAX TO REMOVE PERMISSION: cmod ugo-rwx <file_name/direcotry>
- To change the permission use -> chmod (change mode)
- To remove write permission from group : \$ chmod g-w <file_name/direcotry> (g ==> group, - ==> remove, w ==> write permission)
- To remove read permission from all user, group and others : \$ chomd a-r <file_name/direcotry> (a ==> all , r ==> read permission)
- To remove write permission from user : \$ chmod u-w <file_name/direcotry>
- To add read, write permission to user : \$ chmod u+rw <file_name/direcotry>
- To add read, write permission to group : \$ chmod g+rw <file_name/direcotry>
- To add read, write permission to others : \$ chmod o+rw <file_name/direcotry>
- NOTE : We can see directory have x permission (Execute), does that mean directory can be executed ? No, execute of directory means we can perform cd operation on directory, To verify this, just remove the executable from folder then try to perform cd in to the file.

## Permission assigned using Numeric Mode

- SYNTAX: chomd <NUMBER> <file_name/direcotry>
- chomd 754 <file_name/dir> : 7 ==> user (read,write and execute) || 5 ==> Group (read and execute), 4 ==> other (read)
- check assets/chmod.pdf
- To remove all the permission of user, group and all : \$ chomd 000 <file_name/direc>

---

# File Owership

- There are 2 owners of a file or directory
- Command to change file ownership:
  - chown: changes the ownership of a file
  - chgrp changes the group ownership of a file
- Recursive ownership change option (Cacade) : -R
- chown root <file_name/direc> (Changing to root user)
- chgrp root <file_name/direc> (Changing to root group)

---

# Access Control List (ACL)

- ACL provides an additional, more flexible permission mechanism for file systems. It is desgined to assist the UNIX file permissions. ACL allows you to give permissions for any user or group to any disc resource.
- Use of ACL :
  - Think of a scenario in which a particular user is not a member of group created by you but still you want to give some read or write access, how can you do it without making user a member of group, here comes in picture access control lists, ACL helps us to do this trick.
  - Bascially, ACLs are used to make flexible permission mechianism in Linux.
  - From Linux man pages, ACLs are used to define more fine-grained discretionary access right for files and directories.
  - Commands to assign and remove ACL permissions are :
    - setfacl and getfacl
- List of commands for setting up ACL:
  1. To add permssion for user
  - \$ setfacl -m u:user:rwx /path/to/file
  2. To add permissions for a group
  - \$ setfacl -m g:group:rw /path/to/file
  3. To allow all files or directories to inherit ACL enteries from the directory it is within
  - \$ setfacl -dm "entry" /path/to/file
  4. To remove a specific entry
  - \$ setfacl -x u:user /path/to/file (for a specific user)
  5. To remove all entries
  - \$ setfacl -b path/to/file (for all users)
- NOTE :
  - As you assign the ACL permission to a file/directory it adds + sign at the end of the permssion
  - Setting w permission with ACL does not allow to remove a file
- CMD :
  - \$ sudo su
  - \# cd /
  - \# cd tmp
  - \# touch tx
  - \# ls -l tx
  - \# getfacl tx
  - Currently u are root, but if you want tejas user to give write permission to this file tx -> we can perform this by ACl. note : rightnow 'tejas' is one the user in the root so he falls under OTHER, thus e cannot just directly and give write access to OTHER then all the users in the root will be able access with write permission
  - (open new terminal log as tejas)
    - \$ cd /
    - \$ cd tmp
    - \$ ls -l tx
    - \$ vi tx (read only)
  - \# setfacl -m u:tejas:rw /tmp/tx
  - \# getfacl /tmp/tx (now go and check in other terminal)
  - (To remove this permission from tejas)
  - \# setfacl -x u:tejas /tmp/tx
  - \# setfacl -b /tmp/tx (to remove permission from all the users)
  - (Now other users like tejas cannot delete this file) \$ rm tx

---

# Help commands

- There are 3 types of help commands
  - 'whatis' command
  - command --help
  - 'man' command (man -> manual)
- \$ whatis ls
- \$ whatis pwd
- \$ ls --help
- \$ chmod --help
- \$ man ls
- \$ man pwd

---

NOTE : Shortcuts -> TAB Completion and Up Arrow

- Hitting TAB key completes the avaliable commands, files or direcotries. To see all the files/directory which starts with particular characters pres TAB twice
- Hitting up arrow key on the keyboard returns the last command ran.

---

# Addding Text to Files (Redirects)

- 3 Simple ways to add text to a file
  - vi
  - Redirect command
  - echo
- \$ echo "hello world" (Gives the same output)
- \$ echo "hello jeery" > jerry (This will create a jerry file and will write this text)
- \$ cat jerry (cat -> Read the content inside the file)
- \$ echo "Tom hello" > jerry (override the previous content and add new content/ delete previous file and add this new file)
- \$ echo "Harry potter is great" >> jerry (Will not overide the previous content, but append new content)
- \$ touch listingofdir
- \$ ls -ltr > listingofdir (This will add the list of files inside this file)
- \$ cat listingofdir
- \$ vi listingofdir
- \$ date >> listingofdir

---

# Standard Output of a file (tee)

- "tee" command is used to store and view (both at the same time) the output of any command
- The command is named after the T-splitter used in plumbing. It basically breaks the output of a program so that it can be both displayed and saved in a file. It does both the task simultaneously, copies the result into the specified files or variable and also display the result.
- Check the image : /assets/tee.png
- \$ whoami
- \$ pwd
- \$ hostname
- \$ echo "I am great person" > tsabunkar (write to the file)
- \$ cat tsabunkar
- \$ rm -f tsabunkar
- \$ echo "I am great person" | tee tsabunkar (wirte to the file and also execute the file as we do with cat)
- \$ echo "Tejas is also Healthy person" | tee -a tsabunkar (-a ==> append the text to pervious content)
- \$ cat tsabunkar
- \$ wc -c tsabunkar (To check number of characters in file)
- \$ ls -l | tee listdir
- \$ cat listdir
- \$ ls -l | tee f1 f2 f3
- \$ rm -f fasteric(\*)

---

# Pipes

- A pipe is used by shell to connect the output of one command directly to the input of another command
- syntax : command1 [args] | command2 [args]

- EX:
- \$ cd /etc
- \$ ls -l | more
- \$ ls -ltr | more
- \$ ll | more
- \$ ls -l | tail -1 (gives last line of the output)
- \$ ls -l | tail -2 (gives last two line of the output)
- \$ ls -l | head -2 (gives first line of the output)
- \$ ls -l | head -3 (gives first two line of the output)

---

# File Mantaince Command

- cp (copy)
- rm (remove)
- mv (move/re-name the filename)
- mkdir (make directory)
- rmdir or rm -r (remove directory)
- rm -Rf --> (will forcefully remove all sub-directories and its content as well)
- chgrp (Change ownership of file/dir @group level)
- chown (Change ownership of file/dir @user level)

- EX :
- \$ man cp
- \$ cp <src_file_to_copy> <dest_copied_from_src>
- \$ cp tsabunkar shailesh && cat shailesh
- \$ rm -f shailesh
- \$ touch usha
- \$ echo "Usha is mom" > usha
- \$ cat usha
- \$ mv <src> <des>
- \$ mv usha usabunkar (usha filename has been re-named to usabunkar)
- \$ mv usabunkar /home/tejas/tejas/ (filed moved from '/home/tejas/tejas/play-linux' --to--> '/home/tejas/tejas/')
- \$ mkdir got
- \$ rmdir -r got
- \$ sudo su
- \$ chgrp root <file_name>
- \$ touch ram
- \$ ls -l ram
- \$ chgrp tejas ram (Change ownership of ram file from 'root' to 'tejas' group level)
- \$ ls -l ram
- \$ chown tejas ram (Change ownership of ram file from 'root' to 'tejas' user level)
- \$ ls -l ram
- \$ chown root:root ram (Change ownership of ram file from 'tejas' to 'root' both group and user level)

---

# File Display Commands

- cat
- more
- less
- head
- tail

EX :

- \touch messages
  \$ cat messages
  \$ echo "I am terrific" >> messages
  \$ cat messages (show the content of the file at onces)
- \$ more messages (show the content of the file but one page at a time)
- \$ less messages (shows the content in the file one page at a time in reverse order) ('j' and 'k' KEY / up arrow and down arrow KEY is used to move within the file)
- \$ head messages (shows the first two lines of the file)
- \$ tail messages (shows the last tow lines of the file)

---

# Filters / Text Processors Commands

- cut
- awk
- grep and egrep
- sort
- uniq
- wc

## cut Text Processors Commands

- cut is a command line utility that allows you to cut parts of lines from specified files or piped data and print the result to standard output. It can be used to cut parts of a line by delimiter, byte position and character.
- cut filename
- \$ cut --version
- \$ cut -c1 <filename> (To get the first character of the content in the file)
- \$ touch avengers | vi avengers (enter all avengers name) [avengers ==> file name]
- \$ cat avengers
- \$ cut -c1 avengers (To get the first characters of all the line)
- \$ cut -c1,2,3,4 avengers (Gets the first, second, third and forth characters of all the lines)
- \$ cut -c1,5,2 avengers (Gets the first,fifth and second characters of all the lines)
- \$ cut -c1-5 avengers (list the range of characters from 1 to 5 characters of all lines)
- \$ cut -c1-3,6-9 avengers (get first three characters and sixth,seventh and ninth characters)
- \$ cut -b1-3 avengers (list the bytes size representation from first three range of characters of all line)
- \$ cat /etc/passwd
- \$ cut -d: -f 6 /etc/passwd (delimiter -> : , 6th character after delimiter must be printed)
- \$ cut -d: -f 6-7 /etc/passwd (gives both 6th and 7th strings)
- \$ ls -l | cut -c2,3
- \$ ls -l | cut -c2,3,14-24

## awk Text Processors Commands

- awk is a utility/language designed for data extraction. most of the time it is used to extract fields from a file or from an output.
- \$ awk -W version
- $ awk '{print $1}' avengers (Prints the 1st field from avengers file)
- $ awk '{print $2}' avengers (prints 2nd field from avengers file)
- $ ls -l | awk '{print $1, \$3}' (list 1st and 3rd field of ls -l output)
- $ ls  -l | awk '{print $NF}' (list last column of ls -l output)
- \$ awk '/hulk/ {print}' avengers (It is case sensitive, Search for specific word in the file avengers)
- $ awk -F: '{print $1}' /etc/passwd (output only 1st field of /etc/paswd, delimiter -> :)
- $ awk -F: '{print $6}' /etc/passwd
- $ echo "Hello Tom" | awk '{$2="Jerry"; print $0}' (Replace 'Hello Tom' => 'Hello Jerry' since $2 indicates 'Tom')
- $ cat avengers | awk -F- '{$2="tejas"; print \$0}' (In avengers file, string are sperated by delimiter ==> - then replace with 'tejas', so 'ant-man' ==> 'ant tejas')
- $ awk 'length($0) > 5' avengers (list the lines that have more than 5 bytes size)
- $ ls -l | awk '{if($9 == "hulk") print \$0;}' (if 9th column is ls -l has file name as 'hulk' then prin that)
- \$ ls -l | awk '{print NF}' (Tells that ls -l has 9 fields/columns)

## grep/egrep Text Processors Commands

- grep : this command which stands for 'global regular expression prints any lines which match a specified pattern
- \$ grep --version
- $ grep <keyword> <file_name> [$ grep hulk avengers] (Find the string in the file)
- \$ grep -c hulk avengers (number of occurance of search keyword)
- \$ grep -i HuLK avengers (search by ignoring case)
- \$ grep -n gamora avengers (gives the lines number of search keyword)
- \$ grep -v falcon avengers (gives all the content expect the searched keyword)
- \$ grep -vi groot avengers
- $ grep groot avengers | awk '{print $1}' (gives the first column of searched field)
- $ grep groot avengers | awk '{print $1}' | cut -c1-3
- \$ cd ~
- \$ ls -l | grep Desktop
- \$ egrep -i "Hulk|groot" avengers (Search multiple keywords using pipe)

## sort/uniq- Text Processors Commands

- sort commands : Sorts in alphabetical order
- uniq commands : Uniq command filters out the repated or duplicate lines
- \$ sort --version
- \$ sort avengers (sort the files in alphabetical order)
- \$ sort -r avengers (descending order)
- \$ sort -k2 avengers (Sort the 2nd filed/column)
- \$ ls -l | sort (sort ls -l in ascending order)
- \$ ls -l | sort -r (sort ls -l in descending order)
- \$ uniq avengers (Removes the duplicate strings/words in the avengers file)
- \$ echo hulk >> avengers
- \$ cat avengers
- \$ uniq avengers (This will not remove 'hulk' duplication)
- \$ sort avengers | uniq (Always sort first before using uniq )
- \$ sort avengers | uniq -c (Shows the number of duplicate keyword)
- \$ sort avengers | uniq -d (shows the duplicate keyword)
- \$ ls -l | sort | uniq

## wc - Text Processors Commands

- wc stands for word count
- wc ==> This commands reads either standard input or a list of files and generates: newline count, word count, and byte count
- \$ wc --version
- \$ wc --help
- \$ wc avengers ( o/p : 21 22 183 avengers, Avengers file has 21 -> lines, 22 words and 183 bytes size)
- \$ wc -l avengers (gives only number of lines)
- \$ wc -w avengers (gives only count of words)
- \$ wc -c avengers (gives only byte size of avengers file)
- \$ wc <DIRECTORY> (\$ wc workspace) [cannot run the wc on director]
- \$ ls -l | wc -l (gives the number of lines of list ls -l)
- \$ ls -l | grep drw | wc -l (gives the count of directory)
- \$ cat avengers
- \$ grep hulk avengers | wc -l (gives the count of hulk word present in the avengers files)

---

# Compare files

- diff (compare two files line by line)
- cmp (compare two files byte by byte)
- create a two files superman and supeman2, in these two files add one different string
- \$ diff superman superman2
- \$ cmp superman superman2

---

# Compress and un-compress files

- tar (putting everthing together inside the container)
- gzip (Now to compress the container we zip it)
- gzip -d (or) gunzip (uncompress the zip container)

- \$ tar cvf myFiles.tar ~/tejas/play-linux/ (taring all the files present inside play-linux dircetor to myFiles.tar)
- \$ mkdir foo
- \$ mv myFiles.tar foo/
- \$ cd foo
- \$ tar xvf myFiles.tar (untaring the myFiles.tar inside foo)
- \$ gzip myFiles.tar (ziping the .tar file) [converte myFiles.tar ==> myFiles.tar.gz]
- \$ gzip -d myFiles.tar.gz (uncompress the .tar.gz file) [converte myFiles.tar.gx ==> myFiles.tar]

---

# Truncate File size (truncate)

- truncate command is not used to compress, it chops the file content (resulting lost of the content)
- The linux truncate command is often used to shrink or extend the size of a file to the specified size.
- SYNTAX: truncate -s 10 <file_name>
- \$ touch books
- \$ echo trevor noah 12 years a slave 1984 The power of Your subconsious mind Decepition point > books
- \$ cat books
- \$ ls -l books (Size of the file is 86)
- \$ truncate -s 40 books
- \$ ls -l books (Size has been reduced to 40 bytes)
- \$ cat books [ Some of the content inside the file is lost :( ]
- \$ truncate -s 90 books ( we can also increase the file size)
- \$ ls -l books
- \$ nano books [OS will add -> @^@^@^@^@ to increase the file size, :) Silly right]

---

# Combining and Spliting files

- Multiple files can be combined into one and one file can be split into multiple file
  SYNTAX
- cat file1 file2 file3 > file4
- split file4
- split -l 300 file.txt childfile
- Split file.txt into 300 lines per file and ouptu to childfileaa, childfileab and childfileac
- \$ nano countries
- \$ cat countries | wc -l (13 lines)
- \$ split -l 2 countries sep (splits into two lines for each file, thus OS will create sepaa, sepab, sepac, ..sepag files total 7 files)
- \$ cat sepaa
- \$ cat sepag

---

# Exposure to other technologies:

- OS : Windows, MacOS, Linux, Unix
- Hardware : Lenovo, Mac
- Montoring Tools: Nagios, Splunk, Zenoss
- Cloud: Amazon EC2
- OS tools: Redhat Satellite, kickstart, Active Directory, DNS, Puppet, etc
- DB: SQL, informix, NoSQL etc

---

# What is IT ?

- Transfer of information/data from one person to another, from one location to another through technology
- IT Components : Hardware, OS, Applications/software, Networking, Security
- Enterprise Level IT Component: High Level Security, Storage, Database

---

# Redhat Certifications

- 3 Redhat Certifications
  - RHCSA (Redhat Certified System Adminstrator) ==> Exam : RHCSA-EX200
  - RHCE (Redhat Certified Engineer) ==> Exam: RHCE-EX300
  - RHCA (Redhat Certified Architect) ==> You must have RHCE, RHCSA

---

# Issues w.r.t to Network

- \$ ifconfig
- \$ ifconfig enp0s3
- \$ ifup enp0s3 (Making the network up)
  or
- \$ systemctl restart network.service (Restart network service)
- \$ ps -ef | grep ssh
- \$ systemctl restart sshd

---

# Change File Creation Permission

- We can change the default file permissions using - umask
- umask is a command to set default permission of any newly created file/directory
- ex- umask u+rw, g+r, o-rwx
- \$ touch test1
- \$ ls -ltr test1
- \$ umask u+rw,g+r,o-rwx (now whenever you create new file/di - this permission would be applied)
- \$ touch test2
- \$ ls -ltr test2
- (NOTE: This changed permission is only applied for current particular session terminal but if we want to retain this permissions then - apply this to - .bashrc file)
  - \$ cd ~
  - \$ ls -a
  - \$ ls .bashrc
  - \$ nano bashrc
  - ( End of line add -> umask u+rw,g+r,o-rwx )

---

# Install Oracle Guest Addition (Tools)

- Provides extra tools which provide better adjustment of screens, mouse tracker can come-out of the VM to host without clicking CTRL button, etc
- Make sure that you are running latest kernel
  - \$ yum update kernel\*
- Install following packages
  - \$ rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
  - (Check ==> https://dl.fedoraproject.org/pub/epel/ )
- Install the following pacakage
  - \$ yum install gcc kernel-devel kernel-headers dkms make bzip2 perl
- Mount VirtualBox Guest Additions
  - \$ Devices -> Insert Guest Addition CD images -> run

---

# Virtualization

- What is not Virtual ?
  - Not physical exisiting
- Virtualization Technology
  - Virtualization is the process of creating a software-based or virtual representation of something, such as virtual applications, ervers, storage and networks
- Companies offereing Virtualization Products
  - VMWare
  - Microsoft = Hyper-V
  - Citrix
  - Redhat
  - Oracle
  - Amazon
  - Google
- Virtualization Terms
  - Hypervisor ==> Host / Virtual Servers
  - Virtual Machine ==> Guest OS / VM
  - Virtualization Manager ==> vCenter, OVM Manager, etc
  - Virtual Desktop
  - P2V ==> Physical to Virtual (VMWare Converter)
  - Snapshot ==> take snapshot/state of virtual machine (kind of backup)
  - clone or cloning ==> VMMachine can be cloned/copied to another VM machine
