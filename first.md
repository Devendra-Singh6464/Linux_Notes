!. How to share file using ip address.
1. $ rsync -rac <filename> <username>@ip_address:<destination_path>


2. Create a Linux launcher icon.
$ vi /usr/share/applications/<application_name.desktop>



How to check current default permission?
$umask


chomd: change permission the file
chown: change user/owner permission
chgrp: change group permissioin


if you change the permission inside the folder all files so-------->
chmod -R user:group <folder_name>

if you change 1 file permission so ------>
chmod -r user:group <file_name> 

chown -c devendra 03-file 
chgrp -c devendra 03-file

-------acl commands
getfacl 03-file 

adding permission for user-
setfacl -m u:user:rwx <file_name>

adding permission for group-
setfacl -m g:user:rwx <file_name>

remove a sacific entry-
setfacl -x u:user:rwx <file_name>

remove all entries-
setfacl -b <file_name>

adding permission for user in all the files inside a folder
$setfacl -Rm "entry" <target_file/folder>

Composer----------->
https://www.cherryservers.com/blog/how-to-install-composer-ubuntu


Install secure phpmyadmin--------->
https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-20-04

How to install and configure phpMyAdmin------->
https://ubuntu.com/server/docs/how-to-install-and-configure-phpmyadmin

how to create toa  user?
useradd <usre_name>
adduser <user_name>

useradd -g <group_name> -s /bin/bash -c "This is a tempory user" -m -d /home/<user_name> <user_name>


Modify user-----
root@wadmin-Veriton-M200-H310:/home# id alex
uid=1003(alex) gid=1003(alex) groups=1003(alex)

# Change the default group 
root@wadmin-Veriton-M200-H310:/home# usermod -g demo alex

root@wadmin-Veriton-M200-H310:/home# id alex
uid=1003(alex) gid=1005(demo) groups=1005(demo)

root@wadmin-Veriton-M200-H310:~# usermod -g devendra dev
root@wadmin-Veriton-M200-H310:~# id dev
uid=1002(dev) gid=1001(devendra) groups=1001(devendra)

# add new group but default group also there 
root@wadmin-Veriton-M200-H310:~# usermod -G demo dev

root@wadmin-Veriton-M200-H310:~# id dev
uid=1002(dev) gid=1001(devendra) groups=1001(devendra),1005(demo)


Other usermod options:-------->
-m -d :- /home/newfolder (to move the content of home folder to this new folder)
-p : we can use passwod command also 
-L -U : Lock/Unlock a uer

root@wadmin-Veriton-M200-H310:/home# ls
alex  dev  deva  devendra  wadmin
root@wadmin-Veriton-M200-H310:/home# mkdir alex/demofolder
root@wadmin-Veriton-M200-H310:/home# ls
alex  dev  deva  devendra  wadmin

root@wadmin-Veriton-M200-H310:~# usermod -m -d /home/alex_a alex
root@wadmin-Veriton-M200-H310:/home# ls
alex_a  dev  deva  devendra  wadmin
root@wadmin-Veriton-M200-H310:/home# cd alex_a/
root@wadmin-Veriton-M200-H310:/home/alex_a# ls
demofolder

root@wadmin-Veriton-M200-H310:/home# usermod -m -d /home/alex_x alex
root@wadmin-Veriton-M200-H310:/home# ls
alex_x  dev  deva  devendra  wadmin
root@wadmin-Veriton-M200-H310:/home# cd alex_x/
root@wadmin-Veriton-M200-H310:/home/alex_x# ls
demofolder


Q. Difference between update & upgrade?

UPDATE: keep the old packages, we can rollback.
UPGRADE: will delete the old packages.


if you create a folder inside the folder using one command 
$ mkdir -p <folder1_name>/<folder2_name>


Use set-hostname to Change the Hostname
$ hostnamectl set-hostname new-hostname

### What is Systemd?
1. Systemd is a software suite that provides an initialization system and service management for Linux operating systems.
2. Systemd is the first process started by the Linux kernel (with PID 1).
3. It initializes and configures the userspace environment and services.
4. Services are defined in unit files, which describe how to start, stop, and manage each service.
5. Systemd uses socket-based activation to start services on demand when a request comes in.
6. It also provides features like on-demand starting of daemons, parallelized starting of services, and automatic restarting of crashed services.

