# Open Weather Map Plugin
--------------------------------------------

This plugin alows you to get the current weather data from [http://www.openweathermap.org](http://www.openweathermap.org). 

The plugin offers two different search methods: if the user searches for a empty string, the plugin makes an autodetction with the WAN ip and offers the user the found autodetectresult. The autodetection function uses the geolocation of your WAN ip and searches all available weather stations in a radius of 2.5 km. Otherwise the plugin returns the list of the found search results from the search string.

> **Note**: If you are using a VPN connection, the autodetection will show the results around of your VPN location.