---
layout: page
title: Extra Correlation
permalink: /extracor
---


*****

## Table of Contents

1. [Partial Correlation Coefficient (Section 6.6)](#partial)
2. [Extra Resources](#extra)

*****

### 1. Partial Correlation {#partial}

Partial Correlation can be used when we want to look at the association between two variables while controlling for scores on another, related, variable.  We can ask: what's the association between a person's exam score and anxiety, regardless the number of hours revising?

The general form of pcor() is:
pc <- pcor(c("var1", "var2", "control1", "control2" etc.), var(dataframe)) 

where, the output is saved as an object called "pc" (you can call in anything you want).  You'll have to install the package "ggm".


```r
library(ggm)
```

Create a tibble that includes the necessary variables.

```r
examdata2 <- examdata %>% select(exam, anxiety, revise)
```

Run the partial correlation.

```r
pc <- pcor(c("exam", "anxiety", "revise"), var(examdata2))
```

Test the significance of the new partial correlation coefficient.

```r
pcor.test(pc, 1, 103)
```

```
## $tval
## [1] -2.545307
## 
## $df
## [1] 100
## 
## $pvalue
## [1] 0.01244581
```

|  	|  Exam and Anxiety Controlling for Revise 	| 
|---	|:-:	|
|  Partial Correlation 	|  # 	| 
|  R^2 	|   #	|  
| p value |   #	| 
|  Correlation w/o Controlling for Revise 	|  # 	|  
|   	|   	|  

<a href="#">Go to top</a>

*****

### 2. Extra Resources {#extra}

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

******

<a href="#">Go to top</a>