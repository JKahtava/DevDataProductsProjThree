Developing Data Products Week 4 Project
========================================================
author: Jussi Kahtava   
date: 21st November, 2016
autosize: true

Prediction of diamond price
========================================================

This project developed a Shiny app which allows the user
to predict the price of a diamond from the R `diamonds`
data set.

The Shiny app uses linear regression modeling for estimating
diamond value based on the weight (carat) selected by the user.
In addition,  the app has two pulldown menus for diamond cut 
and diamond color. These allow a comparison of how the predicted 
value of the  diamond changes based on these parameters. The app 
allows the user to try out different color-cut combinations for 
each carat selected.

The shiny app can be found at:

https://jkahtava.shinyapps.io/devdataproductsprojthree/



Background on server.R function
========================================================

In the server.R function, linear prediction is calculated on diamond price for two data sets. One is the complete diamonds data set that acts as a reference (model2). The other prediction is done for a subset selected by the user based on diamond color and cut (model1).

```r
library(ggplot2)
caratInput <- 2.0 # a dummy value for a slider input in the actual Shiny application
model1 <- lm(price ~ carat, data = diamonds[diamonds$cut == "Fair", ])
model2 <- lm(price ~ carat, data = diamonds)
pred1 <- predict(model1, newdata = data.frame(carat = caratInput))
pred2 <- predict(model2, newdata = data.frame(carat = caratInput))
```

Output from server.R
========================================================


```r
diamonds <- diamonds[diamonds$cut == "Fair",] # subsetting which is done by server.R
plot(diamonds$carat, diamonds$price, xlab = "Weight in carats", 
                     ylab = "Price", bty = "n", pch = 16,
                     xlim = c(0.1, 4), ylim = c(300, 20000))
abline(model1, col = "red", lwd = 2)
abline(model2, col = "green", lwd = 2)
points(caratInput, pred1, col = "red", pch = 16, cex = 2)
points(caratInput, pred2, col = "blue", pch = 16, cex = 2)
```
Example plot with diamond cut = FAIR (red line)
========================================================

![plot of chunk unnamed-chunk-3](ShinyPres-figure/unnamed-chunk-3-1.png)
