# Configuration
--------------------------------------------
* [guh](https://github.com/guh/guh/wiki/Configuration#guh)
* [guh-webserver](https://github.com/guh/guh/wiki/Configuration#guh-webserver) 

--------------------------------------------
# guhd

## Global settings
The guh package provides a `guhd.conf` file, which deines the settings for the daemon and can be found in:

    $ cat /etc/guh/guhd.conf

    [JSONRPC]
    port=1234
    interfaces="lo","all"
    ip="IPv4", "IPv6"

    [GPIO]
    rf433rx=27
    rf433tx=22


In the `JSONRPC` section are the settings for the TCP interface of the JSON-RPC API: 

* *port* - Defines the port where the TCP server will listen. If you change the port please keep in mind that the `GuhPort` of the guh-webserver has to be changed to.

* *interfaces* - Defines the networkinterfaces where the TCP server will listen. You can check the networkinterfaces with `$ ifconfig -a`. If the value *all* is in the values, the server will listen on all networkinterfaces. 

* *ip* - Defines the address types of the server. Available address types are `IPv4` and `IPv6`. If the value *any* is in the values, the server will listen on both address types. 

In the `GPIO` section are the settings for the hardware GPIOs depending on the board you are using:

* *rf433rx* - Defines the GPIO pin number (in the filesystem) where the RF 433 MHz receiver is connected. 

* *rf433tx* - Defines the GPIO pin number (in the filesystem) where the RF 433 MHz transmitter is connected.

## Personal settings

The location of the personal settings like configured devices, rules and plugin depends on the user who starts guh.

**User** - If you start guhd as user, the settings can be found in the home directory of the corresponding user: 

        ~/.config/guh/*

**root** -  If you start guhd as root or the system starts it with the init script, the personal settings will be stored in:

        /etc/guh/*


## Reset configuration
 
**user** - If you start guhd as user, you will have to delete following files: 

        $ rm ~/.config/guh/devices.conf
        $ rm ~/.config/guh/rules.conf
        $ rm ~/.config/guh/plugins.conf

**root** -  If you start guhd as root or the system starts it with the init script, you will have to delete following files:


        $ sudo rm /etc/guh/devices.conf
        $ sudo rm /etc/guh/rules.conf
        $ sudo rm /etc/guh/plugins.conf 

> **Note:** you need to restart guhd to clean up also the runtime configurations after deleting the configuration files.

## Logging Database

The logging database is a sqlite3 database and contains every logg event of the guhd server. 

**user** - If you start guhd as user, the logging database will be stored in: 

        ~/.config/guh/guhd.log

**root** -  If you start guhd as root or the system starts it with the init script, the logging database will be stored in: 

        /var/log/guhd.log

To reset the database, just delete the file and restart guhd.

--------------------------------------------
# guh-webserver
The guh-webserver configuration file can be found here:

        $ cat /etc/guh/guh-webserver.conf

        IP = "0.0.0.0"
        Port = 3000
        GuhIP = "127.0.0.1"
        GuhPort = 1234
        StaticFolder = "/usr/share/guh-webinterface/public"


* *IP* - The IP of the web server

* *Port* - The port of the web server

* *GuhIP* - The IP where guhd is running

* *GuhPort* - The port where guhd is listening 

* *StaticFolder* - The folder containing the static files of guh-webinterface










