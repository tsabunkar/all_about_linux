# Downlaod And Install CentOS-8

- http://isoredirect.centos.org/centos/8/isos/x86_64/
- Network > Ethernet (enp0s3) : ON (While installation) and apply - local.domain
- Installation Destination >
  - Storage Configuration
  - Done
  - Manual Partitioning
    - New CentOS linux 8 Installation : LVM
    - CentOS Linux 8.2.2004 for x86_64
      - / 6.2 GB
        - Mount Point : /
        - File System : ext4
        - Check - Reformat (select Reformat, It wil move from this tab to above New Centos Linux 8 Installation tab)
      - /boot 1024 MiB
        - Mount Point : /boot
        - File System : ext4
        - Check - Reformat
      - swap 820 MiB
        - Mount Point (blank)
        - File System : swap
        - Check - Reformat
    - Done
- Software Selection > (select) Server > Additional S/w (select) Basic Web Server
- Reboot
- NOTE: Once installation is completed please change the path of ISO Image from which it was installed of (or) else boot loader will always show the Installation Screen from Live-CD --> Bascially Path show be in-accessible
