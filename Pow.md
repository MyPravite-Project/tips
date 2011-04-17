# Port problems

https://github.com/37signals/pow/issues/60

# Change Pow port

Add to _~/.powconfig_

    export POW_DST_PORT=81

## IPFW

Edit

    /Library/LaunchDaemons/cx.pow.firewall.plist
    
Change to your desired port

    dst-port 81

Unload / load the IPFW rules

    sudo launchctl unload /Library/LaunchDaemons/cx.pow.firewall.plist
    sudo launchctl load /Library/LaunchDaemons/cx.pow.firewall.plist