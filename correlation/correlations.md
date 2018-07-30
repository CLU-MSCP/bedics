---
layout: page
title: Chapter 6 Correlations
permalink: /correlation
---



1. [Looking at Relationships](#dsur6.3)




# Looking at Relationships {#dsur6.3}



### Extra Resources

Formatting and working with Correlations from the [R BLOG](https://www.r-bloggers.com/formatted-correlation-with-effect-size/) 

Example is as follows: 
```r
df <- iris  # Load the iris dataset
```
1. Compute and Store the Results
```r
cor_results <- cor.test(df$Sepal.Length, df$Petal.Length)  # Compute a correlation and store its result
```
2. Install the formatting package from GitHub.
```r
devtools::install_github("neuropsychology/psycho.R")
```
3. Load the package
```r
library(psycho)  
```
4. Examine the result. Nice that is provides a 95% CI. 
```r
psycho::analyze(cor_results)
```
5. Produce as a table
```r
results <- analyze(cor_results)
summary(results)
knitr::kable(summary((results)))
```

