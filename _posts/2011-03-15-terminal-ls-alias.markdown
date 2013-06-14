---
layout: post
title: Terminal 'ls' alias
category: Development
comments: true

excerpt: I use 'ls' very frequently in my mac os x or linux terminal. I've mostly been using 'ls -la' which stands for list the ALL files of current directory and put them nicely in columns.

---

I use 'ls' very frequently in my mac os x or linux terminal. I've mostly been using 'ls -la' which stands for list the ALL files of current directory and put them nicely in columns.

A friend of mine gave me a nice tip yesterday. He also adds capital 'G' en 'h' as option. 'G' give you some nice colored or grouped list and 'h' makes sizes human readable.

Because remembering this or typing this over and over again is rather difficult, he also suggested to make an alias like so:

`alias l='ls -alGh'`

This way you only have to type 'l' and there you have your list, how convenient is that?

But when just executing this line in a terminal, it'll be forgotten next time you open one. In order for your aliases to be persistent (i.e. so they exist in all new Terminal windows) you need to put them in some file that gets read by your shell startup files (see "What startup files are read by the shell?"). So for example add the alias to the '~/.profile' file like so:

`nano ~/.profile`

You can add all kinds of aliases or functions to this file so they wil always be available for your account.