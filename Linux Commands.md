-- Install hp-lip: 
```
apt install hplip
apt install hplip-gui
```
Node js (with out git-hub) install --
```
curl -sL [https://deb.nodesource.com/setup_22.x](https://deb.nodesource.com/setup_22.x) | sudo -E bash -  
sudo apt-get install -y nodejs
nvm install 22
node -v
npm -v
```
-- Increase swap memory in ubuntu [allocated to memory]-------
```
sudo fallocate -l 10G /swapfile1
sudo chmod 600 /swapfile1
```
swapfile on.
```
sudo mkswap /swapfile1
sudo swapon /swapfile1
```
permanent in-cress swap memory:	
```
echo '/swapfile1 none swap sw 0 0' | sudo tee -a /etc/fstab
```
mount `hdd` to permanent.
```
/dev/sdb        /home/users/devendra.singh/hdd  ext4    defaults 0 0
/swapspace none swap sw 0 0

after this `reboot` system.
```
show the information about the `/dev/sdb` partition.
```
fdisk -l /dev/sdb
```
check filesystem type.
```
lsblk -f
```
if your file system type different so change to `ext4`.
```
sudo umount /dev/sdb1
```
```
sudo mkfs.ext4 /dev/sdb1
```
```
mount -a
```
check many users add a single groups.
```
getent group <groupname>
```
where you store source code.
```
/usr/src
```
No machine restart---
```
/etc/NX/nxserver --restart
```
 Flush IP tables. 
```
iptables -F
```
Check IP table allows status 
```
iptables -L
```

--- If you share a file 1 server to another server so using rsync 
Syntax =>
$ rsync -rav <folder(file)_name>/ <destination_username>:@destination_IP_address:<destination_address>
```
rsync -rav devendra/ devendra.singh@192.168.15.138:/home/users/devendra.singh
```
-- create a new folder-
$ rsync -rav <folder(file)_name>/ <destination_username>:@destination_IP_address:<destination_address> <folder_name>

-- Using `scp` command copy and paste file to host server to remote server.
syntax--
```
$ scp -r <folder_name> <destini_user_name>@<destini_ip>:<path where you copy folder>
```
```
$ sudo usermod --shell /bin/sh devendra
```
If you want to change default shell a particular user
```
chsh -s /bin/<shell_name> <user_name>
```
After check 
```
grep <username> /etc/passwd
```
How to check how many shell download in my system
```
echo $SHELLS
```
 and 
```
cat /etc/shells
```
 How to check how to storage in my system
```
du -sh (Specific_folder)
```
All data in my system
```
df -hT
```
Check space in your disk.
```
dh -h
```
If you want to create a permanent alias so edit .bashrc file 
```
vi .bashrc
```
edit--- 
```
alias 32='ssh vagrant@192.168.1.32'
```
If you any change `.bashrc` file so run this command  
```
source ~/.bashrc
```
If you want to check Kernel IP routing table.
```
route -n
```
If you check all runing service port number 
```
netstat -lntp
```
2. Create a Linux launcher icon.
```
vi /usr/share/applications/<application_name.desktop>
```
How to check current default permission?
```
umask
```

chomd: change permission the file
chown: change user/owner permission
chgrp: change group permissioin
-- if you change the permission inside the folder all files so-------->
```
chmod -R user:group <folder_name>
```
-- if you change 1 file permission so ------>
```
chmod -r user:group <file_name> 
```
-- chown -c devendra 03-file 
```
chgrp -c devendra 03-file
```
-- add use to another group--
```
usermod -aG <group_name> <user_name>
```
acl commands
```
getfacl 03-file 
```
 adding permission for user-
```
setfacl -m u:user:rwx <file_name>
```
 adding permission for group-
```
setfacl -m g:user:rwx <file_name>
```
 remove a sacific entry-
```
setfacl -x u:user:rwx <file_name>
```
remove all entries-
```
setfacl -b <file_name>
```
-- adding permission for user in all the files inside a folder
```
setfacl -Rm "entry" <target_file/folder>
```
-- How to create to a user?
```
useradd <usre_name>
adduser <user_name>
```
```
useradd -g <group_name> -s /bin/bash -c "This is a tempory user" -m -d /home/<user_name> <user_name>
```

