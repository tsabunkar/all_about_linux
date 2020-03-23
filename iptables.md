# To block specific website using iptables

- \$ iptables --list
- \$ iptables --help
- $ echo ${USERNAME}
- \$ id (To know the userId of user, 'tejas' uid =1000, 'root' uid=0)

- \$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -p tcp -d www.youtube.com --dport 80 -j DROP
- \$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -p tcp -d www.youtube.com --dport 443 -j DROP
- \$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -p tcp -d www.hotstar.com --dport 80 -j DROP
- \$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -p tcp -d www.hotstar.com --dport 443 -j DROP
- \$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -p tcp -d www.jiocinema.com --dport 80 -j DROP
- \$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -p tcp -d www.jiocinema.com --dport 443 -j DROP
- \$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -p tcp -d www.voot.com --dport 80 -j DROP
- \$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -p tcp -d www.voot.com --dport 443 -j DROP

- \$ sudo iptables --list
- (Now verifiy browsing to youtube both in -> user='tejas' and user='guest')
- \$ (Permantely persist this rules on OUTPUT table) --> Follow below section

- \$ iptables --flush OUTPUT (To delete all the iptables OUTPUT rules)

---

- Reference :
  - https://linuxhandbook.com/uid-linux/
  - https://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html
  - https://www.2daygeek.com/linux-etc-hosts-file-block-certain-website-access-on-linux/
  - https://broexperts.com/block-facebook-twitter-and-youtubes-https-traffic-in-squid-transparent-mode/

---

# How to presist iptables rules on every restart of computer

\$ sudo apt install iptables-persistent netfilter-persistent

(It will tell you that, your iptables rules will be presisted -> /etc/iptables/rules.v6.)

$ sudo netfilter-persistent save
$ sudo netfilter-persistent start

\$ sudo su --login root

~# iptables-save > /etc/iptables/rules.v4
~# ip6tables-save > /etc/iptables/rules.v6

~# iptables-restore < /etc/iptables/rules.v4
~# ip6tables-restore < /etc/iptables/rules.v6

~# systemctl stop netfilter-persistent
~# systemctl start netfilter-persistent
~# systemctl restart netfilter-persistent

---

Above solution will work partially bcoz, youtube is keep on adding the new servers with different ipaddress, so when we browse www.youtube.com our browser will find some or other ipaddress after pre-long loading
Soo better use '/etc/hosts' file to block this url

---

Was not able to connect to google.meet , google hangout and google dirve

- This was bcoz of the above iptables rules set so : Fluhed all policies and rules
- iptables -P INPUT ACCEPT
- iptables -P OUTPUT ACCEPT
- iptables -P FORWARD ACCEPT
- iptables -F

- Then execute above commands to persist this rule permantely
