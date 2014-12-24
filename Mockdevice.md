# Using the *mockdevice* plugin
--------------------------------------------

The *mockdevice* was written to perform tests in *guh*. With this plugin you can test different *action* executions, create *events* and test the behaviour of the system if a *state* changes. 

In order to play with the mock device you need either:

* install the `guh-tests` package from the repository
* build the *guh* source code with tests (See also [*qmake configuration*](https://github.com/guh/guh/wiki/Compile-guh#qmake-configuration))

Once you have installed the `libguh_devicepluginmock.so` and run `guhd` the mock device will appear automatically in you configured device list. The plugin creates a little web server which is running on a random port. In order to find out which port, you can request the device parameter with the [`guh-cli`](https://github.com/guh/guh/wiki/guh-cli) or take a look in the [settings file](https://github.com/guh/guh/wiki/Configuration#devices).

Assuming *guh* is running on you local computer and the webserver is listening on port `4242`, you can open your web browser and check following address:

    http://localhost:4242

> **Note:** if *guh* is running on an other device in your network, replace localhost with the IP of that device.

