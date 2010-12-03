# MySQL

## Various tips

### Find datadir

    mysql> SHOW VARIABLES LIKE 'datadir';

    +---------------+-----------------------+
    | Variable_name | Value                 |
    +---------------+-----------------------+
    | datadir       | /usr/local/var/mysql/ |
    +---------------+-----------------------+
    1 row in set (0.00 sec)


## Backup and Restore

### Backup
  mysqldump -u root -p[root_password (optional, prompted)] [database_name] > dumpfilename.sql

### Restore
  restore:# mysql -u root -p[root_password (optional, prompted)] [database_name] < dumpfilename.sql