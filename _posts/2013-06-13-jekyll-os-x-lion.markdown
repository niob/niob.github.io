---
layout: post
title: Compile Jekyll gem on OS X 10.7 (Lion)
category: dev

excerpt: Hello World! Vestibulum imperdiet adipiscing arcu, quis aliquam dolor condimentum dapibus. Aliquam fermentum leo aliquet quam volutpat et molestie mauris mattis. Suspendisse semper consequat velit in suscipit.

---

On OS X 10.7 or Lion (and up) you can't install the Jekyll gem out of the box. This is probably because one of following reasons:

* GCC toolchain is not installed 
* Xcode 4.x and its command line tools are installed but the ruby version can't compile with the LVVM compiler

A lot of solutions are suggested on blogs and StackOverflow but for me the easiest was to upgrade to the newest version of Ruby with brew.

`brew upgrade ruby`

## give priority to this ruby version by prepending its location to the path environment variable 

`export PATH=/usr/local/opt/ruby/bin:$PATH`

`gem install jekyll`