-- Modify user-----
root@wadmin-Veriton-M200-H310:/home# id alex
uid=1003(alex) gid=1003(alex) groups=1003(alex)

-- Change the default group 
root@wadmin-Veriton-M200-H310:/home# usermod -g demo alex

root@wadmin-Veriton-M200-H310:/home# id alex
uid=1003(alex) gid=1005(demo) groups=1005(demo)

root@wadmin-Veriton-M200-H310:~# usermod -g devendra dev
root@wadmin-Veriton-M200-H310:~# id dev
uid=1002(dev) gid=1001(devendra) groups=1001(devendra)

-- add new group but default group also there 
root@wadmin-Veriton-M200-H310:~# usermod -G demo dev

root@wadmin-Veriton-M200-H310:~# id dev
uid=1002(dev) gid=1001(devendra) groups=1001(devendra),1005(demo)
[]() 
change :-
```
chage [-m mindays] [-M maxdays] [-d lastday] [-I inactive] [-E expiredate] [-W warndays] user_name
```

#### CONTROLLING SERVICE AND DAEMONS---
### systemd :
The systemd daemon manages startup for linux,including service start and service management in general.It actives system resources,server daemons and other processes both at boot time and on a runing system.

### Listin Service Units:
You use the systemctl command to exploer the currecnt state of the system.
This command without any arguments lists that are both loaded and active.
```
systemctl
```
--This command lists only the service units with active activaton states.
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
how check hdd check:
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
--- how to check file system type-
```
sudo blkid /dev/sda1
```

### Firewall d service on ubuntu------ 
how to start firewall d service on ubuntu
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

`systemctl list-dependenies` this command displays a hierachy mapping of dependencies to start the service unit to list reverse dependencies(units that depend on the specified unit), use the --reverse opton with the command.
```
systemctl list-dependencies <service_name>.service
```

### Masking and unmasking Services-----
Masking a Service: When you "mask" a service, you're essentially telling systemd to not start that service under any circumstances. It's a way to completely disable a service.

```
systemctl mask <service_name>.service
```
```
systemctl list unit-files --type==service
```
#### attempting to start a masked service unit fails.
--- how to unmask 
```
systemctl umask <service_name>.service
```
Enabling Services to start or stop at Boot---
To start a service without root or password, use the systemctl enable command 
```
systemctl enable <service_name>.service
``` 
 how many service given sudo privileges----
```
vi /etc/sudoers
```
if using systemctl so. 
```
%Wuser ALL = NOPASSWD: /usr/bin/systemctl
```
command-
```
sudo systemctl start apache2
```

If you facing this type issue so ----
'
E: Failed to fetch https://packagecloud.io/AtomEditor/atom/any/dists/any/InRelease  402  Payment Required [IP: 52.9.110.75 443]
E: The repository 'https://packagecloud.io/AtomEditor/atom/any any InRelease' is no longer signed.
'
```
vi /etc/apt/source.list
```
-- and commant the AtomEditor line
 If you check which all php version on your system and change the php version 
```
update-alternatives --config php
```
Optional---
```
update-alternatives --config php.phar
```
-- How to disable and enable service mode-----

 enmod service-
```
a2enmod service
```
disable service
```
a2dismod service
```
enable php version
```
a2enmod php+version_name
```
disable php older version
```
a2dismod php+version
```
check how many php service enabled
```
ls /etc/apache2/mods-enabled/ | grep php
```

## File Transfer using SFTP
### Initiating an SFTP Connection
```
sftp devendra@192.168.1.145
```
-- Transferring Files from Remote Servers to Local Systems.
> Syntax - get /path/to/remote/server/file.txt
```
get /devendra/first_01
```
> You will see the file is getting copied into the local machine.
-- if you transfer folder so
```
get -r devendra/
```

```
mget /devendra/files_*.
```
> multiple files from remote server.

-- Transferring Files from Local Systems to Remote Servers
Syntax - put /path/to/local/file/abc.txt /path/to/remote/directory

```
put /home/users/devendra.singh/help devendra/dev/
```
 
