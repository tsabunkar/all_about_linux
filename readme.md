# What is Linux ?

- Linux is OS, like Microsoft has windows, Apple has MACOS
- Linux is an OS which sits in the middle of your hardware and users

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
