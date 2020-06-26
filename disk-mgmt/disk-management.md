# System Run Level

- Main System Run levels
  - 0 Shut down (ot halt ) the system
  - 1 Single-user mode; usually aliased as s or S
  - 6 Reboot the system
- Othe Run level
  - 2 Multiuser mode without networking
  - 3 Multiuser mode with networking
  - 5 Multiuser mode with networking and GUI
- \$ init 0
- \$ init 1
- \$ init 6
- \$ who -r (r -> which run level we are in )

---

# Linux Boot Process

- 6 Steps/Process when you login
  - BIOS (Basic Input/Output System executes MBR) --> trys to find Boot loader to up system
  - MBR (Master Boot Record) --> 512MB memory allocated for GRUB
  - GRUB (Grand Unified Bootloader executes Kernel)
  - Kernel (executes /sbin/inittab (or) /etc/systemd/system/default.target)
  - Init (executes runlevel programs)
  - Runlevel (Runlevel programs are executed from /etc/rc.d/rc\*.d/)
- \$ cd /etc/inittab
- \$ more /etc/init.d

- Boot Sequence changed in CentOS/Fedora/Redhat-7 and above
- Systemd is the new service manager in CentOS/RHEL 7 that manages the boot sequence
- It is backward compatible with SysV init scripts used by previous version of RedHat Linux including RHEL 6
- Every system administrator needs to understand the boot process of an OS in order to troubleshoot effectively
- [./assets/boot-process.png]

---

# Message of the Day

- message of the day file location, user will see when they login in to the linux machine
  - \$ nano /etc/motd (Add the static text)
- Steps to Create customize Message text other than default:
  - Create a new file in /etc/profile.d/motd.sh (copy file content from [./assets/motd.sh])
  - Add desired commands in motd.sh file
  - Modify the /etc/ssh/sshd_config file to edit
    - \$ cp /etc/ssh/sshd_config /etc/ssh/sshd_config.org
    - \$ nano /etc/ssh/sshd_config
    - PrintMotd yes (Modifiy - PrintMotd no)
  - Restart sshd service
    - systemctl restart sshd.service
  - \$ reboot (fedora)
  - \$ ssh -l root 192.168.0.105 (ubutu client)

---

# Storage

- 3 types of storage
  - Local Storage (inside of your computer)
  - SAN (Storage Area Network) [Attach to computer via fiber cable]
  - NAS (network Attached Storage) [Attached to computer via NFS, Ip,etc NOTE: in windows is attached via- Samba]

---

# Disk Partition

- Commands for disk partition
  - df
  - fdisk
- \$ ssh -l root 192.168.0.105
- \$ df
- \$ df -h (human readable)
- \$ fdisk -l

---

# Add disk and Creating Partition

- Purpose of adding disk - Out of space, Additional Apps, etc
- Add disk in VM
  - VirtualBox
  - Select the VM (Make sure it is not running)
  - Settings
  - Storage > Controller
  - (there is + icon) > (select) Hard disk
  - VDI
  - Dynamically allocated
  - File location and size - 2GB > Create
  - Ok
  - (run VM)
  - \$ df - h
  - \$ fdisk -l
  - \$ fdisk /dev/sdb
  - /# help
  - /# n (for new partition)
  - (default)
  - /# w (write the partition table)
  - \$ mkfs.xfs /dev/sdb1 (to make the file system- xfs)
  - \$ mkdir /data
  - \$ mount /dev/sdb1 /data (mounting partition to particular file system)
  - \$ nano /etc/fstab (add entry about this new partition - /dev/sdb1 /data xfs defaults 0 0)
  - \$ unmount /data (To unmount)
  - \$ mount -a ( to mount back)

---

# Logical Volume Management (LVM)

- LVM allows disks to be combined together
- [./assets/lvm.png]

- Add disk and Create LVM partition
- [./assets/lvm-2.png]

- Add and Extend disk using LVM

---

# Add/Extend SWAP Space

