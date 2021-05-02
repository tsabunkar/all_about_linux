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
