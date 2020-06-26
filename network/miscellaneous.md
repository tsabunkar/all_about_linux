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

# System Upgrade/Patch Management

- 2 types of upgrade
  - Major version upgrade - 5,6,7 (\$ cat /etc/fedora-release <== To check version of fedora)(\$ cat /etc/redhat-release)
  - Minor version upgrade - 7.3, 7.4
- NOTE: we can easily do minor version update but for major version update (LTS) we should take the backup of our file then procceed which is cumbersome
- \$ yum update
- \$ yum upgrade
- \$ sudo apt update (In ubnutu- apt package manager)
- \$ sudo apt upgrade
- Update v/s update : upgrade will delete the old package version and re-install with new package version, wherease update will preserves the old package version and on-top of it install the newer package version

---

# Create local repository from DVD

- If we don't have internet connection, we cannot reach to Redhat remote repository --> so here we can use local repository to install the packages
- Command : createrepo
- \$ su -l root
- \$ mkdir /localrepo
- \$ cd /localrepo
- ---Refer video----

---

# Advance Package Management

- Installing Package
- Upgrading package
- Deleting package
- View package details information
- Identify source or location information
- Package configuration files
- \$ rpm -a | grep ksh (corn shell)
- \$ yum install ksh\* (asteric -> anything related to this package will also be installed)
- \$ yum install ksh
- \$ rpm -qa | grep ksh
- \$ yum remove ksh (Remove the package)
- Download & Install manually
  - \$ wget https://download-ib01.fedoraproject.org/pub/fedora/linux/releases/32/Everything/aarch64/os/Packages/k/ksh-2020.0.0-3.fc32.aarch64.rpm (download manually)
  - \$ rpm -ivh ksh-2020.0.0-3.fc32.aarch64.rpm (Install manually)
- \$ rpm -qi <name_of_package> (View package details information)
- \$ rpm -qi ksh-2020.0.0-3.fc32.aarch64.rpm
- \$ rpm -qa | grep ksh
- \$ rpm -e ksh (Remove of the package)
- \$ rpm -qc ksh (Configuration files related to this- ksh package, which can be modified for custom settings/config)
- \$ which ksh (To know the path of package)
- \$ cd /usr/bin/
- \$ rpm -qf ksh (Tells which package this command belongs to ?)
- \$ which pwd
- \$ rpm -qf pwd (we can know which package pwd command belongs)
- \$ which whoami
- \$ rpm -qf whoami

---

# Rollback Updates and Patches

- Rollback a package or patch
  - yum install <package_name>
  - yum history undo <id>
- Rollback an update
  - Downgrading a system to minor version (ex- RHEL7.1 to RHEL7.0) is not recommended as this might leave the system in undesired or unstable state
  - yum update -> Update will preserve the old version package
  - yum upgrade -> Upgrade will delete oboselete packages
  - yum history undo <id>
- \$ yum install screen (Record screen)
- \$ yum history
- \$ rpm -qa | grep screen
- \$ yum history undo 11 (Id of screen)
- \$ rpm -qa | grep screen (it will be deleted)
- \$ yum update
- \$ yum upgrade

---

# SSH and TELNET

- Accept connection from outside
- Telnet = Un-secured connection between computers
- SSH = Secured
- Two type of packages for most of the services
  - Client package
  - Server package
- [.assets/ssh.png]
- \$ yum install telnet (No need to download)
- \$ ssh localhost (To login to same server :)
- \# logout
- \$ grep sshd (/usr/sbin/sshd -> process which is listening to all the incoming packets)
- \$ systemctl stop sshd ( to stop this service/daemon)
- \$ grep sshd
- \$ systemctl start sshd
- \$ grep sshd

---

# DNS - Domain Name System

- Translate hostname(www.linked.com) to Ip Address(144.2.22.0), Ip Address to hostname and Hostname to Hostname.
- Hotname to Ip Address --called--> A Record
- Ip Address to Hotname --called--> PTR Record
- Hotname to Hotname --called--> CNAME Record
- File to configure DNS
  - /etc/named.conf
  - /var/named/
- Service
  - systemctl restart named (named is a demon/service)
