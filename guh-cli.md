# Using the *guh-cli*
--------------------------------------------

The *guh-cli* (command line interface) is an admin tool written in python to communicate with the [*guh*](https://github.com/guh/guh) JSON-RPC API and test functionality of *guh*.

## Installation 
--------------------------------------------

First make sure you have installed *python 2.7*. You can find the installation instruction on the [official python homepage](https://www.python.org/download/releases/2.7/).

Now you can clone the [guh-cli repository](https://github.com/guh/guh-cli) from github:

    $ sudo apt-get install git python2.7
    $ git clone https://github.com/guh/guh-cli.git
    $ cd guh-cli/

## Usage 
--------------------------------------------
   
In order to start guh-cli you need to know on which host *guh* is currently running. If guh is running on `localhost` and port `1234`, you can start the application as follows:

    $ ./guh-cli.py

If *guh* is running on a certain host and port, (i.e. `192.168.1.13` and port `43434`), you can pass the IP as a parameter:

    $ ./guh-cli.py 192.168.1.13 43434
    
Once *guh-cli* has established the connection, you will see the main menu. In the main menu you can either use the arrow keys to navigate or the item number of the menu list.

In the you are using the `Log monitor` the output will auto scroll down if the marked line is at the end of the log list. If you are navigating in previous logs a terminal flash will inform you about a new log entry. With the `space` key you can jump down to the newest log entry and the auto scroll will be enabled again.   
