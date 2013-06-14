---
layout: post
title: Android secret code trick for testing purposes
category: Development
comments: true

excerpt: 

---

Android users can launch various tests and other advanced functions straight from the dialer by entering secret codes. These codes follow a certain pattern: *#*#{number}#*#*.

You can use the Android secret code trick in your own apps for lots of reasons; like switching between development and production webservices or toggling debug modes.

Below the gist of trick (pun intended):

First we declare a Broadcast receiver in our manifest.

<script src="https://gist.github.com/2006546.js?file=ReceiverManifest.xml"></script>

Second we write the receiver and flip a boolean value everytime the secret code has been entered in the dialer.

<script src="https://gist.github.com/2006546.js?file=MySecretBroadcastReceiver.java"></script>