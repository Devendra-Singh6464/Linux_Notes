urls:
1. https://www.cybrosys.com/blog/how-to-install-magento-2-4-5-in-ubuntu-22-04
2. https://cloudinfrastructureservices.co.uk/install-magento-2-on-ubuntu-20-04/
3. https://www.mgt-commerce.com/tutorial/how-to-install-magento-2-4-4-on-ubuntu-20-04/
4. latest and old magento versions : https://meetanshi.com/blog/download-magento/

1. Create `magento2` directory in `www/html/` and install composer.
```
cd magento2
composer update
composer install
```
2. Install magento in `magento2 direstory` https://meetanshi.com/blog/download-magento/

map domain--  
```
vi /etc/apache2/sites-available/000-default.conf
```
add this line in `000-default.conf`.
```
<VirtualHost *:80>

         ServerName magento.example.com

         ServerAdmin webmaster@localhost
         DocumentRoot /home/users/devendra.singh/www/html/magento2/pub

         ErrorLog ${APACHE_LOG_DIR}/error.log
         CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
and  /etc/hosts entry.
```
192.168.15.138   magento.example.com
```
restart apache.
```
systemctl restart apache2
```

```
sudo -u devendra.singh bin/magento setup:install --base-url=http://magento.example.com --db-host=localhost --db-name=magento --db-user=root --db-password=Root@123 --admin-firstname=admin --admin-lastname=admin --admin-email=devbhandari876@gmai.com --admin-user=admin --admin-password=admin@123 --language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1
```

after successfully excute this command so we got it this type backend url end `/admin_eezsoj1`.
```
/admin_eezsoj1
```
Front-end URL:
```
192.168.15.138/magento2/pub
```
Back end URL:
```
192.168.15.138/magento2/pub/admin_eezsoj1
```