---
layout: post
title: Compile Jekyll gem on OS X 10.7 (Lion)
category: Development

excerpt: On OS X 10.7 or Lion (and up) you can't install the Jekyll gem out of the box. A lot of solutions are suggested on blogs and StackOverflow but for me the easiest was to upgrade to the newest version of Ruby (from 1.8.x to 2.x) with brew wich is capable of compiling native extensions.

---

On OS X 10.7 or Lion (and up) you can't install the Jekyll gem out of the box. This is probably because one of following reasons:

* Xcode 4.x and its command line tools are installed but the ruby version can't compile with the LVVM compiler
* Xcode is not installed and no GCC toolchain could be found

A lot of solutions are suggested on blogs and StackOverflow but for me the easiest was to upgrade to the newest version of Ruby (from 1.8.x to 2.x) with brew wich is capable of compiling native extensions.

Prerequisites are [brew](http://mxcl.github.io/homebrew/) and [XCode](https://itunes.apple.com/nl/app/xcode/id497799835?mt=12) with [command line tools](http://developer.apple.com/library/ios/#documentation/DeveloperTools/Conceptual/WhatsNewXcode/Articles/xcode_4_3.html#//apple_ref/doc/uid/1006-SW2) or [GCC toolchain](https://github.com/kennethreitz/osx-gcc-installer).

**Upgrade ruby with brew**

`brew upgrade ruby`

**Give priority to this ruby version by prepending its location to the path environment variable**

`export PATH=/usr/local/opt/ruby/bin:$PATH`

note: add this to your ~/.profile to persist

**Install Jekyll**

`gem install jekyll`

And that's it. Ruby 2.x compiles native extensions with LVVM without any trouble.