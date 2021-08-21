# OS Basic

This chapter discuss some fundamental topics in operating system. __Operating System (OS)__ is a vital component of computer system which provides bridge between hardware and other software. OS is a primary component which has to be installed first prior to other software on the computer.

```
             User
              ^
              |
              V
        User Interface
              ^
              |
              V
    +----------------------++
    |   End user software   |
    | and development tools |
    +-----------------------+
              ^
              |
              V
        +-----------+
        |     OS    |
        +-----------+
              ^
              |
              V
        +----------+
        | Hardware |
        +----------+
```

There are many OS available today. Some of them are for a very niche market such as for IoT (Internet of Things), embedded devices, etc. Most OS known to the most users now basically can be categorized into __desktop OS__ and __server OS__. Note that OS subject is complex in computer science curricula, therefore we will discuss OS layer which is used directly by the users and software developers alike. Some examples of OS are:

1. __Linux__ (with so many distributions)
2. __Microsoft Windows__ OS family
3. __BSD family__ (OpenBSD, NetBSD, FreeBSD, DragonFly BSD, etc)

## Operating System Components

Basically, there are only two components in an OS:

1. Kernel
2. Userland software

### Kernel

Kernel is the __core__ of OS. It is the first software to be loaded when a computer is started after booting process (the process from turning on the computer and doing self check). It is a low level software, without user interface. Its main function is to manage all computer resources - be it the hardware and or software. Many software use kernel to access hardware, in this case kernel provides API (Application Programming Interface) in the form of _system call_. In a more detailed explanation, kernel functions are:

1. Manage computer devices and provides API to be used by other software to access those devices.
2. Manage computer memory
3. Manage resources

### Userland software

On top of kernel, resides __userland software__. This kind of software usually has user interface in any form (text, graphical, web, mobile, etc). Userland software usually can be categorized into three categories:

1. Utilities
2. Application Software
3. Development Tools

__Utilities__ is system software which provides support for OS. For example, in Linux we have _find_ to search for file in directory hierarchy, _grep_ to find string which a match a specific pattern, etc.

__Application Software__ is a kind of software which has specific functionality to help user in doing specific tasks. For example, in Linux we have _LibreOffice_ to create documents for office works (document, spreadsheet, presentation), _mutt_ for e-mail client, _GIMP_ for image manipulation, etc.

__Development Tools__ is system software which is used to develop sofware, be it utilities software and or application software. For example, in Linux we have gcc suite which is a set of development tools (compiler, profiler, debugger) for C/C++ programming language, _VisualStudio Code_ for IDE, _Vim/NeoVim_ for programming editor / text editor, PHP, Rust compiler, _Nim_ compiler, _KDevelop_ for IDE (Integrated Development Environment), etc.

## Understanding Linux and Ubuntu Linux

