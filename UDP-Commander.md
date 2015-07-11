# UDP Commander Plugin
--------------------------------------------
This plugin allows to receive UDP packages over a certain UDP port and generates an event if the message content matches the param command.

## Example
If you create an UDP Commander on port 2323 and with the command "Light 1 ON", following command will trigger an Event in guh and allows you to connect this Event with a Rule.

> **Note:** In this example guh is running on localhost

    $ echo "Light 1 ON" | nc -u localhost 2323
    OK

See [dev-doku](http://dev.guh.guru/udpcommander.html) for more information.
