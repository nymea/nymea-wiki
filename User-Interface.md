# User Interfaces
Since you are such a smarty pants and has installed guhIO, you are now in the lucky position to choose from various user interfaces.

## Web Interface
If your took the raspberry netinstallimage 
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
the :3000 at the is necessary, it indicates the port on that guh is listening - default is 3000


## Smartphone App
At the moment wir are developing Apps for Android and iOS. It will take some time that it can be downloaded in the App-Stores. But for the Android Users there is a Alpha Prototype to play around (and report some bugs).