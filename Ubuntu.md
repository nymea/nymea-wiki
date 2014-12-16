# Install *guh*-core on Ubuntu
--------------------------------------------
*guh*-core can be installed from the [*guh* repository](http://repo.guh.guru/) which provides amd64 packages for 

* [Ubuntu 14.04 LTS (Trusty Thar)](https://github.com/guh/guh/wiki/Install-guh-core-on-Ubuntu#ubuntu-1404-lts)
* [Ubuntu 14.10 (Utopic Unicorn)](https://github.com/guh/guh/wiki/Install-guh-core-on-Ubuntu#ubuntu-1410)

## Ubuntu 14.04 LTS
--------------------------------------------
In order to install *guh* on Ubuntu 14.04 LTS amd64 you need to add the *guh*-repository to your `/etc/apt/sources.list`:

1. Add the [*guh*-repo](http://repo.guh.guru/) to the source list file:
        
        $ sudo nano /etc/apt/sources.list
            
    append following two lines at the end of the file:
    
        ## guh repo
        deb http://repo.guh.guru trusty main
        
2. Update your package lists:
    
        $ sudo apt-get update
    
    > **Note:** You may notice that following error will appear:
    >   
    >       ...
    >       
    >       Err http://repo.guh.guru trusty/main i386 Packages                    
    >           404  Not Found
    >       
    >       ...
    >       
    >       W: Failed to fetch http://repo.guh.guru/dists/trusty/main/binary-i386/Packages  404  Not Found
            
    > You can ignore this error unless you have a i386 system. Until now we do not provide packages for i386 systems. If you have a i386 system, please take a look at [[Compile guh]].

    The *guh*-repo provides following packages:
    
        $ apt-cache search guh
    
        guh - server for home automation systems - meta package
        guh-dbg - server for home automation systems - debug symbols
        guh-doc - documentation for the guh package (on-site)
        guh-plugins - server for home automation systems - plugins
        guh-tests - tests for the guh package
        guhd - server for home automation systems
        libguh1 - server for home automation systems - core library
        libguh1-dev - server for home automation systems - development files

3. Install *guh* with following command:
    
        $ sudo apt-get install guh -y --force-yes
        
    > Note: you need to install the packages without verification.

    The repository contains always the latest stable build of the *guh* `master` branch. 

Once, the installation is finised you continue with the [[Getting started]] instruction.

## Ubuntu 14.10
--------------------------------------------
In order to install *guh* on Ubuntu 14.10 amd64 you need to add the *guh*-repository to your `/etc/apt/sources.list`:

1. Add the [*guh*-repo](http://repo.guh.guru/) to the source list file:
        
        $ sudo nano /etc/apt/sources.list
            
    append following two lines at the end of the file:
    
        ## guh repo
        deb http://repo.guh.guru utopic main
        
2. Update your package lists:
    
        $ sudo apt-get update
    
    > **Note:** You may notice that following error will appear:
    >   
    >       ...
    >       
    >       Err http://repo.guh.guru utopic/main i386 Packages                    
    >           404  Not Found
    >       
    >       ...
    >       
    >       W: Failed to fetch http://repo.guh.guru/dists/utopic/main/binary-i386/Packages  404  Not Found
            
    > You can ignore this error unless you have a i386 system. Currently we do not provide packages for i386 systems. If you have a i386 system, please take a look at [[Compile guh]]. 

    The *guh*-repo provides following packages:
    
        $ apt-cache search guh
    
        guh - server for home automation systems - meta package
        guh-dbg - server for home automation systems - debug symbols
        guh-doc - documentation for the guh package (on-site)
        guh-plugins - server for home automation systems - plugins
        guh-tests - tests for the guh package
        guhd - server for home automation systems
        libguh1 - server for home automation systems - core library
        libguh1-dev - server for home automation systems - development files

3. Install *guh* with following command:
    
        $ sudo apt-get install guh -y --force-yes
    
    > Note: you need to install the packages without verification.
    
    The repository contains always the latest stable build of the *guh* `master` branch. 

Once, the installation is finised you continue with the [[Getting started]] instruction.
    
