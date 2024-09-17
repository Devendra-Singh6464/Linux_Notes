
Go to root and 
```
vi /etc/hosts
```

and add this line
```
127.0.0.1    <domain_name>
127.0.0.1    <subdomain_name>
```

go to this `vi /etc/apache2/sites-available/000-default.conf`   directory and add this line

```
<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName bhandari.demo
        ServerAlias dev.bhandari.demo

        ServerAdmin webmaster@localhost
        DocumentRoot /home/users/devendra.singh/www/html

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        # Include conf-available/serve-cgi-bin.conf

        # Redirect "/" "https://127.0.0.1"
</VirtualHost>
```

write ServerName (domain_name)
write  ServerAlias(subdomain_name)
DocumentRoot <your_path>

last ensite the changed file
``````
a2ensite 000-default.conf
```
