
### ODOO16 INSTALLED IN UBUNTU 20.04 OUR LOCAL USER.

Step 1. Update your Server.
```
sudo apt-get update
sudo apt-get upgrade
```

Step 2: Secure your server.
```
sudo apt-get install openssh-server fail2ban
```

Step 3: Installing Packages and libraries.
```
sudo apt-get install -y python3-pip python3-dev python3-venv libxml2-dev libxslt1-dev zlib1g-dev libsasl2-dev libldap2-dev build-essential libssl-dev libffi-dev libmysqlclient-dev libjpeg-dev libpq-dev libjpeg8-dev liblcms2-dev libblas-dev libatlas-base-dev -y
```

Install Web web dependencies:
If npm 
```
sudo apt-get install -y npm
sudo ln -s /usr/bin/nodejs /usr/bin/node
sudo npm install -g less less-plugin-clean-css
sudo apt-get install -y node-less
sudo apt-get install git
```

Step 4: Configure Postgresql
```
sudo apt-get install postgresql 
```

Step 5: Lollowing command will change the Postgres user:
```
sudo su - postgres
```

Step 6: Create data base user for odoo .
```
createuser --createdb --username postgres --no-createrole --no-superuser --pwprompt <username>
```

Step 7: superuser in order to receive further privileges.
```
psql  
ALTER USER odoo16 WITH SUPERUSER;
```

Exit from psql and Postgres user:
```
\q  
exit
```

If You want to Installation for user only  so create all configs files in users home directory.
```
mkdir -p opt/odoo16
cd opt/odoo16
```

Step 8:  Get or Download Odoo 16 community from git.
```
git clone https://www.github.com/odoo/odoo --depth 1 --branch 16.0 --single-branch .   # (.) dot reprsent to current directory
```

Step 9: After download odoo install requirements.
```
pip3 install -r requirements.txt
```

Install Wkhtmltopdf.
```
sudo wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb  
sudo dpkg -i wkhtmltox_0.12.5-1.bionic_amd64.deb  
sudo apt install -f
```

you can cross check installation by running odoo binary 
```
#change directory to installation folder 
./odoo-bin
```
ctrl+c to quit.

Now create a service or systemd file to run odoo as a service (start/stop/restart)
Step 10
: Setup Conf file.

```
mkdir /home/users/devendra.singh/etc
cd /home/users/devendra.singh/etc
vim odoo.conf         # add below script in this file
```

```txt
[options]
   ; This is the password that allows database operations:
   admin_passwd = admin
   db_host = False
   db_port = False
   db_user = odoo16   # change this with your username with your db user
   db_password = False
   addons_path = /opt/odoo16/addons
   logfile = /var/log/odoo/odoo16.log
```

change permission of conf file
```
sudo chmod 640 /home/users/devendra.singh/etc/odoo16.conf
```
create a log directory of Odoo
```
sudo mkdir /home/users/devendra.singh/var/log/odoo
```
Create Odoo service file
```
sudo vim /home/users/devendra.singh/etc/init.d/odoo-server
```

`vim /home/users/devendra.singh/etc/init.d/odoo-server`

Add the contents of the below script in odoo-server file 
https://raw.githubusercontent.com/mohitg1213/odoo_scripts/master/odoo-server

Edit these variables in oddo-server file according to your environment
```
DAEMON=/opt/odoo/odoo-bin   #/home/sandy/opt/odoo16/odoo-bin
CONFIGFILE="/etc/odoo-server.conf" # Specify the Odoo Configuration file path.
USER=odoo # Specify the user name (Default: odoo).
PIDFILE=/var/run/$NAME.pid # pidfile   #/home/sandy/var/run/odoo.pid
```

```
chmod +x odoo-server
```
Start the oddo service
```
sudo /etc/init.d/odoo-server start
```
staus odoo service
```
sudo /etc/init.d/odoo-server start
```
visit the web 
http://localhost:8069


Hip Hip Huree  completed

