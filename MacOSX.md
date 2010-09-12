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