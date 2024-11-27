followed links.
1. https://geekrewind.com/install-dolibarr-erp-crm-on-ubuntu-16-04-17-10-18-04-with-apache2-mariadb-and-php-7-1-support/
2. https://docs.vultr.com/how-to-install-dolibarr-on-ubuntu-20-04
3. https://docs.vultr.com/how-to-install-dolibarr-on-ubuntu-20-04

1. To install Apache2 HTTP.
```shell 
sudo apt update
sudo apt install apache2
```
2. apache2 services
```shell
systemctl status apache2
systemctl start apache2
systemctl stop apache2
systemctl restart apache2
systemctl disable apache2
systemctl enable apache2
```
3. install PHP 7.2 and related modules.
```
sudo apt install php7.1 libapache2-mod-php7.1 php7.1-common php7.1-curl php7.1-intl php7.1-mbstring php7.1-mcrypt php7.1-json php7.1-xmlrpc php7.1-soap php7.1-mysql php7.1-gd php7.1-xml php7.1-cli php7.1-zip
```
4. PHP 7.2, run the commands below to open the PHP default config file for Apache2.
```shell
sudo vi /etc/php/7.1/apache2/php.ini
```
save the changes on the following lines below in the file.
```shell
file_uploads = On
allow_url_fopen = On
memory_limit = 512M
upload_max_filesize = 100M
max_execution_time = 360
date.timezone = America/Chicago
```
5. create the Dolibarr database.
```shell
mysql -u root -p
```
 Note: entry your database password.
```shell
CREATE DATABASE dolibarr;
``` 
show all created databases.
```
show databases;
```
Noted: save your changes and exit.
```shell
FLUSH PRIVILEGES;
EXIT;
```
6. Install Dolibarr in `/home/users/devendra.singh/www/html/dolibarr/`
```shell
 wget https://sourceforge.net/projects/dolibarr/files/Dolibarr%20ERP-CRM/7.0.2/dolibarr-7.0.2.zip
unzip dolibarr-7.0.2.zip
```
7. set the correct permissions for Dolibarr
```shell
sudo chown -R www-data:www-data /var/www/html/dolibarr/
sudo chmod -R 755 /var/www/html/dolibarr/
```
8. Apahce2  configuration file for Dolibarr.
```shell
vi /etc/apache2/sites-available/000-default.conf
```
9. add this configuration in `000-default.conf` file.
```shell
<VirtualHost *:80>

         ServerName dolibarr.example.com

         ServerAdmin webmaster@localhost
         DocumentRoot /home/users/devendra.singh/www/html/dolibarr/htdocs

         ErrorLog ${APACHE_LOG_DIR}/error.log
         CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
10.Enable the Dolibarr
```shell
sudo a2ensite 000-default.conf
sudo a2enmod rewrite
```
11. Restart Apache2.
```shell
systemctl restart apache2
```
