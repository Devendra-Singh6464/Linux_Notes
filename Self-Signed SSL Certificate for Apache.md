Refrence link: https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-18-04

# Create a Self-Signed SSL Certificate for Apache in Ubuntu

Step-1
Enabling mod_ssl

```
sudo a2enmod ssl
```

Restart apache2 server
```
systemctl restart apache2
```

Step 2 – Creating the SSL Certificate
```
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt
```

```
/etc/apache2/sites-available# vi deepaktxt.com.confvi deepaktxt.com-ssl.conf
```
```
a2ensite deepaktxt.com-ssl.conf 
```
```
a2dissite default-ssl.conf
```
```
systemctl reload apache2
```
```
a2enmod ssl
```
```
systemctl restart apache2
```
