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
- sudo snap install stickynotes
- sudo apt install putty-tools (putty key gen)

---

------------------ Parition of Ubuntu SSD and HDD------------------------

120 GB SSD

- 300 MB ( Uses as : EFI System partition )
- Reaming Space ( Uses as : Ext4 file System, Mount : / [ Using as root ==> / ] )

1 TB

- Complete Space ( Uses as : Ext4 file System, Mount : /home [ Using as home ==> ~ ] )

Device for boot loader installation : Select Device whose partition was selected EFI System > 300MB

---

# Download and install nodejs in linux :

sudo apt-get install curl
curl -sL https://deb.nodesource.com/setup_12.14.0 | sudo -E bash -
sudo apt-get install nodejs
