# Using the *boblightd* plugin
--------------------------------------------

In order to use the *boblightd* you need to compile and install boblight. This tutorial shows you how to that.

## Build and install boblight

The project page of boblight can be found [here](https://code.google.com/p/boblight/). 

Install all needed packages:

    $ apt-get update
    $ apt-get install build-essential subversion portaudio19-dev libusb-1.0-0-dev
    
Download the source code using:

    $ svn checkout http://boblight.googlecode.com/svn/trunk/ boblight

Configure the project:

    $ cd boblight
    $ ./configure
    
> **Note:** install the missing packages if *configure* will not finish successfully!

Build everything:
        
    $ make -j9
    
> **Note:** the `-j` argument specifies the number of jobs (commands) to run simultaneously. With `n` CPU's you can run `n+1` jobs.
    
Install the binaries, libs and includes:
    
    $ sudo make install

## Run *boblightd*    

Create your boblight config file and copy it to `/etc/boblight.conf`.

[Boblight conf wiki](https://code.google.com/p/boblight/wiki/boblightconf)

Now you can start the boblight daemon:

    $ sudo boblightd
    
This daemon has to run, otherwise the *boblight-plugin* from guh will not work. The plugin tries to connect to the daemon on `localhost:19333`. The configured light devices from the `/etc/boblight.conf` device will appear automatically in the *guh* device list. 

See also: [Compile guh with *boblightd* support](https://github.com/guh/guh/wiki/Compile-guh#compile-guh-with-boblightd-support).