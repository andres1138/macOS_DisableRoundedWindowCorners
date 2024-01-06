# Disable Rounded Window Corners
>If you detest the rounded corners that were introduced in Big Sur like I do. This will help you disable them. It made my stomach turn when I first laid eyes upon them. The nausea turned into bitter hatred.
> This should work with the newer operating system but I do not know for sure as I do not have a mac at this point and time unfortunately.

# I DO NOT KNOW IF THIS WILL STILL WORK!
> Unfortunately I have not been able to get a new Mac to test this out on. The mac I use now is obsoleete and not supported anymore.

# Instructions

> * REMEMBER to unplug any EGPU's and external monitors before entering in these commands.
> * I speak from expierence, if not unplugged, you will end up reinstalling the operating system. That gets very old after awhile.

1. mkdir ~/livemount
           
2. diskutil list - (It will be under (synthesized), yours may not be named disk2s5) 
           
3. sudo mount -o nobrowse -t apfs  /dev/disk2s5 ~/livemount
           
4. cd ~/livemount

### Make the edits

> If you just want the rounded corners gone, then you can just take my edited DarkAqua.car file and replace the one in ~/livemount/System/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/DarkAqua.car


> I apologize for not having a Aqua.car file ready, I live in dark mode, but I promise I am working on it.

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
> This must be done everytimne Apple puts out a minor macOS update, after installing update and rebooting the roundness returns once again turning my stomach as a look in disgust and agony,
> Rinse and Repeat


### No More Rounded Corners.
![macOS disable rounded corners](./images/NoMoreRoundedCorners.png)
