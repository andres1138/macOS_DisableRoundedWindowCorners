# Disable Rounded Window Corners
>If you detest the rounded corners that were introduced in Big Sur like I do. This will help you disable them. It made my stomach turn when I first laid eyes upon them. The nausea turned into bitter hatred.
> This should work with the newer operating system but I do not know for sure as I do not have a mac at this point and time unfortunately.

# I DO NOT KNOW IF THIS WILL STILL WORK!
> Unfortunately I have not been able to get a new Mac to test this out on. The mac I use now is obsolete and not supported anymore.

### Disable SIP   
> Go into Apple Recovery and open the terminal and type in
```
csrutil disable

# enable it back
csrutil enable
```

# Instructions

> * REMEMBER to unplug any EGPU's and external monitors before entering in these commands.
> * I speak from expierence, if not unplugged, you will end up reinstalling the operating system. That gets very old after awhile.

1. mkdir ~/livemount
           
2. diskutil list  #(It will be under (synthesized), yours may not be named disk2s5)
                      
3. sudo mount -o nobrowse -t apfs  /dev/disk2s5 ~/livemount
           
4. cd ~/livemount

### Make the edits

> If you just want the rounded corners gone, then you can just take my edited DarkAqua.car file and replace the one in ~/livemount/System/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/DarkAqua.car


> I apologize for not having a Aqua.car file ready, I live in dark mode.

5. sudo kmutil install --volume-root ~/livemount --update-all


#### You will get this warning after this step. It is nothing to worry about.
>
>warning: unable to create release extension manager, expect errors
Error Domain=KMErrorDomain Code=34 "Missing Developer Kit: As of macOS 13.0, you will need to install a KDK matching your build 22E252 to rebuild kernel collections." UserInfo={NSLocalizedDescription=Missing Developer Kit: As of macOS 13.0, you will need to install a KDK matching your build 22E252 to rebuild kernel collections.}
>
           
6. sudo bless --folder ~/livemount/System/Library/CoreServices --bootefi --create-snapshot

7. reboot the comp and that's that.
---
---  
#### Caveat  
> This must be done everytime there is an macOS update, the kind of update that requires you to restart, after installing update and rebooting the roundness returns once again turning my stomach the same way it did when I first laid eyes upon it with Big Sur's introduction. 
> Rinse and Repeat, and it will go away until the next update.
---   
### Working with ThemeEngine   
> When you have found the specific piece of graphic to customize, such as these window corners, you may run into an issue where ThemeEngine will not save. What worked for me was open the graphic from ThemeEngine to Photoshop or any image editor you use. When you are finished with your customization edits, save the image as png, and drag it onto the unedited graphic within ThemeEngine and it should save without any problems. 

####### I wish I could exaplin more and have an up to date car file for the newest macOS, I am currently trying to save up the money to do so. Hopefully by next year I will be able to purchase a new mac and update everything. I hope this helps anyone out there who despises these useless rounded corners.

### No More Rounded Corners.
![macOS disable rounded corners](./images/NoMoreRoundedCorners.png)
