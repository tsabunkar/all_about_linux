# Downlaod And Install Debain

- https://cdimage.debian.org/debian-cd/current-live/amd64/bt-hybrid/
- Click > debian-live-10.4.0-amd64-standard.iso.torrent
- (Default setting)
- Device > Network > Network Setting
  - Attached to: Bridge Adapater
  - Name: wlp3s0
  - Promiscuous Mode: Allow All
  - Reboot (your debain)
- (To connect - From host to debain-VM via SSH)
  - (First install SSH at server - debian)
  - \$ systemctl status ssh\* (debain)
  - \$ sudo apt install openssh-server
  - \$ sudo systemctl status ssh (should be active)
  - \$ nano /etc/ssh/sshd_config ( make sure --> PermitRootLogin yes)
  - \$ systemctl restart ssh\*
  - \$ ssh -l root 192.168.0.107 (From host machine - Ubuntu)

---

Ref:
https://phoenixnap.com/kb/how-to-enable-ssh-on-debian
https://wiki.debian.org/SSH
https://superuser.com/questions/539139/putty-password-access-denied

---
