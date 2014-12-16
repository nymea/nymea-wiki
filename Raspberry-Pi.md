# Install *guh*-core on the Raspberry Pi
--------------------------------------------

This tutorial shows you how to install *guh* on the [Raspberry Pi](http://www.raspberrypi.org/). The easiest and recommended way is to use the [raspbian-netinstall](https://github.com/guh/raspbian-netinstall-config) provided by *guh* 
> Thanks to the awesome work of [raspbian-ua-netinst](https://github.com/debian-pi/raspbian-ua-netinst).

## Table of contents:

* Install *guh* on debian *jessie*
    1. Prepare the SD card  
        * ...using Linux
        * ...using MacOS
        * ...using Windows
    2. Copy files
    3. Install *guh*
* Install *guh* on debian *wheezy*
    * Prepare the SD card  
        * ...using Linux
        * ...using MacOS
        * ...using Windows
    * Install *guh*

--------------------------------------------
## Install *guh* on debian *jessie*

If you want a fresh, new and minimal installation of *guh* on the Raspberry Pi, we recommand to use the [raspbian-netinstall](https://github.com/guh/raspbian-netinstall-config) provided by *guh*, which will install everything you need to run *guh*. Basically you just need to do following three steps:

1. Create a `64 Mb FAT32` partition (has to be the only partition) on the SD (1GB is enought).
2. mount the parition and unzip the latest [guh-netinstall-v0.X.X.zip](http://www.guh.guru:8080/job/build-installer/lastSuccessfulBuild/artifact/guh-netinstall-v0.1.5.zip) file on it.
3. Insert the SD card into the Raspberry Pi, connect the network cable, connect the current cable and wait until the Raspberry Pi performs a reboot.

### 1. Prepare the SD card 

In this step we delete all partitions of the SD card and create a single `64 Mb FAT32` partition.

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


delete all partitions (using `d`, `enter`, `d`)

    Command (m for help): d
    Partition number (1,2, default 2): 
    
    Partition 2 has been deleted.

    Command (m for help): d
    Selected partition 1
    Partition 1 has been deleted.
    
create a new dos parition table using `o`
    
    Command (m for help): o
    Created a new DOS disklabel with disk identifier 0x2abef6c0.
    
create a new 64MB partition (`n`, `enter`, `enter`, `enter`, `+64M`)
        
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
    
change the partition type to W95 FAT32 (`t`, `b`)
    
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
    
write the table to disk and exit using `w`

    Command (m for help): w
    
    The partition table has been altered.
    Calling ioctl() to re-read partition table.
    Syncing disks.

Now you have to format the new partition to vfat (FAT32).

    $ sudo mkfs.vfat /dev/sdb1

#### ...using MacOS
> Comming soon...

#### ...using Windows
> Comming soon...


## 2. Copy files to SD card

-> First you need to mount the created partition from your SD card

    mount -t vfat /dev/sdb1 /mnt/raspberry-rootfs/

-> change directory to the partition

    cd /mnt/raspberry-rootfs/

-> download the latest guh-netinstall-v0.X.X.zip file ([link](http://www.guh.guru:8080/job/build-installer/lastSuccessfulBuild/artifact/guh-netinstall-v0.1.5.zip))

    wget http://www.guh.guru:8080/job/build-installer/lastSuccessfulBuild/artifact/guh-netinstall-v0.1.5.zip

-> unzip the file

    unzip guh-netinstall-v0.1.5.zip

-> remove the zip file

    rm guh-netinstall-v0.1.5.zip

-> umount the partition

    cd ../
    umount /dev/sdb1

##  3. Install *guh*
Insert your prepared SD card into your Raspberry Pi, connect the ethernet cable (internet connection needed) and then connect the power supply.

> Note: The order of connection is important. Now you have to wait ~20-30 minutes. You can follow the installation process if you connect a display. When the installation is finished, the new system will reboot and is ready for you:

    ssh root@192.168.1.51
    password: guh





--------------------------------------------
## Install *guh* on debian *wheezy*
> Comming soon...






