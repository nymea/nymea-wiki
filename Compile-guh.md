# Compile the *guh* source code
--------------------------------------------
This tutorial shows you how to compile *guh*.

*guh* is written in [Qt](http://qt-project.org/) which is a full development framework with tools designed to streamline the creation of applications and user interfaces for desktop, embedded, and mobile platforms. With Qt, you can reuse code efficiently to target multiple platforms with one code base.

**You need a Qt version >= 5.2**

Officially is *guh* only supported on Linux platforms, which means this guide is for Linux users only.

--------------------------------------------
## Table of contents:

* [Compile *guh* with the QtCreator](https://github.com/guh/guh/wiki/Compile-guh#compile-guh-with-the-qtcreator)
* [Compile *guh* in the terminal](https://github.com/guh/guh/wiki/Compile-guh#compile-guh-in-the-terminal)
* [*qmake* configuration](https://github.com/guh/guh/wiki/Compile-guh#qmake-configuration)
* [*make* extra targets](https://github.com/guh/guh/wiki/Compile-guh#make-extra-targets)

--------------------------------------------
## Compile *guh* with the QtCreator

1. If you want to open the *guh*-project wit the Qt-SDK (`qtcreator`), you have to install the needed packages either from the official repository of your distribution 

        $ sudo apt-get install build-essential qt5-default qtcreator git

    or you can install Qt manually with the *Qt Installer for Linux*. All necessary downloads can be found here:

    [Download Qt](http://www.qt.io/download-open-source/#)

2. Once you installed Qt you can clone the *guh* source code:
    > **Note:** It's good practice to create a sub folder with the name of the application. The QtCreator will create by default a build directory next to the source folder. This keeps the source folder free of output and binary files. 

        $ mkdir guh
        $ cd guh/
        $ git clone https://github.com/guh/guh.git

    Now open the project file (`/guh/guh/guh.pro`) with the QtCreator and configure your project. You can use the default setting, which will create a `build-guh-<Kit>-Debug` directory next to the source code directory where all build output files and binaries will be generated.

3. In order to speed up the the compilation process you need to know how many CPU's you have:

        $ nproc
        8
        
    In the QtCreator (`guh.pro` opened) do following steps:
    
    * Go to *Projects* on the left side of the window.
    * Go to the *Build* tab of your Kit
    * Under *Build Steps* click on *Detail* of the `Make:` line
    * Write in the *Make arguments* field: `-j9`
    
        > **Note:** the `-j` argument specifies the number of jobs (commands) to run simultaneously. With `n` CPU's you can run `n+1` jobs.

4. Press the *Build* button on the bottom left of the QtCreator window (`Ctrl` + `b`) and follow the build process in the *Compile output* section (`Alt` + `4`).

5. Before you can run the fresh compiled *guh* binary, you need to export the library path to the libguh, otherwise you will get following message:
    
        $ guhd: error while loading shared libraries: libguh.so.1: cannot open shared object file: No such file or directory

    In order to export the lib path, you can run following command in the terminal:     
    > **Note:** customize the path to your guh folder!
        
        $ export LD_LIBRARY_PATH=/PATH_TO_GUH/guh/build-guh-Desktop-Debug/libguh/
    
    To make it permanent, you can add this line to the `/etc/bash.bashrc` file.

6. Now you should be able to run *guhd* by pressing the *Play* button in the QtCreator (or you can press `Ctrl` + `r`). You can follow the stdout in the *Application Output* section (`Alt` + `3`).

    If you want to run the application in the terminal you can start *guh* with following command:

        $ cd build-guh/server/
        $ ./guhd

You can proceed with the [[Getting started]] instructions.

--------------------------------------------
## Compile *guh* in the terminal

1. Install needed packages to compile *guh*:
    > **Note:** If you want to compile *guh* on the Raspbian *wheezy* you need to add a new repository to get `qt5-default` ([Qt5 on raspbian wheezy](https://github.com/guh/guh/wiki/Raspberry-Pi#add-qt-repository))
    
        $ sudo apt-get install build-essential qt5-default git

2. Clone the source code git repository:
   > **Note:** It's good practice to create a sub-folder with the name of the application and create a build directory next to the source directory. This keeps the source folder free of output and binary files. 
        
        $ mkdir guh
        $ cd guh/
        $ git clone https://github.com/guh/guh.git

3. Create a build folder:
    
        $ mkdir build-guh
        $ cd build-guh
        
4. Run `qmake` (See also [*qmake* configuration](https://github.com/guh/guh/wiki/Compile-guh#qmake-configuration))
    
        $ qmake ../guh/
        
5. In order to speed up the the compilation process you need to know how many CPU's you have:
    
        $ nproc
        8  
        
    Compile *guh*:
    > **Note:** the `-j` argument specifies the number of jobs (commands) to run simultaneously. With `n` CPU's you can run `n+1` jobs.
        
        $ make -j9        
        
    
6. Now you have two possibilitis:

    * If you want to install your compiled *guh* version you can type following command in the build directory:

            $ sudo make install    
    
    * If you don't want to install the application you need to export the library path to the libguh before you can start the application, otherwise you will get following message:
    
            $ guhd: error while loading shared libraries: libguh.so.1: cannot open shared object file: No such file or directory

        In order to export the lib path, you can run following command in the terminal:     
        > **Note:** customize the path to your guh folder!
        
            $ export LD_LIBRARY_PATH=/PATH_TO_GUH/guh/build-guh/libguh/
    
        To make it permanent, you can add this line to the `/etc/bash.bashrc` file. 
        
Now you can run *guh* with following command:

> **Note:** ensure that there is no other *guh* installation in your system. If you already have installed *guh* somewhere, there could be a collision with the different libs!

        $ cd build-guh/server/
        $ ./guhd

You can proceed with the [[Getting started]] instructions.

## *qmake* configuration

In order to customize the build process, qmake offers some configurations.

#### Compile guh without *tests*

If you want to compile *guh* witout the test packages you can configure qmake like this:

        $ qmake ../guh/ CONFIG+=disabletesting
    
> **Note:** this will shorten the compilation time significantly.

#### Compile with *coverage*

        qmake ../guh/ CONFIG+=coverage

#### Compile guh using ccache

        qmake ../guh/ CONFIG+=ccache

#### Compile guh for snappy package

        qmake ../guh/ CONFIG+=snappy

#### Configure the installation path

        qmake ../guh/ PREFIX="path/where/i/want/to/install/guh"

Once you call `make install` all project output files will be installed in the corresponding directory.


## *make* extra targets

#### Build documentation

        $ cd build-guh
        $ make doc

#### Build and run tests

        $ cd build-guh
        $ make test

#### Check source code for missing license/copyright header

        $ cd build-guh
        $ make licensecheck

#### Pack all depending libs to a folder

        $ cd build-guh
        $ make packlibs


