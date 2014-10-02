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
* [ ] A place to host your custom receiver and sender apps
* [ ] Chromecast registered on [Google SDK Developer Console](https://cast.google.com/publish/#/devices)
* [ ] Remote debugging working on your Chromecast ([details](https://developers.google.com/cast/docs/custom_receiver#debugging))
* [ ] Custom Receiver and Sender Apps are registerd on [Google SDK Developer Console](https://cast.google.com/publish/#/applications)
* [ ] Your Chromecast has been restarted since your apps were registered

Building the Custom Receiver
=====
To get your receiver app up and running, all you need to do is:

1. Get an APP ID by regitering the custom receiver url in the Google Cast SDK Developer Console
2. Serve a web page from the url you registered

Once you've done this the Chromecast will automatically load your web page when a sender app tries to start a new session.

If you want to do anything interesting though, you'll want to load up the Chromecast Receiver API and start listening to Chromecast Session events. This takes a few more steps:

    // Load the Chromecast Receiver API
    <script src="//www.gstatic.com/cast/sdk/libs/receiver/2.0.0/cast_receiver.js"></script>
    
Then in your JavaScript:

    // Retrieve a reference to CastReceiverManager singleton
    var receiver_mgr = cast.receiver.CastReceiverManager.getInstance();
    
    // Register to handle receiver events
    receiver_mgr.onSenderConnected = function(evt) { ... };
    receiver_mgr.onSenderDisconnected = function(evt) { ... };
    
    // Start receiving events
    receiver_mgr.start()

This will let you track new sender apps connecting and disconnecting to the Chromecast, but you still can't send or receive messages from them.

To send and receiver messages you'll need to get a reference to the [CastMessageBus](https://developers.google.com/cast/docs/reference/receiver/cast.receiver.CastMessageBus) for your app. Each app uses a unique uri to distinguish it's message bus. You don't need to register this and can pick it yourself, but make sure it's not used by other apps.

    var customMessageBus = castReceiverManager.getCastMessageBus('urn:x-cast:super.awesome.example');
    customMessageBus.onMessage = function(event) {
       // Handle message
    }

You can also use the `broadcast()` and `send()` methods of the `customMessageBus` to send messages back to the sender apps.


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