Extract tar file.
Syntax-
``` 
tar -xvzf file_name
```
-- If Any package stops getting installed during installation
```
apt-get install -f
```
-- Firefox update---
```
apt install --only-upgrade firefox
```
-- If you check your hardware information
```
apt install hardinfo
```
--- then
```
hardinfo
```
-- Another option
```
dmidecode
```
-- Check Your Windows 11 License Type
```
slmgr.vbs /dli
```

#### The command will launch a Windows Script Host window. If it says RETAIL Channel, you can continue transferring the license to your new device. If it says OEM Channel, you cannot transfer the license.

-- Check 'groups/users' in linux-
```
getent group/users  
```
 create a group-
```
sudo addgroup 'group_name'
``` 
 Rename a group-
```
sudo groupmod -n test demo1
```
 Add and remove users from a group
 how to check passwd in unencrypted form
```
cat /etc/shadow
```
changing system date
```
date
```
 (will display current date & time)
syntax--
```
MMDDHHmmYYYY.ss
```
it will display no. of lines, words & characters in file.
```
wc file1
```
if you facing system booting time issue and initramfs terminal is comming.
```
(initramfs) fsck /dev/sdaX -y
```
if you give sudo permission to a specific user. So add in the `/etc/sudoers` file.
Syntax.
<user_name> ALL = (ALL:ALL)  ALL
```
devendra.singh ALL =(ALL:ALL) ALL
```
if you want to see error in any process so please go this directory. 
```
cd /var/log/
```
if you watch continually apache error so - 
```
tail -f /var/log/apache2/error.log
```
if you create alias in ubuntu so find alias and add what you want -
```
vi .bashrc
```
after save '.barshrc' file
```
source .bashrc
```
if your Google Chrome not open so-
```
cd /home/users/<user_name>cd ./config/google-chrome
```
```
ls
```
and  `SingletonLock` rename this file`SingletonLock.old`.

-- `shred` command is used to securely delete files from your system, making it much harder to recover them compared to standard deletion.
When you use `shred`, it overwrites the contents of a file multiple times with random data before deleting it. This makes it more difficult for anyone to recover the original data.
```
shred -u <file_name>
```
- **`-u`**: This option tells `shred` to **unlink** (delete) the file after shredding it.
- **`-n 3`**: This specifies the number of times to overwrite the file (default is 3(default) times).

The shred command is also used to overwrite the data of a drive. Drive contains a huge amount of data, hence, a lot of time will be required to shred this data.
syntax:
```
shred <file_name>
```
example.
```
shred /dev/sda1
```
If you only intercept your data not delete so 
```
shred <file_name>
```
how to check how many bit in my system
```
getconf LONG_BIT
```
if set default editor.
```
update-alternatives --config editor
```
Allow users to change PHP version without sudo in ubuntu.
```
devendra.singh ALL=(ALL) NOPASSWD: /usr/bin/update-alternatives --config php
```
if you want to check packages alternatives so 
```
devendra.singh ALL=(ALL) NOPASSWD: /usr/bin/update-alternatives 
```
Check Kernel Logs: Sometimes more information about the error can be found in the kernel logs. Use:
```
dmesg | tail
```
Retrieve the inode of a file.
```
ls -i filename
```
example commands to add new disk
```
lsblk                     # list all disks and partitions
sudo fdisk /dev/sdb       # let's suppose new disk is /dev/sdb
sudo mkfs.ext4 /dev/sdb1  # make filesystem(e.g., ext4) on partition 1
sudo mount /dev/sdb1 /mnt # mount new filesystem to /mnt directory
```
The following are common commands to manage disks:

- Use `lsblk` to list all block devices (disk and partitions).
- Use `fdisk /dev/sdX` to create a new partition on a disk.
- Use `mkfs.ext4 /dev/sdX1` to create a new filesystem on a partition.
- Use `mount /dev/sdX1 /mount/point` to mount a filesystem to a directory.

- If you are facing this type of problem then user cannot save or create his file.
```error
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (30: Read-only file system)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (30: Read-only file system)
```
So `restart` your system and `initramfs` terminal frount of your 
top of terminal you see `/dev/<type>` that means your system no  permission this file. so run this command 
```
fsck /dev/sda<type> -y
```
```
exit
```

