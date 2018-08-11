---
layout: page
title: Non-Parametric Options
permalink: /nonparcor
---


*****

## Table of Contents

1. [Spearman's Rho Section 6.5.5](#spearman)
2. [Kendall's Tau (Section 6.5.6)](#kendall)
3. [Bootstrapping (Section 6.5.7)](#bootstrap)

*****



### 1. Spearman's Rho {#spearman}

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

### 2. Kendall's tau {#kendall}

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
|  Spearman 	|   #	|  
| Kendall |   #	| 

<a href="#">Go to top</a>

*****

### 3. Bootstrap {#bootstrap}


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

*****

<a href="#">Go to top</a>
