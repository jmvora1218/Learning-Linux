# Introduction

* Learning on RHEL7 - Kernel 3.10

* **Operating System:** Interface between harware and usrs. And  Installing and Launching Apps.


* **Two types of OS :**
  1. Server -> With more features, provides servicies to client.
  2. Client -> Less features, accessing servicies of server.


* **Linux :**
  *  Free
  *  GPL License
  *  Highly secure
  *  Used in Desktops, Mainframes
  *  GUI and CLI
  *  RedHat, Ubuntu (Same as Windows!), Gentoo, Mint, LiveWire, CentOS.


* **Windows :**
	*  Proprietory, Not Free
	*  Mainly GUI and less cmd-line
	*  Prone to viruses
	*  Not for super computers and mainframes
	*  Basically Client OS


* **Unix :**
	*  Proprietory, Not Free
	*  Highly Secure
	*  GUI and CLI
	*  Mainly used in mainframes, not mainly for desktop
	*  Solaris by oracle (runs on Sparc and x86), [AIX by IBM, HP-Unix by HP ] -> Runs on their own customized H/W.

<br>
* **History of Linux**
	*  Unix is Mother of Linux, developed by Bell Labs, Licensed and Non-Free
	*  In 1963, Richard Stallman developed a Unix-Like OS and Programmers all over the world developed Apps
	*  In 1991, Linus Torvalds (	*  Using Minix) student of Helsenki developed Linux Kernel (v 0.1) was student of Tanenbaum.
	*  GNU (GNU is Not Unix) contributed utilities called gnu-utils and this utils along with Kernel became LINUX OS.


* **Kernel:**
	*  (Hardware) |<- Kernel ->| (Shell,Apps)


* **File System Hirearchy in Linux :**
	* Each file has a address also the unique identification called the INODE number
	* The Inode number is stored in INODE table.
	*  Everything is a file <- Linux Principle
	*  Regular file, character file, blocked file, linked file, symbolic link, dir file
	*  Divide HDD into partitions and each partition is mounted into Dirs and accessed

| DIR | Description     |
| :------------- | :------------- |
| /       | The main root partition of  the system     |
| /root       | Home Dir of Root User       |
| /home       | Home dir of any user      |
| /boot       | Files required to boot the system      |
| /run | It's recreated every reboot only for running processes |
| /var | dir contains dynamic files, Untouched files are deleted every 10 days automatically and persist accross reboots |
| /usr | installed softwares and libraries (libs are special softwares require to run other softwares )|
| /dev | It contain device files. Any attached h/w in systems are shown here |
| /tmp | Contains temp files, if untouched are automatically deleted every 30 days |
| /opt | Contains 3rd Party software not related to Linux |
| /usr/sbin | Administrator related commands |
| /usr/bin | User related Commands |

* **Example say :** there is a file 'grub.conf' in /boot then you can directly access file from anywhere using absolute path "/boot/grub.conf" or if you have cd into /boot ,you can access it directly by "./grub.conf" or "grub.conf". cat is used to view a txt file.
