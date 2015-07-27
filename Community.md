# Community

Threre are various channels thrue that you can contact the guh Team or the guhIO community.

If you want to present your project or want to share your newest developments, share it please in the
[Google+ Community](https://plus.google.com/u/0/communities/113467056514652214831). There get also the newest stuff about guhIO announced.

If you are facing any troubles, than don't hesitate to reach out for us or the community members, we will be pleased to help you:

* [Mailinglist](https://groups.google.com/forum/#!forum/guhio)
* IRC Channel `#guh on freenode.net`

Please, check before our FAQ or our [Google+ Group](https://groups.google.com/forum/#!forum/guhio) if your question is already answered.

From time to time the guh Team is hosting or attending meet-ups and workshops. If you want to meet the developers of guhIO you can find them there. The next events are listed [here](https://plus.google.com/u/0/communities/113467056514652214831/events).

# Reporting bugs
--------------------------------------------

If you have found a bug in *guh*, please create a new issue with the "**bug**" label in the related repository:

* *guh*-daemon - [https://github.com/guh/guh/issues](https://github.com/guh/guh/issues)
* *guh*-cli - [https://github.com/guh/guh-cli/issues](https://github.com/guh/guh-cli/issues)
* *guh*-webserver - [https://github.com/guh/guh-webserver/issues](https://github.com/guh/guh-webserver/issues)
* *guh*-webinterface - [https://github.com/guh/guh-webinterface/issues](https://github.com/guh/guh-webinterface/issues)

If you don't know where the bug occurs, please use the *guh*-daemon issues link.

## Steps to find out whats wrong

1. In order to find out what's wrong it's very helpful to start the *guh* daemon in the foreground:

        $ guhd -n

    Now you can follow the debug output of the core and check what's going on.

2. Make shure, there is only one instance of `guhd` running on your system, otherwise they will block each others ports.
3. Try to use the [guh-cli](https://github.com/guh/guh/wiki/guh-cli) (which is communicating directly with the JSON-RPC API)
4. If you have made an upgrade of guh, a plugin configuration might have changed. Try to reset the configurations (see [here](https://github.com/guh/guh/wiki/Configuration)) and restart the guh daemon.