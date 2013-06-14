---
layout: post
title: Apache awfully slow caused by antivirus software
category: Development
comments: true

excerpt: I've finally figured out why apache was running so slow on my Windows 7 machine.

---

I've finally figured out why apache was running so slow on my Windows 7 machine.

After trying really lots of suggestions found on the web, I stumbled on the obvious fact that perhaps my antivirus was causing troubles. And yes indeed, after excluding my sites root from the scanner everything worked as it should be.

I've really should of known because playing with a SVN server locally has taught me before about the troubles of antivirus software messing with filesystem access.

Lesson of today: when filesystem intensive software encounters locks or is painfully slow, check if your antivirus program ain't causing the troubles by excluding those directories.

Note: I was using AVG Anti-Virus 9. Open up the dashboard by clicking the AVG icon in the notification area on the taskbar. Open the advanced setting under the tools menu. The directory excludes can be found under the resident shield section.

PS: I know, why still bothering doing webdevelopment on Windows right? So you linux and mac users can have other reason to praise your fine OS :-) And me? Well, I'm really looking out to switch but for some reason didn't do it... yet.