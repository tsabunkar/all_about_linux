List of software to be installed in ubuntu :

- visual studio code
- notepad++
- htop
- chromium browser
- blueman
- gnome-tweak-tool (Dark theme)
- nodejs, npm
- Angular CLI
- Git
- gogh ( Terminal -> Onedark pro theme ), npp (One dark plus theme)
- sudo snap install stickynotes // not recommended
- sudo apt install putty-tools (putty key gen)
- sudo apt-get install -y putty

---

------------------ Parition of Ubuntu SSD and HDD------------------------

120 GB SSD

- 300 MB ( Uses as : EFI System partition )
- 8GB (Swap Area)
- Reaming Space ~ 119GB ( Uses as : Ext4 file System, Mount : / [ Using as root ==> / ] ) [Primary, Begining of space]

1 TB

- Complete Space ( Uses as : Ext4 file System, Mount : /home [ Using as home ==> ~ ] ) [Primary, Begining of space]

Device for boot loader installation : Select Device whose partition was selected EFI System > 300MB

---

sudo apt update && sudo apt upgrade -y

- Install google chrome(download .deb file) : sudo dpkg -i google-chrome-stable_current_amd64.deb
- Install vscode (download .deb file): sudo dpkg -i google-chrome-stable_current_amd64.deb

sudo snap install htop
sudo apt install gnome-tweaks
sudo apt-get install blueman
sudo apt install curl

-----NODEJS & NPM----
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs

$ node -v
$ npm -v

Reference: https://github.com/nodesource/distributions/blob/master/README.md#installation-instructions

----uninstall-----

\$ sudo apt-get remove nodejs
\$ sudo apt-get remove npm

NOTE: Global npm packages are in- /usr/lib/node_modules/ (if you want to delete)

