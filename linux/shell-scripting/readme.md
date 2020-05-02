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
