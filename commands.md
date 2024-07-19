Increase swap memory in ubuntu-------

1. sudo fallocate -l 10G /swapfile
2. sudo chmod 600 /swapfile
3. sudo mkswap /swapfile
4. sudo swapon /swapfile  and 
sudo mount -a after this `reboot`

No machine restart---
$ /etc/NX/nxserver --restart

Check elasticsearch status----
$ sudo /etc/init.d/elaticsearch status

if you want start elasticsearch with less memory so .
-Please edit this line.source ~/.bashrc

# If you want to set fixe memory to elasticsearch ----
So please edit this file-----
```  
vi /etc/elaticsearch/jvm.options
```
#Xms4g
#Xms4g 

after edit this file restart elasticsearch service
```
sudo /etc/init.d/elaticsearch start
```

# How to IP tables flush
$ iptables -F

# Check IP table allows status 
$ iptables -L


# If you share a file 1 server to another server so using rsync 
Syntax =>
$ rsync -rav <user_name>/ <destination_username>:@destination_IP_address:<destination_address>
$ rsync -rav devendra/ devendra.singh@192.168.15.138:/home/devendra.singh

create a new folder-
$ rsync -rav <user_name>/ <destination_username>:@destination_IP_address:<destination_address> <folder_name>

# Using `scp` command copy and paste file to host server to remote server.
$ scp -r <folder_name> <destini_user_name>@<destini_ip>:<path where you copy folder>

$ sudo usermod --shell /bin/sh devendra

# If you want to change default shell a particular user
$ chsh -s /bin/<shell_name> <user_name>

# After check 
$ grep <username> /etc/passwd

# How to check how many shell download in my system
$ cat /etc/shells

# How to check how to storage in my system
$ du -sh (Specific_folder)

# All data in my system
$ df -hT

# If you want to create a parmanent alias so edit .bashrc file 
$  vi .bashrc
edit--- 
# some more ls aliases
alias 32='ssh vagrant@192.168.1.32'

If you any change .bashrc file so run this command  
$ source ~/.bashrc


# If you want to check Kernel IP routing table.
```
route -n
```

# If you check all runing service port number 
```
netstat -lntp
```

## How to share file using ip address.
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
 
chage :-

chage [-m mindays] [-M maxdays] [-d lastday] [-I inactive] [-E expiredate] [-W warndays] user_name


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
Enabled : available across re-boot system.

1. if you want to set the limit any service to tack a memory so 
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

How to change host name:
```
hostnamectl set-hostname <newname>
```

# how check hdd check:
```
lsblk
``` 

----Use the command to verify that the a service unit is currently active(running).-----
```
systemctl is-active/enabled <servce_name>.service  
```

----To verify wheter the unit failed during startup.------
```
systemctl is-failed <service_name>.service
```

## Firewalld service on ubuntu------ 

how to start firewalld service on ubuntu
```
systemctl start firewalld
```

enable--
```
systemctl enable firewalld
```

check status--
```
systemctl status firewalld
```

stop the service-----
```
systemctl stop <service_name>.service
```

`systemctl list-dependenies` this commadn displays a hierachy mapping of dependencies to start the service unit to list reverse dependencies(units that depend on the specified unit), use the --reverse opton with the command.
```
systemctl list-dependencies <service_name>.service
```

## Masking and unmasking Services-----
Masking a Service: When you "mask" a service, you're essentially telling systemd to not start that service under any circumstances. It's a way to completely disable a service.

```
systemctl mask <service_name>.service
```
```
systemctl list unit-files --type==service
```
attempring to start a masked service unit fails.

how to unmask ---------
```
systemctl umask <service_name>.service
```

## Enabling Servies to start or stop at Boot---
To start a service atr boot,use the systemctl enable command 
```
systemctl enable <service_name>.service
```
 
how many service given sudo privilages----
```
vi /etc/sudoers
``` 

# If you faceing this type issue so ----
'
E: Failed to fetch https://packagecloud.io/AtomEditor/atom/any/dists/any/InRelease  402  Payment Required [IP: 52.9.110.75 443]
E: The repository 'https://packagecloud.io/AtomEditor/atom/any any InRelease' is no longer signed.
'
```
vi /etc/apt/source.list
```
-- and commant the AtomEditor line


# If you check which all php version on your system and change the php version 
```
update-alternatives --config php
```
Optional---
```
update-alternatives --config php.phar
```

# How to disable and enable service mode-----

# enmod service-
```
a2enmod service
```

# disable service
```
a2dismod service
```

enable php version
```
a2enmod php+version_name
```

disable php version
```
a2dismod php+version
```
