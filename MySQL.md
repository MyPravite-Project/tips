# MySQL

## Backup and Restore

### Backup
  mysqldump -u root -p[root_password (optional, prompted)] [database_name] > dumpfilename.sql

### Restore
  restore:# mysql -u root -p[root_password (optional, prompted)] [database_name] < dumpfilename.sql