# mbed-client-rpi-executables
Sample executable code that runs on Raspberry Pi and connects to Zatar

# Brief Summary of Features
There are two execuables in this repo:
  
1. mbed-client-rpi-zatar-date. This executable ('mbed-client') can be run alone or in conjunction with the 'watchDog' file (see below). When invoked, this code will attempt to connect your Pi to the Zatar IoT cloud service. Before you try it, make sure your Pi is connected to the Internet hooked up to a keyboard and display, so you can see the on-screen instructions. If all goes well, your board should connect to Zatar with no intervention, but it's good to see the console messages at least for the first few times to fammiliarize yourself with the program's operation. After your Pi is connected to Zatar, you only need go to www.zatar.com, log into your account, and perform the "add device" (or claim) function from your Home World to add your Pi to your account. To do this, you'll need the board's serial number which is displayed for you on the console output of your Pi.
2. watchDog (optional). This executable ('watchDog') will monitor the system to make sure the first program is still running. If the program encounters and error and quits, this program will detect this and simply start the first program back up to help ensure continuous operation. This is useful for long-term monitoring, unattended operations. You can invoke this file at any time before or after the first file is invoked. If you start watchDog first, it will detect mbed-client is not running and start it for you. NOTE: To invoke watchDog, you must type the name of the mbed-client program (full name and path) as a command line argument.
  
# Disclaimers- These are SAMPLE PROGRAMS and not intended for commercial use. You are free to use them in accordance with Zebra's standard free software license, but please understand that you do so at your own risk. Zebra Technologies (or anyone else for that matter) will assume no liability for these sample programs. They are for prototyping and expirimentation only.
# Other
To invoke mbed-client directly, cd to the directory in which the file resides and type the following at the command prompt:
  
    > ./mbed-client-rpi-zatar-date
    
To invoke watchDog, type the following at the command prompt (this assumes both binaries are located in the SAME directory!):
    
    > ./watchDog ./mbed-client-rpi-zatar-date
    
# Miscellaneous
Copyright (c) 2016 Zebra Technologies Corp., All Rights Reserved.