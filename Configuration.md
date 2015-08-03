# Configuration
--------------------------------------------

## Global settings
The guh package provides a `guhd.conf` file, which defines the settings for the daemon and can be found in:

    $ cat /etc/guh/guhd.conf

    [JSONRPC]
    port=1234
    interfaces="lo","all"
    ip="IPv4", "IPv6"

    [Webserver]
    port=3000
    https=false
    certificate=/etc/ssl/certs/guhd-certificate.crt
    certificate-key=/etc/ssl/private/guhd-certificate.key
    publicFolder=/usr/share/guh-webinterface/public

    [GPIO]
    rf433rx=27
    rf433tx=22

--------------------------------------------

> **Note:** you have to restart the server to apply the changes

In the `JSONRPC` section are the settings for the TCP interface of the JSON-RPC API: 

* **port** - Defines the port where the TCP server will listen.

* **interfaces** - Defines the network interfaces where the TCP server will listen. You can check the network interfaces with `$ ifconfig -a`. If the value *all* is in the values, the server will listen on all network interfaces. 

* **ip** - Defines the address types of the server. Available address types are `IPv4` and `IPv6`. If the value *any* is in the values, the server will listen on both address types. 

--------------------------------------------

In the `Webserver` section are the settings for the webserver and the REST API:

* **port** - Defines the port on which the webserver is running

* **https** - Definens if the webserver is using a secure, encrypted connection (TLS 1.2) or not. Allowed values are `true` or `false`.

> **Note:** You need to create a self sigend certificate to use HTTPS. You can find the instructions here [[SSL-Certificate]]  

* **certificate** - Defines the path to the certificate. This option is only needed if you are using `https`.

* **certificate** - Defines the path to the private key for the certificate. This option is only needed if you are using `https`.

* **publicFolder** - Defines the path to the public folder which will be published with from the webserver. This path describes the directory to the webinterface.

--------------------------------------------

In the `GPIO` section are the settings for the hardware GPIOs depending on the board you are using:

* **rf433rx** - Defines the GPIO pin number (in the file system) where the RF 433 MHz receiver is connected. 

* **rf433tx** - Defines the GPIO pin number (in the file system) where the RF 433 MHz transmitter is connected.

## Personal settings
--------------------------------------------

The location of the personal settings like configured devices, rules and plugins depends on the user who starts guh.

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

The logging database is a sqlite3 database and contains every log event of the guhd server. 

**user** - If you start guhd as user, the logging database will be stored in: 

        ~/.config/guh/guhd.log

**root** -  If you start guhd as root or the system starts it with the init script, the logging database will be stored in: 

        /var/log/guhd.log

To reset the database, just delete the file and restart guhd.







