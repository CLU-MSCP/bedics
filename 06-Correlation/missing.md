---
layout: page
title: Missing Data in Correlations
permalink: /missing
---


*****

## Table of Contents

1. [Create the data](#create)
2. [The Everything Method ](#everything)
3. [The "all.obs" method](#allobs)
4. [The "complete.obs" method](#completeobs)
5. [The "pairwise.complete.obs" method](#pairwise)


*****

### 1. Create the Data {#create}


Create the data with the planned missing data. 

```r
library(tidyverse)
```

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

<a href="#">Go to top</a>

*****

### 2. The everything method {#everything}

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

<a href="#">Go to top</a>

*****

### 3. The "all.obs" method {#allobs}

```r
cor(advertNA, use = "all.obs",  method = "pearson")
```

```
Error in cor(advertNA, use = "all.obs", method = "pearson") : 
  missing observations in cov/cor
```
What happened?: 

<a href="#">Go to top</a>

*****

### 4. The "complete.obs" method  {#completeobs}

```r
cor(advertNA, use = "complete.obs",  method = "pearson") 
```

```
##              adverts packetsNA        age
## adverts   1.00000000 0.8778665 0.08276409
## packetsNA 0.87786648 1.0000000 0.54869466
## age       0.08276409 0.5486947 1.00000000
```
What happened?: 

<a href="#">Go to top</a>

*****

### 5. The "pairwise.complete.obs"  {#pairwise}

```r
cor(advertNA, use = "pairwise.complete.obs",  method = "pearson")
```

```
##              adverts packetsNA        age
## adverts   1.00000000 0.8778665 0.02072962
## packetsNA 0.87786648 1.0000000 0.54869466
## age       0.02072962 0.5486947 1.00000000
```
What happened?: 

<a href="#">Go to top</a>

*****

**Complete the Table**

|  	|  Packets and Advertisements 	|  Packets and Age  	|  Age and Advertisement |
|---	|:-:	|:-:	|:-:	|
|  everthing 	|   	|   	|   	|
|  all.obs 	|   	|   	|   	|  
| complete.obs |   	|   	|   	| 
| pairwise.complete.obs  |   	|   	|   	|  

*****

<a href="#">Go to top</a>
