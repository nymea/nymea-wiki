![guh logo](wiki/images/logo.png)

# Welcome to the *guh* wiki!
--------------------------------------------
*guh* (/[guːh]/ - pronounced german and sounds like *goo*) is an open source home automation server, which allows to control a lot of different devices from many different manufacturers. With the powerful rule engine you are able to connect any device available in the system and create individual scenes and behaviours for your home. 

## Structure
--------------------------------------------
The whole system has basically three layers:

1. [*guh* core:](https://github.com/guh/guh) the core is an application written in [Qt](http://qt-project.org/) and contains the whole communication with the hardware, loads the supported devices from the plugins, manages all devices and rules. The core provides a JSON-RCP api to allow clients to communicate with the core.

2. [*guh* rails:](https://github.com/guh/guh_rails) the *guh* rails application is an application written in [Ruby on Rails](http://rubyonrails.org/) and contains a webserver which provides a REST api. This application communicates directly with the core and translates the JSON-RPC to the REST api.

3. [*guh* angular:](https://github.com/guh/guh_angular) the *guh* angular application is an application written in [AngularJS](https://angularjs.org/) and provides the browser based user interface. The application uses the REST api from the guh rails server and offers the user an easy and beautiful possibility to interact with his home. 

In following figure you can see the structure of the whole system:

![Structure of guhOS](wiki/images/structure.png)

# Getting started
--------------------------------------------
*guh* is currently only available for linux based systems and can be installed and compiled on several platforms like the Raspberry Pi or the Beaglebone Black. This gives you the possibility to keep *guh* running 24/7 without high energy costs. 

## Install *guh*-core
Depending on the your platform and operating system, you can choose between following installation instructions:

* [Ubuntu (64.Bit)](https://github.com/guh/guh/wiki/Install-guh-core-on-Ubuntu) 
* [Raspberry Pi](https://github.com/guh/guh/wiki/Install-guh-on-the-Raspberry-Pi)
* [Beaglebone Black - (armhf)](https://github.com/guh/guh/wiki/Install-guh-on-the-Beaglebone-Black)

or you can compile the source code for your own platform / system by following 
* [Compile the *guh*-core source code](https://github.com/guh/guh/wiki/Compile-guh)













