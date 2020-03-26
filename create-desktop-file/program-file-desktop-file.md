# Creating Desktop File for Program/Executable File (Runnable file)

- Suppose you have program/executable file (Runnable) file but it doesn't have Desktop file (i.e- Can't find this software application in search)
- \$ cd ~/.local/share/applications
- \$ touch eclipse.desktop (file name with ext .desktop)
- \$ nano eclipse.desktop
- \$ copy + paste the content of eclipse.desktop

---

Source : https://askubuntu.com/questions/695382/how-to-install-eclipse-using-its-installer

---

# For Firefox Developer Edition :

https://medium.com/@js_debugger/how-to-install-firefox-developer-edition-on-ubuntu-1c7f5f2b6883

- Download : https://www.mozilla.org/en-US/firefox/developer/
- \$ cd ~/Downloads
- \$ tar xjf firefox-75.0b8.tar.bz2
- \$ sudo mv ~/Downloads/firefox /opt
- \$ cd /opt
- $ sudo chown -R $USER /opt/firefox
- \$ nano ~/.bashrc
- $ export PATH=/opt/firefox/firefox:$PATH (Copy paste this line inside .bashrc file)
- \$ cd ~/.local/share/applications/
- \$ touch firefoxDeveloperEdition.desktop
- \$ nano firefoxDeveloperEdition.desktop
- Copy + paste the content inside -> '/create-desktop-file/firefoxDeveloperEdition.desktop'
  <!-- - \$ chmod +x firefoxDeveloperEdition.desktop  (not needed)-->
- $ cp -rp ~/.local/share/applications/firefoxDeveloperEdition.desktop /home/$USER/Desktop (Copy paste the icon to Desktop icons)

---