__Linux__ is name of operating system kernel and was created around 1991 by _Linus Benedict Torvald_. In the beginning, Linux depends on many software from the GNU Project (http://www.gnu.org), therefore many person or organization usually call Linux as ___"GNU/Linux"___ while some people still call it only _"Linux"_. We will not go into detail regarding this name since this could lead to unfinished debate. _Ubuntu Linux_ (http://www.ubuntu.com) is a set of distributions of Linux OS.

Usually, since Linux and its software ecosystem are massively available and they usually licensed as free software, therefore people are free to create a distribution (sometimes also called a distro) which uses any components from free software communities (or maybe some of them can also mix with non-free software). These freedom to create distribution resulting many distribution of Linux OS. Among the oldest distributions which still available today are *RedHat, Debian, Slackware, SuSE*, etc. The main differences between all of those distributions are:

1. __Package and package manager__ (RedHat and SuSE use RPM with different package manager software).
2.  __Init software__, a software which manage services in operating system level.
3.  __Software packages__, usually depends on the goal of the distribution (Kubuntu: KDE for Ubuntu, Kali Linux: security oriented, Fedora: desktop OS, Ubuntu Server: for server related tasks, etc).
4. __Distro specfic tools__, some distros develop their own tools.
5. __Support__, community and / or company.
6. __Community__.
7. __Filesystem__.
8. and maybe still some minor differences.

Currently, as of end of May 2018, Distrowatch (https://www.distrowatch.com) has this statistic:
- Number of all distributions in the database: __888__
- Number of active distributions in the database: __310__
- Number of dormant distributions: __54__
- Number of discontinued distributions: __524__
- Number of distributions on the waiting list: __191__
- Number of distributions waiting for evaluation: __54__

Of all those distributions, in this handbook, we will use __Ubuntu Linux__. Ubuntu Linux is a distribution which was created by _Canonical_, based on Debian (https://www.debian.org/). Its initial release was at 20 October 2004. Ubuntu was created to handle uncertainty of distro release in Debian. As a result, Canonical decides to release its distros every 6 months while the LTS (Long Term Suppor) edition releases occur every two years. Ubuntu has these official flavours of their distros (the URL redirects to the latest release as of May 2018):

1. Kubuntu: https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/Kubuntu
2. Lubuntu: https://lubuntu.me/bionic-released/
3. Ubuntu Budgie: https://ubuntubudgie.org/blog/2018/04/26/18-04-Its-ubuntu-budgie-released
4. Ubuntu Kylin: https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/Ubuntukylin
5. Ubuntu MATE: https://ubuntu-mate.org/blog/ubuntu-mate-bionic-final-release/
6. Ubuntu Studio: https://wikiubuntu.com/BionicBeaver/ReleaseNotes/UbuntuStudio
7. Xubuntu: http://wiki.xubuntu.org/releases/18.04/release-notes

The latest release informastion available at Ubuntu Wiki (https://wikiubuntu.com/). For installation, you may go to Ubuntu Help (https://help.ubuntu.com/). After installation finish and Ubuntu can be booted then turned on into the GUI, at least master Ubuntu from this documentation: https://help.ubuntu.com/Its/ubuntu-help/index.html.

## GUI (Graphical User Interface) and Its Basic Operation

In Linux, GUI is served using __X Window System__ (also known as "X" and "X11"). X11 only provides barebones for GUI processing in Linux. On top of X11, there must be another software which provides better user experience: window manager or desktop environment. _Window Manager_ (abbreviated "wm") only provides infrastructure to handle window. A running program (the GUI one) will usually be placed inside a window. WM is the software to manage windows in X11. Example of WM are _IceWM, Awesome, WindowMaker, AfterStep,_ and many others. For more complete software and GUI experience, people usually use desktop environment (DE). DE provides many software packages which usually needed by users in their desktop computer operation (such as office related tasks, browsing, etc). Every DE usually also comes with WM included. Example of DE software are _GNOME, KDE, LXDE, XFCE, Mate,_ etc.

GUI operations are not difficult since itu depends on visual display and any icon usually represent task. User run application using menu or maybe click an icon. To help in GUI operations, users need to understand its basic operations. This basic operations are available at Ubuntu Desktop Guide (see https://help.ubuntu.com/Its/ubuntu-help/index.html). Users may also use GNOME documentation available elsewhere since Ubuntu uses GNOME for its desktop. Specifically, these guide should be learned and practiced sequentially:

1. Introduction to GNOME (see https://help.ubuntu.com/Its/ubuntu-help/shell-introduction.htmlen). Also see GNOME documentation (see: https://help.gnome.org/).
2. How to login and logout or switch users (see: https://help.ubuntu.com/Its/ubuntu-help/shell-exit.html.en)
3. How to launch a GUI application (see: https://help.ubuntu.com/Its/ubuntu-help/shell-apps-open.html.en)
4. Study help under "Applications and Windows" at https://help.ubuntu.com/Its/ubuntu-help/shell-overview.html.en
5. You may also customize your desktop using help from "Customize your desktop" at
https://help.ubuntu.com/Its/ubuntu-help/shell-overview.html.en
6. As a developer, one need to master shell, so study "GnomeTerminal" which is an application from GNOME to present console / shell (see: https://help.ubuntu.com/community/GnomeTerminal). Also see here: https://help.ubuntu.com/community/UsingTheTerminal.

## CLI (Command Line Interface) and Its Basic Commands

The power of Linux can not be revealed without extensive knowledge about CLI / shell. Therefore, one need to master some important CLI commands. First, developer need to understand how to look for help. In CLI, there are some commands that deal with help:

1. __man__: display manual page of a command. To use this command, developer needs to know name of the command and then precede the command with man: __man ls__ (to display manual page about __ls__). Some command also have __info__ file(s) which can be displayed using __info command-name__ (example: __info ls__).
2. __whatis__: display a short description of a command, for example, whatis __ls__ will display __ls (1) - list directory contents__.
3. __whereis__: display location of the command in file system, __whereis ls__ will display __ls: /usr/bin/ls /usr/share/man/mant1/ls.1p.gz /usr/share/man/man1/Is.1.gz__.
4. __apropos__: search for manual page, example is __apropos tar__ which will display name of manual page which can be displayed using __man__.

CLI and shell command usually reside at __/usr/bin/__ directory. Go see the location and try to display and understand the content of the man page. At the minimium, these should be understood:

1. __Navigating and managing filesystem, files, and directories__: ls, rm, pwd, cd, mkdir, rmdir, touch, cat, less, more, mv, cp, In, chmod, chown, grep, tail, head.
2. __Superuser operation__: sudo, apt, dpkg, useradd, userdel, poweroff, shutdown, su, mount, umount, ip, ifconfig
3. __Utilities__: free, top, df, du, uname, find

### Shell

Shell is a userland software which provides the way to give command to computer using a set of text without mouse click. Shell also provides a quite complete programming language to enable user to manipulate tasks and also automate tasks using a set of programming language constructs. If one compile those constructs into a set of command known by shell to solve a task, then it said that one create a shell script.

There are more than one shell available in (Ubuntu) Linux. _Bash_ comes as the default but of course other software can be used also. Some well known shell implementation:

1. Bash (https://www.gnu.org/software/bash/)
2. tesh (http://www.tcsh.org/)
3. fish (https://fishshell.com/)
4. zsh (https://www.zsh.org/)

We will study shell and shell script in Chapter 2. Bash will be used through out this short guide.