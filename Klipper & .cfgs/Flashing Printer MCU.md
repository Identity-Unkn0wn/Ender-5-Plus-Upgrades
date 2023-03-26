# Flashing Printer MCU
So this part isn't really that hard, but you do have to pay attention to what you're selecting. I will place a link with the vanilla .cfg files from Klipper. You are more than welcome to use mine and change it, but remember this is what works for me and you will want to adjust for your preferences.
> * *Reference:* [Klipper Config SKR 3](https://github.com/Klipper3d/klipper/blob/master/config/generic-bigtreetech-skr-3.cfg) / [Ender 5 Plus](https://github.com/Klipper3d/klipper/blob/master/config/printer-creality-ender5plus-2019.cfg) vanilla files

## Building MCU Firmware
This for the BTT SKR 3 EZ
* In your terminal, insert ` cd ~/klipper/ ` and press enter
* insert ` make menuconfig ` and press enter
> * **NOTE:** *A menu will apppear well go through it*
* press the space bar to ` Enable extra low-level configuration options `
* Arrow down to ` Processor model (***) ' (* it'll have something stock here) and press enter
* Arrow down until you see ` STM32H743 ` and press enter
* Ensure ` Bootloader offset ` is set to ` 128kiB `
* Arrow down to ` Clock Refrence ` and press enter
* Arrow down to ` 25 MHz crystal ` and press enter
* Everything else here can stay the same
* Press ` q ` 
* When dialog box appears type ` y `. This will bring you back to the main screen.
* insert `make ` and press enter

## Flashing MCU
You will need the SD card that came with your printer (or similar). to be inserted into your computer at this time.
* Open up WinSCP ([downlad](https://winscp.net/eng/download.php))
* Ensure ` SFTP ` is selected
* Insrt your host name(this will be your IP address)
* Insert your user name and password
* Select ` Login `
> * **NOTE:** *On the left hand side you will want to ensure you open the folder where your removable drive is*
> * **NOTE:** *On the right will be your raspberry pi folders and where this next section will refering to*
* ensure you are in path `/home/(your username)/klipper/out
* drag and drop the ` klipper.bin ` file over to the sd card side
* rename the file to ` firmware.bin `
* close out of the program
* eject the sd card out of the computer
> * **NOTE:** *Ensure your printer is off at this point*
* Insert your sd card into the MCU 
* power on the printer
* I usually let the printer sit for 5ish minutes to ensure its flashed, but it doesn't really take that long.
* Power off and remove SD card
> * **NOTE:** *MCU should be flashed at this point, to verify insert SD card back into PC and check that the file has gone form `firmware.bin` to `FIRMWARE.bin` the all camps firmware is your confirmation*

## Serial Port Path
This part might be better off in another section, but since were not in the UI just yet best to just grab this information now.
> * **NOTE:** *Your printer should be connected to your raspberry pi at this point.*
* Open up your terminal of choice
* insert ` ls /dev/serial/by-id/* `
> * **NOTE:** *It should display something like this `/dev/serial/by-id/usb-Klipper_stm32h743xx_400029000B51303138393138-if00`*
* Copy your serial address to somewhere you can get to later on.


<sub> [Mainsail Configuration](Mainsail.md)

<sub>[Home](../readme.md)

<sub>[Top](#flashing-printer-mcu)