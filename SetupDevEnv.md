# Setup Development Environment

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

## DO SOME MORE STUFF HERE

## Generate SSH public key

	ssh-keygen -t rsa

## Copy SSH public key to GitHub

	cat ./ssh/id_rsa.pub | pbcopy
