# Process and Jobs

- Application ~ Services (apps that run on the computer)
- Script- Shell scripts or commands are list of instructions ex: adduser, cd, pwd, etc
- Process- When we run an application, then that app/service generate a process (with process ID - pid) each service is associated with one or more process
- Daemon- Is like a process which keeps running continously until it is interupted.
- Threads- Every process could have multiple threads associated with it (Service --> process1 --> Thread1 (or many))
- Job- is like workorder which run a service or process at a schedule time

---

# Process and Service Commands

- systemctl or service (service commands is replaced by latest commands- systemctl)
- ps (list of process running in the system)
- top (All process running in the system, memory info, cpu inform)
- kill (kills the process by name or id)
- crontab (is used to Schedule the process or services, when we run the crontab which schedule the process --> that become a job)
- at (like crontab but, at is schedule one time basis or adhoc process)

PRACTICE:

- \$ sudo su -l root (need to root)
- \$ systemctl restart ntpd (ntpd- nkt time protocol daemon) [To re-start your ntp process]
- \$ ps -ef (To view all the process running)
- \$ ps -ef | grep ntpd
- \$ systemctl status ntpd
- \$ systemctl stop ntpd (to stop the process)
- \$ ps -ef | grep ntpd
- \$ systemctl enable ntpd (enable the process, when the system start everytime this daemon will be started with it)
- \$ ps -ef | grep rsyslog (rsyslog- process which collect system logs)
- \$ systemctl status rsyslog (o/p- Currently this process is running and Active in green color)
- \$ top (shows realtime all the process which are running in our system -linux env)
- \$ htop (Loves htop which is adding color scheme on top - need to install as external lib)
- \$ systemctl stop ntpd (stops the process)
- \$ kill <process_id> (Kills the process by id)
- \$ ps -ef | more
- \$ htop (Kill the process with is utilizing maximum CPU usage )
- \$ date
- \$ date -s "13 Mar 2018 13:20:00" (To set the data and time manullay)
- \$ crontab -e (to edit the crontab and shedule a new job)
  -> 38 20 asteric 4 asteric echo "This is my first crontab entry" > crontab-entry [38 -> Minute, 20 -> hour, asteric -> day of the month, 4 -> Month, asteric -> day of the week ]
- crontab -l

---

# Cron Jobs

- By default there are 4 different types of cronjobs.
  - Hourly
  - Daily
  - Weekly
  - Monthly
- If you have any task/job to be schedule you can do it 2 ways:
  - Using crontab -e
  - Have a script added inside hourly, daily, weekly and monthly directory ==> /etc/cron. (directory)
- The timing for each for daily, weekly and monthly are set in : /etc/anacrontab
- The timing for each for hourly is set in : /etc/cron.d/0hourly

PRACTICE:

- \$ cd /etc
- \$ ls -l cron.\*
- \$ ls -l | grep cron
- \$ cd cron.daily
- \$ ls (These are scripts which will run daily)
- \$ cd ..
- \$ cd cron.hourly
- \$ ls (These are scripts which will run hourly)
- \$ cat /etc/anacrontab (Specifiy - which date cron.mothly, which time cron.daily, etc.. will run)
- \$ cat /etc/cron.d/0hourly (Specifiy - which time hourly will run) --> I dont have this file

---

# Process Management

- Process running background ==> Ctrl-z, jobs and bg
- Foreground ==> fg
- Run process even after exit ==> nohup process &
  - OR = nohup process > /dev/null 2>&1 &
- Kill a process by name ==> pkill
- Process priority = nice (ex: nice -n 5 process)

NOTE: The niceness scale goes from -20 to 19. The lower the number more priority that
task gets

- process monitoring ==> top
- list process ==> ps

PRACTICE

