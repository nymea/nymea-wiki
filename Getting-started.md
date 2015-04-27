# Getting started with *guhd*
--------------------------------------------
Once you have installed *guh* successfully you can start the *guhd* daemon. There are two possibility's to start guhd:

* starting guh as daemon (service) 
* starting guh as application (terminal application) and see all debug outputs.

In order to get help you can type in the terminal `guhd -h`:

    $ guhd -h
    Usage: guhd [options]

    guh ( /[guːh]/ ) is an open source home automation server, which allows to
    control a lot of different devices from many different manufacturers.
    guhd 0.2.0 (C) 2014-2015 guh
    Released under the GNU GENERAL PUBLIC LICENSE Version 2.
    
    Options:
      -h, --help       Displays this help.
      -v, --version    Displays version information.
      -n, --no-daemon  Run guhd in the foreground, not as daemon.

    
By default, `guhd` will start as a daemon. If you want to start guhd as an application, you can pass the parameter `-n` and it will start in the foreground. 

The `guhd` package provides also an initscript, which allows you to start, stop, restart and get the status the *guh*-daemon.

    $ sudo service guhd
    Usage: /etc/init.d/guhd {start|stop|restart|status}

#### Start the service
In order to start the service you can call following command:

    $ sudo service guhd start

#### Stop the service
In order to stop the service you can call following command:

    $ sudo service guhd stop

#### Restart the service
In order to restart the service you can call following command:

    $ sudo service guhd restart

#### Get the status of the daemon
In order to find out if the service is running or not you can call following command:

    $ sudo service guhd status

## Autostart guhd
If you want to autostart guhd on boot, you can enable the service by calling following command:

    $ sudo update-rc.d guhd defaults
    
     Adding system startup for /etc/init.d/guhd ...
       /etc/rc0.d/K20guhd -> ../init.d/guhd
       /etc/rc1.d/K20guhd -> ../init.d/guhd
       /etc/rc6.d/K20guhd -> ../init.d/guhd
       /etc/rc2.d/S20guhd -> ../init.d/guhd
       /etc/rc3.d/S20guhd -> ../init.d/guhd
       /etc/rc4.d/S20guhd -> ../init.d/guhd
       /etc/rc5.d/S20guhd -> ../init.d/guhd

### Disable autostart guhd
If you want to disable auto starting guhd on boot, you can call following command:

    $ sudo update-rc.d -f guhd remove
     
     Removing any system startup links for /etc/init.d/guhd ...
       /etc/rc0.d/K20guhd
       /etc/rc1.d/K20guhd
       /etc/rc2.d/K80guhd
       /etc/rc3.d/K80guhd
       /etc/rc4.d/K80guhd
       /etc/rc5.d/K80guhd
       /etc/rc6.d/K20guhd

--------------------------------------------
In order to interact and play with the guhd you can use the command line interface `guh-cli`.

See also [guh-cli documantation](https://github.com/guh/guh/wiki/guh-cli)

# *guh* webserver
--------------------------------------------

If you want to install the guh-webserver (REST-API) together with the `guh-webinterface` you can run following command:

    $ sudo apt-get install guh-webserver

This will install the webserver and the the webinterface, which will be accessable by default on port 3000. First you need to start the webserver:

    $ sudo service guh-webserver start

The `status` `restart` and `stop` commands are the same as for the `guh` daemon. If you want to autostart the `guh-webserver` at boot you can enable it with

    $ sudo update-rc.d guh-webserver defaults

and disable it with:

    sudo update-rc.d -f guh-webserver remove

## Access the web-interface

Once the web-server is running you can open your favorite web-browser and enter open following URL:

> Assuming the guh-webserver is running on your `localhost`. If the guh-webserver is running on an other location in you network replace `127.0.0.1` with the IP of your location.

[http://127.0.0.1:3000](http://127.0.0.1:3000)

If you have installed avahi (`$ apt-get install avahi-daemon avahi-utils` you can access the the webserver with the `hostname` of the device where guh-webserver is running:

hostname.local:3000

> Example: if you are using a Raspberry Pi and the [guh-netinstal](https://github.com/guh/guh/wiki/Raspberry-Pi#install-guh-on-debian-jessie-minimal-net-install-system) the hostame will be `guh`:

[http://guh.local:3000](http://guh.local:3000)

