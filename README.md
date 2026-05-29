# macOS Disable Rounded Window Corners
> Big Sur introduced a lot of absolute nonsense, Notification Center cannot be disabled and removed, the wallpapers have diminished down to a simpleton level of creativity, Finder got a logo make over it did not need along with a chunky title bar that is mostly dead space and above all as a final insult to injury the radius of the window corners got cranked up to a level that is way below good taste. If you detest these rounded window corners like I do. This will help you disable them. I honestly can't forget how my stomach turned when realizing that I was stuck with it. I had to figure out a way to get rid of them and achieved that goal. The is the original repo to help others in need.
---
> [!NOTE]
>  If you take a look at my png's I created you can see that I created a very subtle 3px corner radius and the reason being is that if I took the easy way out and just slopped it a single color with a 90 degree corner. It does not have that smooth aesthetic to it. Why go from extremely rounded to extrememly square when you can go back to what Apple had in the good old days.

---
> [!CAUTION]
>  Backup any and all files that will be edited.

> [!WARNING]
>  Unplug any external GPUs before attempting this.


> [!NOTE]
>  This works and has been tested on macOS 15.5


### Disable SIP & Authenticated Root Volume
```
csrutil disable
csrutil authenticated-root disable
```
### Backup System Appearance Resources
```
# I chose to back the resources to a folder on my desktop
rsync -rI \
    /System/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/  ~/Desktop/saResourcesBackup
```

### Find the disk volume 
```
# this command will find the correct disk instead of manually seaching for it with diskutil list command
df / | tail -1 | awk '{print $1}' | sed 's/s[0-9]*$//'
# mine is /dev/disk2s5
```
### Create the livemount directory and mount it
```
mkdir ~livemount

# mount it
sudo mount -o nobrowse -t apfs  /dev/disk1s5 ~/livemount

# At this point you can copy the DarkAqua.car files into ~/livemount/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/

# After you have replaced the DarkAqua.car you will need to bless it so macOS boots from the modified filesystem
sudo bless --mount ~/livemount --bootefi --create-snapshot
```
## Reboot and the annoying rounded corners are gone.

### I have already done the work for you and have ready DarkAqua.car files for the newer macOS operating systems.

---  
#### Caveat  
> This must be done everytime there is a macOS update, the kind of update that requires you to restart, after rebooting it is back to same bullshit.
> Rinse and Repeat, and it will go away until the next update.
---   
### Working with ThemeEngine   
> When you have found the specific piece of graphic to customize, such as these window corners, you may run into an issue where ThemeEngine will not save. What worked for me was to open the graphic from ThemeEngine to Photoshop or any image editor you use. When you are finished with your customization edits, save the image as a png, and drag it onto the unedited graphic within ThemeEngine and it should save without any problems. 




### BTC Address
> 1FEGm3Bp45rzjfKKuGQbFsbWtFSmgVsaAP
### ETH Address
> 0x72982BdEd804E4dD320Ea5F308b9201209f4C34F

### No More Rounded Corners.
![macOS disable rounded corners](./images/NoMoreRoundedCorners.png)
