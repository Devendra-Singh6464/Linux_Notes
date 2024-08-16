# Map Domain and Subdomain in Ubuntu.

## Step 1.
```
cd /etc/apache2/site-available
```
copy ya backup 000-default.conf file--
 
```
cp 000-default.conf devweb.com.conf
```
## Step 2.
Edit file--
``` 
vi devweb.com.conf 
```
add this line --
```
<VirtualHost *:80>

    ServerName devweb.com
    ServerAlias www.devweb.com
    ServerAdmin webmaster@localhost
    DocumentRoot /home/users/devendra.singh/www/html/web/index.html
   
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

## Step 3.
After edit file run this command and dismod 000-default.conf file---
```
a2dissite 000-default.conf
```
and enable our site--
```
a2ensite devweb.com.conf
```

## Step 4.
add host entry.---
```
vi /etc/hosts
```

your_ip	your_web_site_name
``` 
127.0.0.1	devweb.com
```

## Step 5. 
```
cd /home/users/devendra.singh/www/html/
```

create web(your web name)
```
mkdir web
```
```
cd web
```
```
/home/users/devendra.singh/www/html/web
```
create file index.html and edit this line---
```
vi index.html 
```
```
<h1> Hello This is demo domian name </h1>
```
 
