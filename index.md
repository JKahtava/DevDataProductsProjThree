---
title       : Slidify Demo      
subtitle    : HTML5 slides from R Markdown
author      : Jussi Kahtava
job         : Budding data scientist
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Read-And-Delete

1. Edit YAML front matter
2. Write using R Markdown
3. Use an empty line followed by three dashes to separate slides!

--- .class #id 

## Slide 1

Animated list

> 1. Point 1
> 2. Point 2
> 3. Point 3

---

## Some code


```r
library(shiny)
shinyUI(fluidPage(
        titlePanel("Predict Diamond price from its weight"),
        sidebarLayout(
                sidebarPanel(
                        sliderInput("sliderCarat", "How many carats is the diamond?", 0.2, 4.0, value = 0.8),
                        selectInput("selectCut", "What is the cut of the diamond?", c("Fair"="Fair","Good"="Good",
                                "Very Good"="Very Good","Premium"="Premium", "Ideal"="Ideal")),
                        selectInput("selectColor", "What is the color of the diamond?", 
                                    c("D"="D","E"="E","F"="F","G"="G","H"="H",
                                      "I"="I","J"="J")),
                        checkboxInput("showModel1", "Show/Hide model for selected features", value = TRUE),
                        checkboxInput("showModel2", "Show/Hide model for all diamonds", value = TRUE)
                ),
                mainPanel(
                        plotOutput("plot1"),
                        h3("Predicted price from selected features:"),
                        textOutput("pred1"),
                        h3("Predicted price from all diamonds:"),
                        textOutput("pred2")
                )
        )
))
```

<!--html_preserve--><div class="container-fluid">
<h2>Predict Diamond price from its weight</h2>
<div class="row">
<div class="col-sm-4">
<form class="well">
<div class="form-group shiny-input-container">
<label class="control-label" for="sliderCarat">How many carats is the diamond?</label>
<input class="js-range-slider" id="sliderCarat" data-min="0.2" data-max="4" data-from="0.8" data-step="0.05" data-grid="true" data-grid-num="9.5" data-grid-snap="false" data-keyboard="true" data-keyboard-step="1.31578947368421" data-drag-interval="true" data-data-type="number" data-prettify-separator=","/>
</div>
<div class="form-group shiny-input-container">
<label class="control-label" for="selectCut">What is the cut of the diamond?</label>
<div>
<select id="selectCut"><option value="Fair" selected>Fair</option>
<option value="Good">Good</option>
<option value="Very Good">Very Good</option>
<option value="Premium">Premium</option>
<option value="Ideal">Ideal</option></select>
<script type="application/json" data-for="selectCut" data-nonempty="">{}</script>
</div>
</div>
<div class="form-group shiny-input-container">
<label class="control-label" for="selectColor">What is the color of the diamond?</label>
<div>
<select id="selectColor"><option value="D" selected>D</option>
<option value="E">E</option>
<option value="F">F</option>
<option value="G">G</option>
<option value="H">H</option>
<option value="I">I</option>
<option value="J">J</option></select>
<script type="application/json" data-for="selectColor" data-nonempty="">{}</script>
</div>
</div>
<div class="form-group shiny-input-container">
<div class="checkbox">
<label>
<input id="showModel1" type="checkbox" checked="checked"/>
<span>Show/Hide model for selected features</span>
</label>
</div>
</div>
<div class="form-group shiny-input-container">
<div class="checkbox">
<label>
<input id="showModel2" type="checkbox" checked="checked"/>
<span>Show/Hide model for all diamonds</span>
</label>
</div>
</div>
</form>
</div>
<div class="col-sm-8">
<div id="plot1" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
<h3>Predicted price from selected features:</h3>
<div id="pred1" class="shiny-text-output"></div>
<h3>Predicted price from all diamonds:</h3>
<div id="pred2" class="shiny-text-output"></div>
</div>
</div>
</div><!--/html_preserve-->



