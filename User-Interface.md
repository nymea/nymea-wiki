# User Interfaces

Since you are such a smarty pants and has installed guhIO, you are now in the lucky position to choose from various user interfaces.

## Web Interface

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

## Smartphone App

At the moment wir are developing Apps for Android and iOS. It will take some time that it can be downloaded in the App-Stores. But for the Android Users there is a Alpha Prototype to play around (and report some bugs).

## Command Line Interface

Here is a Link on how to install guh-cli


Start Screen V1.0.3

![guh-cli ](https://cloud.githubusercontent.com/assets/5207214/8826753/fbd254ec-3088-11e5-9e07-10c3a276de39.png)

Devices Screen V1.0.3

![guh-cli devices](https://cloud.githubusercontent.com/assets/5207214/8826760/0cfab5b6-3089-11e5-9012-df0aad571f08.png)
