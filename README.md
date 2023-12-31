# Presentation-
---
title: "Swiss Fertility and Socioeconomic Indicators Data (1888) Exploration"
author: "Amber Wang"
date: "3/7/2018"
output: ioslides_presentation
smaller: true
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
```

## Introduction
This is the reproducible pitch presentation for the final course porject of Coursera Data Science Specialization Course 9: Developing Data Science Tools. This document will go over the basics of developing the Shiny app. For more information, please see the following links:

1. The Swiss Fertility and Socioeconomic Indicators Data (swiss data) can be accessed with **data(swiss)** in R
3. The GitHub repository containing the R codes required to build the Shiny App (**server.R** and **ui.R**)can be accessed [here](https://github.com/wamber-aww/data-products)
2. The Shiny app can be accessed [here](https://wamber.shinyapps.io/swissdata/), which contains
  - Exploring the distribution of each variable in a histogram
  - Exploring the relationship of up to three variables in a scatter plot

## The Swiss Data {.smaller}
- Except for fertility, all variables are expressed in the proportions (%) of the population
- Use **?swiss** to read more about the study
```{r, echo = T}
data(swiss)
summary(swiss)
```

## Codes for Histogram {.smaller}
```{r, echo = T}
inputVar <- 'Fertility'; inputBin <- 10; histVal <- swiss[, inputVar]
hist(histVal, breaks = seq(min(histVal), max(histVal), length.out = inputBin+1),
     xlab = inputVar, main = paste('Distribution of', inputVar),
     col = 'darkgray', border = 'white')
```

## Codes for Scatter Plot {.smaller}
```{r, echo = T, fig.width=6, fig.height=3.9, fig.align = 'center'}
library(ggplot2)
scatX <- 'Fertility'; scatY <- 'Education'; scatC <- 'Examination'
ggplot(data = swiss, aes(x = Fertility, y = Education, color = Examination)) + 
      geom_point() + xlab(scatX) + ylab(scatY) + labs(colour = scatC) +
      ggtitle(paste('Scatter plot of', scatX, 'vs', scatY)) +
      theme(plot.title = element_text(hjust = 0.5))
```
