# Install *guh*-core on Ubuntu
--------------------------------------------

In order to install *guh* on Ubuntu you need to create the `/etc/apt/sources.list.d/guh.list` file and add the *guh*-repository:

1. Create the [*guh*-repository](http://repo.guh.guru/) list file:
        
        $ sudo nano /etc/apt/sources.list.d/guh.
        
    *Note:* please replace `<dist>` with the codename of your Ubuntu distribution. You can get your system version with `lsb_release -a`. In the repository are following distributions available:`trusty` `utopic` and `vivid`. Available architectures are `amd64` `i386` and `armhf`.
     
    Copy following lines into the file (with replaced `<dist>`) and save it:
        ## guh repo
        deb http://repo.guh.guru <dist> main
        deb-src http://repo.guh.guru <dist> main
        
    > **Alternative:** `$ echo -e "\n## guh repo\ndeb http://repo.guh.guru <dist> main\ndeb-src http://repo.guh.guru <dist> main" | sudo tee /etc/apt/sources.list.d/guh.list`
    
    Add the public key of the [*guh*-repo](http://repo.guh.guru/) to your keylist.
    
        $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 6B9376B0
    
        
2. Update your package lists:
    
        $ sudo apt-get update

    The *guh*-repo provides following packages:
    
        $ apt-cache search guh
    
        guh - Server for home automation systems - meta package
        guh-cli - guh command line interface - python
        guh-dbg - server for home automation systems - debug symbols
        guh-doc - Documentation for the guh package (on-site) - documentation
        guh-plugins - Plugins for guh server home automation systems
        guh-tests - Tests for the guh package
        guh-webinterface - Browser based user interface for guh
        guh-webserver - A REST-API webserver for the guh-webinterface
        guhd - Server daemon for home automation systems
        libguh1 - Server for home automation systems - core library
        libguh1-dev - Server for home automation systems - development files

3. Install *guh* with following command:
    
        $ sudo apt-get install guh guh-cli guh-webserver
        
    The repository contains always the latest stable build of the *guh* `master` branch. 
    If you want to install the source code you can install:
        
        $ sudo apt-get source guh        
        $ sudo apt-get source guh-cli
        $ sudo apt-get source guh-webserver
        $ sudo apt-get source guh-webinterface
        
Once, the installation is finished you continue with the [[Getting started]] instruction.

