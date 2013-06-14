---
layout: post
title: Useful subversion alias
category: Development
comments: true

excerpt: Add new files ready to commit to svn as alias

---

After using subversion from terminal for a while now, i've found following command so useful, I've turned it into an alias.

**Add new files ready to commit**

`svn st | grep "^?" | awk '{print $2}' | xargs svn add`

This command is a mouthful but saves you from adding each file individually.

When you want to use this alias you'll have to take care of the nested quotes and escape them.

`alias sa='svn st | grep "^?" | awk '\''{print $2}'\'' | xargs svn add'`

One could make several variations on this alias for svn remove, revert or others. You'll just have to change the grep and xargs arguments.