# Setup Development Environment

Based on [The Install (Snow Leopard Edition)](http://blog.therubymug.com/blog/2010/05/20/the-install-osx.html)

## Setup Dotfiles

From

	http://github.com/hashrocket/dotmatrix
	http://github.com/jferris/config_files
	http://github.com/ryanb/dotfiles
	

## Remove system gems

	sudo rm -r /System/Library/Frameworks/Ruby.framework/Versions/1.8/usr/lib/ruby/gems/1.8
	sudo gem update --system
	sudo gem clean

## Install [Homebrew](http://github.com/mxcl/homebrew)

	ruby -e "$(curl -fsS http://gist.github.com/raw/323731/install_homebrew.rb)"

## Install [Xcode](http://developer.apple.com/technology/xcode.html)

Don't use Xcode from DVD. Download the newest version.

## Install Git

	brew install git

## Install MySQL

	brew install mysql

## Edit my.cnf for UTF-8 ([Source](http://darwinweb.net/articles/configuring-mysql-for-utf8-under-homebrew))

	vim /usr/local/var/mysql/my.cnf
	
The file should contain

	[mysqld]
	collation_server=utf8_general_ci
	character_set_server=utf8
	
Then restart MySQL

	launchctl stop com.mysql.mysqld
	launchctl start com.mysql.mysqld

## Install [RVM](http://rvm.beginrescueend.com/rvm/install/)

	bash < <( curl http://rvm.beginrescueend.com/releases/rvm-install-head )

## Link Homebrew's Readline

	brew link readline

## Install Rubies ([Source](http://blog.plataformatec.com.br/tag/rvm/))

	rvm install 1.8.7 -C --enable-shared,--with-readline-dir=/usr/local
	rvm install ree -C --enable-shared,--with-readline-dir=/usr/local
	rvm install 1.9.2 -C --enable-shared,--with-readline-dir=/usr/local
	
Setup gemsets ([Source](http://www.cantinaconsulting.com/2010/08/25/rocking-out-with-ruby-rails-and-rvm/))

	rvm gemset create rails2
	rvm gemset create rails3
	rvm use 1.8.7@rails2
	gem install rails
	rvm use 1.8.7@rails3
	gem install rails

Switch between Rails 2 and 3

	rvm use 1.8.7@rails2
			OR
	rvm use 1.8.7@rails3

Finally, set default Ruby

	rvm --default 1.8.7@rails2


## DO SOME MORE STUFF HERE

## Generate SSH public key

	ssh-keygen -t rsa

## Copy SSH public key to GitHub

	cat ./ssh/id_rsa.pub | pbcopy
