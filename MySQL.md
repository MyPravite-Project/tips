# MySQL

## Various tips

### Start and Stop (Homebrew)

Start

    launchctl load -w ~/Library/LaunchAgents/com.mysql.mysqld.plist

Stop

    launchctl unload -w ~/Library/LaunchAgents/com.mysql.mysqld.plist


### My.cnf (Homebrew)

    /Users/[username]/.my.cnf
    
Config file:
    
    [mysqld]
    #Max packetlength to send/receive from to server.
    max_allowed_packet=64M
    socket = /tmp/mysql.sock
    collation_server = utf8_unicode_ci 
    character_set_server = utf8
    skip-character-set-client-handshake # enforce using of utf8 encoding in db

    #This option makes InnoDB to store each created table into its own .ibd file.
    innodb_file_per_table

    [mysql]

    [client]
    socket = /tmp/mysql.sock

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