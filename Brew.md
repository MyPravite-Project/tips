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