- Setting up DNS to my local IP Address on enp0s3
  - Take snapshot of ur VM
  - \$ ifconfig (enp0s3 --> IP : 192.168.0.105)
  - \$ yum install bind bind-utils (Install DNS package )
  - \$ rpm -qa | grep bind
  - Configure DNS Server
    - \$ cd /etc
    - \$ ll named.conf
    - \$ cp /etc/named.conf ./named.conf.org
    - \$ ll named.con\*
    - \$ nano /etc/named.conf
    - (listen-on port 53 { 127.0.0.1; 192.168.0.105;}; <== Add IP Adress)
    - (Make changes as shown in zone ==> [./config/named.conf])
    - Create Zone files:
      - \$ cd /var/named
      - \$ touch forward.lab (These are the zone files, we keep forward lookup entries that is If want to resolve hostname to Ip go this entry/file )
      - \$ touch reverse.lab (These are the zone files, we keep reverse lookup entries that is If want to resolve Ip to hostname go this entry/file)
      - \$ nano forward.lab
      - (Copy the content from [./config/forward.lab])
      - \$ nano reverse.lab
      - (Copy the content from [./config/reverse.lab])
      - \$ systemctl start named
      - \$ systemctl enable named
      - \$ systemctl stop firewalld (Disable firewalld)
      - \$ systemctl disable firewalld
      - Configuring Permissions, Ownership, and SELinux
        - \$ chgrp named -R /var/named
        - \$ chown -v root:named /etc/named.conf
        - \$ restorecon -rv /var/named
        - \$ restorecon /etc/named.conf
      - Test DNS configuration and zone files for any syntax errors
        - \$ named-checkconf /etc/named.conf
        - \$ named-checkzone lab.local /var/named/forward.lab
        - \$ named-checkzone lab.local /var/named/reverse.lab
      - Add DNS Server Information to network file
        - \$ ifconfig
        - \$ ifconfig enp0s3
        - \$ nano /etc/sysconfig/network-scripts/ifcfg-enp0s3
        - (Add -> DNS=192.168.0.105)
      - Restart network service
        - \$ systemctl restart network [Error: Failed to restart network.service: Unit network.service not found]
        - \$ systemctl restart NetworkManager.service
      - Modify /etc/resolv.conf
        - \$ nano /etc/resolv.conf
        - (Replace your nameserver from - nameserver 192.168.0.1 to ==> nameserver 192.168.0.105)
      - Test DNS server
        - \$ dig masterdns.lab.local (dig/nslookup are same to veirfy the hostname and IP mapping)
        - \$ nslookup masterdns.lab.local (Verify Forward Lookup)
        - \$ nslookup clienta.lab.local
        - \$ nslookup clientb.lab.local
        - \$ nslookup 192.168.1.240 (Verify Reverse Lookup)
        - \$ nslookup 192.168.1.241
- Resotre your VM from the previous Snapshot if you want to remove above configuration.

---

# Hostname/IP Lookup

- Command used for DNS lookup
  - nslookup
  - dig
- These command used to resolve- hostname to IP, IP to hostname , hostname to hostname
- \$ nslookup
- \# www.google.com
- \# exit
- \$ nslookup www.hotmail.com
- \$ dig www.hotmail.com (more details compared to nslookup)

---

# Network Time Protocol (NTP)

- NTP purpose is to synchronize time with another server
- NTP Port : 123
- File : /etc/ntp.conf
- Service: \$ systemctl restart ntpd
- command : ntpd
- \$ rpm -qa | grep ntp
- \$ yum install ntp (if you dont have this ntp package)
- \$ nano /etc/ntp.conf (Add line --> server 8.8.8.8) [This ip is for google]
- \$ systemctl restart ntpd
- \$ systemctl status ntpd
- \$ ps -ef | grep ntp
- \$ ntpq
- \# peers (You can see my local m/c server is getting its time from - dns.google)
- \$ systemctl stop ntpd
- \$ ps -ef | grep ntp

---

# chronyd (New version of NTP)

- chronyd - It is deamon which is to replace NTP daemon
- Purpose of chronyd is for Time synchronization (Sync our local time with that of remote time which can be Redhat/Google servers)
- Package name : chronyd
- Config file : /etc/chronyd.conf
- Log file : /var/log/chrony
- Service : systemctl start chronyd
- Command : chronyc
- \$ sudo su -l root
- \$ rpm -qa | grep chrony
- \$ ll /etc/chrony.conf
- \$ nano /etc/chrony.conf
- ( Add line ==> server 8.8.8.8)
- \$ systemctl status ntpd
- \$ systemctl stop ntpd
- \$ systemctl restart ntpd
- \$ ps -ef | grep ntpd
- \$ chronyc
- \# help
- \$ nano /etc/chrony.conf (remove the changes)
- \$ systemctl restart ntpd

---

# Sendmail

- This service - help to send and recieve emails
- Files :
  - /etc/mail
  - /etc/mail/sendmail.mc
  - /etc/mail/sendmail.cf
