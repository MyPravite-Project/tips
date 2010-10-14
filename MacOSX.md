# Dashboard

To turn Dashboard off: 
	defaults write com.apple.dashboard mcx-disabled -boolean YES 

To turn Dashboard on:
	defaults write com.apple.dashboard mcx-disabled -boolean NO 

You have to restart the Dock after making either change for it to take effect:
	killall Dock

# Dock

Lock the dock

	defaults write com.apple.dock contents-immutable -bool true
	osascript -e 'tell application "Dock" to quit'
	
Unlock the dock

	defaults write com.apple.dock contents-immutable -bool false
	osascript -e 'tell application "Dock" to quit'
	
# Finder

  [How to restore a folder that has turned into a package in OS X](http://www.switchingtomac.com/tutorials/how-to-restore-a-folder-that-has-turned-into-a-package-in-os-x/) using [File Matey](http://www.macupdate.com/info.php/id/25470/file-matey)
  
# Sharing

  [Enable Screen Sharing or ARD Via SSH](http://www.farawaymac.com/mac-server/enable-screen-sharing-or-ard-via-ssh/)