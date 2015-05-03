# Unitec Plugin
--------------------------------------------

This plugin allows to controll RF 433 MHz actors from [Leynew](http://www.unitec-elektro.de/) devices.

The unitec socket units have a learn function. If you plug in the switch, a red light will start to blink. This means the socket is in the learning mode. Now you can add a Unitec switch (48111) to guh with your desired Channel (A,B,C or D). In order to pair the socket you just have to press the power ON, and the switch has to be in the pairing mode. If the pairing was successfull, the switch will turn on. If the switches will be removed from the socket or there will be a power breakdown, the switch has to be re-paired. The device can not remember the teached channel.

Currently following devices are supported:

* Unitec switch (48111)
  

**Info**: If you want to controll RF 433 MHz devices with *guh*, you need extra hardware like the RF 433 [Brematic Home Automation Gateway](http://www.brennenstuhl.de/de-DE/steckdosenleisten-schaltgeraete-und-adapter/brematic-hausautomation/brematic-home-automation-gateway-gwy-433-3.html) from [Brennenstuhl](http://www.brennenstuhl.de/). If you have such a gateway *guh* will find it automatically in you local network and the added RF 433 MHz devices will be switchable.