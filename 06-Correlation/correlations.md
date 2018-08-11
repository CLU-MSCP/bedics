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

*****

### 1. Correlations in R (Sections 6.1-6.4) {#coroverview}

The textbook example examines the association between exam score (Exam), test anxiety (Anxiety) and hours revising (Revise) using the `ExamAnxiety.dat` data.  We also use the Big Liar data (`liar.dat`) to practice non-parametric correlations. 

As always, ignore anything related to R Commander in the textbook. 

a. Import the data
```r
library(tidyverse)
examdata <- as.tibble(read.delim("ExamAnxiety.dat"))
names(examdata) <- casefold(names(examdata))
```

**Correlations in R**

Table 6.2 in the textbook is helpful.

| Function 	|  Pearson 	|  Spearman  	|  Kendall | p-value | CI | Multiple Correlations |
|---	|:-:	|:-:	|:-:	| :-: | :-: | :-: |	
|  cor() 	|  &#x2705; 	|  &#x2705; 	| &#x2705;  	| &#x274C;  | &#x274C;  | &#x2705;  |
| cor.test()	|  &#x2705; 	| &#x2705;  	|  &#x2705; 	| &#x2705;  | &#x2705;  | &#x274C;   |
| rcorr()  	| &#x2705;  	|   &#x2705;	| &#x274C;  	| &#x2705; | &#x274C; | &#x2705; |

<a href="#">Go to top</a>

*****

### 2. Practice with cor() {#cor}
Here is the function for `cor(x,y, use = "everything", method = "correlation type")` 
The default is a Pearson correlation.  Use `cor()` to fill in the table below.  


a. Anxiety and Number of Revisions
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

R^2 is a type of effect size. Here you can times the result by 100 to get the % of variance accounted for in one variable from another. 
```r
(cor(examdata2)^2)*100
```

The coefficient of determinations ranges from 15-50%.
```
##            revise      exam   anxiety
## revise  100.00000  15.73873  50.30345
## exam     15.73873 100.00000  19.44752
## anxiety  50.30345  19.44752 100.00000
```


|  	|  Anxiety & Revise 	|  Anxiety and Exam Score  	|  Revise and Exam Score |
|---	|:-:	|:-:	|:-:	|
|  Pearson 	|  &#x2753; 	|  &#x2753; 	| &#x2753;  	| 
|  r^2 %	|  &#x2753; 	| &#x2753;  	| &#x2753;   	| 


<a href="#">Go to top</a>

*****


### 2. Practice with cor.test() {#cor_test}
Let's test the significance using `cor.test(x,y, alternative = "string", method = "correlation type", conf.level = 0.95)`.  Report the exact p values and the confidence intervals (95%) for each of the pairs. Complete the table. You can copy some values from above.


a. Anxiety and Number of Revisions
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
|  correlation 	|  &#x2753; 	| &#x2753;  	| &#x2753;  	|
|  r^2 %	|   &#x2753;	|   &#x2753;	| &#x2753;  	| 
| t (df) |   &#x2753;	|   &#x2753;	| &#x2753;  	| 
| p value  |   &#x2753;	|   &#x2753;	| &#x2753; 	| 
| CI   |   &#x2753; to &#x2753;	|  &#x2753; to &#x2753;	| &#x2753; to &#x2753;  	|  
	

*****

### 3. Practice with rcorr() {#rcorr}
The data needs to be in a matrix format and requires the `Hmisc` package which you might need to install. Generally, this function is not worth the hassle.

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

******

<a href="#">Go to top</a>