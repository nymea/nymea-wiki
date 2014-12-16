# Install *guh*-core on the Beaglebone Black
--------------------------------------------
## Install Ubuntu Trusty
In order to install guh on the [Beaglebone Black](http://beagleboard.org/black) we recomand to use the Ubuntu Trusty 14.04 LTS image. A verry good an easy installation instruction for the microSD card can be found here: 

> Note: this will delete all data from your microSD card!

[Downloads Ubuntu Trusty 14.04 LTS on the BeagleBone Black](http://www.armhf.com/download/)

[Installation of Ubuntu Trusty 14.04 LTS on the BeagleBone Black](http://www.armhf.com/boards/beaglebone-black/bbb-sd-install/)

### Install Ubuntu to eMMC (internal flash drive)
Once you have installed Ubuntu Trusty 14.04 LTS on your microSD you can connect the network cable and power on the Beaglebone Black. This description works theoreticaly with eny other distribution (not tested).

1. Finding the Beaglebone Black in the network. Assuming the router has the ip `192.168.1.1` you can use `nmap` for discovering your device:
    
        $ sudo nmap -sP 192.168.1.1/24
    
    You should get a list of all devices connected to the network. An example of a Beaglebone Black could look like this:
    
        Nmap scan report for 192.168.1.51
        Host is up (-0.093s latency).
        MAC Address: 11:22:33:44:55:66 (Texas Instruments)
        
    > Note: the device with *Texas Instruments* in it is possibly the Beaglebone Black.

2. SSH login to the Beaglebone Black with the user `ubuntu` and the password `ubuntu` (also the nativ root password): 
        
    $ ssh ubuntu@192.168.1.51
        
3. Find out which device is the eMMC:
    
        $ sudo fdisk -l
        
    should give you something like this
    
        Disk /dev/mmcblk1: 3867 MB, 3867148288 bytes
        4 heads, 16 sectors/track, 118016 cylinders, total 7553024 sectors
        Units = sectors of 1 * 512 = 512 bytes
        Sector size (logical/physical): 512 bytes / 512 bytes
        I/O size (minimum/optimal): 512 bytes / 512 bytes
        Disk identifier: 0x00000000
        
            Device Boot      Start         End      Blocks   Id  System
        /dev/mmcblk1p1   *        2048      198655       98304    e  W95 FAT16 (LBA)
        /dev/mmcblk1p2          198656     7553023     3677184   83  Linux

    In this case, the partitions of the eMMC have allready the right size and system.

4. Format the partitions:
    > Note: this will delete all data from your microSD eMMC!
    
        $ sudo mkfs.vfat /dev/mmcblk1p1
        $ sudo mkfs.ext4 /dev/mmcblk1p2
    
5. Mount the partions:
    
        $ sudo mkdir /mnt/boot
        $ sudo mount /dev/mmcblk1p1 /mnt/boot/
        $ sudo mkdir /mnt/rootfs
        $ sudo mount /dev/mmcblk1p2 /mnt/rootfs/
    
6. Download the uboot and the rootfs of Ubuntu Trusty 14.04 LTS (links from [here](http://www.armhf.com/download/):
    
        $ wget http://s3.armhf.com/dist/bone/bone-uboot.tar.xz
        $ wget http://s3.armhf.com/dist/bone/ubuntu-trusty-14.04-rootfs-3.14.4.1-bone-armhf.com.tar.xz
    
7. Install the system:
    
        $ sudo tar xJvf bone-uboot.tar.xz -C /mnt/boot/
        $ sudo tar xJvf ubuntu-trusty-14.04-rootfs-3.14.4.1-bone-armhf.com.tar.xz -C /mnt/rootfs/
    
8. Poweroff the Beaglebone Black, remove the microSD card and boot into your brand new Ubuntu Trusty 14.04 LTS.

## Install *guh*

> Comming soon...











