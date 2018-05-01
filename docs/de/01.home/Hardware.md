# Hardware
--------------------------------------------

In order to use some hardware devices, *guh* allows you to interact over *General Purpose Input/Outputs* (GPIOs) with them. They are provided from many kinds of chip, and are familiar to Linux developers working with embedded and custom hardware. Each GPIO represents a bit connected to a particular pin. Board schematics show which external hardware connects to which GPIOs. Drivers can be written generically, so that board setup code passes such pin configuration data to drivers.

Following devices can be used currently in *guh* over the GPIOs:

* [[RF 433 MHz]]
* [[Buttons]]
* [[Encoders]]
