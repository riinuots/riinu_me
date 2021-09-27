---
title: 'Latex tables: column widths and alignments'
author: Riinu Ots
date: '2014-11-04'
categories:
  - LaTex
tags:
  - latex
  - tables
slug: latex-tables-column-widths-and-allignments
---

Firstly, start off your table in <http://www.tablesgenerator.com/>.

Tables Generator will do a lot for you. Its most useful features are importing from .csv and merging cells. The Booktabs table style (alternative to default table style from the menu) looks a bit nicer and is "publication quality". Note that publication quality tables should not contain vertical lines.

![Screen shoti of Tables Generator](http://riinudata.files.wordpress.com/2014/09/tablesgenerator1.png)

<p class="caption">Screen shot of Tables Generator</p>

![](https://riinudata.files.wordpress.com/2014/11/table-1.png)

<p class="caption">Code#1</p>

[Code #1](http://pastebin.com/FS2QLSDF) is the code from Tables Generator with the addition of caption, label and Latex document begin-end (so it's compilable). Continuing from that table, let's centre the contents of columns 1-3 and the whole table in your document, by adding \centering and changing the [table specs](http://en.wikibooks.org/wiki/LaTeX/Tables#The_tabular_environment) from l's to c's: [Code #2](http://pastebin.com/bxLpsydd).

![](https://riinudata.files.wordpress.com/2014/11/table-21.png)

<p class="caption">Code#2</p>

Finally, if your cell contents are long and need wrapping:

![table 3](https://riinudata.files.wordpress.com/2014/11/table-3.png)

 Note that if your table is too wide for your document margins, then LaTex issues a warning, not an error. So you need check for warnings like _"Overfull \hbox (9.75735pt too wide) in paragraph at lines 55--63"_ in your compilation log. A quick solution to wide cells is [like this](http://stackoverflow.com/questions/790932/how-to-wrap-text-in-latex-tables) ([Code#4](http://pastebin.com/GMXj4dap)):

![Code#4](https://riinudata.files.wordpress.com/2014/11/table-4.png)

<p class="caption">Code#4</p>

But this solution does not include decent central alignment. Using m (so m{2cm} instead of p{2cm}) would do the vertical centering (_e.g._ look how the first row is alligned), but still not horizontal. So following [this ](http://tex.stackexchange.com/questions/12703/how-to-create-fixed-width-table-columns-with-text-raggedright-centered-raggedlef)StackOverflow post, I started defining column types and widths using the array package. See [Code#5](http://pastebin.com/EWsvVfqH).

![Code#5](https://riinudata.files.wordpress.com/2014/11/table-5.png)

<p class="caption">Code#5</p>

Next time I might write a post on how to add extra space between lines.
