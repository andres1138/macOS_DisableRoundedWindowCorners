# Disable Rounded Window Corners
>If you detest the rounded corners that were introduced in Big Sur like I do. This will help you disable them. It made my stomach turn when I first laid eyes upon them. The nausea turned into bitter hatred very quickly.
> This should work with the newer operating system,  but I do not know for sure as I do not have a mac at this point and time unfortunately.

### Disable SIP
> Unfortunately System Integrity Protection must be disabled in order to make this work.
> * REMEMBER to unplug any EGPU's and external monitors before entering in these commands.
> * I speak from expierence, if not unplugged, you will end up reinstalling the operating system. That gets very old after awhile.

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

# Now make your changes within System Appearance bundle, if you just want to get rid of the rounded window corners, you can just drop my .car files to replace the ones you have
# after making the edits, enter these commands

sudo kmutil install --volume-root ~/livemount --update-all
# ignore warnings

# bless it and create the snap shot
sudo bless --folder ~/livemount/System/Library/CoreServices --bootefi --create-snapshot

# Reboot and that's that
```
---  
#### Caveat  
> This must be done everytime there is an macOS update, the kind of update that requires you to restart, after installing update and rebooting the roundness returns once again turning my stomach the same way it did when I first laid eyes upon it with Big Sur's introduction. 
> Rinse and Repeat, and it will go away until the next update.
---   
### Working with ThemeEngine   
> When you have found the specific piece of graphic to customize, such as these window corners, you may run into an issue where ThemeEngine will not save. What worked for me was open the graphic from ThemeEngine to Photoshop or any image editor you use. When you are finished with your customization edits, save the image as png, and drag it onto the unedited graphic within ThemeEngine and it should save without any problems. 

####### I wish I could exaplin more and have an up to date car file for the newest macOS, I am currently trying to save up the money to do so. Hopefully by next year I will be able to purchase a new mac and update everything. I hope this helps anyone out there who despises these useless rounded corners.

### Please donate if possible
> Recently a house fire destroyed my home and everything that had sentimental value to me burned to ashes, I am greatful I was able to get my cat out with me. I have been slowly trying to buiild everything back, any donations would help.
#### BTC
1FEGm3Bp45rzjfKKuGQbFsbWtFSmgVsaAP

### No More Rounded Corners.
![macOS disable rounded corners](./images/NoMoreRoundedCorners.png)
