# Disable Rounded Window Corners
Big Sur brought about a lot of nonsense in my opinion. The quality of the desktop wallpapers have diminished down to a simpleton level of creativity.The one visible change that just turns my stomach is the rounded window corners, I absolutely detest these rounded window corners that were introduced in Big Sur. After searching for awhile and not going anywhere, I finally found a solution. If it was not for ThemeEngine. I would have not been able to pull this off. I have included this within this repository as well.


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
> This must be done everytimne Apple puts out a minor macOS update, after reboot the ball sack corners are back. Rinse and repeat.
>


### No More Rounded Corners.
![macOS disable rounded corners](./images/NoMoreRoundedCorners.png)
