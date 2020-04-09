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
