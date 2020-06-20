- Interactive Admin acces \$ sudo -i
- To list all the process currently running in process list/task manager \$ ps aux
- To find/Search a word in output command use 'grep' \$ ps aux | grep <word_find>
- To find the history of cmds \$ history
- \$ clear
- Go to Home directory $ cd ~
  Go to Root directory $ cd /
- Absolute path \$ pwd
- To know the username of logged in user \$ whoami
- List all the directories $ ls or $ ls -a
- List all the directories with detail \$ ls -l
- Create directory \$ mkdir <directory_name>
- Create file \$ touch <file_name.ext>
- Remove directory \$ rmdir <directory_name>
- Remove a file \$ rm <file_name>
- Copy file or directory : \$ cp source destination
- Move file or directory : \$ mv source destination
- Open file/directory with editors : \$ vi abc.txt (or) code . (or) code-insiders .
- To give complete admin acess/privliege : \$ sudo chmod +x <directory_name or file_name>
- 1=> Execute, 2 => Write, 4 => Read | 3 privliege : Admin, Group and Public
  $ chmod <'admin' 'group' 'public'> <file_name or directory_name>
 ex- $ chmod 764 test.txt -> Admin has rwx, Group has rw and Public has only r access
- To get/download latest update for packages from remote : \$ sudo apt-get update -> (apt-get is Package Tool Management)
- To Install the download updates \$ sudo apt-get upgrade
- To remove unused packages : \$ sudo apt-get autoremove
- To Un-intall a package : \$ sudo apt-get --purge remove <package_name>
- To Find list of install packages \$ dpkg --list
- To uninstall a package from dpkg packages \$ sudo dpkg --purge <packgae_name>
- To change the privilige to admin of particular command just append with 'sudo'
- Shutdown now : \$ shutdown now
- Reboot \$ sudo reboot
- To know ip4 address : \$ ip -4 address
- Using snap package manager :- \$ snap list (list all the packages installed through snap)
- Remove package from snap : \$ sudo snap remove <package> (ex- sudo snap remove vlc)
- To list all the packages that are installed/uninstalled/etc : \$ sudo dpkg --get-selections
- To list packages that are on hold/not liable for upgrade : \$ sudo dpkg --get-selections | grep "hold"
- To hold a specific package for upgrade : \$ sudo apt-mark hold package_name
- To unhold the above package for upgrade : \$ sudo apt-mark unhold package_name
- To find the list of prcoess whcih are using the memory usage : \$ htop
- To know number of threads, cpu, architecture of your computer : \$ lscpu
- To kill running process : $ ps aux (Get the JobId of the process u want to kill)
										 $ sudo kill <JobId>
- To Enter as Root : sudo su - (Switch user)
- To know which shell I am using in my terminal : echo \$SHELL or echo \$0
- To Change hostname : \$ sudo hostname ubuntu (To change permantely, edit hostname inside '/etc/hsotname' file by login in as admin)
- If you want to run vsocde with super-user privilege : \$ sudo code --user-data-dir="/etc" ("etc" -> absolute file path)
- Switch between users : su --help, \$ su --login guest
- Install .deb file :\$ sudo apt install ./<file_name> (Naviagate to that deb file)
- To open folder with GUI from Terminal: \$ nautilus <path>
- TO check software is installed:
  - \$ sudo dpkg --get-selections | grep rsync (Ubuntu)
  - \$ rpm -qa | grep rsync (Redhat OS- Centos/Fedora)
- To know system architecture:
  - \$ uname -a
  - \$ arch
  - \$ dpkg --print-architecture (OS is 64-bit - amd64 and OS is 32-bit - i386 )
  - \$ getconf LONG_BIT
  - \$ file /sbin/init
- $ echo $? (To check if the previous command run successfully -> 0 = successful, 1 = error)

---

Reference:

- https://www.cyberciti.biz/faq/show-display-get-installed-packages-software-list-linux-freebsd-openbsd/