--------NVM-----------
$ sudo apt-get update
$ sudo apt-get install build-essential libssl-dev
$ cd ~
\$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
$ export NVM_DIR="$HOME/.nvm"  
$ [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
$ [ -s "$NVM_DIR/bash_completion" ] && \. "\$NVM_DIR/bash_completion"
\$ nvm --version
\$ nvm install node (install latest node version)
\$ nvm install 12.18.2 (install specific node version)
\$ nvm ls
\$ nvm use v14.5.0
\$ node -v
\$ npm -v
\$ npm i -g typeorm-model-generator
(Each npm/node will have its own global versions of libraries)
(installed in nvm specific node v12.18.2) [i.e- not under -> /usr/lib/node_modules {which is global b/w all npm}][but rather under -> $ cd ~/.nvm]
\$ npm link typeorm-model-generator (Inorder this link this global lib from nvm)
\$ npm config get prefix
\$ npm config set prefix /usr/lib/node_modules/ (If you want to change the global modules path)

Ref-
https://github.com/nvm-sh/nvm
https://medium.com/@nbanzyme/easy-way-to-install-nvm-on-ubuntu-18-04-2cfb19ee5391
https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-16-04
https://stackoverflow.com/questions/5926672/where-does-npm-install-packages#:~:text=If%20you%20want%20to%20change,path%20of%20global%20npm%20modules.

---

sudo npm install -g @angular/cli
$ ng --version
sudo apt install git-all
$ git --version
Reference: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

sudo apt-get install -y putty
sudo apt install putty-tools

Gogh

- https://github.com/Mayccoll/Gogh
  \$ sudo apt-get install dconf-cli uuid-runtime

Java
https://jdk.java.net/14/ (download openjdk or jdk.java.net [same as openjdk-> supported by oracle])
https://computingforgeeks.com/how-to-install-java-14-on-ubuntu-debian/

- openjdk-14_linux-x64_bin.tar.gz
- Extract : \$ tar xvf openjdk-14_linux-x64_bin.tar.gz
- sudo mv jdk-14 /opt/
- sudo tee /etc/profile.d/jdk14.sh <<EOF
  export JAVA_HOME=/opt/jdk-14
  export PATH=\$PATH:\$JAVA_HOME/bin
  EOF
- source /etc/profile.d/jdk14.sh
- echo \$JAVA_HOME
- java -version

Eclipse
https://www.eclipse.org/downloads/download.php?file=/oomph/epp/2020-03/R/eclipse-inst-linux64.tar.gz (download)
https://websiteforstudents.com/how-to-install-eclipse-oxygen-ide-on-ubuntu-167-04-17-10-18-04/

- tar xfz eclipse-inst-linux64.tar.gz (extract file)
- eclipse-installer/eclipse-inst (to run the extracted file)
- Steps to select
  - Eclipse for Enterprise Java Developer
  - Installation folder : /home/tejas/tejas/software
  - Launch
- Choose the workspace director: ~/tejas/workspace/eclipse
- eclipse folder would be created in ~/tejas/software ==> Which we need to map - in order to enable global search eclipse
- Create Eclipse App Launcher
  - cd ~/.local/share/applications/
  - touch eclipse.desktop
  - nano eclipse.desktop
  - Copy file from eclipse.desktop (login as root)
  - sudo chown -R \$USER ~/.local/share/applications/eclipse.desktop (giving myself write access)

* sudo apt install chromium-browser

Download TOR browser
https://www.howtogeek.com/423866/how-to-install-and-use-the-tor-browser-on-linux/

- tar xf tor-browser-linux64-9.0.9_en-US.tar.xz
- ./tor-browser_en-US/Browser/start-tor-browser &

VLC

- sudo snap install vlc

Code-Insider

- sudo dpkg -i code-insiders

ifconfig :
sudo apt install net-tools -y

VirtualBox:

- ubuntu software > VirtualBox

Spotify:

- ubuntu software > Spotify

---

---

Speed up your machine for Latest 20.04 -> Install Missing Graphic Drivers

- Software & Updates > Additional Drivers > Installing the proprietary graphics driver

---

Reference : https://fossbytes.com/things-to-do-after-installing-ubuntu/

https://askubuntu.com/questions/730754/how-do-i-show-the-git-branch-with-colours-in-bash-prompt

---

# Sensor to detect CPU temperature

- https://itsfoss.com/check-laptop-cpu-temperature-ubuntu/
- \$ sudo apt install lm-sensors hddtemp
- \$ sudo sensors-detect
- \$ sensors (Gives temperature details in CLI)
- \$ sudo apt install psensor (Display in top panel)

# Control brightness of External Monitor using CLI

- https://askubuntu.com/questions/974207/control-brightness-on-the-second-monitor
- https://wiki.archlinux.org/title/xrandr
- \$ xrandr -q | grep " connected" (To know the display/monitor name which is connected)
- \$ xrandr --output DP-1 --brightness 1 (Set brightness of monitor name- `DP-1` to 1)
- \$ xrandr --output DP-1 --brightness 0.7 (Set brightness of monitor name- `DP-1` to 0.7)
- \$ xrandr --output DP-1 --auto (Set default settings to external monitor)

## Control brightness of External Monitor using GUI

- https://askubuntu.com/questions/218953/can-i-control-brightness-on-second-monitor
- \$ xrandr -q | grep " connected" (To know the display/monitor name which is connected)
- \$ sudo add-apt-repository ppa:apandada1/brightness-controller
- \$ sudo apt update
- \$ sudo apt install brightness-controller
- Seach for brightness > Primary Brightness : DP-1 > you can use the slider to change brightness settings

## Install Playstore in Ubuntu without genymotion

- https://www.clusterednetworks.com/blog/post/install-google-play-store-anbox
- https://anbox.io/
- https://www.2daygeek.com/anbox-best-android-emulator-for-linux/
- \$ snap install --devmode --beta anbox
- \$ snap refresh --beta --devmode anbox
- \$ sudo apt update && sudo apt upgrade 
- \$ sudo apt install wget curl lzip tar unzip squashfs-tools
- \$ wget https://raw.githubusercontent.com/geeks-r-us/anbox-playstore-installer/master/install-playstore.sh (install playstore for anbox)
- \$ chmod +x install-playstore.sh
- \$ ./install-playstore.sh
- \$ reopen the anobox

## Terminal Vertical spilt using Tmux

- Install Tmux which is default in freeBSD
- https://github.com/tmux/tmux/wiki
- https://danielmiessler.com/study/tmux/ 
- \$ apt install tmux
- \$ tmux new -s session-name (Create a new session)
- \$ tmux detach (detach from session) (ctrl+b, d)
- \$ tmux ls (list of running session)
- \$ tmux attach -t <session-name> (Attaching an existing session)
- \$ tmux kill-session -t <session-name> (Killing an running session)
- Spilt a session into 2 vertical window/pane :
	- Create a session 
	- ctrl+b, "
	- ctrl+b, o (Toggle between the pane/window)

## Installing VSCodium

- FOSS of VSCode: https://vscodium.com/
- \$ wget -qO - https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/-/raw/master/pub.gpg | gpg --dearmor | sudo dd of=/etc/apt/trusted.gpg.d/vscodium.gpg
- \$ echo 'deb https://paulcarroty.gitlab.io/vscodium-deb-rpm-repo/debs/ vscodium main' | sudo tee --append /etc/apt/sources.list.d/vscodium.list
- \$ sudo apt update && sudo apt install codium


## Installing zsh as default CLI rather than bin/bash

- zsh is much enhanced version than bin/bash and much customizable
- Install zsh:
- \$ sudo apt install zsh
- \$ zsh --version
- Now install ohmyzsh which is the package manager for zsh shell (just provides easy configuration of zsh shell)
- \$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
- Restart you are system to make zsh as default terminal
- \$ echo ${SHELL} (should say zsh, rather than /bin/bash)
- for uninstall of oh-my-zsh:
- \$ sudo chmod 777 ~/.oh-my-zsh/tools/uninstall.sh
- \$ ~/.oh-my-zsh/tools/uninstall.sh
- for uninstall of zsh:
- \$ sudo apt-get --purge remove zsh
- \$ sudo apt autoremove

- NOTE: If migrating from bash to zsh, you would get error execute - "node -v" or "tmux ls" or "npm -v" as these 
user-env-variables (or) ${PATH} (or) alias are only defined in ~/.bashrc or ~/.profile (previously called ~/.bash_profile)
 but not in ~/.zshrc
- Add below lines ~/.zshrc file:

```
# If you come from bash you might have to change your $PATH.
export PATH=$HOME/bin:/usr/local/bin:$PATH
#----enable above line for all the ${PATH} variables avaliable in zsh (Tejas)
```
and since you are using NVM for nodejs and npm the env variable should be manually copied from ~/.bashrc file to ~/.zshrc file

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

- SUPER_IMP_NOTE: After every change in the ~/.zshrc file kill all the terminals and restart it to see the effect <Wasted loot of time for the same reason >

- https://askubuntu.com/questions/510709/i-cannot-find-bash-profile-in-ubuntu
- https://stackoverflow.com/questions/18428374/commands-not-found-on-zsh 
