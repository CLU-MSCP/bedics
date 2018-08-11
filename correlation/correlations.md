---
layout: page
title: Chapter 6 Correlations
permalink: /correlation
---


*****

## Table of Contents

1. [Correlations in R](#coroverview)
2. [Practice with cor()](#cor)
3. [Practice with cor.test()](#cor_test)
4. [Practice with rcorr()](#rcorr)
5. [The Effect of Missing Data in Correlations](#missing)
6. [Spearman's Rho Section 6.5.5](#spearman)
7. [Kendall's Tau (Section 6.5.6)](#kendall)
8. [Bootstrapping (Section 6.5.7)](#bootstrap)
9. [Partial Correlation Coefficient (Section 6.6)](#partial)
10. [Extra Resources](#extra)

*****

### 1. Correlations in R (Sections 6.1-6.4) {#coroverview}

The textbook example examines the association between exam score (Exam), test anxiety (Anxiety) and hours revising (Revise) using the `ExamAnxiety.dat` data.  We also use the Big Liar data (`liar.dat`) to practice non-parametric correlations. 

As always, ignore anything related to R Commander. 

1. Import the data
```r
library(tidyverse)
examdata <- as.tibble(read.delim("ExamAnxiety.dat"))
names(examdata) <- casefold(names(examdata))
```

**Correlations in R**

Table 6.2 is helpful

| Function 	|  Pearson 	|  Spearman  	|  Kendall | p-value | CI | Multiple Correlations |
|---	|:-:	|:-:	|:-:	| :-: | :-: | :-: |	
|  cor() 	|  &#x2705 	|   	|   	|   |  |   |
| cor.test()	|  &#x2705 	|   	|   	|   |  |   |
| rcorr()  	| &#x2705;  	|   	|   	| 

<a href="#">Go to top</a>

*****

### Practice with cor() {#cor}
Here is the function for `cor`: cor(x,y, use = "everything", method = "correlation type") 
The default is a Pearson correlation.  Use `cor()` to fill in the table below.  Replace the `#` values with your statistics in the tables that follow.


a. Anxiety and # of Revisions
```r
cor(examdata$anxiety, examdata$revise)
```

```
[1] -0.7092493
```

b. Anxiety and Exam Score
```r
cor(examdata$anxiety, examdata$exam)
```

```
[1] -0.4409934
```

c. Exam Score and # of Revisions
```r
cor(examdata$revise, examdata$exam)
```

```
[1] 0.3967207
```

Calculate the R^2 all at once.  In order to do so, the dataframe can only include the variables that you want to correlate.  In this case, we want to remove gender.

```r
examdata2 <- examdata %>% select(revise, exam, anxiety)
cor(examdata2)
```

```
##             revise       exam    anxiety
## revise   1.0000000  0.3967207 -0.7092493
## exam     0.3967207  1.0000000 -0.4409934
## anxiety -0.7092493 -0.4409934  1.0000000
```

```r
(cor(examdata2)^2)*100
```

```
##            revise      exam   anxiety
## revise  100.00000  15.73873  50.30345
## exam     15.73873 100.00000  19.44752
## anxiety  50.30345  19.44752 100.00000
```


|  	|  Anxiety & Revise 	|  Anxiety and Exam Score  	|  Revise and Exam Score |
|---	|:-:	|:-:	|:-:	|
|  Pearson 	|  -.71 	| -.44  	| .40  	| 
|  r^2 as %	|   50%	|   19%	| 16%  	| 
|   	|   	|   	|   	| 

<a href="#">Go to top</a>

*****


### 2. Practice with cor.test() {#cor_test}
Let's test the significance using `cor.test`: cor.test(x,y, alternative = "string", method = "correlation type", conf.level = 0.95).  Report the exact p values and the confidence intervals (95%) for each of the pairs.  You can copy the first two rows from above into the first two rows below since they'll be the same. 


a. Anxiety and # of Revisions
```r
cor.test(examdata$anxiety, examdata$revise)
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  examdata$anxiety and examdata$revise
## t = -10.111, df = 101, p-value < 2.2e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.7938168 -0.5977733
## sample estimates:
##        cor 
## -0.7092493
```


b. Anxiety and Exam Score
```r
cor.test(examdata$anxiety, examdata$exam)
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  examdata$anxiety and examdata$exam
## t = -4.938, df = 101, p-value = 3.128e-06
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.5846244 -0.2705591
## sample estimates:
##        cor 
## -0.4409934
```

c. Exam Score and # of Revisions
```r
cor.test(examdata$revise, examdata$exam)
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  examdata$revise and examdata$exam
## t = 4.3434, df = 101, p-value = 3.343e-05
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.2200938 0.5481602
## sample estimates:
##       cor 
## 0.3967207
```

|  	|  Anxiety & Revise 	|  Anxiety and Test Score  	|  Revise and Test Score |
|---	|:-:	|:-:	|:-:	|
|  correlation 	|  -.71 	| -.44  	| .40  	|
|  r^2 as %	|   50%	|   19%	| 16%  	| 
| t (df) |   -10.11	|   -4.94	| 4.34  	| 
| p value (two-sided) |   2.2e-16	|   3.12e-06	| 3.43e-05  	| 
| CI  (two-sided) |   -.79 to -.60	|  -.58 to -.27	| .22 to .55  	|  
|   	|   	|   	|   	|   	

*****

### 3. Practice with rcorr() {#rcorr}
The data needs to be in a matrix format and requires the `Hmisc` package which you might need to install.

Load `Hmisc` assuming you already installed it. 
```r
library(Hmisc)
```

```r
exammatrix <- as.matrix(examdata2)
rcorr(exammatrix)
```

```
##         revise  exam anxiety
## revise    1.00  0.40   -0.71
## exam      0.40  1.00   -0.44
## anxiety  -0.71 -0.44    1.00
## 
## n= 103 
## 
## 
## P
##         revise exam anxiety
## revise          0    0     
## exam     0           0     
## anxiety  0      0
```

<a href="#">Go to top</a>

******

### 4. Missing Data {#missing}


Create the data with the planned missing data. 
```r
adverts <- c(5, 4, 4, 6, 8)
packetsNA <- c(8, 9, 10, NA, 15)
age <- c(5, 12, 16, 9, 14)
```

Create the dataframe and convert to tibble format.
```r
advertNA <- as.tibble(data.frame(adverts, packetsNA, age))
advertNA
```

```
## # A tibble: 5 x 3
##   adverts packetsNA   age
##     <dbl>     <dbl> <dbl>
## 1      5.        8.    5.
## 2      4.        9.   12.
## 3      4.       10.   16.
## 4      6.       NA     9.
## 5      8.       15.   14.
```

a. The everything method.

```r
cor(advertNA, use = "everything",  method = "pearson")
```

```
##              adverts packetsNA        age
## adverts   1.00000000        NA 0.02072962
## packetsNA         NA         1         NA
## age       0.02072962        NA 1.00000000
```
What happened?

b. The "all.obs" method. What happened?

```r
#cor(advertNA, use = "all.obs",  method = "pearson")
```
Answer: 

c. The "complete.obs" method.  What happened?

```r
cor(advertNA, use = "complete.obs",  method = "pearson") 
```

```
##              adverts packetsNA        age
## adverts   1.00000000 0.8778665 0.08276409
## packetsNA 0.87786648 1.0000000 0.54869466
## age       0.08276409 0.5486947 1.00000000
```
Answer: 

d. The "pairwise.complete.obs".  What happened?

```r
cor(advertNA, use = "pairwise.complete.obs",  method = "pearson")
```

```
##              adverts packetsNA        age
## adverts   1.00000000 0.8778665 0.02072962
## packetsNA 0.87786648 1.0000000 0.54869466
## age       0.02072962 0.5486947 1.00000000
```
Answer: 


|  	|  Packets and Advertisements 	|  Packets and Age  	|  Age and Advertisement |
|---	|:-:	|:-:	|:-:	|
|  everthing 	|  # 	| #  	| #  	| #  	|
|  all.obs 	|   #	|   #	| #  	|  # 	|
| complete.obs |   #	|   #	| #  	|  # 	|
| pairwise.complete.obs  |   #	|   #	| #  	|  # 	|
|   	|   	|   	|   	|   	|

<a href="#">Go to top</a>

*****

### 5. Spearman's Rho {#spearman}

Spearman Rho and Kendall Tau are nonparametric procedures when data violates assumptions of normality or in the case of small sample data.  The formulas are calculated based on rankings in the data.

We use the text example to look at the "Big Liar" data.  The data are taken from a contest testing who can lie the best.  The data examines the association between your "Position" or the place you scored (i.e., 1st, 2nd, 3rd, etc) and your score on creativity.  Is there an association between your level of creativity and place in the contest?  "Position" is an ordinal variable.  

a. Import the data set called `liar.dat`

```r
liardata = read.delim("liar.dat",  header = TRUE)
names(liardata) <- casefold(names(liardata))
#liarData = read.delim(file.choose(),  header = TRUE)
```

Run the Spearman Correlation Coefficient for position with creativity in the `liardata`

```r
cor(liardata$position, liardata$creativity, method = "spearman")
```

```
## [1] -0.3732184
```

```r
cor.test(liardata$position, liardata$creativity, alternative = "less", method = "spearman")
```

```
## 
## 	Spearman's rank correlation rho
## 
## data:  liardata$position and liardata$creativity
## S = 71948, p-value = 0.0008602
## alternative hypothesis: true rho is less than 0
## sample estimates:
##        rho 
## -0.3732184
```
<a href="#">Go to top</a>

*****

### 6. Kendall's tau {#kendall}

Run the Kendall's tau for the positiion and creativity.

```r
cor(liardata$position, liardata$creativity, method = "kendall")
```

```
## [1] -0.3002413
```

```r
cor.test(liardata$position, liardata$creativity, alternative = "less", method = "pearson")
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  liardata$position and liardata$creativity
## t = -2.6115, df = 66, p-value = 0.005574
## alternative hypothesis: true correlation is less than 0
## 95 percent confidence interval:
##  -1.0000000 -0.1116741
## sample estimates:
##        cor 
## -0.3060314
```

|  	|  Creativity and Position 	| 
|---	|:-:	|
|  Pearson 	|  # 	| 
|  Spearman 	|   #	|  
| Kendall |   #	| 
|   	|   	|   

<a href="#">Go to top</a>

*****

### 7. Bootstrap {#bootstrap}


```r
library(boot)
```

```r
bootTau <- function(liardata,i)cor(liardata$position[i], liardata$creativity[i], use = "complete.obs", method = "kendall")
```


```r
boot_kendall <- boot(liardata, bootTau, 2000)
boot_kendall
```

```
## 
## ORDINARY NONPARAMETRIC BOOTSTRAP
## 
## 
## Call:
## boot(data = liardata, statistic = bootTau, R = 2000)
## 
## 
## Bootstrap Statistics :
##       original      bias    std. error
## t1* -0.3002413 0.001077982   0.1002341
```

```r
boot.ci(boot_kendall)
```

```
## BOOTSTRAP CONFIDENCE INTERVAL CALCULATIONS
## Based on 2000 bootstrap replicates
## 
## CALL : 
## boot.ci(boot.out = boot_kendall)
## 
## Intervals : 
## Level      Normal              Basic         
## 95%   (-0.4978, -0.1049 )   (-0.5076, -0.1217 )  
## 
## Level     Percentile            BCa          
## 95%   (-0.4787, -0.0929 )   (-0.4729, -0.0816 )  
## Calculations and Intervals on Original Scale
```

```r
boot.ci(boot_kendall, 0.99)
```

```
## BOOTSTRAP CONFIDENCE INTERVAL CALCULATIONS
## Based on 2000 bootstrap replicates
## 
## CALL : 
## boot.ci(boot.out = boot_kendall, conf = 0.99)
## 
## Intervals : 
## Level      Normal              Basic         
## 99%   (-0.5595, -0.0431 )   (-0.5919, -0.0677 )  
## 
## Level     Percentile            BCa          
## 99%   (-0.5328, -0.0086 )   (-0.5255,  0.0009 )  
## Calculations and Intervals on Original Scale
## Some BCa intervals may be unstable
```

<a href="#">Go to top</a>

*****

### 9. Partial Correlation {#partial}

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

### 10. Extra Resources {#extra}

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