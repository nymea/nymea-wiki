# Install *guh*-core on the Raspberry Pi
--------------------------------------------

This tutorial shows you how to install *guh* on the [Raspberry Pi](http://www.raspberrypi.org/). The easiest and recommended way is to use the [raspbian-netinstall](https://github.com/guh/raspbian-netinstall-config) provided by *guh* 
> Thanks to the awesome work of [raspbian-ua-netinst](https://github.com/debian-pi/raspbian-ua-netinst).

## Table of contents:

* [Install *guh* on Debian *jessie*](https://github.com/guh/guh/wiki/Raspberry-Pi#install-guh-on-debian-jessie)
    * [1. Prepare the SD card](https://github.com/guh/guh/wiki/Raspberry-Pi#1-prepare-the-sd-card)  
        * [...using Linux](https://github.com/guh/guh/wiki/Raspberry-Pi#using-linux)
        * [...using MacOS](https://github.com/guh/guh/wiki/Raspberry-Pi#using-macos)
        * [...using Windows](https://github.com/guh/guh/wiki/Raspberry-Pi#using-windows)
    * [2. Copy files](https://github.com/guh/guh/wiki/Raspberry-Pi#2-copy-files-to-sd-card)
    * [3. Install *guh*](https://github.com/guh/guh/wiki/Raspberry-Pi#3-install-guh)
    * [Install *guh* on existing Debian *jessie*](https://github.com/guh/guh/wiki/Raspberry-Pi#install-guh-on-existing-debian-jessie)
* [Install *guh* on Debian *wheezy*](https://github.com/guh/guh/wiki/Raspberry-Pi#install-guh-on-debian-wheezy)
    * [Add Qt repository](https://github.com/guh/guh/wiki/Raspberry-Pi#add-qt-repository)
    * [Install *guh*](https://github.com/guh/guh/wiki/Raspberry-Pi#install-guh)

--------------------------------------------
## Install *guh* on Debian *jessie*

If you want a fresh, new and minimal installation of *guh* on the [Raspberry Pi](http://www.raspberrypi.org/), we recommand to use the [raspbian-netinstall](https://github.com/guh/raspbian-netinstall-config) provided by *guh*, which will install everything you need to run *guh*. Basically you just need to do following three steps:

1. Delete all partitions of the SD card (minimal size of 1GB) and create a new single `64 Mb FAT32` partition.
2. Mount the parition and unzip the latest [guh-netinstall-v0.X.X.zip](http://www.guh.guru:8080/job/build-installer/lastSuccessfulBuild/artifact/guh-netinstall-v0.1.5.zip) file on it.
3. Insert the SD card into the Raspberry Pi, connect the network cable, connect the power cable and wait until the Raspberry Pi performs a reboot.

This procedure will install the whole system directly from the internet with the newest packages and a pre-configured guh installation.

### 1. Prepare the SD card 

In this step we delete all partitions of the SD card and create a new single `64 Mb FAT32` partition.

#### ...using Linux
Assuming your SD card is the device `/dev/sdb`...

    $ sudo fdisk /dev/sdb

Print the partition table using `p` to make sure this is the correct device! (In this example it is a 4GB SD card)

    Command (m for help): p
    Disk /dev/sdb: 3.7 GiB, 3947888640 bytes, 7710720 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x00000000

    Device    Boot     Start       End  Blocks  Id System
    /dev/sdb1             16     97727   48856   b W95 FAT32
    /dev/sdb2          97728   7710719 3806496  83 Linux


Delete all partitions (using `d`, `enter`, `d`)

    Command (m for help): d
    Partition number (1,2, default 2): 
    
    Partition 2 has been deleted.

    Command (m for help): d
    Selected partition 1
    Partition 1 has been deleted.
    
Create a new dos partition table using `o`
    
    Command (m for help): o
    Created a new DOS disklabel with disk identifier 0x2abef6c0.
    
Create a new 64MB partition (`n`, `enter`, `enter`, `enter`, `+64M`)
        
    Command (m for help): n
    
    Partition type:
       p   primary (0 primary, 0 extended, 4 free)
       e   extended
    Select (default p):
    
    Using default response p.
    Partition number (1-4, default 1): 
    First sector (2048-7710719, default 2048): 
    Last sector, +sectors or +size{K,M,G,T,P} (2048-7710719, default 7710719): +64M         

    Created a new partition 1 of type 'Linux' and of size 64 MiB.
    
Change the partition type to W95 FAT32 (`t`, `b`)
    
    Command (m for help): t
    
    Selected partition 1
    Hex code (type L to list all codes): b
    If you have created or modified any DOS 6.x partitions, please see the fdisk documentation for additional information.
    Changed type of partition 'Linux' to 'W95 FAT32'.

Now your partition table should look like this (`p`):

    Command (m for help): p
    Disk /dev/sdb: 3,7 GiB, 3947888640 bytes, 7710720 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x00000000
    
    Device     Boot Start    End Sectors Size Id Type
    /dev/sdb1        2048 133119  131072  64M 83 Linux
    
Write the partition table to the disk and exit using `w`

    Command (m for help): w
    
    The partition table has been altered.
    Calling ioctl() to re-read partition table.
    Syncing disks.

Now you have to format the new partition to vfat (FAT32).

    $ sudo mkfs.vfat /dev/sdb1

#### ...using MacOS
In order to prepare the SD card under MacOS, you need to download the SD Formatter 4.0 for Mac. The *Disk Utility* application from MacOS some how does not fotmat the FAT32 patition corretly. 

1. Download the the *SD Formatter 4.0* application from following link:
    [https://www.sdcard.org/downloads/formatter_4/eula_mac/](https://www.sdcard.org/downloads/formatter_4/eula_mac/)

    You need to agree to the *End User License Agreement* to download the application.
    
2. Install the application by opening the downloaded file `pkg` file and follow the wizard.

3. Open the application (you need to enter your password), choose "Quick Format", name the partiiton to "Boot" and click  `Format `:

    ![SD Formatter MacOS](images/macos-sd-formatter.png)
    
Once the formating is complete you can continue with step [2. Copy files](https://github.com/guh/guh/wiki/Raspberry-Pi#2-copy-files-to-sd-card)

#### ...using Windows
> Coming soon...

### 2. Copy files to SD card

This step should be clear for Windows and MacOS users. Just download the latest [guh-netinstall-v0.X.X.zip](http://www.guh.guru:8080/job/build-installer/lastSuccessfulBuild/artifact/guh-netinstall-v0.1.5.zip) and unzip the file to the new 64 MB partition. 

Also Linux users can do that with the mouse, but for the completeness here are the console instructions:

Mount the SD card:
    
    $ sudo mkdir /mnt/raspberry-boot/
    $ sudo mount -t vfat /dev/sdb1 /mnt/raspberry-boot/    
    $ cd /mnt/raspberry-boot/

Download the latest latest [guh-netinstall-v0.X.X.zip](http://www.guh.guru:8080/job/build-installer/lastSuccessfulBuild/artifact/guh-netinstall-v0.1.5.zip) file:

    $ sudo wget http://www.guh.guru:8080/job/build-installer/lastSuccessfulBuild/artifact/guh-netinstall-v0.1.5.zip

Unzip the file:

    $ sudo unzip guh-netinstall-v0.1.5.zip

Delete the zip file:

    $ sudo rm guh-netinstall-v0.1.5.zip

Umount the partition:

    $ cd ../
    $ sudo umount /dev/sdb1

###  3. Install *guh*
Insert your prepared SD card into your [Raspberry Pi](http://www.raspberrypi.org/), connect the ethernet cable (internet connection needed) and then connect the power supply. That's it! Now you have to wait ~20-30 minutes. Once the installation is finished, the Raspberry Pi will reboot and boot into the new system. 

> **Note:** It's important to connect the network cable **before** you connect the power cable! DHCP will be one of the first things during the installation!

> **Info:** You can follow the installation process if you connect the Raspberry Pi to a HDMI display!

> **Info:** The log file of the whole *guh*-installation process can be found in `/var/log/installer.log`.

In order to check if the installation has finished you can try to connect over `ssh` to the Raspberry Pi. When the installation has finished, the Raspberry Pi will reboot and boot the fresh system...and you will be able to connect:

    $ ssh root@192.168.1.51
    $ password: guh

Now you have a fresh, clean and minimal installation of Debian *jessie* with *guh*. The `root` password is `guh`!

You can proceed with the [[Getting started]] instructions.

### Install *guh* on existing Debian *jessie*
If you already have a Debian *jessie* installation and want to install *guh* you need to add the *guh*-repository to your `/etc/apt/sources.list`:

1. Add the [*guh*-repo](http://repo.guh.guru/) to the source list file:
        
        $ sudo nano /etc/apt/sources.list
            
    Append following two lines at the end of the file:
    
        ## guh repo
        deb http://repo.guh.guru jessie main

2. Update your package lists:
    
        $ sudo apt-get update
    
    The *guh*-repo provides following packages:
    
        $ apt-cache search guh
    
        guh - server for home automation systems - meta package
        guh-dbg - server for home automation systems - debug symbols
        guh-doc - documentation for the guh package (on-site)
        guh-plugins - server for home automation systems - plugins
        guh-tests - tests for the guh package
        guhd - server for home automation systems
        libguh1 - server for home automation systems - core library
        libguh1-dev - server for home automation systems - development files

3. Install *guh* with following command:
    
        $ sudo apt-get install guh libgl1-mesa-dev -y --force-yes
        
    > Note: you need to install the packages without verification.

    The repository contains always the latest stable build of the *guh* `master` branch. 

Once, the installation is finished you continue with the [[Getting started]] instruction.

--------------------------------------------
## Install *guh* on Debian *wheezy*

> Coming soon...

### Add Qt repository

> Coming soon...

### Install *guh*

> Coming soon...



