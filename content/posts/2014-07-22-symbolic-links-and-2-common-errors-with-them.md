---
title: Symbolic links and 2 common errors with them
author: Riinu Ots
date: '2014-07-22'
categories:
  - Unix
tags:
  - errors
  - ln
  - symbolic link
  - unix
slug: symbolic-links-and-2-common-errors-with-them
---

I don't know if it's good or bad, but I like when the files I'm working with are in the working directory (so instead of using pathnames to my files I can just type filename or ./filename). But to avoid copying data and wasting space, symbolic links are the way to go. The command for that is:

`ln -s target_file sym_link`,

where -s stands for "symbolic" (just ln would create a hard link)

However, if you are not a complete UNIX guru, then trying to access your linked files is likely to produce one of these errors:

No such file or directory OR Too many levels of symbolic links

The solution to both of these is to **always use full paths** to the files and their symbolic links (`ln -s /home/folder/file.txt /home/folder2/file.txt`). For further information, see [this](http://superuser.com/questions/322319/when-creating-a-symbolic-link-how-do-i-troubleshoot-too-many-levels-of-symboli) and [this](http://www.unix.com/unix-for-dummies-questions-and-answers/11324-too-many-levels-symbolic-links.html). Apparently you can have 32 levels of symbolic links, so getting a "Too many levels of symbolic links" after just creating one, means that there is some serious recursion going on.

Remove symbolic links just as you remove files:

`rm sym_link`
