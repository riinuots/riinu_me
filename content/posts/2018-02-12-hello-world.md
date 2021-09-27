---
title: "Hello world: blogdown loves Hugo"
author: Riinu Ots
date: '2018-02-12'
slug: hello-world
thumbnailImage: /img/thumbnails/blogdown.png
metaAlignment: center
coverMeta: out
categories:
  - scripting
tags:
  - blogdown
  - hugo
  - r
  - github
  - netlify
---


![](https://riinudata.files.wordpress.com/2018/02/blogdown_hugo.png?w=736)

# We are live!

I wrote my last blog post on Wordpress on 20-October 2017 and promised myself this was the last time. I've been blogging on Wordpress since 2014 and the more I used it the more painful it got! This is most likely caused by the fact that I have been thrifting further and further away from point-and-click interfaces anyway...oh and discovering MARKDOWN.


### My two rules:

* text is written in Markdown (I use R Markdown/knitr/bookdown, e.g. see how easy it is to create a book: ["HealthyR: the eBook"](https://surgicalinformatics.github.io/healthyr_book/))
* data analysis ends up in a Shiny app (e.g., see ["If it’s not worth putting in a Shiny app it’s not worth doing."](https://riinu.me/2017/10/20/your-first-shiny-app/))


## So I finally got round to creating a blogdown-Hugo site:


[Hugo](https://gohugo.io/) is a website generator that is code-based (no more dragging around those pesky Wordpress elements); [blogdown](https://bookdown.org/yihui/blogdown/) is an R package that will help you generate Hugo, Jekyll, or Hexo sites, especially if you will be including R Markdown in it.

### Steps on 12-February 2018: 

* Created a new blogdown project on RStudio, set `kakawait/hugo-tranquilpeak-theme` as the theme
* Edited my name, email etc. information in the *config.toml*.
* Absolutely could not figure out how to change `coverImage = "cover.jpg"`. Tried putting my cover image in `/static/img/`, `/static/_images/`, `source/assets/images` and tried linking to these any way I could think of (e.g. with and without the first `/`) but it just wasn't happening. Ended up putting my picture in `/themes/hugo-tranquilpeak-theme/static/images/` and blatantly naming it `cover.jpg` (replacing the theme's default photo). This worked.
* Pushed the whole project to https://github.com/riinuots/hugo-tranquil-website and then created a submobule in https://github.com/riinuots/hugo-tranquil-website/tree/master/themes so when the theme gets updated I can pull the new version. This is not essential. I need to figure out the cover image issue though.
* Set up Netlify as in https://bookdown.org/yihui/blogdown/netlify.html which was superquick but then spent some time troubleshooting why my theme wasn't displaying properly. Turns out that for this theme, it is essential to set the `baseURL = "https://riinu.netlify.com/"` (in *config.toml*). 
* Created this Hello World post which seemed to work fine at first. I then added an unquoted semicolon to the title, broke everything and spent 2 h trying to figure out what went wrong. These were the errors I was getting and that no-one else in the world (Google) seemed to have reported:
   - edits to the new post not happening, but the site isn't broken either
   - `clean_site()` errors with: 
   
   ```rmarkdown::clean_site() Error in file.exists(files) : invalid 'file' argument```
   
   -  after spending 2h on Google/github/rstudio/rmarkdown, blogdown book, blogdown repo, Hugo documentation, I finally came across `hugo -v` (v for verbose). Noticed 
   
   ````yaml: line 1: mapping values are not allowed in this context````
   
   (which I had indeed seen before at some point during these 2 hours). Anyway, seeing it for the second time clicked - markdown thinks I'm mapping something that shouldn't be mapped (mapping usually means defining variables). My title was (second line of the markdown file, really) `title: Hello world: blogdown loves Hugo`, but if using a semicolon you need quotes: `title: "Hello world: blogdown loves Hugo"`.

# Still better than Wordpress.

![](https://riinudata.files.wordpress.com/2018/02/pandas.gif)

## Next steps:

* Set up Disqus (comments).
* Bring over old posts from https://riinudata.wordpress.com
* Write all the new posts ideas I've been gathering over the past 4 months.



