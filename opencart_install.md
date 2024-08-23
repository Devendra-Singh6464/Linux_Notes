Opencart  installation --

```
wget https://github.com/opencart/opencart/releases/download/4.0.0.0/opencart-4.0.0.0.zip
```
```
unzip opencart-4.0.0.0.zip -d /home/users/devendra.singh/www/html/opencart/
```
```
chown -R devendra.singh:Wuser /home/users/devendra.singh/www/html/opencart/
```
```
chmod -R 755 /home/users/devendra.singh/www/html/opencart/
```
```
sudo cp /home/users/devendra.singh/www/html/opencart/upload/{config-dist.php,config.php}
```
```
sudo cp /home/users/devendra.singh/www/html/opencart/upload/admin/{config-dist.php,config.php}
```
```
chown -R devendre.singh:Wuser /home/users/devendra.singh/www/html/opencart/upload/ config.php
```
```
chown -R devendre.singh:Wuser /home/users/devendra.singh/www/html/opencart/upload/admin config.php
```
```
CREATE USER 'opencart'@'localhost' IDENTIFIED BY 'webkul';
```
```
GRANT ALL PRIVILEGES ON opencart . * TO 'opencart'@'localhost';
```
