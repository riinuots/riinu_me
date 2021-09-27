---
title: Add up two variables of a netCDF file
author: Riinu Ots
date: '2014-05-29'
categories:
  - netCDF
tags:
  - ncap2
  - NCO
  - netcdf
slug: add-up-the-values-of-two-variables-of-a-netcdf-file
---

[NCO:ncap2](http://nco.sourceforge.net/nco.html#ncap2-netCDF-Arithmetic-Processor) is the function to do it:

`ncap2 -s 'new_var=var1+var2' in_filename.nc out_filename.nc`

The output file will have all of the variables that exist in the input file as well as the new_var. Add -O if your input and output files are the same (overwrite).

I do not know what the -s stands for.

BUT the new_var will have the same long_name as the first variable used for summing (i.e. it could make some things a bit confusing). To change it, use a very complicated (but allegedly also very powerful) [NCO:ncatted](http://nco.sourceforge.net/nco.html#ncatted-netCDF-Attribute-Editor). Fortunately, its documentation has just the right example:


Change the value of the `long_name` attribute for variable `T` from whatever it currently is to "temperature":

`ncatted -a long_name,T,o,c,temperature in.nc`

