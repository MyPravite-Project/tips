# RVM and Textmate

From [http://rheimbuch.posterous.com/rvm-and-textmate](http://rheimbuch.posterous.com/rvm-and-textmate)

## From a terminal run
    
    rvm [ruby-version] --symlink textmate

ie.

    rvm 1.8.7 --symlink textmate
    
or

    rvm jruby --symlink textmate

Run the previous command whenever you want to change the ruby that Textmate uses

## In Textmate goto

Preferences -> Advanced -> Shell Variables

Add a variable named TM\_RUBY

Set the value of TM\_RUBY to: /Users/[username]/.rvm/bin/textmate_ruby

