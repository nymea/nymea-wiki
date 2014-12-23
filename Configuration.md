# Configuration of *guh*!
--------------------------------------------
* [General configuration](https://github.com/guh/guh/wiki/Configuration#general-configuration)
    * [GPIO section](https://github.com/guh/guh/wiki/Configuration#gpio-section)
* [Devices](https://github.com/guh/guh/wiki/Configuration#devices)
* [Rules](https://github.com/guh/guh/wiki/Configuration#rules)
* [Reset configuration](https://github.com/guh/guh/wiki/Configuration#reset-configuration)
--------------------------------------------

*guh* saves all the configured devices and rules in two separated config files, which can be found in

    $ ~/.config/guh/

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
    

