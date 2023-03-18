# Installing Klipper
What a trip we've had right, sit tight were almost done.

## Prep an OS image
* Download OS
  * Insert Micro SD card into computer
  * Download *[Raspberry Pi Imager](https://downloads.raspberrypi.org/imager/imager_latest.exe)*
  * Once installed select `Choose OS`
   > * **NOTE:** If it gives an error about downloading an OS directory, exit and open it back up, seems to be a common issue(maybe for just me?).
  * Scroll to `Raspberry Pi OS (Other)` and select
  * Scroll to `Raspberry PI on Lite (64 bit)` and select
    > * You will see a settings icon appear, we will get to that shortly
  * select `Choose Storage`
    > * Please please please make sure you select the correct storage device Don't come crying on here that I caused your hard drive to be wiped. I have yet to see any of mine show up but I have see YT vids of it happening.
  * Select the `Settings Icon` on the bottom right
  * *Optional:* You can set your host name, just be sure you remember/ write it down it will come into play later.
  * Scroll to `Enable SSH` and enable the box
  * Scroll down from there and set your SSH `User Name` & `Password`
  > * WRITE THIS DOWN; YOU WILL NEED IT LATER!
  * *Optional:* Configure your wireless LAN 
  >  *  This part is optional if your intent is to use a wired connection, nothing is needed here.
  > * Don't forget to set your `Wireless LAN Country` (example: if you're in good ole 'Murica scroll to select `US`)
  * Next, select `Set Local Settings` 
  >  * Set things to your local setting
  * Select `Save`
   > * Window will close
  *  Select `Write`
 > My computer usually pops a notification, just ignore or close them out. This part may take a while, just sit tight and let it finish. Once it's complete it will auto eject the drive.

## Installing Raspberry Pi OS
Buckle up this one is going to be a long one.
* if your Pi is powered up, turn it off
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
   > * You set up your user name in the "[Prep an OS Image](#prep-an-os-image)" section.
   > * If you ste up a hostname it will be *"username@whateveryouput.local"*
     * It will then give you a *"warning"* about its authenticity, and if you want to continue type `yes` and press enter
  * Enter your `password` when prompted. 
  > * *Note: The password you type will not appear, but it is there.*
  * Enter `sudo apt-get update`
  * Enter `sudo apt-get upgrade`
  > * If it ask you to continue, just press enter; yes is the default. This sometimes take a minute or two, be patient.
  * Enter `sudo reboot`
  * Give it a minute or two then SSH back into your Raspberry Pi.

## Installing Klipper/ User Interface (UI)
For this portion I'll be using Mainsail as my UI You don't have to use this program, but I've tried Fluidd and Octoprint and while on Marlin I did like Octoprint, Mainsail just jives better for me with Klipper. 

This method is not for everyone, but I can definitely say beginners will probably like this route better than figuring out through the klipper website. Additionally, on the KIAUH website it says the `Raspberry Pi OS Lite (32bit)` is compatible, but I've been using the 64 bit version for a few months and its been working without issue.

* Install git `sudo apt-get install git -y`
* Use this command to download KIAUH into your home directory `cd ~ && git clone https://github.com/th33xitus/kiauh.git`
* Next, you will start KIAUH with `./kiauh/kiauh.sh`
> * Don't be afraid of the interface that pops up after pressing enter
* Type in `1` and press enter
> * This will take you to the install menu
* Type in `1` again and press enter
> * This will start the process of installing Klipper
* Next type `1` to install recommended version of Python and press enter
* Next type in the number of instances of klipper you would like to install
> * You will need 1 per printer
> * if you type in more than 1 instance it will confirm the amount, just hit `Enter` yes is the default
* Next it will give you the option of creating custom names, you can do this later so just enter No is the default.
> * It will now begin installing however many instance of klipper you chose, be patient and let it do the work.
* One that is finished, it will ask to add user to group, hit enter as Yes is the default. 
> * If you hit no you will not have the permissions you need to get to the printer
 * From here it will take you back to the instillation UI screen
 * Now we will install moonraker, Type `2` and press enter
 * it should detect how many instances of klipper you installed and display it, if not type that number in and press enter.
 > * If you have more than one instance, it will ask you to confirm the amount you want to install. Hit enter as Yes is the default.
 * This should be quick, but if not, be patient and let it install.
 * Once this is complete It will take you back to the instillation UI again.
 > * If you have more than one, all of your instances will appear with their IP address.

> Example:

<div align="center">

|Instance Number|IP Address          |
|:-------------:|:------------------:|
| Instance 1:   |192.168.111.345:7125|
| Instance 2:   |192.168.111.345:7126|
</div>

> From here the instance number will continue to rise for the amount of instances you installed and only the digits after the ":" will rise by one number.
* Okay, moving on. Next up, you will want to type `3` to begin installing Mainsail.
> * *NOTE:* It will immediately begin installing
> * *NOTE:* You don't have to choose Mainsail, but that is what I will be continuing on with.
> * *NOTE:* You only need one instance of Mainsail to control all of your printers
* It will pause mid install sad ask if you want to install recommended macros, press enter.
* Wait for it to complete and will boot you back to the install UI
* 