--- kazam simplescreenrecord Recording the Black Screen in linux.
Open the file.
```
vi /etc/gdm3/custom.conf
```
 and uncomment this line. 
` #WaylandEnable=false `
To 
` WaylandEnable=false `

If You check how many ports run on.
```
Starting Nmap 7.80 ( https://nmap.org ) at 2024-10-09 09:24 IST
Nmap scan report for _gateway (192.168.15.1)
Host is up (0.00048s latency).

``` 
-- If you redirect output in a file (saving output to a file):
syntax.
```
command > file.txt
```
example.
```
ls > file.txt
```
-- If you want to capture both standard output and standard error in the same file, use:
```
command > output.txt 2>&1
```
if you know the any topic related to linux command definition in 1 line. 
```
whatis route
```
error
```
route: nothing appropriate.
```
run : update manual entry's.
```
mandb
```
If you block to single IP `ssh` on your system.
```
vi /etc/hosts.deny
```
-- syntax:
`sshd: <system_ip>` 
```
sshd: 192.168.1.32
```
Change Default `SSH` Port.
```
vi /etc/ssh/sshd_config
```
uncomment this and change port.
```
#Port 22
```
-- Check any service process ID.
```
pgrep <service_name>
```
if you kill process 
```
pgrep <service_name> | xargs kill -9
```
if see parent process and child process.
```
pstree
```
-- show all run process for user.
```
pstree -p -u devendra.singh
```
how to forward process to background.
syntax.
```
<cammand> &
```
	
```
sleep 20 &
```
--- If you `erase` your disk fully no any one can access after erase data using any data recovery tool so.
syntax.
`badblocks -ws <disk_path>`
```
badblocks -ws /dev/sda
```
&&
syntax.
`dd =if/dev/zero of=/dev/<disk_name>`
```
dd if=/dev/zero of=/dev/sda
```

 1. The `shred` command overwrites the contents of a file multiple times, making recovery difficult. By default, it overwrites the file three times, but you can specify the number of overwrites with the `-n` option.
```
shred -n 5 -z -u filename
```
2. `wipe`
```
wipe filename 
```
after add `scsi` disk  and scan without reboot system.
```
ls /sys/class/scsi_host/ | while read host ; do echo "- - -" > /sys/class/scsi_host/$host/scan ; done
```
If you check graphically.
```
for x in `ls /sys/class/scsi_host/` ; do echo " $x scanned"; > /sys/class/scsi_host/$x/scan ; done
```
check your disk type.
syntax.
```
sudo parted /dev/sdX print
```
```
parted /dev/sdb print
```
-- check all LDAP users:
```
getent passwd
```
ubuntu drivers install.
```
sudo ubuntu-drivers autoinstall
```
```
sudo systemctl status wpa_supplicant
```
use `sed` command [if you add some changes in the file or script so use set command].
```
sed -i 's/devendra/deepak/g' 01.sh 
```
`this command changed devendra to deepak in 01.sh file`.


sudo rm -rf /var/lib/apt/lists/*
sudo rm -rf /var/lib/command-not-found/*

sudo vi /etc/apt/apt.conf.d/50command-not-found
and comment this line
```
#APT::Update::Post-Invoke-Success
```
```
sudo apt --fix-broken install
```

Download the Elasticsearch Debian Package. 
```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.15.0-amd64.deb
```

Check all services and which they are port runing .
```
sudo lsof -i -P -n | grep LISTEN
```

how to update composer.
```
composer self-update
```
  Use return the back version
```
composer self-update --rollback
```

how to check redis extension enabled or not.
```
php --ini | grep redis
```
- disbale php version.
```
vi /etc/php/7.4/mods-available/<extensions>
```
and 
```
; configuration for php common module
; priority=20
extension=fileinfo.so
```
`;` : comment the extension.
```
; configuration for php common module
; priority=20
; extension=fileinfo.so
```
dismod extensions.
```
phpdismod <extension>
```
restart your web server
```
systemctl restart apache2
```
Run to see a list of processes and their ports.
```
sudo netstat -tlpn 
```