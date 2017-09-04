# Install *guh*-core on Ubuntu

The repository provides packages for following architectures:

| Ubuntu     | 16.04 Xenial | 17.04 Zesty  | 
|:-----------|:------------:|:------------:|
| `amd64`    |       ✔      |       ✔      |
| `i386`     |       ✔      |       ✔      |
| `armhf`    |       ✔      |       ✔      |
| `arm64`    |       ✔      |       ✔      |
--------------------------------------------

In order to install *guh* on Ubuntu you need to create the `/etc/apt/sources.list.d/guh.list` file and add the *guh*-repository:

1. Create the [*guh*-repository](http://repository.guh.io/) list file:
        
        $ sudo nano /etc/apt/sources.list.d/guh.list
        
    In the repository are following distributions available:
    * ~~`trusty`~~ (end of support: 10.05.2016)
    * ~~`utopic`~~ (end of support: 29.04.2016)
    * ~~`vivid`~~ (end of support: 16.02.2017)
    * `wily`
    * `xenial` 

    Available architectures are `amd64` `i386` and `armhf`.
    
    > *Note:* please replace `<dist>` with the codename of your Ubuntu distribution. You can get your system version with `lsb_release -a` or `$ cat /etc/os-release`. 

    Copy following lines into the file (with replaced `<dist>`) and save it:

        ## guh repo
        deb http://repository.guh.io <dist> main
        deb-src http://repository.guh.io <dist> main
        

    > **Alternative:** `$ echo -e "\n## guh repo\ndeb http://repository.guh.io <dist> main\ndeb-src http://repository.guh.io <dist> main" | sudo tee /etc/apt/sources.list.d/guh.list`
    
    Add the public key of the [*guh*-repo](http://repository.guh.io) to your keylist.
    
        $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key A1A19ED6

        
2. Update your package lists:
    
        $ sudo apt-get update

    The *guh*-repo provides following packages:
    
        $ apt-cache search guh
    
        guh - An open source IoT server - meta package
        guh-cli - guh command line interface - python
        guh-dbg - An open source IoT server - debug symbols
        guh-doc - Documentation for the guh package (on-site) - documentation
        guh-plugins - Plugins for guh IoT server
        guh-plugins-maker - Plugins for guh IoT server - for maker, tinker and hackers
        guh-plugins-merkur - Plugins for guh IoT server - 6LoWPAN Merkur boards
        guh-tests - Tests and mock plugin for the guh package
        guh-webinterface - Browser based user interface for guh
        guh-webinterface-doc - Documentation of the guh webinterface source code (on-site) - documentation
        guhd - An open source IoT server - daemon
        libguh1 - An open source IoT server - core library
        libguh1-dev - An open source IoT server - development files


3. Install *guh* with following command:
    
        $ sudo apt-get install guh guh-cli guh-webinterface
        
    The repository contains always the latest stable build of the *guh* `master` branch. 
    If you want to install the source code you can install:
        
        $ sudo apt-get source guh        
        $ sudo apt-get source guh-cli
        $ sudo apt-get source guh-webinterface
        
Once, the installation is finished you continue with the [[Getting started]] instruction.

