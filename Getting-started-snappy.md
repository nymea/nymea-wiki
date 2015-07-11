# Getting started with *guh* snappy
--------------------------------------------

Once you have successfully installed the guh snappy package ([[Snappy]]) the guh daemon and the guh-webserver should already be running. The guh snappy package contains the whole guh software:

* guhd
* libguh
* guh-cli
* guh-webserver
* guh-webinterface

The guhd daemon and the guh-webserver are services and can be controlled with `systemd`. The command line interface is installed as binary and can be started with `guh.guh-cli`

But first log in to Ubuntu Core device:

        $ ssh ubuntu@webdm.local	# password: ubuntu

    
> **Note:** the avahi sometimes does not work correctly. In this case try to replace `webdm.local` with the ip of your device.

Now you should see running two services from guh:

        $ systemctl list-units | grep guh

        guh_guhd_0.1.3.service        loaded active running   Daemon for the guh home automation systems
        guh_webserver_0.1.3.service   loaded active running   The guh REST-API webserver

If you want to follow the debug output to see whats going on you can run:

        $ sudo journalctl -f -u guh_guhd_0.1.3.service

or for the webserver:

        $ sudo journalctl -f -u guh_webserver_0.1.3.service

If you want to play with the API you can start the command line interface [[guh-cli]] as user `ubuntu`:

        $ guh.guh-cli

The guh REST API and the guh-webinterface are accessible over port 3000. The guhd JSON-RPC API runns on port 1234.

## Configurations

All guh config files are stored in:

        $ ls -l /writable/system-data/apps/guh.sideload/current/config/


The log files will be saved to:

        /var/log/guhd.log










