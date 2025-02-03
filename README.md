# Disable Rounded Window Corners
> Big Sur introduced a lot of absolute nonsense, Notification Center cannot be disabled and removed, the wallpapers have diminished down to simpleton level of creativity, Finder got a logo make over it did not need along with a chunky title bar that is mostly dead space and above all as a final insult to injury the radius of the window corners got crancked up to a level that is way below good taste. If you detest these rounded window corners like I do. This will help you disable them. I honestly can't forgot how my stomach turned when realizing there was absolutely no way to revert them.
> This will work with Ventura, it may work for the newer ones. I do not know, if someone out there tries and succeeds I would love to know.

### Disable SIP
> Unfortunately System Integrity Protection must be disabled in order to make this work.
> * REMEMBER to unplug any EGPU's and external monitors before entering in these commands.
> * I speak from expierence, if not unplugged, you will end up reinstalling the operating system. 

#### Instructions
```
# Disabling SIP
# if you are using pple Silicon macOS 13.x.x OR newer
csrutil enable --without fs --without debug --without nvram
# warnings can be ignored

# if you are using Apple Silicon macOS 12.x.x
csrutil disable --with kext --with dtrace --with basesystem

# launch the terminal when macOS finishes booting up

# make a back up of the System Appearence files
rsync -rI \
    /System/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/  ~/Desktop/saResourcesBackup

# create livemount directory
mkdir ~/livemount

# list devices and volumes
# find your main HD or SS macOS is installed on, more than likely your disk is not named disk2s5
diskutil list

# mount your HD SS disk into livemount
sudo mount -o nobrowse -t apfs  /dev/disk2s5 ~/livemount

# Now make your changes within System Appearance bundle, if you just want to get rid of the
#rounded window corners, you can just drop my .car files to replace the ones you have
# after making the edits, enter these commands

# I can't find the KDK for my specific build which is 22H417 to succesfully run this command, It can be skipped.
sudo kmutil install --volume-root ~/livemount --update-all


# bless it and create the snap shot
sudo bless --folder ~/livemount/System/Library/CoreServices --bootefi --create-snapshot

# Reboot and that's that
```
---  
#### Caveat  
> This must be done everytime there is a macOS update, the kind of update that requires you to restart, after rebooting it is back to same bulls**t.
> Rinse and Repeat, and it will go away until the next update.
---   
### Working with ThemeEngine   
> When you have found the specific piece of graphic to customize, such as these window corners, you may run into an issue where ThemeEngine will not save. What worked for me was to open the graphic from ThemeEngine to Photoshop or any image editor you use. When you are finished with your customization edits, save the image as a png, and drag it onto the unedited graphic within ThemeEngine and it should save without any problems. 

###### Hopefully in the forseeable future I will be able to purchase a new Mac to be able to create car files for the current macOS.


### No More Rounded Corners.
![macOS disable rounded corners](./images/NoMoreRoundedCorners.png)
