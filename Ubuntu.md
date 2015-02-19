# Install *guh*-core on Ubuntu
--------------------------------------------
*guh*-core can be installed from the [*guh* repository](http://repo.guh.guru/) which provides packages for: 

* [Ubuntu 14.04 LTS (Trusty Thar)](https://github.com/guh/guh/wiki/Ubuntu#ubuntu-1404-lts)
* [Ubuntu 14.10 (Utopic Unicorn)](https://github.com/guh/guh/wiki/Ubuntu#ubuntu-1410)

--------------------------------------------
## Ubuntu 14.04 LTS

In order to install *guh* on Ubuntu 14.04 LTS (64 bit) you need to create the `/etc/apt/sources.list.d/guh.list` file and add the *guh*-repository:

1. Create the [*guh*-repo](http://repo.guh.guru/) list file:
        
        $ sudo nano /etc/apt/sources.list.d/guh.list
            
    Append following two lines at the end of the file:
    
        ## guh repo
        deb http://repo.guh.guru trusty main
        
    > **Alternative:** `$ echo -e "\n## guh repo\ndeb http://repo.guh.guru trusty main" | sudo tee /etc/apt/sources.list.d/guh.list`
    
    Add the public key of the guh-repo to your keylist.
    
        $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 6B9376B0
    
        
2. Update your package lists:
    
        $ sudo apt-get update

    The *guh*-repo provides following packages:
    
        $ apt-cache search guh
    
        guh - server for home automation systems - meta package
        guh-dbg - server for home automation systems - debug symbols
        guh-doc - documentation for the guh package (on-site)
        guh-plugins - server for home automation systems - plugins
        guh-tests - tests for the guh package
        guh-webinterface - Browser based user interface for guh
        guh-webserver - A REST-API webserver for the guh-webinterface
        guhd - server for home automation systems
        libguh1 - server for home automation systems - core library
        libguh1-dev - server for home automation systems - development files

3. Install *guh* with following command:
    
        $ sudo apt-get install guh guh-webserver
        
    The repository contains always the latest stable build of the *guh* `master` branch. 

Once, the installation is finished you continue with the [[Getting started]] instruction.

--------------------------------------------
## Ubuntu 14.10

In order to install *guh* on Ubuntu 14.10 (64 bit) you need to create the `/etc/apt/sources.list.d/guh.list` file and add the *guh*-repository:

1. Create the [*guh*-repo](http://repo.guh.guru/) list file:
        
        $ sudo nano /etc/apt/sources.list.d/guh.list
            
    Append following two lines at the end of the file:
    
        ## guh repo
        deb http://repo.guh.guru utopic main
        
    > **Alternative:** `$ echo -e "\n## guh repo\ndeb http://repo.guh.guru utopic main" | sudo tee /etc/apt/sources.list.d/guh.list`
    
    Add the public key of the guh-repo to your keylist.
    
        $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 6B9376B0
    
2. Update your package lists:
    
        $ sudo apt-get update 

    The *guh*-repo provides following packages:
    
        $ apt-cache search guh
    
        guh - server for home automation systems - meta package
        guh-dbg - server for home automation systems - debug symbols
        guh-doc - documentation for the guh package (on-site)
        guh-plugins - server for home automation systems - plugins
        guh-tests - tests for the guh package
        guh-webinterface - Browser based user interface for guh
        guh-webserver - A REST-API webserver for the guh-webinterface
        guhd - server for home automation systems
        libguh1 - server for home automation systems - core library
        libguh1-dev - server for home automation systems - development files

3. Install *guh* with following command:
    
        $ sudo apt-get install guh guh-webserver
        
    The repository contains always the latest stable build of the *guh* `master` branch. 

Once, the installation is finished you continue with the [[Getting started]] instruction.

    
