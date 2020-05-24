# Internet Access to VM

- Open VM
- Select the machine you cannot get internet on
- Click the settings button
- Click the Network
- Switch to Bridge Adaptor in the attached to drop-down menu
- OK
- Start VM

---

# Network Components

- IP (internet protocol):
  - IP address. An Internet Protocol address (IP address) is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication.
  - An IP address serves two main functions: host or network interface identification and location addressing.
- subnet mask:
  - A subnetwork or subnet is a logical subdivision of an IP network.
  - The practice of dividing a network into two or more networks is called subnetting.
- Gateway
  - A gateway is a piece of networking hardware used in telecommunications for telecommunications networks that allows data to flow from one discrete network to another.
- Static vs DHCP
  - When a device is assigned a static IP address, the address does not change.
  - dynamic IP addresses, which are assigned by the network when they connect and change over time.
- Interface (Port)
- Interface MAC
  - media access control address (MAC address) is a unique identifier assigned to a network interface controller (NIC) for use as a network address in communications within a network segment

---

# Network files and commands

- Interface Detection
- Assigning an IP Address
- Interface configuration files
  - /etc/nsswitch.conf (tell the system resolve hostname to ip address)
  - /etc/hosts
  - /etc/sysconfig/network (or) /etc/hostname
  - /etc/sysconfig/network-scripts/ifcfg-<interface_name>
    - cd /etc/sysconfig/network-scripts
  - /etc/resolv.conf (defines dns, resolve ip to hostname and vice-versa)
- Network Commands
  - ping
  - ifconfig (List all the network interfaces)
  - ifup or ifdown (Bring Up or down the network)
  - netstat (list the gateway)
  - tcpdump (Traces of all the transactions going-out and coming-in to your machine)
- \$ ping www.google.com
- \$ ifconfig
- \$ netstat -rnv
- \$ tcpdump -i enp4s0
