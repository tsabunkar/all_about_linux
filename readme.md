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
