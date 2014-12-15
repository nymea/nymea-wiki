# *guh* wiki

Welcome to the *guh* wiki. *guh* (/[guːh]/ - pronounced german and sounds like *goo*) is an open source home automation server, which allows to control a lot of different devices from many different manufacturers. With the powerful rule engine you are able to connect any device available in the system and create individual scenes and behaviours for your home. 

## Structure
The whole system has basically three layers:

1. [*guh* core:](https://github.com/guh/guh) the core is an application written in [Qt](http://qt-project.org/) and contains the whole communication with the hardware, loads the supported devices from the plugins, manages all devices and rules. The core provides a JSON-RCP api to allow clients to communicate with the core.

2. [*guh* rails:](https://github.com/guh/guh_rails) the *guh* rails application is an application written in [Ruby on Rails](http://rubyonrails.org/) and contains a webserver which provides a REST api. This application communicates directly with the core and translates the JSON-RPC to the REST api.

3. [*guh* angular:](https://github.com/guh/guh_angular) the *guh* angular application is an application written in [AngularJS](https://angularjs.org/) and provides the browser based user interface. The application uses the REST api from the guh rails server and offers the user an easy and beautiful possibility to interact with his home. 
