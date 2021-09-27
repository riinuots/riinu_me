---
title: Saving some variables from a netCDF to a new file
author: Riinu Ots
date: '2014-05-29'
categories:
  - netCDF
tags:
  - ncdump
  - ncks
  - NCO
  - netcdf
slug: saving-some-variables-from-a-netcdf-to-a-new-file
---

The NCO ([**n**et**C**DF **O**perator](http://nco.sourceforge.net/)) command ncks ([netCDF Kitchen Sink](http://nco.sourceforge.net/nco.html#ncks-netCDF-Kitchen-Sink)).

From the [documentation](http://nco.sourceforge.net/nco.html#ncks-netCDF-Kitchen-Sink):


> The nickname "kitchen sink" is a catch-all because `ncks` combines most features of `ncdump` and `nccopy` with extra features to extract, hyperslab, multi-slab, sub-set, and translate into one versatile utility. `ncks` extracts (a subset of the) data from input-file and and writes (or pastes) it in netCDF format to output-file, and optionally writes it in flat binary format to binary-file, and optionally prints it to screen.

> /.../

> `ncks` extracts (and optionally creates a new netCDF file comprised of) only selected variables from the input file (similar to the old `ncextr` specification). Only variables and coordinates may be specifically included or excluded—all global attributes and any attribute associated with an extracted variable are copied to the screen and/or output netCDF file.


The flag for extracting variables is -v (followed by variable name(s) separated by commas):

`ncks -v var1,var2 in.nc out.nc`         no space after the comma!

In case you've forgotten what the names of your variables are, do:

`ncdump -h in__filename_.nc`

-h prints headers only (and not the values). I usually direct the output of ncdump to a text file:

`ncdump -h in__filename_.nc > ncdump.txt`

Also, if you forgot some of the variables that you wanted then you don't have to do the whole list again - NCO is always willing to append variables. So if you run:

`ncks -v var3 in.nc out.nc`

but the out.nc already exists, then NCO will prompt you with this:


> ncks: out.nc exists---`e'xit, `o'verwrite (i.e., delete existing file), or `a'ppend (i.e., replace duplicate variables in and add new variables to existing file) (e/o/a)?


So you can enter a and hit 'return'.
