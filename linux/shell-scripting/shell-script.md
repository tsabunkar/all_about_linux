# Shell Scripting

- What is a shell script ?
  - A shell script is an executable file containing multiple shell commands that are executed sequentially. The file can contain:
    - Shell (#!/bin/bash) [NOTE: ! ==> exclamation mark is called bang] (Thus #! refered as : "hash-bang", "she-bang" or "sha-bang")
    - Comments(# comments)
    - Commands (echo, cp, grep, etc)
    - Statements (if, while, for etc)
- Shell scripts should have executable permissions (ex: -rwx r-x r-x)
- Shell scripts has to be called from absolute path (ex: /home/userdir/script.bash)
- It can also be called from current location then ./script.bash

---

# Basic Scripts

- Output to screen using "echo"
- Creating tasks
  - Telling your id, current location, your files/directories, system info
  - Creating files or directories
  - Output to a file ">"
- Filters/text processors through scripts (cut, awk, grep, sort, uniq, wc)
  PRACTICE:
- \$ ifconfig
- \$ pwd
- \$ cd /home/tejas/
- \$ mkdir myscripts
- \$ cd myscripts
- \$ touch output-stream
- \$ nano output-stream
- \$ chmod a+x output-stream (Giving executable permission to this file)
- \$ ./output-stream
- \$ /home/tejas/myscripts/output-stream (Run the executable file by absolute path)
- \$ chmod u+x tasks (Giving permission to user)
