# Linux Kernel

- What is kernel ?
  - Kernel is a program which is stored inside operating system
  - Act as an interface between hardware and software
  - kernel basically takes the command from shell
- Check the diagram assets/linux-kernel

---

# Shell

- What is Shell ?
  - Its GUI (in windows), bash (in linux) , csh
  - Its like a container
  - Interface between users and kernel/OS
  - Terminals/CLI is a cheel
- Find your shell
  - Which shell are u using : $ echo $0
  - Avaliable Shells \$ cat /etc/shells
  - Your Shell is inside : \$ cat /etc/passwd
- Windows GUI is a shell
- Linux KDE GUI is a shell
- Linux sh, bash etc is a shell
- Linux GNOME Shell (Graphical environment)
- Different types of Linux Shells
  - Gnome (Desktop GUI environment)
  - KDE (Desktop GUI environment)
  - sh [bourne shell] (CLI environment) ==> developed by Stephen R. Bourne
  - bash [Bourne again shell] (CLI environment) [enahanced version of sh]
  - csh and tcsh [Shell] (CLI environment)
  - ksh (korn shell) [used in solaris os] ==> developed by David korn

---

# Input/Output in Scripts

- Create script to take input from the user
  - read
  - echo

---

# if-then scripts

- 'If' I win the lottery 'then' I will buy a house
- 'If' I get off early from work 'then' we can go to a concert

---

# Comparisons:

-eq --> equal to for numbers
== --> equal to for letters
-ne --> not equal to
!== --> not equal to for letters
-lt --> less than
-le --> less than or equal to
-gt --> greater than
-ge --> greater than or equal to

---

# File Operation

-e --> files exists
-s --> file exists and is not empty
-f --> file exists and is not a directory
-d --> directory exists
-x --> file is executable
-w --> file is writable
-r --> file is readable

---

# Loops

## for loop

- running until specified number of variables ex: variable = 10 then run the script 10 times or variable = green, blue, red (then run the script 3 times for each color)

## do-while loop

- The while statement continually executes a block of statements while a particular condition is true or met
  - ex : Run a script untill 2pm

---

# CASE Statement Scripts

- If option a selected = do this
- If option b selected = do that ... etc

---

# Check servers connectivity

- A script to check the status of remote host
- check files: check-all-ip, hosts, check-server

---

# Aliases

- Aliases is a very popular command that is used to cut down on lengthy and reptitive commands
- \$ alias l="ls -al"
- \$ l (This is alias name for above command)
- \$ alias pl="pwd; ls"
- \$ alias tell="whoami; hostname; pwd"
- \$ alias dir="ls -l | grep ^d" (grep anything which start with d --> To list all directories)
- \$ dir
- $ df -h | awk '{print $6}' | cut -c1-4 (list 6th column and substring to 4 characters)
- $ alias d="df -h | awk '{print \$6}' | cut -c1-4 "
- \$ alias (To list all the alias which was created)
- \$ unalias <alias_name_created> (It will remove the alias name which was created)
- \$ unalias l

---

# Creating User or Gloabl Aliases

- User = Applies only to a specific user profile
- Gloab = Applies to everyone who has account on the system
- User = /home/user/.bashrc (Local aliases)
- Global = /etc/bash.bashrc (global aliases)
- \$ hh
- \$ alias hh="hostname"
- \$ alias
  NOTE: Above alias is only present in current terminal session

- NOW if I want to make this alias name to my user account then (local Aliases)
- \$ nano /home/tejas/.bashrc
  Write your aliases
  #---Personal Aliases (start)---
  alias hh="hostname"
  #---Personal Aliases (end)---

- NOW if I want to make this alias name to my all user account then (Global Aliases)
- \$ sudo nano /etc/bash.bashrc
  Write your aliases
  #---Personal Aliases (start)---
  alias whereami="pwd"
  #---Personal Aliases (end)---

REF: https://askubuntu.com/questions/610052/how-can-i-preset-aliases-for-all-users

---

# Shell History

- \$ history (number of all commands you have ran uptill now from day1)
- \$ history | more
- \$ !<history_command_line_number> (You can run the command which you ran in past by rembering the number)
- \$ !1005
- \$ history | grep awk (find all the instance of awk)
- \$ history | grep chmod
- \$ cat /home/tejas/.bash_history
- NOTE:
  - The file where history of your shell commands saved => /home/tejas/.bash_history
  - To view other users history of shell commands
    - Become root (su -)
    - cat /home/tejas/.bash_history
