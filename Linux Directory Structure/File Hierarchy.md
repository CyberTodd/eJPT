The Linux File Hierarchy Structure or the Filesystem Hierarchy Standard (FHS) defines the directory structure and directory contents in Unix-like operating systems. It is maintained by the Linux Foundation. 

-   In the FHS, all files and directories appear under the root directory /, even if they are stored on different physical or virtual devices.
-   Some of these directories only exist on a particular system if certain subsystems, such as the X Window System, are installed.
-   Most of these directories exist in all UNIX operating systems and are generally used in much the same way; however, the descriptions here are those used specifically for the FHS and are not considered authoritative for platforms other than Linux.

![[Pasted image 20230125175456.png]]

**1. / (Root):** Primary hierarchy root and root directory of the entire file system hierarchy.
-   Every single file and directory starts from the root directory
-   The only root user has the right to write under this directory
-   /root is the root user’s home directory, which is not the same as /

**2. /bin :** Essential command binaries that need to be available in single-user mode; for all users, e.g., cat, ls, cp.   
-   Contains binary executables
-   Common linux commands you need to use in single-user modes are located under this directory.
-   Commands used by all the users of the system are located here e.g. ps, ls, ping, grep, cp

**3. /boot :** Boot loader files, e.g., kernels, initrd.   
-   Kernel initrd, vmlinux, grub files are located under /boot
-   Example: initrd.img-2.6.32-24-generic, vmlinuz-2.6.32-24-generic

**4. /dev :** Essential device files, e.g., /dev/null. 
-   These include terminal devices, usb, or any device attached to the system.
-   Example: /dev/tty1, /dev/usbmon0

**5. /etc :** Host-specific system-wide configuration files.
-   Contains configuration files required by all programs.
-   This also contains startup and shutdown shell scripts used to start/stop individual programs.
-   Example: /etc/resolv.conf, /etc/logrotate.conf.

**6. /home :** Users’ home directories, containing saved files, personal settings, etc.
-   Home directories for all users to store their personal files.
-   example: /home/kishlay, /home/kv

**7. /lib :** Libraries essential for the binaries in /bin/ and /sbin/.
-   Library filenames are either ld* or lib*.so.*
-   Example: ld-2.11.1.so, libncurses.so.5.7