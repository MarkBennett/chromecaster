chromecaster
============

A demonstration Chromecast app.


What is Chromecast?
============

A HDMI dongle for your TV that lets you communicate with and control an HTML receiver app running on the Chromecast from your web browser.

![Launching an app](https://docs.google.com/drawings/d/1LkJFn5XWxA_KPXxmrV0bqGMHrY5CeY0zD_TYqsbl0bE/pub?w=960&h=720)

What do you need to get started?
=====

* [ ] A Chromecast
* [ ] A Google account
* [ ] A place to host your custom receiver
* [ ] Chromecast registered on [Google SDK Developer Console](https://cast.google.com/publish/#/devices)
* [ ] Custom Received App registerd on [Google SDK Developer Console](https://cast.google.com/publish/#/applications)

Troubleshooting
===
1. *Check that you registered your development Chromecast properly.* You can confirm this by getting the Chromecast IP from the Chromecast app on your phone then trying to access http://CHROMECAST_IP:9222. [Read the docs for more details](https://developers.google.com/cast/docs/custom_receiver#debugging).
2. *Try restarting Chrome* If you've just changed the details of your receiver app, especially the end point or it's configuration, you'll want to restart Chrome.
3. *Try restarting your Chromecast* If the receiver app just isn't available, and your sure your Chromecast is registered for a development (aka you can do remote debugging) then try restarting it once you've confirmed your app is registered in the Google Cast SDK Developer Console.

links
======

* [receiver](https://rawgit.com/MarkBennett/chromecaster/gh-pages/receiver.html)
* [sender](https://rawgit.com/MarkBennett/chromecaster/gh-pages/sender.html)
* [app console](https://cast.google.com/publish/#/overview)
* [reveiver dev guide](https://developers.google.com/cast/docs/custom_receiver)
* [sender dev guide](https://developers.google.com/cast/docs/chrome_sender)
