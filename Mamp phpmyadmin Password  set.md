
If you set phpmyadmin login password so.
go to  `.zshrc`.
1.
```
vi /Applications/MAMP/bin/phpMyAdmin/config.inc.php
```
 and set phpmyadmin password.
 
```
 phpmyadmin <your_password>.
```

2. 
```
vi /Applications/MAMP/bin/phpMyAdmin5/config.inc.php
```
Edit `password`
```
$cfg['Servers'][$i]['user']          = 'root';      // MySQL user
$cfg['Servers'][$i]['password']      = 'webkul123';      // MySQL password (only needed).
```

if you set mamp default php version also terminal.
```
export PATH=/Applications/MAMP/bin/php/<your_php_version>/bin:PATH
```

edit`password`
```
$cfg['Servers'][$i]['user']          = 'root';      // MySQL user
$cfg['Servers'][$i]['password']      = 'webkul123'; // MySQL password (only needed
```

and
```
/Applications/MAMP/Library/bin/mysqladmin -u root -p password 
```

