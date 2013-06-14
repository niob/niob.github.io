---
layout: post
title: Fix "The server is not responding" for PhpMyAdmin on Mac OS X
category: Development
comments: true

excerpt: 

---

First I downloaded and moved all PhpMyAdmin files to an appropriate directory and added an alias to my Apache's httpd.conf.

But PhpMyAdmin or better the mysql extension could not connect to my local mysql server, it gave me following message:

> #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

Luckily there's an easy fix. The mysql extension apparently seems not capable of resolving localhost, so replacing the host with 127.0.0.1 did the trick.

Hoorah!