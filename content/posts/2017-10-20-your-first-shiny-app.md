---
title: Your first Shiny app
author: Riinu Ots
date: '2017-10-20'
thumbnailImage: /img/thumbnails/shiny_first_app_bubbles.png
categories:
  - R
tags:
  - shiny
slug: your-first-shiny-app
---

### What is Shiny?

Shiny is an R package (`install.packages("shiny")`) for making your outputs interactive. Furthermore, Shiny creates web apps meaning your work can be shared online with people who don't use R. In other words: with Shiny, R people can make websites without ever learning Javascript etc.

I am completely obsessed with Shiny and these days I end up presenting most of my work in a Shiny app.

{{< alert info >}}
If it's not worth putting in a Shiny app it's not worth doing.
{{< /alert >}}

### Your first Shiny app

Getting started with Shiny is actually a lot easier than a lot of people make it out to be. So I created a very short (8 slides) presentation outlining my 5-step programme for your first Shiny app.

This is the app: <https://riinu.shinyapps.io/shiny_testing/>

<iframe src="https://riinu.shinyapps.io/shiny_testing/" width="600" height="600" frameBorder="0"></iframe>

Here's the presentation: http://rpubs.com/riinu/shiny

And here are the steps (also included in the presentation):

**STEP 0**: `install.packages("shiny")`. Use RStudio.

**STEP 1**: Create a script called `app.R` using this skeleton:

```r
library(shiny)
library(tidyverse)
library(gapminder)

# User Interface
ui <- basicPage(
  
  plotOutput(outputId = "myplot")
  
)

# Server
server <- function(input, output) {
  
  output$myplot <- renderPlot({
    #your plot code here:
  })  
  
}

shinyApp(ui, server)
```

https://gist.github.com/riinuots/c6ec0691633df2929adc7de90bdbc792

**STEP 2**: Copy your plot code into the renderPlot function.

```r
# Server
server <- function(input, output) {
  
  output$myplot <- renderPlot({
    #your plot code here:
    gapminder %>% 
      filter(year == 2007) %>% 
      ggplot(aes(y = lifeExp, x = continent)) +
      geom_jitter(aes(size = pop/1000000, fill = lifeExp),
                  shape = 21, colour = "grey", alpha = 0.8, width = 0.15) +
      scale_fill_distiller(palette = "Paired") +
      coord_cartesian(ylim = c(30,85)) +
      scale_size("Population, millions", range = c(5, 25), breaks = c(10, 50, 100, 250, 1000)) +
      theme_bw() +
      labs(caption = "Each bubble is a country.", ylab = "Life expectancy")  +
      theme(aspect.ratio=0.6)
  })  
  
}
```

**STEP 3**: Add a `sliderInput` to your User Interface (`ui`). A slider is just one of the many Shiny widgets you could be using: https://shiny.rstudio.com/gallery/widget-gallery.html

```r
# User Interface
ui <- basicPage(
  
  sliderInput("year", "Select year:",
              min = 1952, max = 2007, value = 2007,
              step = 5,
              # so thousands are not separated with a comma
              # (without sep = "" the scale defaults to 1,952 - 2,007)
              sep = ""   
  ),       # note this comma here - different to our usual R code
  plotOutput(outputId = "myplot")
  
)
```

**STEP 4**: Tell your Server you wish the `dplyr::filter()` to use the value from the slider. All inputs from the User Interface (`ui`) are stored in `input$variable_name`: replace the `2007` with `input$year`.

Change this

```r
gapminder %>% 
  filter(year == 2007) %>%
  ggplot(aes(y = lifeExp, x = continent)) +
  ...

```

to this:

```r
gapminder %>% 
  filter(year == input$year) %>%
  ggplot(aes(y = lifeExp, x = continent)) +
  ...

```

Press `Control+Shift+Enter` or the "Run App" button.

You now have a fully functioning Shiny app and all you had to do was wrap your beautiful plot code inside some `({})`s, add a `sliderInput()`, and replace `2007` with `input$year`.

**STEP 5 (optional)**: Add `animate = TRUE` inside `sliderInput()`.

The final resulting app and code: https://riinu.shinyapps.io/shiny_testing/

* You now understand the basic skeleton - that there is a user interface (ui) and a server.
* More about getting started with Shiny can found here: https://shiny.rstudio.com/articles/basics.html
* Free Shiny book: https://mastering-shiny.org/

* It is possible to separate app.R into two separate scripts: ui.R and server.R. This does not change the functionality but allows to better organise your code. Furthermore, if you find yourself writing very large and complicated Shiny apps, then look into 'modularizing Shiny code'. `library(golem)` is particularly helpful for creating modular Shiny apps.


* This tutorial runs a Shiny app on your computer. To share it with the world it will need to be deployed to a server running R.
    - It's easiest to use https://www.shinyapps.io/, a few small apps are free to deploy and share
    - Your company/team/institute may host Shiny apps using RStudio Connect software
    - Or you may install Shiny Server Opensource on a server you own and manage: https://www.rstudio.com/products/shiny/download-server/