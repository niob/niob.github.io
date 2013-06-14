---
layout: post
title: Fix Mac OS X svn ssl bug 'bad decompression'
category: Development
comments: true

excerpt: 

---

Using SVN over SSL has been a real pain on Mac OS X (tested on snow leopard and lion).

More 'heavy' SVN commands may cause "SSL handshake failed: SSL error: bad decompression", depending on your server configuration.

After some research this should be due a bug in the SSL library bundled with Apple's developer tools.

On the CollabNet forums someone suggested switching the standard http library called Neon for a new one called [Serf](http://code.google.com/p/serf/) written by some Google developers. This library should be really performant and handles SSL by itself.

Sadly the SVN tools from Apple don't come with the Serf library so we have to [download a package](http://subversion.apache.org/packages.html#osx) which does.

The trick is the configure SVN to use the Serf library instead of the Neon library.

Owkay, so let's fix this step by step!

**Step 1: check existing svn**

Open up a terminal and check if the Serf library is for some reason already available by using following command:

`svn --version`

![Check svn version](/static/2011/07/subversion-bug-screen1.png)

The library is available when you find "\*ra_serf" in the list. If so, goto step 4.

**Step 2: install svn package**

*Snow Leopard*

[Download a SVN package](http://subversion.apache.org/packages.html#osx) and install. Remember the location where the svn tools will live. (note: i've used CollabNet but registration is required, others should do fine also I think)

*Lion*

At the time of writing this post there seems to be no package available for Lion on CollabNet but you can with [MacPorts](http://www.macports.org/). After upgrading to Lion, you'll also have to upgrade (sudo port -v selfupdate) or install MacPorts but you'll also need the latest Xcode (>= 4.1). You can install subversion with MacPorts with "sudo port install subversion". Following steps stay the same except the svn tools will live in another directory, for me that's /opt/local/bin.

**Step 3: check for serf library**

Let's check again if Serf's available. (note: replace path with your own install location)

`/opt/subversion/bin/svn --version`

![Check svn version](/static/2011/07/subversion-bug-screen2.png)

As you can see, the Serf library is available!

**Step 4: configure svn**

Great, now we just have to configure your subversion settings so it will use the Serf library. 

`open ~/.subversion/servers`

Search for the [global] section and add "http-library = serf" and save file.

![Edit subversion servers config](/static/2011/07/subversion-bug-screen3.png)

**Step 5: add new svn tools to path**

To complete this, we add the freshly installed svn tools to the environment path.

`open ~/.profile`

And add following:

`export PATH=/opt/subversion/bin:$PATH`

Again, use the path to which you've installed the tools. Make sure the existing path gets appended so the new svn tools will take precedence over old ones.

**Step 6: retry failed svn commands**

After this, you should be able to execute svn command without the SSL "bad decompression" error.

If not, check if you really using the new svn tools and make sure they got exported to your environment. (note: initiate new terminal session so path changes take effect)

A good command to diagnose the problem in my case was doing a recursive svn list command.

`svn ls -R https://svn.example.com/project/trunk`

That's it! Enjoy!