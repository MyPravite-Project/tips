# Fixing problems

## Error: Cannot write to /usr/local

    sudo chmod -R g+w /usr/local
    sudo chgrp -R staff /usr/local

or

    sudo chown -R `whoami` /usr/local

or

    sudo chmod -R u+rwX /usr/local
      
    
# Brew commands

Use _man brew_ to view the manpage.

## Updating

Update brew

    brew update

Update packages

    brew upgrade

# Gnutls build error

Remove dependencies (pkg-config, libgpg-error, libgcrypt, libtasn1)

    for dep in $(brew deps gnutls); do brew remove --force $dep; done
    
Install Gnutls

    brew install gnutls

# MySQL

    Set up databases to run AS YOUR USER ACCOUNT with:
        unset TMPDIR
        mysql_install_db --verbose --user=`whoami` --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp

    To set up base tables in another folder, or use a differnet user to run
    mysqld, view the help for mysqld_install_db:
        mysql_install_db --help

    and view the MySQL documentation:
      * http://dev.mysql.com/doc/refman/5.5/en/mysql-install-db.html
      * http://dev.mysql.com/doc/refman/5.5/en/default-privileges.html

    To run as, for instance, user "mysql", you may need to `sudo`:
        sudo mysql_install_db ...options...

    Start mysqld manually with:
        mysql.server start

    A "/etc/my.cnf" from another install may interfere with a Homebrew-built
    server starting up correctly.

    To connect:
        mysql -uroot

    To launch on startup:
    * if this is your first install:
        mkdir -p ~/Library/LaunchAgents
        cp /usr/local/Cellar/mysql/5.5.10/com.mysql.mysqld.plist ~/Library/LaunchAgents/
        launchctl load -w ~/Library/LaunchAgents/com.mysql.mysqld.plist

    * if this is an upgrade and you already have the com.mysql.mysqld.plist loaded:
        launchctl unload -w ~/Library/LaunchAgents/com.mysql.mysqld.plist
        cp /usr/local/Cellar/mysql/5.5.10/com.mysql.mysqld.plist ~/Library/LaunchAgents/
        launchctl load -w ~/Library/LaunchAgents/com.mysql.mysqld.plist

    You may also need to edit the plist to use the correct "UserName".
    