- Service :
  - systemctl restart sendmail (It is still the dameon but doesn't have 'd' at end)
- Command : mail -s "subject line" email@domain.com
- \$ rpm -qa | grep sendmail
- \$ yum install sendmail
- \$ yum install sendmail-cf
- \$ cd /etc/mail
- \$ nano /etc/mail/sendmail.mc
- (Modifiy --> dnl define(`SMART_HOST',`smtp.your.provider')dnl)
- \$ systemctl restart sendmail
- \$ systemctl status sendmail
- \$ mail -s "mail setup" tsabunkar@gmail.com [Error : -bash: mail: command not found --> yum -y install mailx]
- (Write mail body) [Ctrl+D] -> quite mail CLI and Send

---

# Web Server (httpd)

- Service or Package name -> httpd
- Files :
  - /etc/http/conf/httpd.conf
  - /var/www/html/index.html (Main page of the web-server will be located inside html directory)
- Service:
  - systemctl restart httpd
  - systemctl enable httpd
- Log files : /var/log/httpd/
- \$ rpm -qa | grep http\*
- \$ yum install httpd
- \$ cd /etc/httpd/conf
- \$ ll
- \$ more httpd.conf
- \$ cd /var/www/html
- \$ touch index.html
- \$ nano index.html (write the code for your web page)
- \$ systemctl restart httpd
- \$ ifconfig
- \$ ifconfig enp0s3 (192.168.0.105)
- (Since your using Bridge Adapter) - http://192.168.0.105/ (in you Ubuntu Browser- Another server)
- [If not work: $ systemctl stop firewalld]

---

# Central Logger (rsyslog)

- Purpose of this server is - to generate logs or collect logs from other servers
- Service/package name : rsyslog
- Configuration file : /etc/rsyslog.conf
- Service
  - systemctl restart rsyslog
  - systemctl enable rsyslog
- \$ rpm -qa | grep rsyslog
- \$ yum install rsyslog (if not there)
- \$ nano /etc/rsyslog.conf
- \$ systemctl restart rsyslog

---

# Linux OS Hardening - (OS Hardening : System Secure)

- User Account
- Remove un-wanted packages
- Stop un-used services
- Check on listening Ports
- Secure SSH confifuration
- Enable firewall (iptables/firewalld) (old version of firewall- iptables, new version of firewall - firewalld ) [Tell the firewall to accept only particular PORT no and filter other traffic]
- Enable SELinux (Security Enhance Linux) --> Control access of service/application
- Change Listening Services Port Numbers
- Keep your Os upto date (updated security patches)
- \$ cat /etc/passwd
- \$ chage -l root (Last password change)
- \$ chage -l guest
- \$ chage --help
- \$ cat /etc/shadow
- \$ cat /etc/login.defs | more
- \$ cd /etc/pam.d
- \$ more system-auth
- \$ rpm -qa (list of all packages)
- \$ rpm -qa | wc -l (total no of packages)
- \$ rpm -e <package_name> (to remove a package)
- \$ systemctl -a (daemon/service is active and inactive)
- \$ netstat -tunlp (all the listening PORT which are active)
- \$ cd /etc/ssh
- \$ more sshd_config (this file can be modified - to make SSH more secure ---tosecure--> Change PORT, PermitRootLogin make this paramter as No)
- \$ firewall-config (open GUI) [sudo apt install firewall-config]
- \$ firewall-cmd --help (CLI Tool)
- \$ more /etc/sysconfig/iptables-config (old version to modifiy firewall)
- \$ more /etc/firewalld/firewalld.conf (new version to modifiy firewall)
- \$ sestatus (To Check SE Linux is enabled)
- \$ cd /etc/sysconfig
- \$ more selinux (To enable/disable SE Linux)
- \$ stat <file_name> (gives status of that file)
- \$ cd ~/play
- \$ stat sample.pdf
- \$ man chcon
- \$ man checkpolicy
- (Keep update the security realted to packages)

---

# OpenLDAP Installation

- What is OpenLDAP
- OpenLDAP Service : slapd
- Start/Stop the service:
  - systemctl start slapd
  - systemctl enable slapd
  - systemctl stop slapd
- Config file : /etc/openldap/slapd.d
- \$ yum install _openldap_
- \$ systemctl start slapd
- \$ systemctl status slapd
- \$ ps -ef | grep slapd
- \$ cd /etc/openldap/slapd.d/
- \$ ls
- \$ more /etc/nsswitch.conf

---

# Trace Network Traffic (traceroute)

- The traceroute command is used in Linux to map the journey that a packet of information undertakes from its source to its destination.
- One use for traceroute is to locate when data loss occurs throughout a network, which could signify a node that's down
- Because each hop in the record reflects a new server or router between the originating PC and the intended target, reviewing the results of a traceroute scan also lets you identify slow points that may adversely affect your network traffic
- Example:
  - \$ traceroute www.google.com (start with your Gateway then goto google ip -> 172.217.26.196)
  - \$ netstat -rnv (To know your gateway)

---

# How to open image file

- We can open a text file - vi, nano, etc
- We can open image using CLI
  - \$ yum install ImageMagick
- Ref : ( https://www.ostechnix.com/how-to-display-images-in-the-terminal/)

---

# Access Remote Server without Password (SSH-Keys)

- Two reasons to access a remote machine without password
  - Reptitive login
  - Automation through scripts
- Keys are generated at user level
  - guest
  - root
- [./assets/ssh-key.png]
- Example: First time employee join a new office he is only allowed to enter the office when he sign the registry at gate/entry level but from next day of office he will provided by ID card so that he should not always sign the registry at gate (this ID card --think---> SSH Keys)
- Steps
- \$ ifconfig (Client m/c - Ubuntu)
- \$ ifconfig wlp3s0 (Ubuntu) [Ipaddr- 192.168.0.106]
- \$ ifconfig (Server m/c - Fedora)
- \$ ifconfig enp0s3 (Fedora) [Ipaddr- 192.168.0.105]
- \$ ssh root@<ip_addr_server> (from client- Ubuntu)
- \$ ssh root@192.168.0.105 (Ubuntu)
- \$ sshkeygen (Client machine - Ubuntu)
- \$ cat /home/tejas/.ssh/id_rsa
- (Now we need to copy this generated public key from client to server)
  - \$ ssh-copy-id root@<ip_addr_server> (Ubuntu)
  - \$ ssh-copy-id root@192.168.0.105 (Ubuntu)
  - \$ ssh root@192.168.0.105 (Ubuntu) [ Now login Again - This time it will not prompt to enter password for every login]
  - \$ ssh -l root 192.168.0.105
  - \$ ssh -l guest 192.168.0.105
- (Optional) Inorder To verify keys are copied correctly from client to server
  - \$ cd /root/.ssh/ (Fedora)
  - \$ ll
  - \$ cat authorized_keys

---

# Firewall

- The Firewalld had multiple zone, to get a list of all zones
  - \$ firewall-cmd --get-zones
  - \$ systemctl restart firewalld.service
  - \$ systemctl status firewalld.service
- To get a list of active zones
  - \$ firewall-cmd --get-active-zones
- To get firewall rules for public zones
  - \$ firewall-cmd --zone=public --list-all
    or
  - \$ firewall-cmd --list-all
- All services are pre-denfined by firewalld. What if you want to add a 3rd party services:
  - \$ ll /usr/lib/firewalld/services/<allservices.xml>
  - \$ nano /usr/lib/firewalld/services/<allservices.xml>
- To add a service(http):
  - \$ firewall-cmd --add-service=http
  - \$ firewall-cmd --list-all (Check in the services: http will be added now)
  - \$ curl 192.168.1.162
- To remove the a service :
  - \$ firewall-cmd --remove-service=http
  - \$ firewall-cmd --list-all
- To reload the firewalld configuration
  - \$ firewall-cmd --reload
- To add or remove a service permanently
  - \$ firewall-cmd --add-service=http --permanent
  - \$ firewall-cmd --remove-service=http --permanent
- To add a service that is not pre-defined by firewalld
  - \$ cd /usr/lib/firewalld/services/
  - \$ cp ssh.xml sap.xml
  - \$ nano sap.xml (copy content of - [.assets/sap.xml])
  - \$ systemctl restart firewalld
  - \$ firewall-cmd --get-services
  - \$ firewall-cmd --get-services | grep sap
  - \$ firewall-cmd --add-service=sap
  - \$ firewall-cmd --list-all (sap service is added)
  - \$ firewall-cmd --remove-service=sap
- To add a port :
  - \$ firewall-cmd --add-port=1110/tcp
  - \$ firewall-cmd --list-all
- To remove a port :
  - \$ firewall-cmd --remove-port=1110/tcp
  - \$ firewall-cmd --list-all
- To reject incoming traffice from an IP address :
  - \$ firewall-cmd --add-rich-rule='rule family="ipv4" source address="192.168.0.25" reject'
- To block and unblock ICMP incoming traffic
  - \$ firewall-cmd --add-icmp-block-inversion (block)
  - \$ firewall-cmd --list-all
  - \$ firewall-cmd --remove-icmp-block-inversion (unblock)
- To block outgoing traffic to a specific website/IP Address
  - \$ host -t a www.facebook.com ( To find the ip address of domain)
  - \$ systemctl restart firewalld
  - \$ ping 31.13.79.35
  - \$ firewall-cmd --direct --add-rule ipv4 filter OUTPUT 0 -d 31.13.79.35 -j DROP