- \$ sudo su
- \$ sleep 5 (Delay certain program for specific period of time, sleep for 5 seconds)
- \$ sleep 100 (This is another process) [to stop this process --> Ctrl+z note it is not Ctrl+c ]
- \$ jobs (to see all the process)
- \$ bg (To send a particular process to background)
- \$ jobs (Now it shows sleep process is running not stopped)
- \$ ps -ef | grep sleep
- \$ fg (to bring that sleep process from background to foreground) [ To again move this process to background -> Ctrl+z ]
- (How to run a process without effecting the process eventhough Terminal is closed) ==> nohup
- \$ nohup sleep 700 & (Running the process in background, but this process is not attached to a terminal)
- \$ jobs
- \$ nohup sleep 750 > /dev/null 2>&1 & (Send all those warning to null don't show anything in terminal)
- \$ jobs
- \$ nice -n 5 sleep 700 (Tells cpu to give this sleep 700second process with prioirty 5 NOTE : range of priorities [-20, 19])

---

# System Monitoring Commands

- top
- df
- dmesg
- iostat 1
- netstat
- free
- cat /proc/cpuinfo
- cat /proc/meminfo

---

- \$ top
- \$ df (Disk partion information)
- \$ df -h (human readable) [if system crahes, check if the disk is not 100% used]
- \$ man du (documentation to free up your partition space)
- \$ dmesg | more (monitor the system)
- \$ sudo apt install sysstat
- \$ iostat (how we are communicating with peripherial/internal/external devices)
- \$ iostat 1 (Refresh every 1 second)
- \$ netstat (Gateway, rounting information)
- \$ netstat -rnv
- \$ free (display physcial memory and swap space -> is your virtual memory)
- \$ cat /proc/cpuinfo (To know the complete CPU inform)
- \$ cat /proc/meminfo (To know the complete memory inform)

---

# System Logs Monitoring

- NOTE : Log Directory of system ==> /var/log
- boot
- chronyd = NTP
- cron
- maillog
- secure
- messages
- maillog
- secure ==> /var/log/auth.log or /var/log/secure
- messages ==> Renamed to : /var/log/syslog or /var/log/messages
- httpd

- \$ cd /var/log
- \$ ll | more
- \$ ll boot.log
- \$ more boot.log (only root has read access)
- \$ sudo su -l root
- \$ cd /var/log
- \$ ll boot.log
- \$ more boot.log (Contains log information about bot)
- \$ ll auth.log (present inside /var/log)
- \$ more auth.log (store authentication logs, including both successful and failed logins and authentication methods)
- \$ ll syslog
- \$ more syslog (general messages, as well as system-related information. Essentially, this log stores all activity data across the global system. FIrst thing need to check if system carshes)
- \$ cat syslog | wc -l (number of lines in this syslog file)
- \$ grep -i error syslog (shows all the content which has keyword as error)

---

# System Maintance Commands

- shutdown
- init 0-6
  - 0 Halt the system
  - 1 Single user mode
  - 2 Multiuser mode without networking
  - 3 Multiuser mode with networking
  - 4 Not used
  - 5 Multiuser with networking and X windows
  - 6 Reboot the system
- reboot
- halt (shutdown the computer forceful, any process are running will be terminate abruptly)

- \$ man shutdown
- \$ man init
- \$ man reboot (restart your command)
- \$ man halt

---

# Changing System Hostname

- hostnamectl set-hostname <newhostname>
- Version 7 => Edit /etc/hostname
- Version 6 => Edit /etc/sysconfig/network

- \$ hostname
- \$ cat /etc/hostname (file which has hostname information)
- \$ hostnamectl set-hostname ubuntu
- \$ init 6 (reboot) [inorder to reflect the above hostname modified]

---

# Finding System Information

- \$ hostname
- \$ whoami
- \$ cat /etc/redhat-release (Redhat OS-> like: CentOS)
- \$ uname -a
- \$ sudo dmidecode
- \$ sudo dmidecode | more

---

# System Architecture

- Difference types of system architecture are: 32bit and 64bit CPU
- A big difference b/w 32bit and 65bit processors is the number of calculations per second they can perform, which affects the speed at which they can complete tasks. 64bit processors can come in dual core, quad core, six cores, eight cores, soon..
- Multiple cores allow for an increased number of calculation per second that can be performed, which can increase the processing power and help make a computer run faster.
- Software programs that require many calculations to function smoothly can operate faster and more efficient on the multi-core 64bit processors.
- you can run 32bit applications in 64bit application but vice-versa is not possible.

- \$ arch (Gives the architecture) ==> [x86_64 => 64 bit arch]
- \$ uname -a

---

# Terminal Control Keys

- Several key combinations on your keyboard usually have a specified effect on the terminal.
- CTRL+u (Earse everything you have typed)
- CTRL+c (Stop/kill a command/process running)
- CTRL+z (Suspend a command/process)
- CTRL+d (exit from an interactive program)
- CTRL+ALT+T (Open new terminal)
- CTRL+SHIFT+T (Open new window in same terminal)
- ALT+Number1/2 (Shift between windows)
- CTRL+SHIFT+C (Copy content from terminal)
- SHIFT+Insert (Paste the content into the terminal)

---

# Terminal Commands

- clear (Clear your screen)
- exit (Exit out of the shell, terminal or a user session)
- script (The script command stores terminal activities in a log file that can be named by a user, when a name is not provided by a user, the default file name, typescript is used)

- \$ clear
- \$ exit
- \$ cd ~/tejas/play-linux/
- \$ script logfileactivity.log (All your commands running will be logged in this file which is stored inside play-linux directory)
- \$ ls -ltr
- \$ history
- \$ pwd
- \$ whoami
- \$ cat logfileactivity.log | more
- \$ exit (To exit this recording of scripts) o/p- [Script done, file is logfileactivity.log]

---