- what is swap ?
  - Swap space in linux is used when the amount of physical memory (RAM) is full.
  - if the system needs more memory resources and the RAM is full, inactive pages in memory are moved to the swap space.
  - While swap space can help machines with a small amount of RAM, it should not be considered a replacement for more RAM
  - Swap space is located on hard drives, which have a slower access time than physical m'my
- Recommended swap size = Twice the size of RAM
- Commands :
  - dd
  - mkswap
  - swapon or swapoff
- \$ free -m (how much memeory we have)
- (Increase size of swap)
- \$ sudo su -l root
- \$ dd if=/dev/zero of=/newswap bs=1M count=1024 (takeing the disk parition and allocation to swap area, bs -> byte size, count -> total size of file)
- \$ cd /
- \$ ls -ltr
- \$ chmod go-r newswap or chmod 600 newswap
- \$ mkswap /newswap (Make that newswap file as type - swap)
- \$ swapon /newswap (turn on the swap)
- \$ free -m
- \$ nano /etc/fstab (new line -> /newswap swap swap defaults 0 0)
- (reboot)
- \$ swapoff /newswap (to delete swap area)
- \$ rm /newswap
- \$ free -m

---

# RAID

- RAID (Redundant Array of Independent Disks) - if one disk dies, we can use another disk
- Types of RAID
  - RAID0
  - RAID1
  - RAID5
- [./assets/raid.png]

---

# File System Check

- fsck -> There from Unix Area, xfs_repai command-> repairs xfs file system
- Linux fsck utility is used to check and repair linux filesystems ext2, ext3, ext4, etc
- Linux xfs_repair utility is used to check and repair linux filesystems for xfs filesystem type
- Depending on when was the last time a file system was checked, the system runs the fsck during boot time to check wheather the file system is in consistent state
- System admin could also run it manually when there is a problem with the filesystems
- To make sure to execute the fsck on an unmounted file systems to avoid any data corruption issues
- Force a filesystem check even if its clean using option -> -f
- Attempt to fix detected problems automatically using option -> -y
- The xfs_repair utility is highly scalable and is designed to repair even very large file systems with many inodes efficiently. Unlike other Linux file systems, xfs_repair does not run at boot time
- The following are the possible exit codes for fsck command:
  - 0 : No errors
  - 1 : Filesystem errors corrected
  - 2 : System should be rebooted
  - 4 : Filesystem errors left uncorrected
  - 8 : Operational error
  - 16 : Usage or syntax error
  - 32 : fsck canceled by user request
  - 128 : Shared-library error
- \$ df -h
- $ df -h | awk '{print $1}'
- \$ df -T (Tells the file types)
- \$ fsck /dev/sda1
- \$ xfs_repair /dev/sda1 (Note : you need to unamount the file and then run this command)
- \$ unamount /data (Copy this befor unamounting)
- \$ xfs_repair /dev/sda1
- $ echo $? (To check if the previous command run successfully -> 0 = successful, 1 = error)
- \$ mount /dev/sda1 /data (mounting back)
- \$ df -h

---

# System backup (dd command)

- Many way we can do system backup, one way -> dd command
- 5 diffrent types of backups:
  - System backup (entire image using tools such as acronis, veeam, commvault etc)
  - Application backup (3rd party application backup solution)
  - Database backup (Oracle datagaurd, SQL backup etc)
  - Filesystem backup (tar, gzip directories etc)
  - Disk backup or disk cloning (dd command)
- dd is a command line utility for Unix and Unix-like os whose primary purpose is to convert and copy files
- As a result, dd can be used for tasks such as backing up the boot sector of a hard drive, and obtaining a fixed amount of random data
- To backup or clonw an entire hard disk to another hard disk connected to the same system, execute the dd command as shown:
  - dd if=<source_file> of=<target_file> [Options](sytnax)
  - dd if=/dev/sda of=/dev/sdb (Example) [Copying the entier disk to destn/target]
