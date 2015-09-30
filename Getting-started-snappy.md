# Getting started with *guhIO* snappy
--------------------------------------------

Once you have successfully installed the guhOP snappy package ([[Snappy]]) the guh daemon should already be running on the system. The guhIO snappy package contains the whole guh software:

* guhd
* libguh
* plugins
* guh-cli
* guh-webinterface

The `guhd` daemon is a service and can be controlled with `systemd`. The command line interface `guh-cli` is installed as binary and can be started with `guhio.guh-cli`

But first log in to Ubuntu Core device:

        $ ssh ubuntu@webdm.local	# password: ubuntu

    
> **Note:** the avahi sometimes does not work correctly. In this case try to replace `webdm.local` with the IP of your device.

Now you should see running two services from guh:

        $ systemctl list-units | grep guh

        guhio_guhd_ICGAWgEBRJKY.service  loaded    active running    Daemon for the guh IoT server

> **Note:** if you don't install the package from the store, the version string will be replaced with a uuid. In this example *ICGAWgEBRJKY*. You will have a different uuid.

If you want to follow the debug output of the guhd service and to see what's going on you can run:

        $ sudo journalctl -f -u guhio_guhd_ICGAWgEBRJKY.service

If you want to play with the API you can start the command line interface [[guh-cli]] as user `ubuntu`:

        $ guhio.guh-cli

The guh REST API and the guh-webinterface are accessible over port 3333. The guhd JSON-RPC API runns on port 2222 for the TCP connection and on 4444 for the websocket connection.

## Configurations

All guh config files are stored in:

        $ ls -l /var/lib/apps/guhio.sideload/<currentUuid>/


The log files will be saved to:

        $ ls -l /var/lib/apps/guhio.sideload/<currentUuid>/guhd.log


