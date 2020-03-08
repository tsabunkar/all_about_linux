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