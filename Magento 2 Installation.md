urls:

https://www.cybrosys.com/blog/how-to-install-magento-2-4-5-in-ubuntu-22-04

https://cloudinfrastructureservices.co.uk/install-magento-2-on-ubuntu-20-04/

https://www.mgt-commerce.com/tutorial/how-to-install-magento-2-4-4-on-ubuntu-20-04/

latest and old magento versions : https://meetanshi.com/blog/download-magento/

https://webkul.com/blog/write-your-own-shell-bash-script-to-install-magento-2/

https://help.uvdesk.com/en/member/ticket/view/78190(uvdesk ticket link).

Create magento2 directory in www/html/ and install composer.

cd magento2
composer install
composer update
Install magento in magento2 direstory https://meetanshi.com/blog/download-magento/
Note: If you install magento 2 latest version so configure this opensearch.

Optional-
map domain--

vi /etc/apache2/sites-available/000-default.conf
add this line in 000-default.conf.

<VirtualHost *:80>

         ServerName magento.example.com

         ServerAdmin webmaster@localhost
         DocumentRoot /home/users/devendra.singh/www/html/magento2/pub

         ErrorLog ${APACHE_LOG_DIR}/error.log
         CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
and  /etc/hosts entry.

192.168.15.138   magento.example.com
restart apache.

systemctl restart apache2
Install Opensearch. https://opensearch.org/downloads.html
wget https://artifacts.opensearch.org/releases/bundle/opensearch/2.18.0/opensearch-2.18.0-linux-x64.deb
Go to vi /etc/opensearch/opensearch.yml file and add this line in last.
vi /etc/opensearch/opensearch.yml
add.
plugins.security.disabled: true
dpkg -i opensearch-2.18.0-linux-x64.deb
start and enable opensearch service.
systemctl start opensearch
systemctl enable opensearch
set CPU limit in jvm.options file.
jvm.options
(optional) If you install latest magento 2.4.7 so jdk version 11 and 17
sudo apt install openjdk-11-jdk
sudo apt install openjdk-17-jdk
Enter Database Shell;
mysql -u root -p  
Note: Enter your database password

CRATE DATA BASE
CREATE DATABASE magento2;
Note: your choice which name you want to set your data base
Exit database shell
6. Run this command to your magento installation directory.

cd /home/aditi/www/html/magento2
install composer;
composer install
composer update
php bin/magento setup:install --base-url=http://192.168.25.155/magento2/pub --db-host=localhost --db-name=magento2 --db-user=root --db-password=webkul --admin-firstname=admin --admin-lastname=admin --admin-email=test@webkul.com --admin-user=admin --admin-password=admin123 --language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1
syntax:

--base-url=http://192.168.25.155/magento2/pub <http://localhost/magento2/pub>,  --db-name=magento <your_database_name>, --db-user=root<your_database_username>,
--db-password=Root@123<your_database_password>,  --admin-email=devbhandari876@gmail.com <your_email_id>, --admin-user=admin <your_login-admin_name>, --admin-password=admin@123 <your_login_admin_password>
After run this command you have backend url in output end last.
If you forgot backend url so. please check this.
check backend url in this directory.
aditi@aditi155:~/www/html/magento2/app/etc$ vi env.php 
after successfully excute this command so we got it this type backend url end /admin_eezsoj1.

/admin_eezsoj1
Front-end URL:

192.168.15.138/magento2/pub
Back end URL:

192.168.15.138/magento2/pub/admin_eezsoj1
