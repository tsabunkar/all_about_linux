# User Account Management

- Commands to manage user account
  - useradd
  - groupadd
  - userdel
  - groupdel
  - usermod (modifiy the user)
- Files
  - /etc/passwd
  - /etc/group
  - /etc/shadow
- ex : useradd -g superheros -s /bin/bash -c "user description -m -d /home/spiderman spiderman
  (-g ==> add a group, -s ==> Shell environment, -c ==> to define user decription -m, -d ==> user home directory)

PRACTICE:

- \$ sudo su
- \$ useradd -m spiderman (Create a user called spiderman, -m ==> by creating it in home directory)
- \$ id spiderman (To verifiy the user was created with particular id)
- \$ cd ~ (HOME Directory of logged in user)
- \$ cd / (ROOT Directory)
- \$ cd home
- \$ ls -ltr (List of users avaliable in your system)
- \$ groupadd avengers (Create a new group called avengers)
- \$ cat /etc/group (To verifiy the group was created)
- \$ userdel -r spiderman (delete the user spiderman, and also the directory present inside /home)
- \$ groupdel avengers (delete the group avengers)
- \$ man usermod
  NOTE: \$ useradd -m spiderman [ This will create a user called spiderman and also create a group same as - username i.e- spiderman ]
- \$ usermod -G avengers spiderman (Add spiderman user to avengers group as well)
- \$ grep spiderman /etc/group (To know the which group(s) sipderman belongs to -> avengers group and spiderman group [b'coz bydefault when user is created then it will also create the group with same name and add the user to that group])
- \$ grep tejas /etc/group
- \$ grep guest /etc/group
- \$ grep spiderman /etc/group
- \$ ls -ltr (inside /home)
- \$ chgrp -R avengers spiderman (To change spiderman group from spiderman to avengers, -R ==> To cascade this permission to all the folders)
- \$ ls -ltr
- \$ cat /etc/passwd ( o/p- spiderman:x:1002:1002::/home/spiderman:/bin/sh ==> <username>:<passwrd_encrypted>:<userid>:<groupid>:<empty_description>:<home_direc>:<shell_user_is_using> )
- \$ cat /etc/shadow (Shows the encrypted password)
- \$ grep spiderman /etc/shadow
- \$ useradd -m ironman -g avengers -s /bin/bash -c "Ironman Superhero desc" -d "/home/ironman"
  (-g ==> group name to add the user, -s ==> Shll to use, -c ==> Description for username, -d ==> Specifiying the home directory manually)
- \$ ls -ltr
- \$ passwd ironman (To specifiy the password for user - ironman)

---

# Switch Users and sudo Access

- Commands Syntax
  - su - username
  - sudo command
  - visudo (edits the configuration file of sudoers --> /etc/sudoers)
- \$ ifconfig
- \$ sudo su -l root (To become root)
- \$ sudo su -l <username> (To become other user)
- \$ sudo visudo
- \$ sudo dmidecode
- \$ sudo fdisk -l (Information about ur disk)

---

# Monitor Users

- \$ who (who has logged in)
- \$ last (all the users who have logged in)
- \$ w (who have logged in currently)
- \$ finger [sudo apt install finger]
- \$ id
- $ last | awk '{print \$1}' | sort | uniq
- \$ id <user_name>

---

# Talking to users

- users
- wall (broadcast your message to all users)
- write (message to only particular user)

- How to use wall ->

\$ wall

Please loggoff, this system is coming down for maintance

- How to use write ->

\$ write spiderman

SpiderMan you cannot be Ironma

---
