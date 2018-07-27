---
layout: page
title: Correlations in R
permalink: /correlation
---



## Correlations in R (Sections ## & ##) 

Formatting and working with Correlations from the [R BLOG](https://www.r-bloggers.com/formatted-correlation-with-effect-size/) 

Example is as follows: 

df <- iris  # Load the iris dataset

1. Compute and Store the Results

cor_results <- cor.test(df$Sepal.Length, df$Petal.Length)  # Compute a correlation and store its result

2. Install the formatting package from GitHub.
devtools::install_github("neuropsychology/psycho.R")

3. Load the package
library(psycho)  

4. Examine the result. Nice that is provides a 95% CI. 
psycho::analyze(cor_results)

5. Produce as a table

results <- analyze(cor_results)
summary(results)
knitr::kable(summary((results)))


