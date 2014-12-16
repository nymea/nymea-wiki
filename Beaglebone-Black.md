# Install *guh*-core on the Beaglebone Black
--------------------------------------------
In order to install guh on the [Beaglebone Black](http://beagleboard.org/black) we recomand to use the Ubuntu Trusty 14.04 LTS image. A verry good an easy installation instruction for the microSD card can be found here: 

> Note: this will delete all data from your microSD card. 

[Downloads Ubuntu Trusty 14.04 LTS on the BeagleBone Black](http://www.armhf.com/download/)

[Installation of Ubuntu Trusty 14.04 LTS on the BeagleBone Black](http://www.armhf.com/boards/beaglebone-black/bbb-sd-install/)

### Install Ubuntu to eMMC (internal flash drive)
Once you have installed Ubuntu Trusty 14.04 LTS on your microSD you can connect the network cable and power on the Beaglebone Black. This description works theoreticaly with eny other distribution (not tested).

First you need to find the Beaglebone Black in the network. Assuming your router has the ip `192.168.1.1` you can use `nmap for discovering your device`:

    $ sudo nmap -sP 192.168.1.1/24

You should get a list of all devices connected to the network. An example of a Beaglebone Black could look like this:

    Nmap scan report for 192.168.1.51
    Host is up (-0.093s latency).
    MAC Address: 11:22:33:44:55:66 (Texas Instruments)
    
> Note: the device with *Texas Instruments* in it is possibly the Beaglebone Black.

Now you can log in to the beaglebone black with the user `ubuntu` and the password `ubuntu`. 

    $ ssh ubuntu@192.168.1.51
    
