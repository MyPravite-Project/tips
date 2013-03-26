# Dashboard

To turn Dashboard off: 

    defaults write com.apple.dashboard mcx-disabled -boolean YES 

To turn Dashboard on:

    defaults write com.apple.dashboard mcx-disabled -boolean NO 

You have to restart the Dock after making either change for it to take effect:

    killall Dock

# Dock

Lock the Dock to Prevent Changes to Contents

	defaults write com.apple.dock contents-immutable -bool true
	osascript -e 'tell application "Dock" to quit'
	
Unlock the dock

	defaults write com.apple.dock contents-immutable -bool false
	osascript -e 'tell application "Dock" to quit'
	
Lock the Dock to Prevent Changes in Size

	defaults write com.apple.Dock size-immutable -bool yes
	killall Dock
  
Lock the Dock’s Position on the Screen

	defaults write com.apple.Dock position-immutable -bool yes
	killall Dock
	
# Finder

* [How to restore a folder that has turned into a package in OS X](http://www.switchingtomac.com/tutorials/how-to-restore-a-folder-that-has-turned-into-a-package-in-os-x/) using [File Matey](http://www.macupdate.com/info.php/id/25470/file-matey)

* "Open with" cleanup:

		/System/Library/Frameworks/CoreServices.framework/Versions/A/Frameworks/LaunchServices.framework/Versions/A/Support/lsregister -kill -r -domain local -	domain system -domain user
  
# Sharing

  [Enable Screen Sharing or ARD Via SSH](http://www.farawaymac.com/mac-server/enable-screen-sharing-or-ard-via-ssh/)

# Adding DivX/Xvid etc. into iTunes

    /Developer/Tools/SetFile -c TVOD -t MooV [.avi moviefile]

FILE TYPE, FOR: MooV<br />
CREATOR, FOR: TVOD

# Add latency to localhost

[Link](http://daniel.haxx.se/blog/2010/12/14/add-latency-to-localhost/)
  
To simulate a far away server, add RTT time to the localhost device. For example if we add 100 milliseconds (which then makes 200ms ping time to localhost):

    tc qdisc add dev lo root handle 1:0 netem delay 100msec

Restore it back to normal again with:

    tc qdisc del dev lo root
    
# Lion

## Turn off zooming windows

    defaults write NSGlobalDomain NSAutomaticWindowAnimationsEnabled -bool NO

## Screenshots

Disable shadow

    defaults write com.apple.screencapture disable-shadow -bool true
    
Change the type (jpeg, tiff og png)

    defaults write com.apple.screencapture type jpeg
    
Restart SystemUI server

    killall SystemUIServer

Longer deep sleep delay for rMBP

    sudo pmset -a standbydelay 57600