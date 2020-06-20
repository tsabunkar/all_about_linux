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
