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
- \$ su -l guest
- \$ whoami

## Steps to Install and Configure FTP on the Client server

- These are steps for Client Server/Server-A - (sabunkar)
- \$ su -l root
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
- \$ su -l guest
- \$ cd ~
- \$ ls (you can superman had been copied here)

- NOTE: for GUI you can use Ubuntu inbuilt ftp client -> Nautilus
  - Other Network
  - Connect to Server : ftp://192.168.0.105/ > Connect
  - username : guest, password : <pass_guest>
