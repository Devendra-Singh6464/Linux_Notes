# Odoo 17 Installation in 22.04:
-------------------------------

Update server:
```
sudo apt update && sudo apt-get upgrade -y
```
Install some dependencies for PostgreSQL and Odoo itself:
```
sudo apt-get install -y python3-pip python3-dev python3-venv libxml2-dev libxslt1-dev zlib1g-dev libsasl2-dev libldap2-dev build-essential libssl-dev libffi-dev libmysqlclient-dev libjpeg-dev libpq-dev libjpeg8-dev liblcms2-dev libblas-dev libatlas-base-dev -y
```
```
sudo apt-get install -y npm
sudo ln -s /usr/bin/nodejs /usr/bin/node
sudo npm install -g less less-plugin-clean-css
sudo apt-get install -y node-less
```
Install git
```
apt-get install git
```
Install postgreSQL:
```
sudo apt-get install postgresql -y
```
Start and enable the PostgreSQL service and check the status execute:
```
systemctl start postgresql && systemctl enable postgresql status postgresql
```
Install Wkhtmltopdf:
```
sudo wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb
sudo dpkg -i wkhtmltox_0.12.5-1.bionic_amd64.deb
sudo apt install -f
```
Create odoo Folder:
```
mkdir odoo17
```
```
cd odoo17/ 
```
Install and Configure Odoo 17:
```
git clone https://www.github.com/odoo/odoo --depth 1 --branch 17.0 /opt/odoo17/odoo17
```
activate the Python virtual environment:
```
cd /opt/odoo17
python3 -m venv odoo17-venv
source odoo17-venv/bin/activate
pip install --upgrade pip
pip3 install wheel
pip3 install -r odoo17/requirements.txt
```
deactivate the environment and create the Odoo add-on directories and Odoo log file:
```
deactivate
mkdir /opt/odoo17/odoo17-custom-addons
chown -R wadmin:wadmin /opt/odoo17/odoo17-custom-addons
sudo mkdir -p /var/log/odoo17
sudo touch /var/log/odoo17.log
sudo chown -R wadmin:wadmin /var/log/odoo17
```
create the configuration file:
```
sudo vi /etc/odoo17.conf
```
```
[options]
admin_passwd = YourStrongPasswordHere
db_host = False
db_port = False
db_user = wadmin
db_password = False
xmlrpc_port = 8069
logfile = /var/log/odoo17/odoo17.log
addons_path = /opt/odoo17/odoo17/addons,/opt/odoo17/odoo17-custom-addons 
```
Create an Odoo systemd unit file:
```
sudo vi /etc/systemd/system/odoo17.service
```
```
[Unit]
Description=odoo17
After=network.target postgresql@14-main.service

[Service]
Type=simple
SyslogIdentifier=odoo17
PermissionsStartOnly=true
User=wadmin
Group=wadmin
ExecStart=/opt/odoo17/odoo17-venv/bin/python3 /opt/odoo17/odoo17/odoo-bin -c /etc/odoo17.conf
StandardOutput=journal+console

[Install]
WantedBy=multi-user.target
```
Reload the daemon, then start and enable the Odoo service:
```
sudo systemctl daemon-reload
sudo systemctl start odoo17 && sudo systemctl enable odoo17
```
Check the status:
```
sudo systemctl status odoo17
```
As you can see, the service is up and running. To access your Odoo website, you need to access your server’s IP address in your web browser on port 8069.
```
http://yourserverip:8069
```
