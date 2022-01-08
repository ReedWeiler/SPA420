# SPA420

Repository for winter data science project 

##Relationship between Vaccination and American Economy
---
<<<<<<< Updated upstream
authors: 
  -  Na Li^[American University]
  -  Reed Weiler^[American University]
  -  YunJen Tsai^[American University]
date: "2022-01-09"
abstract: "This is our informative abstract of fewer than 200 words. It describes what we investigate, how we investigate it, and what we find."
=======
Title: "Personal Income and COVID-19 Vaccination Rates"
Author: 
  -Na Li^[American University]
  -Reed Weiler^[American University]
  -YunJen Tsai^[American University]
Date: "2022-01-09"
Abstract:
There is a growing media consensus that income might have something to do with vaccination rates, so we wanted to investigate whether there is any merit to these claims. Research on this topic could potentially aid in understanding how economic inequality poses a barrier to effective strategies for combating the pandemic, and inform future pandemic response strategies. 
>>>>>>> Stashed changes
output: 
  pdf_document:
    number_sections: true
bibliography: main.bib
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

```{r echo=FALSE, message=FALSE}
# This chunk might read our data.
# It might clean the data, create new variables, etc.
# Now our data are ready for our paper.

# Because echo=FALSE, this chunk itself is not shown.
# Because message=FALSE, any R messages from this chunk do not appear in our paper.

data("cars")
```

```{r eval=FALSE, echo=FALSE}
# Because eval=FALSE, this chunk is not run.

df <- read.csv()
```


# Introduction

There is a growing media consensus that income might have something to do with vaccination rates (CNN article), so we wanted to investigate whether there is any merit to these claims. Research on this topic could potentially aid in understanding how economic inequality poses a barrier to effective strategies for combatting the pandemic, and inform future pandemic response strategies. 


# [Our Substance and Context Section Title Here]

(Jenell) Talk about why we choose the two data sets and what methods that we plan to use to see the relations that we are trying to describe. 

(Emphasize personal health benefits to boost COVID-19 vaccination rates: https://www.pnas.org/content/pnas/118/32/e2108225118.full.pdf)


(Correlation Between Health and Wealth: https://militaryfamilieslearningnetwork.org/2019/08/08/correlations-between-health-and-wealth/)


# Data and Methods
\label{section:data}

Data is drawn from two separate sources. One data set contains personal income level (GDP) by state, the other contains total vaccination rates by state. Our combined dataset has 50 observations, representing each of the 50 united states. 

We chose to use a simple linear regression to test the relationship between income per capita and COVID-19 vaccination rates at a state level within the United States. In this analysis, the explanatory variable was income level, and the outcome variable was COVID-19 vaccination rates. We created a scatter plot to model the relationship between income and vaccination rate by state, displayed below.


# [Our Results Section Title Here]

Here, we explain and interpret our results. We try to learn as much as we can about our question as possible, given the data and analysis. We present our results clearly. We interpret them for the reader with precision and circumspection. We avoid making claims that are not substantiated by our data.

Note that this section may be integrated into Section \ref{section:data}, if joining the two improves the overall presentation.

Our results for the `cars` data include estimating the linear model 

$$\text{Distance}_i = \beta_0 + \beta_1 (\text{Speed}_i) + \epsilon_i.$$

```{r echo=FALSE}
# Estimate a linear model:
lm_out <- lm(dist ~ speed, data = cars)
# Extract the coefficient on speed:
cars_speed_coef <- coef(lm_out)["speed"]
```

Below we show the model estimates. The first table uses `xtable()`, the second uses `stargazer()`.

```{r echo=FALSE, message=FALSE, results='asis'}
# We can print regression tables with xtable or stargazer:
regr_table <- xtable::xtable(lm_out,
                             digits = 2,
                             caption = "Our Informative Caption")

print(regr_table, comment = FALSE)
```

```{r echo=FALSE, message=FALSE, results='asis'}
# We can print regression tables with xtable or stargazer:
stargazer::stargazer(lm_out, 
                     title = "Our Informative Title",
                     dep.var.caption = "Outcome",
                     digits = 2,
                     header = FALSE)
```

Using the `cars` data, we find that each unit of speed is associated with `r round(cars_speed_coef, 1)` more units of distance.

# Discussion

One limitation of our data is that the CDC doesn’t specify whether the “total vaccination” data counts each dose of the vaccine as a separate instance of “vaccination”, nor does it specify how it would account for booster shots, etc. So, there is some ambiguity as to how to interpret the results of our analysis, since the outcome variable could potentially be measuring a variety of different scenarios. Future research should strive to distinguish between instances of single-dose vaccination, double-dose vaccination, inclusion of a booster shot, and/or non-vaccination status as separate categories so as to better isolate the statistical impact of income level on each distinct outcome. 

# References 

Cohen, Elizabeth. “Parents’ income might predict covid-19 vaccination choices for their children”. CNN Health. November 11th, 2021. https://www.cnn.com/2021/11/10/health/parents-covid-19-vaccine-choices-income/index.html


“Gross Domestic Product by State, 3rd Quarter 2021”. Bureau of Economic Analysis. https://www.bea.gov/data/gdp/gdp-state

Data Table for COVID-19 Vaccinations in the United States
https://covid.cdc.gov/covid-data-tracker/#vaccinations_vacc-total-admin-count-total

Data for total population (by state)
https://www.census.gov/data/tables/time-series/demo/popest/2020s-national-total.html#par_textimage



