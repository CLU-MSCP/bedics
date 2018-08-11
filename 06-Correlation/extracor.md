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

|  	|  Exam and Anxiety Controlling for Revisions 	| 
|---	|:-:	|
|  Partial Correlation 	|  &#x2753; 	| 
|  R^2 	|   &#x2753;	|  
| p value |   &#x2753;	| 
|  Correlation w/o Controlling for Revise 	|  &#x2753; 	|  

<a href="#">Go to top</a>

*****

### 2. Extra Resources {#extra}

Formatting and working with Correlations from the [R BLOG](https://www.r-bloggers.com/formatted-correlation-with-effect-size/) 

a. Import the data 
```r
df <- as.tibble(iris)  # Load the iris dataset
df

# A tibble: 150 x 5
   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
          <dbl>       <dbl>        <dbl>       <dbl> <fct>  
 1          5.1         3.5          1.4         0.2 setosa 
 2          4.9         3            1.4         0.2 setosa 
 3          4.7         3.2          1.3         0.2 setosa 
 4          4.6         3.1          1.5         0.2 setosa 
 5          5           3.6          1.4         0.2 setosa 
 6          5.4         3.9          1.7         0.4 setosa 
 7          4.6         3.4          1.4         0.3 setosa 
 8          5           3.4          1.5         0.2 setosa 
 9          4.4         2.9          1.4         0.2 setosa 
10          4.9         3.1          1.5         0.1 setosa 
# ... with 140 more rows
```

b. Compute and Store the Results
```r
cor_results <- cor.test(df$Sepal.Length, df$Petal.Length)
cor_results


	Pearson's product-moment correlation

data:  df$Sepal.Length and df$Petal.Length
t = 21.646, df = 148, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.8270363 0.9055080
sample estimates:
      cor 
0.8717538 

```

c. Install and load the formatting package from GitHub.
```r
devtools::install_github("neuropsychology/psycho.R") # only once!
```
Load the package
```r
library(psycho)  
```

d. Examine the result. Nice that is provides a 95% CI. 
```r
psycho::analyze(cor_results)
```

e. Produce as a table
```r
results <- analyze(cor_results)
summary(results)

     effect statistic  df            p  CI_lower CI_higher
1 0.8717538  21.64602 148 1.038667e-47 0.8270363  0.905508

```

Use `kable` from `library(knitr)`
```r
knitr::kable(summary((results)))
```

and get this in R:
```r
|    effect| statistic|  df|  p|  CI_lower| CI_higher|
|---------:|---------:|---:|--:|---------:|---------:|
| 0.8717538|  21.64602| 148|  0| 0.8270363|  0.905508|
```

...which looks this when rendered in Markdown:

|    effect| statistic|  df|  p|  CI_lower| CI_higher|
|---------:|---------:|---:|--:|---------:|---------:|
| 0.8717538|  21.64602| 148|  0| 0.8270363|  0.905508|

Nice!

******

<a href="#">Go to top</a>