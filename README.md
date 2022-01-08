# SPA420

repository for winter data science project 
new changes
Should we graph two data set first before we run the regression analysis
##Final Project Template
---
  title: "Relations between Vaccination and American Economy"
author: 
  - Your Na Li^[American University]
  - Your Reed Weiler^[American University]
  - Your YunJen Tsai^[American University]
date: "2022-01-09"
abstract: "This is our informative abstract of fewer than 200 words. It describes what we investigate, how we investigate it, and what we find."
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

In this section, we introduce the reader to the phenomenon we investigate. We describe the way in which our analysis contributes to an important intellectual debate, or how it answers a pressing political or social question. We introduce our hypotheses, data, and results. We signpost for the reader what's coming in the rest of the paper.


# [Our Substance and Context Section Title Here]

Here we go deeper into the intellectual debate, the political and social context of our investigation. To give the reader a clear sense of why we are writing this paper, we describe the relevant scholarly, technical, or popular literature.  We cite at least two published, peer-reviewed scholarly works. For example, we could cite @mooree20 or @moorav12, which we discussed in class.^[To cite a paper within parentheses, use, e.g., [@moore12].] We only cite others' work in our paper when it enhances the reader's understanding of what we, the authors of this paper, are doing.  We connect everything we cite to _our_ investigation; this is our original research, not a book report or an annotated bibliography.

In order to integrate citations into the References section below, we add entries into our file `main.bib`. This is a plain-text file that we edit in RStudio. We store `main.bib` in the same folder as our paper's `.Rmd` and `.pdf` files. Its entries are formatted so that they can be knit to `.pdf`; see [https://j.mp/2UzTXEZ](https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex#The_bibliography_file) for example entries for articles, books, and miscellaneous. We can get these entries automatically from Google Scholar by turning on BibTeX in the Google Scholar Settings - Bibliography Manager.

# Data and Methods
\label{section:data}

This section describes the data we analyze. We describe the source of the data, and its primary features. We describe the methods we use to answer our question and to test our hypotheses.

If our data were `cars`, loaded in the chunk above, we could note that our data have `r nrow(cars)` observations.

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

We remind the reader what this paper was about, why it was important, and what we found. We reflect on limitations of the data or methods. If we have specific advice for someone picking up where we leave off, we provide that guidance. We avoid making trite statements like "more research should be done".

# References 

#Linear regression result
> x <- df_out$`2021 Q3p Ratio`
> y <- df_out$`Vaccination Ratio`
> fit1 <- lm(y ~ x)
> summary(fit1)
Call:
lm(formula = y ~ x)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.37372 -0.12425 -0.03765  0.12482  0.43398 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  1.58548    0.07471   21.22  < 2e-16 ***
x            4.05829    1.02741    3.95  0.00025 ***
---
Signif. codes:  0 ．***・ 0.001 ．**・ 0.01 ．*・ 0.05 ．.・ 0.1 ． ・ 1

Residual standard error: 0.1866 on 49 degrees of freedom
Multiple R-squared:  0.2415,	Adjusted R-squared:  0.226 
F-statistic:  15.6 on 1 and 49 DF,  p-value: 0.0002502
