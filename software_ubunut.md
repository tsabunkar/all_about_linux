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
- Reaming Space ~ 119GB ( Uses as : Ext4 file System, Mount : / [ Using as root ==> / ] )  [Primary, Begining of space]

1 TB 
- Complete Space ( Uses as : Ext4 file System, Mount : /home [ Using as home ==> ~ ] )  [Primary, Begining of space]


Device for boot loader installation : Select Device whose partition was selected EFI System > 300MB  

---------------------------------------------------------------------------------------------

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

----------------


sudo npm install -g @angular/cli
$ ng --version
sudo apt install git-all
$ git --version
Reference: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git


sudo apt-get install -y putty
sudo apt install putty-tools


Gogh
-  https://github.com/Mayccoll/Gogh
$ sudo apt-get install dconf-cli uuid-runtime


Java 
https://jdk.java.net/14/  (download openjdk or jdk.java.net [same as openjdk-> supported by oracle])
https://computingforgeeks.com/how-to-install-java-14-on-ubuntu-debian/

- openjdk-14_linux-x64_bin.tar.gz
- Extract :  $ tar xvf openjdk-14_linux-x64_bin.tar.gz
- sudo mv jdk-14 /opt/
- sudo tee /etc/profile.d/jdk14.sh <<EOF
export JAVA_HOME=/opt/jdk-14
export PATH=\$PATH:\$JAVA_HOME/bin
EOF
- source /etc/profile.d/jdk14.sh
- echo $JAVA_HOME
- java -version


Eclipse
https://www.eclipse.org/downloads/download.php?file=/oomph/epp/2020-03/R/eclipse-inst-linux64.tar.gz  (download)
https://websiteforstudents.com/how-to-install-eclipse-oxygen-ide-on-ubuntu-167-04-17-10-18-04/

- tar xfz  eclipse-inst-linux64.tar.gz (extract file)
- eclipse-installer/eclipse-inst  (to run the extracted file)
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
    - sudo chown -R $USER ~/.local/share/applications/eclipse.desktop (giving myself write access)



- sudo apt install chromium-browser



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

---------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------

Speed up your machine for Latest 20.04 -> Install Missing Graphic Drivers
- Software & Updates > Additional Drivers > Installing the proprietary graphics driver


-------------------------------------------------------------------------------

Reference : https://fossbytes.com/things-to-do-after-installing-ubuntu/