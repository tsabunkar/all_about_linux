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
