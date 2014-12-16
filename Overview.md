# Overview of *guh*-core
--------------------------------------------
A detailed documentation of the source code can be found in the [*guh* | developer documentation](http://dev.guh.guru/).The source code of *guh* is basicaly structured in three moduls:

* ***server:*** The *guh* server is the instance that communicates with the hardware and provides a JSON-RPC interface for communicating with the clients. It also contains the rule engine and the core application. The detailed documentation of it can be found [here](http://dev.guh.guru/server-module.html).


* ***libguh:*** The *libguh* contains all needed types and classes (for *guh* and the plugins) and contains also the hardware drivers. The detailed documentation of it can be found [here](http://dev.guh.guru/libguh-module.html).


* ***plugins:*** The *plugins* module contains all plugins of *guh* which will be loaded dynamicaly from the *server*. Each plugin brings support for many devices or services to *guh*. A detailed description how to write a plugin will be published in the [*guh* | developer documentation](http://dev.guh.guru/). The whole list of plugins and services and it's description can be found [here](http://dev.guh.guru/plugins.html).