Install PHP8.2 and Php8.2-fpm --
```
sudo apt install php8.2 php8.2-fpm
```

Go to ` vi /etc/apache2/sites-available/000-default.conf ` and map domain and sub domain- 
add this line domain mapped to time.

```
<VirtualHost *:80>

    <FilesMatch \.php$>
	    SetHandler "proxy:unix:/run/php/php8.2-fpm.sock|fcgi://localhost/"
    </FilesMatch>

</VirtualHost>
```

At this point, you have successfully installed Apache2 with php8.2-fpm. Note that the path of the php.ini is ‘/etc/php/8.2/fpm/php.ini:
If you need, we can increase the memory limit and the maximum file size for uploads as well as other values by editing:
```
vi /etc/php/8.2/fpm/php.ini
```
+ memory_limit = 256M  
+ upload_max_filesize = 16M  
+ post_max_size = 16M

