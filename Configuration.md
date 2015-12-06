# Configuration
--------------------------------------------

## Global settings
The guh package provides a `/etc/guh/guhd.conf` file, which defines the settings for the guh server and can be found in:

> **Note:** you have to restart the guhd to apply the changes in this file.

    $ cat /etc/guh/guhd.conf

    [JSONRPC]
    port=2222
    interfaces="lo", "all"
    ip="IPv4", "IPv6"
    
    [WebServer]
    port=3333
    https=false
    publicFolder=/usr/share/guh-webinterface/public
    
    [WebSocketServer]
    https=false
    port=4444
    
    [SSL-Configuration]
    certificate=/etc/ssl/certs/guhd-certificate.crt
    certificate-key=/etc/ssl/private/guhd-certificate.key
    
    [GPIO]
    rf433rx=27
    rf433tx=22

--------------------------------------------

In the `JSONRPC` section are the settings for the TCP interface of the JSON-RPC API: 

* **port** - Defines the port where the TCP server will listen.

* **interfaces** - Defines the network interfaces where the TCP server will listen. You can check the network interfaces with `$ ifconfig -a`. If the value *all* is in the values, the server will listen on all network interfaces. 

* **ip** - Defines the address types of the server. Available address types are `IPv4` and `IPv6`. If the value *any* is in the values, the server will listen on both address types. 

--------------------------------------------

In the `WebServer` section are the settings for the webserver and the REST API:

* **port** - Defines the port on which the webserver is running

* **https** - Definens if the webserver is using a secure, encrypted connection (TLS 1.2) or not. Allowed values are `true` or `false`. The certificate and private key file has to be loaded successfully.

* **publicFolder** - Defines the path to the public folder which will be published with from the webserver. This path describes the directory to the webinterface.

--------------------------------------------

In the `WebSocketServer` section are the settings for the websocket server:

* **port** - Defines the port on which the websocket server is running

* **https** - Definens if the websocket server is using a secure, encrypted connection (TLS 1.2) or not. Allowed values are `true` or `false`. The certificate and private key file has to be loaded successfully.

--------------------------------------------

In the `SSL-Configuration` section are the settings for the SSL configuration used in guh. You need to create a certificate to use HTTPS, otherwise the connection will not be secure. 

You can find the instructions how to create a certificate here [[SSL-Certificate]].  

* **certificate** - Defines the path to the certificate. This option is only needed if you are using `https`.

* **certificate** - Defines the path to the private key for the certificate. This option is only needed if you are using `https`.


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

        ~/.config/guh/guhd.sqlite

**root** -  If you start guhd as root or the system starts it with the init script, the logging database will be stored in: 

        /var/log/guhd.sqlite

To reset the database, just delete the file and restart guhd.

## Log file

The log file contains the debug console logs of the guh daemon. In order to control the files guhd provides a config file for logrotate `/etc/logrotate.d/guhd` 

**user** - If you start guhd as user, the log file will be stored in: 

        ~/.config/guh/guhd.log

>**Note:** if you start guhd as user, logrotate will not trigger on that file. You need to control the filesize by your self (because `guhd` was designed to run as daemon)

**root** -  If you start guhd as root or the system starts it with the init scripts / systemd, the logfile will be stored in: 

        /var/log/guhd.log








