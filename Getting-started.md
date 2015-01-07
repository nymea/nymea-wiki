# Getting started with *guh*-core
--------------------------------------------
Once you have installed *guh* successfully you can start the *guhd* daemon. There are two possibilitys to start guhd:

* starting guh as daemon (service) 
* starting guh as application (terminal application) and see all debug outputs.

In ordert to get help you can type in the terminal `guhd -h`:

    $ guhd -h
    
    guhd 0.2.0 (C) 2014-2015 guh
    Released under the GNU GENERAL PUBLIC LICENSE Version 2

    guh (/[guːh]/ - pronounced German and sounds like "goo") is an open source
    home automation server, which allows to control a lot of different devices 
    from many different manufacturers.

    options:
       -h,     --help              print this help message
       -v,     --version           print version
       -e,     --executable        start guh as application, not as daemon

    
The `-e` argument executs `guhd` as executable binary. Without this parameter, guh will start as daemon in the background.

If you ant to stop the service, currently you need to do that the hard way:

    $ killall guhd

    > **Note:** For the `killall` you need to install `psmisc`.



In order to interact with the guhd you can use the `guh-cli` application.

See also [guh-cli documantation](https://github.com/guh/guh/wiki/guh-cli)

# *guh* webserver
--------------------------------------------

> Coming soon...
