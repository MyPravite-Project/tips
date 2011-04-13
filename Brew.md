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
