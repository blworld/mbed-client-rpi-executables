# mbed-client-rpi-executables
Demo program that connects a Raspberry Pi with attached [PiBrella board](pibrella.com) to [Zatar](http://www.zatar.com)

## Summary of Features
* Connects your Pi to zatar as a device via our LwM2M Device API using the [ARM mBed Client](https://www.mbed.com/en/development/software/mbed-client/)
* Provides a universal Avatar for your Pi on Zatar, and makes it available via our [Device Portal](https://api2.zatar.com/rdm-js), the [Zatar iPhone app](https://itunes.apple.com/us/app/zatar-rdm-for-iphone/id720896275?mt=8), or our REST API
* Exposes three LEDs and one Button from PiBrella expansion board and makes them accessible via Zatar
* You can toggle any of the LEDs from the API, Device Portal, iPhone App.
* When you press the button on the piBrella, you can see the state of the button ("UP" or "DOWN") on the Pi's Avatar change, as well as see all LEDs toggle, and see a counter increment each time the button is pressed.
* You can reset the button counter via the API, Device Portal, or iPhone App.
* Demo program sends a "keep-alive" signal to Zatar every 30 sec
* Status displayed on Pi console during operation

## Summary of Contents of Repo
There are two execuables in this repo:
  
1. **mbed-client-rpi-zatar**. This executable ('mbed-client') can be run alone or in conjunction with the 'watchDog' file (see below). When invoked, this code will connect your Pi to the Zatar IoT cloud service. 

2. **watchDog** (optional). This executable ('watchDog') will monitor the system to make sure the first program is still running. If the program encounters an error and quits, this program will detect this and simply start the first program back up to help ensure continuous operation. This is useful for long-term monitoring, unattended operations.

## Hardware
To run the demo program you will need the following hardware:

1. The sample program assumes you have a Raspberry Pi Model A, B, 2, or 3 running latest version of Raspian OS.
2. The best way to run the demo is to format an SD card (8GB or larger) and then perform a clean install of the latest version of Raspian by using NOOBS. You can get that [here](https://www.raspberrypi.org/downloads/noobs/).
3. For best results, you also need to install a PiBrella board, which attaches to the Pi's GPIO pins and provides the LEDs and button. You can read about the PiBrella board [here](http://www.pibrella.com). You can run the demo without a PiBrella, but it will have very limited functionality.
4. Keyboard, mouse, and display connected to your Pi so you can view console messages as the program operates.

## Set up and Operation

1. Make sure your Pi is powered up, connected to the Internet, and hooked up to a keyboard and display, so you can see the on-screen messages.
2. To get the files onto your Pi, clone this repo onto your Pi by typing the following at the command prompt (substitute your actual github account username where indicated):

 > git init
 > 
 > git clone https://yourUsername@github.com/zatar-iot/mbed-client-rpi-executables.git
 
3. Then cd to the directory containing the executable files.
4. To invoke mbed-client directly, type the following at the command prompt:

 > sudo ./mbed-client-rpi-zatar

5. When the program runs, it will display its progress on the console. After it has successfully registered your Pi on Zatar, it will display "Success!" and output the serial number of the Pi. Make sure you keep this number handy because you'll need it in the next step. 
6. After your Pi is connected to Zatar, you need go to www.zatar.com, log into your account, and perform the "add device" function from your Home World to add your Pi to your account by following the steps below:
	
 >1. Log into your account on Zatar.	
 >2. Select your Home World.
 >3. From this screen, click on the "Add+" button next to "Devices" to add a new device to your World, and select "Add Device".
 >4. When the dialog appears, type in the serial number of your Pi (from above) into the text box, and hit Next.
 >5. After this, you will be asked to specify the following information:
 >6. **Device Type** - Click on the first drop-down and select "IoTKit".
 >7. **Manufacturer** - Click on the second drop-down and select "Raspberry Pi Foundation".
 >8. **Model** - Click on the third drop-down and select "RaspberryPiIoTKit".
 >9. Hit "Next".
 >10. In the next dialog you can optionally enter a name for your Avatar as well as text describing its location. Both are optional and can be changed later if you wish. When you are done, hit "Next".

7. After that, you should see your Pi's Avatar in the Zatar Device Portal with status of "online". **Your Pi is now on Zatar!**

### Optional Program "watchDog"
The "mbed-client-rpi-zatar' program is written so that it will terminate whenever it encounters a problem, such as network errors, etc. To help keep the program running longer, you may choose to optionally use the included program called "watchDog".

This program will simply watch for the execution of the main program, and if it determines the program has terminated, watchDog will restart it.

To invoke watchDog, type the following at the command prompt (this assumes both binaries are located in the SAME directory!):

 > sudo ./watchDog ./mbed-client-rpi-zatar

 You can invoke this file at any time before or after the first file is invoked. If you start watchDog first, it will detect mbed-client is not running and start it for you. NOTE: To invoke watchDog, you must type the name of the mbed-client program (full name and path) as a command line argument.
  
# Disclaimers
**These are SAMPLE PROGRAMS and not intended for commercial use. They are for demonstration purposes only. You are free to use them in accordance with Zebra's standard free software license, but you do so at your own risk. Zebra Technologies Corp. will assume no liability for these programs, and makes no warranty for their suitability for any purpose.** 
    
## Copyright
Copyright (c) 2016 Zebra Technologies Corp., All Rights Reserved.
