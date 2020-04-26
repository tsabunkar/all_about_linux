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

sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
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



---------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------

Speed up your machine for Latest 20.04 -> Install Missing Graphic Drivers
- Software & Updates > Additional Drivers > Installing the proprietary graphics driver


-------------------------------------------------------------------------------

Reference : https://fossbytes.com/things-to-do-after-installing-ubuntu/