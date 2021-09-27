---
title: How long did my R script run?
author: Riinu Ots
date: '2016-04-15'
categories:
  - R
slug: how-long-did-my-script-run
---

This to the beginning:

strt<-[Sys.time](http://inside-r.org/r-doc/base/Sys.time)()

And this to the end:

[print](http://inside-r.org/r-doc/base/print)([Sys.time](http://inside-r.org/r-doc/base/Sys.time)()-strt)

Example output:

> print(Sys.time()-strt)
Time difference of 16.39691 secs
