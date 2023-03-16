# Installing Klipper
What a trip we've had right, sit tight were almost done.

## Prep an OS image
* Download OS
  * Inserd Micro SD card into computer
  * Download [Raspberry Pi Imagur](https://downloads.raspberrypi.org/imager/imager_latest.exe)
  * Once installed select `Choose OS`
   > * **NOTE:** if it gives an error exit and open it back up, seems to be a common issue.
  * Scroll to `Raspberry Pi OS (Other)` and select
  * Scroll to `Raspberry PI on Lite (64 bit)` amd select
    > * You will see a settings icon appear, we will get to that shortly
  * select `Choose Storage`
    > * Please please please make sure you select the correct storage device Don't come crying on here that I caused your hard drive to be wiped. I have yet to see any of mine show up but I have see YT vids of it happening.
  * Select the `Settings Icon` on the bottom right
  * Scroll to `Enable SSH` and enable the box
  * Scroll down from there and set your SSH `User Name` & `Password`
  * *Optional:* Configure your wireless LAN 
  >  *  This part is optional if your intent is to use a wired connection, nothing is needed here.
  > * Don't forget to set your `Wireless LAN Country` (example if you're in good ole 'Murica scroll to select `US`)
  * Next, select `Select Local Settings` 
  >  * Set things to your local setting
  * Select `Save`
   > * Window will close
  *  Select `Write`
 > My computer usually pops a notification, just ignore or close them out. This part may take a while, just sit tight and let it finished. Once it's complete it will auto eject the drive.

## Installing Raspbeery Pi OS
Buckle up this one is going to be a long one.
* if your Pi is powerd up, turn it off
* Insert SD card into SD card slot on said Pi
* Power the Pi up    
* Wait a few minutes
* Then it should be done
* :P
  
## SSHing into your Raspbeery Pi
Ok so there are other ways of doing it, like Putty, but I like using Windows powershell. Most of the steps should be the same either way. If this is your first time using a terminal I promise its not that scary. Well here we go!
* SSH into your Raspberry Pi from a terminal:
  * Open up your favorite terminal
  * Type in `ssh username@your IP address`
   > * You can find your IP address from your router or a program like WinSCP ([here](https://winscp.net/download/WinSCP-5.21.7-Setup.exe))
  * It 