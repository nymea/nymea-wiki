# Getting started with *guhd*
--------------------------------------------
Once you have installed *guh* successfully you can start the *guhd* daemon. There are two possibility's to start guhd:

* starting guh as daemon (service) 
* starting guh as application (terminal application) and see all debug outputs.

> **Note:** if you have installed the snappy package, please follow the [Getting started with guh snappy](https://github.com/guh/guh/wiki/Getting-started-snappy) instructions.

In order to get help you can type in the terminal `guhd -h`:

    $ guhd -h
    Usage: guhd [options]

    guh ( /[guːh]/ ) is an open source IoT (Internet of Things) server, 
    which allows to control a lot of different devices from many different. 
    manufacturers. With the powerful rule engine you are able to connect any 
    device available in the system and create individual scenes and behaviours 
    for your environment.

    guhd 0.7.0 (C) 2014-2015 guh
    Released under the GNU GENERAL PUBLIC LICENSE Version 2.

    API version: 34

    Options:
      -h, --help       Displays this help.
      -v, --version    Displays version information.
      -n, --no-daemon  Run guhd in the foreground, not as daemon.
      -p, --print-all  Enables all debug categories. This parameter 
                       overrides all debug category parameters.  
      -d, --debug <[No]DebugCategory> ...

Also a manual page is available:

    $ man guhd

By default, `guhd` will start as a daemon. If you want to start guhd as an application, you can pass the parameter `-n` and it will start in the foreground. 

If you want to see a special debug category, you can pass that category to the parameter. You can find all available categories in the help message (`guhd -h`):

> **Example:** start guhd in the foreground and enable the `JsonRpc` and `Hardware` debug messages:
    
    $ guhd -n -d JsonRpc -d Hardware

The `guhd` package provides also systemd service, which allows you to start, stop, restart and get the status the *guh*-daemon.

Start the service:

    $ sudo systemctl status guhd

Stop the service:

    $ sudo systemctl stop guhd

Restart the service:

    $ sudo sudo systemctl restart guhd

Get the status of the service:

    $ sudo systemctl status guhd

## Autostart guhd
If you want to auto start guhd on boot, you can enable the service by calling following command:

    $ systemctl enable guhd
    
    Created symlink from /etc/systemd/system/multi-user.target.wants/guhd.service to /etc/systemd/system/guhd.service.

### Disable autostart guhd
If you want to disable auto starting guhd on boot, you can call following command:

    $ sudo systemctl disable guhd

    Removed symlink /etc/systemd/system/multi-user.target.wants/guhd.service.

## Follow debug output

If you have guhd running in the background (as daemon and started with systemd) you can see the live debug out by monitoring the log file. You can do that with following command:

    $ sudo tail -f /var/log/guhd.log 


--------------------------------------------
# *guh*-cli

In order to interact and play with the guhd you can use the command line interface `guh-cli`.

The *guh-cli* (command line interface) is an admin tool written in python to communicate with the [*guh*](https://github.com/guh/guh) JSON-RPC API and test the functions of *guh*. The installation guide can be found [[guh-cli]](here).

In order to start guh-cli you need to know on which host *guh* is currently running. If guh is running on `localhost`, you can start the application as follows:

    $ guh-cli

If you need help you can run:

    $ man guh-cli
        
or you can run directly:

    $ guh-cli -h
    usage: guh-cli [-h] [-v] [--host HOST] [--port PORT]

    The guh-cli (command line interface) is an admin tool written in python to
    communicate with the guh daemon JSON-RPC API and test functionality of guh.

    optional arguments:
      -h, --help     show this help message and exit
      -v, --version  show program's version number and exit
      --host HOST    the location of the guh daemon (default 127.0.0.1)
      --port PORT    the port of the the guh daemon (default 2222)

Once *guh-cli* has established the connection to guhd, you will see the main menu. In the main menu you can either use the arrow keys to navigate or the item number of the menu list.

In the you are using the `Log monitor` the output will auto scroll down if the marked line is at the end of the log list. If you are navigating in previous logs a terminal flash will inform you about a new log entry. With the `space` key you can jump down to the newest log entry and the auto scroll will be enabled again.

## Access the web-interface

Once the *guhd* daemon is running you can open your favourite web-browser and enter open following URL:

> Assuming *guhd* is running on `localhost`. If guhd is running on an other location in you network replace `127.0.0.1` with the IP of your location.

[http://127.0.0.1:3333](http://127.0.0.1:3333)

If you have installed avahi (`$ apt-get install avahi-daemon avahi-utils`) you can access the the webserver with the `hostname` of the device where guhd is running:

hostname.local:3333

> Example: if you are using a Raspberry Pi and the [guh-netinstal](https://github.com/guh/guh/wiki/Raspberry-Pi#install-guh-on-debian-jessie-minimal-net-install-system) the host name will be `guh` [http://guh.local:3333](http://guh.local:3333)

If you want to enable an encrypted connection using SSL you can checkout the [[Configuration]] wiki.


