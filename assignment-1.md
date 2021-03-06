# Linux Kernel Assignment:
## Problem #1     
## Block System call: (still looking for answers)
#### (a) block system call for date command 
```
```
#### (b) block system call for Firefox as well
```
```
## Problem #2  
## Play with Directory:
#### (a) create a directory without name from command line
```
[chinmayjain@localhost ~]$ mkdir $'\n' # tried with space first, which was wrong; still not correct way, I think
```
![ls](https://github.com/CRJain/reboot-2.0/blob/master/image.png)
#### (b) create a directory with name "-okgoogle"
```
[chinmayjain@localhost ~]$ mkdir ./-okgoogle
[chinmayjain@localhost ~]$ ls
Desktop    Downloads  -okgoogle  Public     Videos
Documents  Music      Pictures   Templates
```
Or
```
[chinmayjain@localhost ~]$ mkdir -- -okgoogle
[chinmayjain@localhost ~]$ ls
Desktop    Downloads  -okgoogle  Public     Videos
Documents  Music      Pictures   Templates
```
Source:
> https://www.tecmint.com/manage-linux-filenames-with-special-characters/
## Problem #3
## Create a Directory Structure:
![Question](https://1.bp.blogspot.com/-x6vLWgVIU7Q/XvjlJyKJsnI/AAAAAAAAU0M/lmH8ddGkm90gXPNwUZCUvwCTN6XfJINZgCLcBGAsYHQ/s320/Screenshot%2B2020-06-29%2Bat%2B12.12.55%2BAM.png)
```
[chinmayjain@localhost ~]$ mkdir -p A/{B/{G/K,H/J},C/{I/J,J/L},D/{E/M,F/L}}/Reboot.txt
[chinmayjain@localhost ~]$ tree A
A
├── B
│   ├── G
│   │   └── K
│   │       └── Reboot.txt
│   └── H
│       └── J
│           └── Reboot.txt
├── C
│   ├── I
│   │   └── J
│   │       └── Reboot.txt
│   └── J
│       └── L
│           └── Reboot.txt
└── D
    ├── E
    │   └── M
    │       └── Reboot.txt
    └── F
        └── L
            └── Reboot.txt

21 directories, 0 files
```
## Problem #4
#### (a) create two users named Jack and Jill from command line
```
[chinmayjain@localhost ~]$ sudo adduser Jack
[chinmayjain@localhost ~]$ sudo passwd Jack 
Changing password for user Jack.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
passwd: all authentication tokens updated successfully.

[chinmayjain@localhost ~]$ sudo adduser Jill
[chinmayjain@localhost ~]$ sudo passwd Jill
Changing password for user Jill.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
passwd: all authentication tokens updated successfully.
```
#### (b) login with Jack user and create a file name Jack.txt using vim editor and write "Hello Jack"
```
[chinmayjain@localhost ~]$ su - Jack
Password:
[Jack@localhost ~]$ vim Jack.txt
Hello Jack
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
:wq
[Jack@localhost ~]$ cat Jack.txt 
Hello Jack
```
#### (c) from Jack user also create two directories named Jack1 & Jack2
```
[Jack@localhost ~]$ mkdir Jack1 Jack2
[Jack@localhost ~]$ ls
Jack1  Jack2  Jack.txt
```
#### (d) now login from Jill user and create a file Jill.txt using vim editor and write "Hello Jill"
```
[Jack@localhost ~]$ su - Jill
Password: 
[Jill@localhost ~]$ vim Jill.txt
Hello Jill
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                                                                        :wq
[Jill@localhost ~]$ cat Jill.txt 
Hello Jill
```
#### (e) from Jill user also create two directoires named Jill1 & Jill2
```
[Jill@localhost ~]$ mkdir Jill1 Jill2
[Jill@localhost ~]$ ls
Jill1  Jill2  Jill.txt
```
#### (f) swap these files and directories in between users (don't use root account)
```
[Jill@localhost ~]$ su - Jack 
Password:
[Jack@localhost ~]$ chmod 777 -R /home/Jack/
[Jack@localhost ~]$ ls -l
total 12
drwxrwxrwx. 2 Jack Jack 4096 Jul  3 12:31 Jack1
drwxrwxrwx. 2 Jack Jack 4096 Jul  3 12:31 Jack2
-rwxrwxrwx. 1 Jack Jack   11 Jul  3 12:31 Jack.txt

[Jack@localhost ~]$ su - Jill
Password:
[Jill@localhost ~]$ chmod 777 -R /home/Jill/
[Jill@localhost ~]$ ls -l
total 12
drwxrwxrwx. 2 Jill Jill 4096 Jul  3 12:34 Jill1
drwxrwxrwx. 2 Jill Jill 4096 Jul  3 12:34 Jill2
-rwxrwxrwx. 1 Jill Jill   11 Jul  3 12:53 Jill.txt

[Jill@localhost ~]$ mv /home/Jack/Jack1 /home/Jill/
[Jill@localhost ~]$ mv /home/Jack/Jack2 /home/Jill/
[Jill@localhost ~]$ mv /home/Jack/Jack.txt /home/Jill/
[Jill@localhost ~]$ ls
Jack1  Jack2  Jack.txt  Jill1  Jill2  Jill.txt

[Jill@localhost ~]$ su - Jack 
Password: 
[Jack@localhost ~]$ mv /home/Jill/Jill1 /home/Jack/
[Jack@localhost ~]$ mv /home/Jill/Jill2 /home/Jack/
[Jack@localhost ~]$ mv /home/Jill/Jill.txt /home/Jack/
[Jack@localhost ~]$ ls
Jill1  Jill2  Jill.txt
[Jack@localhost ~]$ ls /home/Jill
Jack1  Jack2  Jack.txt
```
Source:
> https://www.guru99.com/file-permissions.html
## Problem #5
## Play with Files and Directories:
#### (a) create 4 files named abc.txt ok fine g.txt under /tmp directory
```
[chinmayjain@localhost ~]$ touch /tmp/{abc.txt,ok,fine,g.txt}
[chinmayjain@localhost ~]$ ls /tmp/
abc.txt
fine
g.txt
ok
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-chronyd.service-pi1fXe
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-colord.service-TSmSmj
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-dbus-broker.service-E9s2Tf
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-earlyoom.service-6JuKtj
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-fwupd.service-S3XeTg
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-geoclue.service-3ua6ph
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-ModemManager.service-N8j1Ff
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-rtkit-daemon.service-Rn0zwg
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-switcheroo-control.service-kqDmfh
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-systemd-logind.service-mtcQQf
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-upower.service-8rbO1f
tracker-extract-files.1000
```
#### (b) create 3 directories aa aaa aaaa under /tmp directory
```
[chinmayjain@localhost ~]$ mkdir /tmp/{aa,aaa,aaaa}
[chinmayjain@localhost ~]$ ls /tmp/
aa
aaa
aaaa
abc.txt
fine
g.txt
ok
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-chronyd.service-pi1fXe
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-colord.service-TSmSmj
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-dbus-broker.service-E9s2Tf
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-earlyoom.service-6JuKtj
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-fwupd.service-S3XeTg
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-geoclue.service-3ua6ph
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-ModemManager.service-N8j1Ff
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-rtkit-daemon.service-Rn0zwg
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-switcheroo-control.service-kqDmfh
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-systemd-logind.service-mtcQQf
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-upower.service-8rbO1f
tracker-extract-files.1000
```
#### (c) give ls command to list the content of /tmp directory [make sure it will only list the content (file|directory)  having 2 char in their name]
```
[chinmayjain@localhost ~]$ ls --hide='???*' /tmp
aa  ok
```
Sources:
> https://www.cyberciti.biz/faq/how-to-delete-files-containing-character-numberdigit/
> https://www.computerhope.com/unix/uls.htm
## Problem #6
## Run command without any output:
#### open terminal and type any command, once you press enter your output of given command must not print [you are not allowed to redirect output anywhere]
```
[chinmayjain@localhost ~]$ bash -D
bash-5.0$ date
bash-5.0$ cal
bash-5.0$ $"Hello World" # A list of all double-quoted strings preceded by $ is printed on the standard output.
"Hello World"
```
Source:
> https://www.tutorialspoint.com/unix_commands/bash.htm
## Problem #7
## Create a shell script:
#### (a) create a shell script named /root/delvex.sh
```
[root@localhost ~]# nano /root/delvex.sh
```
#### (b) make sure it will run /bin/sh shell
```
[root@localhost ~]# cat /root/delvex.sh 
#!/bin/sh
```
#### (c) a user will be running this script by using a command named "opensource"
```
[root@localhost ~]# nano /usr/bin/opensource
  GNU nano 4.9.3                        /usr/bin/opensource                                   
#!/bin/bash
/root/delvex.sh $1





                                       [ Read 2 lines ]
^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos
^X Exit        ^R Read File   ^\ Replace     ^U Paste Text  ^T To Spell    ^_ Go To Line
[root@localhost ~]# chmod +x /root/delvex.sh
[root@localhost ~]# chmod +x /usr/bin/opensource
```
> delvex.sh
```
[root@localhost ~]# cat /root/delvex.sh 
#!/bin/sh
if [ $# -gt 0 ]
then
	if [ $1 == "time" ]
	then
		echo "Current Time: `date +%T`"
	elif [ $1 == "user" ]
	then
		echo "Users: `users`"
	elif [ $1 == "windows" ]
	then
		echo "Shutting down system... "
		sleep 2
		shutdown now
	elif [ $1 -eq 100 ]
	then
		c=$1
		while [ $c != 0 ]
		do
			echo "$c Hello Delvex"
			sleep 1
			c=$(($c-1))
		done
	fi
else
	echo "Name of Kernel: `uname -s`"
	echo "Version of Kernel: `uname -r`"
	echo "Current Date: `date +'%d/%m/%y'`"
	echo "Name of OS: `uname -o`"
	echo "Last Boot Time: `who -b | awk '{ print $4 }'`"
fi
```
#### (d) when a user run like "opensource time" it must give current time only
```
[root@localhost ~]# opensource time
Current Time: 12:56:08
```
#### (e) when it runs like "opensource user" it will give list of interactive shell users only
```
[root@localhost ~]# opensource user
Users: root
```
#### (f) when run like "opensource 100" it must print "Hello Delvex" 100 times in interval of 1 sec
```
[root@localhost ~]# opensource 100
100 Hello Delvex
99 Hello Delvex
98 Hello Delvex
97 Hello Delvex
96 Hello Delvex
95 Hello Delvex
94 Hello Delvex
93 Hello Delvex
92 Hello Delvex
91 Hello Delvex
90 Hello Delvex
```
#### (g) if runs like "opensource windows" then it must shutdown OS
```
[root@localhost ~]# opensource windows
Shutting down system...

```
#### (h) if run "opensource" command without any parameter then it must show out --
 - name of kernel 
 - version of kernel 
 - current date in the format of /DD/MM/YY
 - name of OS 
 - last reboot time 
```
[root@localhost ~]# opensource 
Name of Kernel: Linux
Version of Kernel: 5.6.19-300.fc32.x86_64
Current Date: 12/07/20
Name of OS: GNU/Linux
Last Boot Time: 13:03
```
## Problem #8
## Create a user with default settings:
#### (a) create a user named delvex and password of this user will be fedora
> Editing /etc/skel/.bashrc to add following lines
 - HISTSIZE=5000
 - HISTFILE="$HOME/myhist.txt"
 - SHELL=/bin/sh
```
[root@localhost ~]# nano /etc/skel/.bashrc
  GNU nano 4.9.3                         /etc/skel/.bashrc                                    
# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi

# User specific environment
if ! [[ "$PATH" =~ "$HOME/.local/bin:$HOME/bin:" ]]
then
    PATH="$HOME/.local/bin:$HOME/bin:$PATH"
fi
export PATH

# Uncomment the following line if you don't like systemctl's auto-paging feature:
# export SYSTEMD_PAGER=

# User specific aliases and functions
HISTSIZE=5000
HISTFILE="$HOME/myhist.txt"
SHELL=/bin/sh

                                      [ Read 21 lines ]
^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos
^X Exit        ^R Read File   ^\ Replace     ^U Paste Text  ^T To Spell    ^_ Go To Line
```
> Creating user delvex
```
[root@localhost ~]# adduser delvex
[root@localhost ~]# passwd delvex 
Changing password for user delvex.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
passwd: all authentication tokens updated successfully.
```
#### (b) when user get created, below listed things will come by default -
 - history size will be 5000 
 - history file will be  /home/delvex/myhist.txt
 - default shell will be  /bin/sh 
```
[root@localhost ~]# su - delvex
[delvex@localhost ~]$ printf "$HISTSIZE \n$HISTFILE \n$SHELL \n"
5000 
/home/delvex/myhist.txt 
/bin/sh
```
## Extra Tasks
#### (a) Write in a Directory:
```
[chinmayjain@localhost ~]$ mkdir temp
[chinmayjain@localhost ~]$ setfattr -n user.msg -v "Hello World" temp/
[chinmayjain@localhost ~]$ getfattr -n user.msg temp
# file: temp
user.msg="Hello World"
```
#### (b) Run some command without letting bash store it in history:
```
[chinmayjain@localhost ~]$ history
  339  echo Adding HISTCONTROL=ignoreboth to .bashrc
  340  nano .bashrc
  341  echo Added Successfully
  342  history
[chinmayjain@localhost ~]$ history # after running " history -d 340"
  339  echo Adding HISTCONTROL=ignoreboth to .bashrc
  340  echo Added Successfully
  341  history
```
