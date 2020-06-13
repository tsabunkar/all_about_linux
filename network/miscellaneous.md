# Download File or Apps

- Windows has browser to download a file and App
- In Linux = wget (w --> world wide web, Get from www)
- Example of Linux wget: http://website.com/filename.ext
- \$ yum install putty
- Get the url which you want to download a file/app/etc
- http://www.africau.edu/images/default/sample.pdf (Download sample file)
- \$ cd ~
- \$ mkdir play
- \$ cd play
- \$ wget http://www.africau.edu/images/default/sample.pdf (wget download this sample file in the current directory)

---

# Curl and Ping Commands

- In windows to browse to internet we have chrome browser GUI
- In Linux we don't have GUI so make use of curl
- curl (c --> see url, See we can get to a particular url from our machine)
- To check if server is up/working --use--> ping
- To check if the page(which is running by http/Apache) is up in that server --use--> curl
- curl http://website.com/file
- \$ ping www.facebook.com
- \$ ping www.google.com
- \$ curl -O http://website.com/file (if we want to download a file use --> -O)
- \$ wget -O http://www.africau.edu/images/default/sample.pdf

---

# FTP File Transfer Protocol

- The File Transfer Protocol is standard network protocol used for the transfer of computer files between a client and server on a computer network.
- FTP is built on a client-server model architecture using separate control and data connections between the client and the server.
- Protocol --> Set of rule used by computers to communicate
- Default FTP Port = 21
- Default SSH Port = 22
- Default DNS Port = 53
- To verify FTP protocol we require 2 linux machine
  - Client ==> hostname: sabunkar (ubuntu- workstation)
  - Server ==> hostname: fedora.server (Fedora- server)
- Consider we want to send file from Server-A(sabunkar) - which act as client [As it is transmitter] to Server-B(fedora.server) - which act as remote server [reciever]

## Steps to Install and Configure FTP on the remote server

- These are steps for Remote Server/Server-B - (fedora.server)
- Become root : \$ su
- \$ whoami
- \$ rpm -qa | grep vsftpd (if result empty - not downloaded)
- \$ ping www.google.com (check internet avaliable)
- \$ yum install vsftpd
- \$ cd /etc/vsftpd
- \$ cp -f vsftpd.conf vsftpd.conf.org (before mofifiying - make copy)
- \$ nano /etc/vsftpd/vsftpd.conf

- Inside vsftpd.conf file

  - anonymous_enable=NO (uncomment)
  - ascii_upload_enable=YES (uncomment)
  - ascii_download_enable=YES (uncomment)
  - ftpd_banner=Welcome to blah FTP service. (uncomment)
  - # Local Time
  - use_localtime=YES (Add this line at the end of file)

- \$ systemctl start vsftpd
- \$ systemctl status vsftpd
- \$ systemctl enable vsftpd (This will make sure that vsftpd service will start, whenever system reboot/start everytime)
- \$ systemctl status firewalld
- \$ systemctl stop firewalld (NOT Recommended in PROD env)
- \$ systemctl disable firewalld
- \$ sudo su -l guest
- \$ whoami

## Steps to Install and Configure FTP on the Client server

- These are steps for Client Server/Server-A - (sabunkar)
- \$ sudo su -l root
- Using ftp clients currently avaliable - Nautilus, FillZilla, sudo apt install ftp
- \$ cd ~/tejas/play-linux
- \$ touch superman (we want to send this file to server)
- \$ ftp 192.168.0.105
- username : guest, password : <pass_guest>
- (230 Login successful.)
- ftp> bin (Switching to Binary mode)
- ftp> hash (Hash mark printing on (1024 bytes/hash mark).)
- ftp> put superman (file to txer)
- ftp> bye

- Now goto Server
- \$ sudo su -l guest
- \$ cd ~
- \$ ls (you can superman had been copied here)

- NOTE: for GUI you can use Ubuntu inbuilt ftp client -> Nautilus
  - Other Network
  - Connect to Server : ftp://192.168.0.105/ > Connect
  - username : guest, password : <pass_guest>

---

# SCP - Secure Copy Protocol

- The secure copy protocol helps to transfer computer files securely from a local to a remote host. It is somewhat similar to the FTP but it adds security and authenication.
- Default SCP Port = 22 (same as SSH)
- WHat is the use of SSH ?
  - SSH is typically used to log into a remote machine and execute commands, but it also supports tunneling, forwarding TCP ports and X11 connections; it can transfer files using the associated SSH file transfer (SFTP) or secure copy (SCP) protocols. SSH uses the client-server model.
- Client Machine (ubuntu)
  - \$ sudo su -l tejas
  - \$ cd ~/tejas/play-linux
  - \$ touch mario
  - \$ sudo scp mario 192.168.0.105:/home/guest/ (In your client --> ifconfig enp0s3)
  - (above syntax - scp <srcfile> 192.168.0.105:/<dest_directory>)
  - [If we want to copy file from remote servver to client]
  - \$ rm -f mario
  - \$ sudo scp 192.168.0.105:/home/guest/mario .

---

# rsync - Remote Synchronization

- rsync is a utility for efficiently transferring and synchronizing files within the same computer or to a remote computer by comparing the modification times and size of files.
- rsync is lot faster than ftp or scp
- This utility is mostly used to backup the files and directories from one server to another
- Default rsync Port = 22 (same as SSH protocol)
- Syntax of rsync command : rsync otions <source_path> <destination_path>
- Send the File within the same machine using rsync
  - \$ cd ~/tejas/play-linux
  - \$ rsync --help (Check rsync is avaliable- \$ sudo dpkg --get-selections | grep rsync )
  - \$ tar cvf dump.tar . (Creating the backup of current directory into- tar file )
  - \$ mkdir /tmp/backup (Place where want to store/transfer the above backup)
  - \$ rsync -zvh dump.tar /tmp/backup
- rsync a directory on the local machine
  - \$ cd ~/tejas/play-linux
  - \$ rsync -azvh foo /tmp/backup
- rsync a file to a remote machine/server
  - Goto Remote server (fedora-server) run - ifconfig , ifconfig enp0s3 -> inet 192.168.0.105
  - mkdir /tmp/backup/ (Create a direcotry where you want to store the txed file from src) [In fedora]
  - rsync -avz dump.tar root@192.168.0.105:/tmp/backup/ [In ubuntu]
- rsync a file from remote machine
  - \$ cd ~/tejas/play-linux [In ubuntu]
  - \$ rsync -avzh root@192.168.0.105:/root/anaconda-ks.cfg . [In ubuntu]
  - \$ ll anaconda-ks.cfg

---

# System Updates and Repos

- yum (CentOs/Fedora), apt-get / apt (Linux)
- rpm (Red hat package manager)
- Difference b/w rpm and yum :- rpm is used to install the package which you have already in your loacl machine wherease, yum is used to download the package from internet and then install it as-well. (So rpm is mainly used in env where we don't have internt access)
- \$ yum install ntp
- \$ rpm -qa (all packages installed)
- \$ rpm -qa | wc -l
- \$ rpm -qa | grep bind (DNS package)
- \$ yum install bind
- \$ rpm -ihv <location_of_rpm> (to install the package using rpm)
- \$ rpm -e <package_name> (to remove/uninstall a pakage)
- \$ rpm -e bind (we can also remove/uninstall packages that was install by yum/rpm)
- \$ yum remove bind (same as rpm to remove/uninstall a package from local machine)

---