## Key Components of Systemd
1. systemd: The main daemon that manages the system
2. systemctl: The command-line tool to control the system and service manager
3. journalctl: The tool to view and query logs managed by the systemd journal
4. systemd-analyze: The tool to analyze system boot-up performance

## Benefits of Systemd
1. Faster boot times: Systemd can start services in parallel, leading to faster boot times.
2. Improved dependency management: Systemd can automatically start required services based on dependencies.
3. Better logging: Systemd provides a centralized logging system called the journal.
4. Easier service management: Systemd provides a consistent way to manage services using systemctl.

```
$grep
```
The name "grep" comes from the ed (a Unix line editor) command g/re/p which means “globally search for a regular expression and print all lines containing it”.

1. https://digitalwatchdog.happyfox.com/kb/article/919-locating-a-usb-drive-on-ubuntu-linux/#:~:text=When%20a%20USB%20flash%20drive,to%20open%20the%20USB%20device.


## CONTROLLING SERVICE AND DAEMONS---

systemd :
The systemd daemon manages startup for linux,including service startu and service management in general.It actives system resources,server daemons and other processes both at boot time and on a runing system.

# Listin Service Units:
You use the systemctl command to exploer the currecnt state of the system.
This command without any arguments lists that are both loaded and active.
```
systemctl
```

This command lists only the service units with active activaton states.
```
systemctl list-units --type=service
systemctl --type=service
```

enabled : available across re-boot system.


1. if you want to set the limeit any service to tack a memory so 
```
systemctl set-property (service_name)httpd.service MemoryLimit=200M
```
```
systemctl status httpd
```

oom kiiler: out of memory killer. 

if you restart the any service that means `pid` changed
how to cheack `pid`
```
pidof <service_name>
```

if you reload the any servcie so service `pid` not changed-
```
systemctl reload <service_name>
```

if you change apache default port:80 so
```
vi /etc/httpd/conf/httpd.conf
```
and change the `listen`
```
systemctl restart httpd
```



--- change host name:
```
hostnamectl set-hostname <name'ip_last'>
```

--- memory hdd check:
```
lsblk
```
----------------------------------------------------------------------------------------------------------------------------------------------------------

Increase swap memory in ubuntu-------
```
sudo fallocate -l 10G /swapfile
```
```
sudo chmod 600 /swapfile
```
```
sudo mkswap /swapfile
```
```
sudo swapon /swapfile  and 
```
```
sudo mount -a after this `reboot`
```

No machine restart---
```
/etc/NX/nxserver --restart
```

Check elasticsearch status----
```
sudo /etc/init.d/elaticsearch status
```

if you want start elasticsearch with less memory so .
-Please edit this line.source ~/.bashrc

#Xms4g
#Xms4g 
```
vi /etc/elaticsearch/jvm.options
```

# How to IP tables flush
```
iptables -F
```

# Check IP table allows status 
```
iptables -L
```

# If you share a file 1 server to another server so using rsync 
Syntax =>
```
rsync -rav <user_name>/ <destination_username>:@destination_IP_address:<destination_address>
```
```
rsync -rav devendra/ devendra.singh@192.168.15.138:/home/devendra.singh
```
create a new folder-
```
rsync -rav <user_name>/ <destination_username>:@destination_IP_address:<destination_address> <folder_name>
```

# Using `scp` command copy and paste file to host server to remote server.
```
scp -r <folder_name> <destini_user_name>@<destini_ip>:<path where you copy folder>
```

```
sudo usermod --shell /bin/sh devendra
```

# If you want to change default shell a particular user
```
chsh -s /bin/<shell_name> <user_name>
```

# After check 
```
grep <username> /etc/passwd
```

# How to check how many shell download in my system
```
cat /etc/shells
```

# How to check how to storage in my system
```
du -sh (Specific_folder)
```

# All data in my system
```
df -hT
```

# If you want to create a parmanent alias so edit .bashrc file 
```
vi .bashrc
```

edit--- 
# some more ls aliases
alias 32='ssh vagrant@192.168.1.32'

If you any change .bashrc file so run this command  
```
source ~/.bashrc
```





  
