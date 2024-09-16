Backup database:
--------------------------------------------
```
mysqldump --opt -h <servername> -u <username> -p<password> <dbname> | gzip > <bkup_file_name.gz>
```

```
mysqldump --opt -h localhost -u root -pRoot@123 test | gzip > bkup.gz; 
```

all database backup:
```
mysqldump -u root -p --all-databases > backup.sql
```

Restore Database:
---------------------------------------------
```
mysql -u <username> -p<password> -e 'CREATE DATABASE <dbname>';
```

```
gunzip < <bkup_file_name.gz> | mysql -u <username> -p<password> <dbname>;
```

```
mysqldump -u root -pRoot@123 --databases txt woldp wp magento> bkp.sql
```

```
mysql -u root -p < backup.sql(filename)
```

restore data using SQL:
```
mysql -u root -pRoot@123 <./bkp.sql
```


Create database table.
```
CREATE TABLE USERS1(ID int(10), name varchar(50), city varchar(50),PRIMARY KEY(id));
```

Insert data into data base table.
```
INSERT INTO USERS1 VALUES(101,'rahul','delhi');  
```


mysql database backup and restore  
backup mysql database- mysqldump -u root -p --all-databases > backup.sql(filename give to the backup file)  
  