- To backup/copy the disk partition
  - dd if=/dev/sda1 of=/root/sda1.img (backup file is named as sda1.img)
- Restoring this image file to other machine after copying the .img
  - dd if=/root/sda1.img of=/dev/sdb3
- \$ df -h
- \$ dd if=/dev/sda1 of=/data/boot.img (copying from parition to file system)
- \$ ls -l /data/boot.img
- \$ dd if=/data/boot.img /dev/sda1 (To recovery file system, if something error happend)

---

# NFS (Network File System)

- Sharing files with other computer, It is called NAS
- NFS Stands for Network file system, a file system developed by Sun Microsystems, Inc (Developed by- Solaris Unix OS)
- It is a client/server system that allows users to access files across a network and treat them as if they resided in a local file directory
- For ex- If you were using a computer linked to a second computer via NFS, you could access files on the second computer as if they resided in a directory on the first computer. This is accomplished through the processes of exporting (the process by which an NFS server provided remote clients with access to its files) and mounting (the process by which client map NFS shared filesystem)
- Below example- we will consider the server which will expose the files and client which will consume this file and show this shared direcotry as a mounted disk

## Steps for NFS Server Configuration (Fedora-192.168.0.105)

- \$ ssh -l root 192.168.0.105
- \$ rpm -qa | grep nfs
- Install NFS packages : \$ yum install nfs-utils libnfsidmap
- Once the packages are installed, enable and start NFS Services
  - \$ systemctl enable rpcbind (enable -> to start at boot time)
  - \$ systemctl enable nfs-server
  - \$ systemctl start rpcbind
  - \$ systemctl start nfs-server
  - \$ systemctl start rpc-statd
  - \$ systemctl start nfs-idmapd
- Create NFS share directory and assign permissions
  - \$ cd /
  - \$ mkdir /mypretzels (Creating shared file directory)
  - \$ ll
  - \$ chmod a+rwx /mypretzels
  - \$ cd /mypretzels
  - \$ touch a b c
  - \$ echo "Hello there" > kramerServer
- Modify /etc/exports file to add new shared filesystem
  - \$ cp /etc/exports /etc/exports.org
  - \$ nano /etc/exports
  - (copy the content from [.assets/exports])
- Export the NFS filesystem
  - \$ exportfs -rv (r -> publish everything, v -> verbose)
- Disable firewall in server
  - \$ systemctl status firewalld
  - \$ systemctl stop firewalld

## Steps for NFS Client Configuration (Have another -> Linux Machine to act as client - centos)

- Install NFS packages
  - \$ yum install nfs-utils rpcbind
- Once the packages are installed enable and start rpcbind service
  - \$ systemctl start rpcbind
  - \$ systemctl status rpcbind
- Make sure firewalld or iptables stopped (if running)
  - \$ ps -ef | egrep "firewall|iptable"
  - \$ systemctl stop firewalld
  - \$ systemctl disable firewalld
- Show mount from the NFS server
  - \$ showmount -e <server_ip>
  - \$ showmount -e 192.168.0.105 (Server IP of Fedora) [run in centos/client]
- Create a mount point
  - \$ mkdir /mnt/kramer
- Mount the NFS filesystem
  - \$ mount 192.168.0.105:/mypretzels /mnt/kramer
- Verify mounted filesystem
  - \$ df -h
  - \$ cd /mnt/kramer
  - \$ ls -ltr (you can see- same files which was there in the server now present in client as mounted disk)
  - \$ touch sabunkar (Check in the server this sabunkar file is present)
- To unmount
  - \$ cd /
  - \$ unmount /mnt/kramer

---

# Samba

