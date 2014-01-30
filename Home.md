#Hive wiki
Hive is a home automation platform for the raspberry pi and can contoll several RF-Modules like swiches and sensors...

For this project a custom wheezy image was created with all the packages needed for this project (Qt 5.1.2, ruby 2.1, Rails 4 ecc.). The image currently is just available for the developer team, so please be patient, the end-users image will be published in 2014. 

#Tabel of content
* [Getting started](https://github.com/HiveFive/Hive/wiki#getting-started)
* [Setup Raspberry Pi SD ](https://github.com/HiveFive/Hive/wiki#setup-raspberry-pi-sd)
* [Customize your new system on the Raspberry Pi](https://github.com/HiveFive/Hive/wiki#customize-your-new-system-on-the-raspberry-pi)
    * [Change your password](https://github.com/HiveFive/Hive/wiki#change-your-password)
    * [Setup your WLAN network](https://github.com/HiveFive/Hive/wiki/#setup-your-wlan-network)
    * [Compile and execute the Hive sourcecode](https://github.com/HiveFive/Hive/wiki#compile-and-execute-the-hive-sourcecode)

##Getting started
To getting started with the code you need:
* Raspberry Pi (Model B)
* RF-Transmitter and Receiver with 433.92 MHz and/or 868 MHz (available on [ebay](http://www.ebay.com/itm/433Mhz-WL-RF-Transmitter-Receiver-Module-Link-Kit-for-Arduino-ARM-MCU-Wireless-/380717845396?pt=LH_DefaultDomain_0&hash=item58a48d4b94) , [Conrad 433 MHz](http://www.conrad.at/ce/de/product/130428/Funk-Sender-Empfaenger-Set-433-MHz-AM-Baustein-Sender-3-12-VACDC-Empfaenger-5-VACDC-Reichweite-max-30-m/?ref=detview1&rt=detview1&rb=2), [Conrad 868 MHz](http://www.conrad.at/ce/de/product/190939/Funk-Sende-Empfaenger-Set-868-MHz-Baustein-Sender-3-12-VACDC-Empfaenger-5-VACDC-Reichweite-max-200-m/?ref=detview1&rt=detview1&rb=2))
* SD Card (minimum 8 GB SD or SDHC card)
* a breadbord or something similar to connect the RF-modules to the GPIO Pins of the RPi

## Setup Raspberry Pi SD
First we have to download the latest hive-wheezy-image from the [hiveyourhome.org FTP](http://www.hiveyourhome.org/) area (currently just available for the hive developer team, sorry).
If the download is finished, unzip and flash the image to the SD card.
Under linux and Mac OSX you can do that with the command (make shore the SD is not mounted)
> replace /dev/sdX with your SD path -> you can find out with the command `fdisk -l` (under Mac OSX `diskutil list`

`dd if=/path/to/image/version-wheezy.img of=/dev/sdX bs=4M`

This could take some minutes...

Now we have our image on the SD card and can boot our system. To do that insert the SD into the RPI, connect the LAN cabel and then connect the power cabel to start the RPi.

To connect over ssh with the RPi we have to find out which IP address the RPi got from the router. A easy way to do that in the terminal is the following commend!! (under Mac OSX you can install `nmap` with [brew](http://brew.sh/) or [macports](http://guide.macports.org/) - I recommand brew).

Execute the command as root (`sudo su`) to get the full message.

>**replace** 10.10.10.1 with the IP from your router

`nmap -sP 10.10.10.1/24`

you should see something like this:

    Nmap scan report for 10.10.10.52
    Host is up (0.013s latency).
    MAC Address: B8:27:EB:57:AC:CA (Raspberry Pi Foundation)

Now we can ssh login into the RPi in the terminal.
> **replace** 10.10.10.52 with the IP from your RPi |-> default user: _hive_ , password: _hive_

`ssh hive@10.10.10.52`

## Customize your new system on the Raspberry Pi
now you should be logged in as hive user in your system.
### Change your password
If you want to change the password type `passwd`, enter the current password and than two times your new password.

### Setup your WLAN network
first you can look if your WiFi stick got recognized by the system. With `lsusb` you should see something like this:

`Bus 001 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]`

With following command you can check all networkinterfaces:

`ifconfig`

if the wlan0 interface appears you can try to scan for your networks with the command:

> NOTE: if you want all information about the visible networks just run `iwlist scan`

`iwlist scan | grep ESSID`

Now you can try to connect to your WiFi network. To do that automaticaly you need to create a wpa_passphrase an add you network into /etc/wpa_supplicant/wpa_supplicant.conf

    hive@hivepi ~ $ sudo su
    [root@hivepi hive]# wpa_passphrase "my_essid" "secret_password" >> /etc/wpa_supplicant/wpa_supplicant.conf

### Compile and execute the Hive sourcecode

run the udate_hive.sh in the hive home directory...

`./update_hive.sh`

this skript updates hive. if everything is ok you can run hive simple with the command hive. If any errors occure, please send me the ~/updatelog.txt file.

### Mount the image on the laptop
if you want to mount the image on the laptop run following command:
`sudo mount -o loop,offset=62914560 20140130_hive-wheezy.img /mnt/hiveimage`

if you change something in the image and unmount it you can reflash the system with this changes...


