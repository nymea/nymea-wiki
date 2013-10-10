Welcome to the Hive wiki!

Hive is a home automation platform for the raspberry pi and can contoll several RF-Modules like swiches and sensors...

#Getting started
To getting started with th code you need:
* Raspberry Pi (Model B)
* RF-Transmitter adn Receiver with 433.92 MHz and/or 868 MHz (available on [ebay](http://www.ebay.com/itm/433Mhz-WL-RF-Transmitter-Receiver-Module-Link-Kit-for-Arduino-ARM-MCU-Wireless-/380717845396?pt=LH_DefaultDomain_0&hash=item58a48d4b94) , [Conrad 433 MHz](http://www.conrad.at/ce/de/product/130428/Funk-Sender-Empfaenger-Set-433-MHz-AM-Baustein-Sender-3-12-VACDC-Empfaenger-5-VACDC-Reichweite-max-30-m/?ref=detview1&rt=detview1&rb=2), [Conrad 868 MHz](http://www.conrad.at/ce/de/product/190939/Funk-Sende-Empfaenger-Set-868-MHz-Baustein-Sender-3-12-VACDC-Empfaenger-5-VACDC-Reichweite-max-200-m/?ref=detview1&rt=detview1&rb=2))
* SD Card (minimum 4 GB SD or SDHC card)
* a breadbord or something similar to connect the RF-modules to the GPIO Pins of the RPi

# Setting up Raspberry Pi
First we need the latest Raspbian image [download](http://www.raspberrypi.org/downloads).
If the download is finished, unzip and flash the image to the SD card.
Under linux you can do that with the command (make shore the SD is not mounted)
> replace /dev/sdX with your SD path -> you can find out with the command `fdisk -l`

`dd if=/path/to/image/version-wheezy.img of=/dev/sdX bs=4M`

This could take some minutes...

Now we have our image on the SD card and we boot our system. Put the SD into the RPI, connect the LAN cabel and start the RPi.
To connect over ssh with the RPi we have to find out what IP address the RPi got from the router. A easy way to do that in the terminal is the following commend !!

>**replace** 10.10.10.1 with the IP from your router

`nmap -sP 10.10.10.1/24`

you should see something like this:

_Nmap scan report for 10.10.10.52
Host is up (0.013s latency).
MAC Address: B8:27:EB:57:AC:CA (Raspberry Pi Foundation)_

Now we can ssh login into the RPi in the terminal.
> default user: _pi_ , password: _raspberry_