- Samba is Linux tool or utility that allows sharing for Linux resources such as files and printers to with other operating systems
- It works exactly like - NFS but the difference is NFS Shares within Linux or Unix like system whereas samba shares with other OS (ex- Windows, MAC)
- For ex- computer "A" shares its filesystem with computer "B" using Samba at its end then only computer "B" will see that shared filesystem as if it is mounted as the local filesystem
- SMB v/s CIFS
  - Samba shares its filesystem through a protocol called SMB (Server Message Block) which was invented by IBM
  - Another protocol used to share samba is through CIFS (Common Internet File System) invented by Microsoft and NMB (NetBios Named Server)
  - CIFS became the extension of SMB and now Microsoft has introduced newer version of SMB v2 and v3 that are mostly used in the industry
  - In simple term, most people, when they use either SMB or CIFS are talking about the same excat thing

## Samba Installation and Configration

- Install samba packages
  - \$ Become root user
  - \$ yum install samba samba-client samba-common
- Enable samba to be allowed through firewall (Only if you have firewall running)
  - \$ firewall-cmd --permanent --zone=public --add-service=samba
  - \$ firewall-cmd –reload
- To stop and disable firewall or iptables
  - \$ systemctl stop firewalld
  - \$ systemctl stop iptables
  - \$ systemctl disable firewalld
  - \$ systemctl disable iptables
- Create Samba share directory and assign permissions
  - \$ mkdir -p /samba/morepretzels
  - \$ chmod a+rwx /samba/morepretzels
  - \$ chown -R nobody:nobody /samba
- Also, you need to change the SELinux security context for the samba shared
  directory as follows: (Only if you have SELinux enabled) - \$ chcon -t samba_share_t /samba/morepretzels
- If you want to disable SELinux, follow these instructions

  - \$ sestatus To check the SELinux status)
  - \$ vi /etc/selinux/config

  ```
  Change
  SELINUX=enforcing
  To
  SELINUX=disabled
  ```

- (reboot)
- Modify /etc/samba/smb.conf file to add new shared filesystem (Make sure to
  create a copy of smb.conf file) Delete everything from smb.conf file and add the following parameters

  ```
  [global]
  workgroup = WORKGROUP
  netbios name = centos
  security = user
  map to guest = bad user
  dns proxy = no
  [Anonymous]
  path = /samba/morepretzels
  browsable = yes
  writable = yes
  guest ok = yes
  guest only = yes
  read only = no
  ```

- Verify the setting
  - \$ testparm
- Once the packages are installed, enable and start Samba services

  - \$ systemctl enable smb
  - \$ systemctl enable nmb
  - \$ systemctl start smb
  - \$ systemctl start nmb

- Mount on Windows client
  o Go to start
  o Go to search bar
  o Type \\192.168.1.95

- Mount on Linux client - $ yum -y install cifs-utils samba-client
Create a mount point directory
    - $ mkdir /mnt/sambashare
- Mount the samba share
  - \$ mount -t cifs //192.168.1.95/Anonymous /mnt/sambashare/
  - \$ Entry without password

## Secure Samba Server

- Create a group smbgrp & user larry to access the samba server with proper
  authentication
  - \$ useradd larry
  - $ groupadd smbgrp - $ usermod -a -G smbgrp larry
  - \$ smbpasswd -a larry
    New SMB password: YOUR SAMBA PASS
    Retype new SMB password:
    REPEAT YOUR SAMBA PASS
    Added user larry
- Create a new share, set the permission on the share:
  - \$ mkdir /samba/securepretzels
  - \$ chown -R larry:smbgrp /samba/securepretzels
  - \$ chmod -R 0770 /samba/securepretzels
  - \$ chcon -t samba_share_t /samba/securepretzels
- Edit the configuration file /etc/samba/smb.conf (Create a backup copy first)
  - \$ vi /etc/samba/smb.conf
    Add the following lines
    [Secure]
    path = /samba/securepretzels
    valid users = @smbgrp
    guest ok = no
    writable = yes
    browsable = yes
- Restart the services
  - \$ systemctl restart smb
  - \$ systemctl restart nmb

---

# Difference Between Linux 5, 6, 7 and 8

- CentOS and RHEL are smae, only difference is RHEL is supported by Redhat support team but CentOS is FOSS
