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

# Convert all tables to InnoDB

From http://technotes.twosmallcoins.com/?p=356

Change DATABASE to the database name

    mysql -p -e "show tables in DATABASE;" | tail --lines=+2 | xargs -i echo "ALTER TABLE {} ENGINE=INNODB;" > alter_table.sql

    mysql --database=DATABASE -p < alter_table.sql