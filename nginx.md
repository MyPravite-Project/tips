## Startup script

### Download nginx startup script
    
    wget -O init-deb.sh http://library.linode.com/assets/660-init-deb.sh

### Move the script to the init.d directory & make executable

    sudo mv init-deb.sh /etc/init.d/nginx
    sudo chmod +x /etc/init.d/nginx

### Add nginx to the system startup

    sudo /usr/sbin/update-rc.d -f nginx defaults

### Now we can control nginx using

    sudo service nginx stop
    sudo service nginx start
    sudo service nginx restart
    sudo service nginx reload