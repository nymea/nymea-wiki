# User Interfaces - Under Construction

Since you are such a smarty pants and has installed guhIO, you are now in the lucky position to choose from various user interfaces.

# Web Interface

If you took the raspberry netinstall image, guh will be availble at:
`http://guh.local:3000`

you should be directed to your raspberry pi.
But there are some problems with routers that cannot resolv the name, so we have to find out the IP Adress.
`ifconfig`

take the inet adress in my case 10.0.0.1
then i run

`nmap -sP 10.0.0.1/24`

Nmap told me guh or whatever your devicename is

> Nmap scan report for guh (10.0.0.6)
> Host is up (0.0076s latency).

now you can type the Adress into your Browser


`http://10.0.0.6:3000`
the additoin of ":3000" is necessary, it indicates the port guh is listening - default is 3000

***

* **Web Interface Start Screen**
![web interface start screen](https://cloud.githubusercontent.com/assets/5207214/8827351/87b17bd4-308c-11e5-96df-43ba3681fc6c.png)

***

* **Web Interface Add Device Screen**
![web interface add device](https://cloud.githubusercontent.com/assets/5207214/8827355/8bec6326-308c-11e5-80e3-83fdef2a2899.png)

***



# Smartphone App

At the moment there are Apps for Android and iOS in develoment. It will take some time until it can be downloaded in the App-Stores. For the Android users is a alpha prototype [App available](https://guh.guru/downloads/mobileapp/guh-mobile_0.1.0_android-debug.apk).

***

* **Settings Screen**

![Edit Settings Screen](https://cloud.githubusercontent.com/assets/5207214/8828811/51dc1bec-3094-11e5-8805-b2be415ece97.png)

***

* **Device Screen**

![Device Screen](https://cloud.githubusercontent.com/assets/5207214/8829159/720dbf0a-3095-11e5-9b80-6c6c9c05dc1a.png)

***

* **Rule Screen*

![Rule Screen](https://cloud.githubusercontent.com/assets/5207214/8828873/956c125e-3094-11e5-8970-221f0d8bef89.png)

## Command Line Interface
--------------------------------------------

The *guh-cli* (command line interface) is an admin tool written in python to communicate with the [*guh*](https://github.com/guh/guh) JSON-RPC API and test functionality of *guh*.

### Installation 
--------------------------------------------

If you have added the guh repository to your source liste (see [install guh](https://github.com/guh/guh/wiki/Install)) you can run:

    $ sudo apt-get update
    $ sudo apt-get install guh-cli
    
If you want to download the source code you can run:

    $ sudo apt-get source guh-cli

--------------------------------------------

If you want to install it manually you can clone the repository and start the application directly in your folder.
First make sure you have installed *python 2.7*. You can find the installation instruction on the [official python homepage](https://www.python.org/download/releases/2.7/).

Now you can clone the [guh-cli repository](https://github.com/guh/guh-cli) from github:

    $ git clone https://github.com/guh/guh-cli.git
    $ cd guh-cli/    
    $ ./guh-cli

### Usage 
--------------------------------------------

In order to start guh-cli you need to know on which host *guh* is currently running. If guh is running on `localhost`, you can start the application as follows:

    $ guh-cli

If you need help you can run:

    $ man guh-cli
    
or you can run directly:

    $ guh-cli -h
    usage: guh-cli [-h] [-v] [--host HOST] [--port PORT]

    The guh-cli (command line interface) is an admin tool written in python to
    communicate with the guh daemon JSON-RPC API and test functionality of guh.

    optional arguments:
      -h, --help     show this help message and exit
      -v, --version  show program's version number and exit
      --host HOST    the location of the guh daemon (default 127.0.0.1)
      --port PORT    the port of the the guh daemon (default 1234)


Once *guh-cli* has established the connection to guhd, you will see the main menu. In the main menu you can either use the arrow keys to navigate or the item number of the menu list.

In the you are using the `Log monitor` the output will auto scroll down if the marked line is at the end of the log list. If you are navigating in previous logs a terminal flash will inform you about a new log entry. With the `space` key you can jump down to the newest log entry and the auto scroll will be enabled again.


Start Screen V1.0.3

![guh-cli ](https://cloud.githubusercontent.com/assets/5207214/8826753/fbd254ec-3088-11e5-9e07-10c3a276de39.png)

Devices Screen V1.0.3

![guh-cli devices](https://cloud.githubusercontent.com/assets/5207214/8826760/0cfab5b6-3089-11e5-9012-df0aad571f08.png)
