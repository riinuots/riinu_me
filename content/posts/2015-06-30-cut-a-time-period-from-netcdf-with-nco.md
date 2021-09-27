---
title: Cut a time period from netCDF with nco
author: Riinu Ots
date: '2015-06-30'
categories:
  - netCDF
tags:
  - ncks
slug: cut-a-time-period-from-netcdf-with-nco
---

`ncks -d time,start_time,end_time in.nc out.nc`

`start_time` and `end_time` are integers.

Add -F, if you want to use Fortran indexing (to start from 1).

No space between dimension name and start-end points!
