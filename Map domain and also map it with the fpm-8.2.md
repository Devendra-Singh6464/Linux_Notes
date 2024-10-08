Go to ` vi /etc/apache2/sites-available/000-default.conf ` and map domain and sub domain- 
add this line domain mapped.

```
<VirtualHost *:80>

    ServerName vikas.unopim.com

        <FilesMatch \.php$>
           SetHandler "proxy:unix:/run/php/php8.2-fpm.sock|fcgi://localhost/"
        </FilesMatch>

</VirtualHost>
```

