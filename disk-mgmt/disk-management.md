# System Run Level

- Main System Run levels
  - 0 Shut down (ot halt ) the system
  - 1 Single-user mode; usually aliased as s or S
  - 6 Reboot the system
- Othe Run level
  - 2 Multiuser mode without networking
  - 3 Multiuser mode with networking
  - 5 Multiuser mode with networking and GUI
- \$ init 0
- \$ init 1
- \$ init 6
- \$ who -r (r -> which run level we are in )

---

# Linux Boot Process

- 6 Steps/Process when you login
  - BIOS (Basic Input/Output System executes MBR) --> trys to find Boot loader to up system
  - MBR (Master Boot Record) --> 512MB memory allocated for GRUB
  - GRUB (Grand Unified Bootloader executes Kernel)
  - Kernel (executes /sbin/inittab (or) /etc/systemd/system/default.target)
  - Init (executes runlevel programs)
  - Runlevel (Runlevel programs are executed from /etc/rc.d/rc\*.d/)
- \$ cd /etc/inittab
- \$ more /etc/init.d

- Boot Sequence changed in CentOS/Fedora/Redhat-7 and above
- Systemd is the new service manager in CentOS/RHEL 7 that manages the boot sequence
- It is backward compatible with SysV init scripts used by previous version of RedHat Linux including RHEL 6
- Every system administrator needs to understand the boot process of an OS in order to troubleshoot effectively
- [./assets/boot-process.png]
