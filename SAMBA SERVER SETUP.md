# Install Samba

``` shell
sudo apt install samba -y
sudo apt update 
```

*  Check the Samba version
``` shell
samba -V
```

* Confirm that the Samba service is running.
``` shell
systemctl status smbd
```

#  Create a Shared Directory
``` shell
sudo mkdir -p /home/sharing
```

# Configure Samba's Global Options

``` shell
sudo vi /etc/samba/smb.conf
```

* Go to the end of the file and add the following lines.
``` shell
[sharing]
comment = Samba share directory
path = /home/sharing
read only = no
writable = yes
browseable = yes
guest ok = no
valid users = Devendra.singh
```

* Run the Samba **`testparm`** utility to check for syntax errors
``` shell
testparm
```

# Set Up a User Account
*  To create a user account, set a username and password with:
``` shell
sudo smbpasswd -a username
```

``` shell
sudo smbpasswd -a devendra.singh
```

* Both users need to have read, write, and execute access to the _sharing_ directory. While the user _devendra.singh_ has these permissions by default, _new_user_ does not.

To grant read, write, and execute permissions to the _sharing_ directory, run **`setfacl`**:

``` shell
sudo setfacl -R -m "u:new_user:rwx" /home/sharing
```

*   Restart the samba server.
``` shell
sudo systemctl restart smbd
```
