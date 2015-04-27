# Configuration
--------------------------------------------
* [guh](https://github.com/guh/guh/wiki/Configuration#guh)
    * [General configuration](https://github.com/guh/guh/wiki/Configuration#guh#general-configuration)
        * [GPIO section](https://github.com/guh/guh/wiki/Configuration#guh#gpio-section)
    * [Devices](https://github.com/guh/guh/wiki/Configuration#guh#devices)
    * [Rules](https://github.com/guh/guh/wiki/Configuration#guh#rules)
    * [Reset configuration](https://github.com/guh/guh/wiki/Configuration#guh#reset-configuration)
* [guh-webserver](https://github.com/guh/guh/wiki/Configuration#guh-webserver) 

--------------------------------------------
# guh
*guh* saves all the configured devices and rules in two separated config files, which can be found in

    $ ~/.config/guh/

> **Note:** if you start guhd as daemon, the home folder will be currently at `/`, because a daemon does not need a user to start. All configuration files will be stred in `/.config/guh/`. This will be fixed as soon as possible.


Depending on the user how starts *guh*, the config files will be stored in that home directory (`$ cd ~`). If you are starting *guh* as `root` this folder will be in the root home directory. 

   
## General configuration

The *guhd* configurations will be stored in:

    $ ~/.config/guh/guhd.conf

#### GPIO section

> Coming soon...

## Devices
    
The configured *devices* will be stored in:

    $ ~/.config/guh/devices.conf

## Rules

The created *rules* will be stored in:

    $ ~/.config/guh/rules.conf

## Reset configuration

If you want to reset all guh configuration, just delete everything in this folder and restart *guh*.

    $ rm ~/.config/guh/*
    
--------------------------------------------
# guh-webserver
The guh-webserver configuration file can be found here:


    $ sudo nano /etc/guh/guh-webserver.conf

    IP = "0.0.0.0"
    Port = 3000
    GuhIP = "127.0.0.1"
    GuhPort = 1234
    StaticFolder = "/usr/share/guh-webinterface/public"

`IP`           ...The IP of the web server

`Port`         ...The port of the web server

`GuhIP`        ...The IP where guhd is running

`GuhPort`      ...The port where guhd is listening 

`StaticFolder` ...The folder containing the static files of guh-webinterface










