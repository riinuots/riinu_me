---
title: Handling your .bib file (LaTex bibliography)
author: Riinu Ots
date: '2017-06-17'
thumbnailImage: /img/thumbnails/latex.png
categories:
  - LaTex
slug: handling-your-bib-file-latex-bibliography
---

To create a .bib file that only includes the citations you used in the manuscript:

`bibexport -o extracted_file.bib manuscript.aux`

There are a few issues with this though. The command [bibexport](https://www.ctan.org/pkg/bibexport) comes with the installation of TexLive, but my Windows computer (bless) does not cooperate ("bibexport is not recognised as an internal or external command...") . So I can only use it on my Mac (luv ya).
