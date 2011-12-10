# Problems

## Error starting application

### NameError: uninitialized constant YAML::ENGINE

    Create .rvmrc file under your product with "rvm 1.9.2" if you are using Ruby 1.9.2 for that project.

## Port problems

https://github.com/37signals/pow/issues/60

# Change Pow port

Add to _~/.powconfig_

    export POW_DST_PORT=81

## IPFW

Edit

    /Library/LaunchDaemons/cx.pow.firewall.plist
    
Change to your desired port

    dst-port 81

List rules

    sudo ipfw list

Delete older rule

    sudo ipfw delete [rule_id] # For example 00100

Unload / load the IPFW rules

    sudo launchctl unload /Library/LaunchDaemons/cx.pow.firewall.plist
    sudo launchctl load /Library/LaunchDaemons/cx.pow.firewall.plist

Restart Pow

## Rails 2.3

Create a file under your Rails root named config.ru

    # RAILS_ROOT/config.ru
    require "config/environment"

    use Rails::Rack::LogTailer
    use Rails::Rack::Static
    run ActionController::Dispatcher.new
    
## Linking Pow to app

    ~/.pow $ ln -s /path/to/myapp myapp