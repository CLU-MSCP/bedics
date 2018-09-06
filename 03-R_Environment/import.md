---
layout: page
title: Chapter 3 The R Environment
permalink: /import
---


1. [Before you start](#dsur3_1)
2. [Tidyverse Import](#dsur3_2)
3. [GitHub Import](#dsur3_3)
4. [OSF Import](#dsur3_4)


*****

## Before you start {#dsur3_1}

The chapter provides a background and overview of R.  A nice YouTube video can introduce you to both: [Getting Started with R and R Studio](https://www.youtube.com/watch?v=lVKMsaWju8w)

The [setup](https://clu-mscp.github.io/bedics/setup) instructions could be helpful if you have not done so already.

*****

#### The Working Directory
Prior to pulling in data, you'll need to make sure that you're "pointing" R in the right direction to find the file.  To figure where R is pointing send this or, more realistically, type this in the console:

```r
getwd()
```

The file path is where R will look to get your file.   If you are working in a R Project, which you should always be doing, it will go to the main folder for that project.  If you have a subfolder in that R Project then you can direct the import to that folder as noted below in the first, *.csv, example.  You can, although you really shouldn't have to, set your file path using by using the command `setwd(FILE PATH)` or using the dropdown menu in R Studion under `Session`.

******

#### R Studio Cheatsheat

Go the source and check out the [RStudio Data Import Cheatsheet](https://rawgit.com/rstudio/cheatsheets/master/data-import.pdf). 

*****

## Importing Data in R {#dsur3_2}

Below are commonly used functions for importing data that rely on the following libraries all of which are contained with in the `library(tidyverse` but you could load seperately:
```{r}
library(readr) # for *.csv and *.dat in class
library(haven) # for *.sav (spss files) and *.dta (stata files)
library(readxl) # for *.xlsx and *.xls files
```

Here are examples:

*CSV loading the readr library*
```{r}
data.tb <- readr::read_csv("dsur.csv")
```
*CSV in Subfolder*
```{r}
data.tb <- read_csv("03-data/data.csv")
```

*CSV in Base R*
```{r}
data.tb <- read.csv("data.csv", header=T) 
```

*Excel Required library(readxl)*
```{r}
data.tb <- read_excel("data.xlsx")
```
*SPSS data using `haven`*
```{r}
data.tb <- read_sav("data.sav") 
```

*SPSS data using `haven` but loading inline*
```{r}
data.tb <- haven::read_sav("data.sav") 
```
*Data File*
```{r}
data.tb <- readr::read_delim("data.dat", delim="\t")
```

*Data File in Base R*
```{r}
data.tb <- read.delim("data.dat") # non Tidyverse way
```

*Stata data using `haven`*
```{r}
data.tb <- haven::read_dta("data.dta") 
```

_Notice:_
1. All these require that R is going to the correct working directory (i.e., where you data lives).  If you're working in an R Project then you're good to go unless you have a subfolder like in the second example.
2. You can use the `::` to designate the library to be loaded.  In this case you don't have to do `library()`

*****

## 3.  Get data from GitHub {#dsur3_3}

GitHub is a great resource for data analysis projects.  You can certainly download the data and then put it in your R Project folder.   You can also directly import from the web.  The following is an example of how to import the data directly form a website.  

The data here is from the crowdsourcing study on soccer red cards.  Accessible introductions to the data can be found in [Nature](https://www.nature.com/news/crowdsourced-research-many-hands-make-tight-work-1.18508) and in Andrew Gelman's [blog](http://andrewgelman.com/2015/01/27/crowdsourcing-data-analysis-soccer-referees-give-red-cards-dark-skin-toned-players/).

A GitHub user has put the data up using a `.csv` file.  Here's the [URL](https://github.com/cgonza12/Soccer/blob/master/data.csv) to the user's account.  However, this is not the URL you need to import.  Click on "View Raw" and the following URL will appear along with some unsightly data 'https://raw.githubusercontent.com/cgonza12/Soccer/master/data.csv'.  This is your link to get the data. Follow the steps


A) Install and load the required library.
```r
library(RCurl) # load the library.
```

B) Paste the URL into the `""` space.
```r
redcard <-read.csv(text=getURL("https://raw.githubusercontent.com/cgonza12/Soccer/master/data.csv"))  
```

C. Make it a tibble for accessibility
```r
redcard.tb <- tibble::as.tibble(redcard)
redcard.tb

# A tibble: 146,028 x 27
   playerShort player club  leagueCountry birthday height weight position games
   <fct>       <fct>  <fct> <fct>         <fct>     <int>  <int> <fct>    <int>
 1 lucas-wilc… Lucas… Real… Spain         31.08.1…    177     72 Attacki…     1
 2 john-utaka  John … Mont… France        08.01.1…    179     82 Right W…     1
 3 abdon-prats " Abd… RCD … Spain         17.12.1…    181     79 NA           1
 4 pablo-mari  " Pab… RCD … Spain         31.08.1…    191     87 Center …     1
 5 ruben-pena  " Rub… Real… Spain         18.07.1…    172     70 Right M…     1
 6 aaron-hugh… Aaron… Fulh… England       08.11.1…    182     71 Center …     1
 7 aleksandar… Aleks… Manc… England       10.11.1…    187     80 Left Fu…     1
 8 alexander-… Alexa… Norw… England       04.04.1…    180     68 Defensi…     1
 9 anders-lin… Ander… Manc… England       13.04.1…    193     80 Goalkee…     1
10 andreas-be… Andre… 1899… Germany       13.03.1…    180     70 Right F…     1
# ... with 146,018 more rows, and 18 more variables: victories <int>, ties <int>,
#   defeats <int>, goals <int>, yellowCards <int>, yellowReds <int>,
#   redCards <int>, photoID <fct>, rater1 <int>, rater2 <int>, refNum <int>,
#   refCountry <int>, meanIAT <dbl>, nIAT <int>, seIAT <dbl>, meanExp <dbl>,
#   nExp <int>, seExp <dbl>

```

*****

## 4. Get data from Open Science Framework {#dsur3_4}

You'll use OSF throughout your time at CLU.   Similar to GitHub, OSF is a great place to find projects and share material.  Just like GitHub, you could easily download the data and place it in an R Project.  In this example, however, I'll provide code showing how you can import *directly* from OSF. Here we'll get data used to conduct the P-curve analysis for the Power Poses discussed at [Data Colada](http://datacolada.org/37) by the authors and also in [Slate](http://www.slate.com/articles/health_and_science/science/2016/01/amy_cuddy_s_power_pose_research_is_the_latest_example_of_scientific_overreach.html) article by Andrew Gelman.


A) `httr` package is need for the `GET` command. Install and load.
```{r}
library(httr) 
```

B) Here you need: 1) The name of the file and in this case it's an `.xlsx` file. 2) The URL followed by `/?action=download` and saved as `data` 3) Our file is in `data` and we'll call it `pp.xlsx` to preserve the original extension.  The names `data` and `pp` are irrelevant.

```{r}
if (!file.exists('p-curve disclosure table for Power Posing review - 2016 09 26.xlsx')) {
    data <- GET('osf.io/2fq9c//?action=download',
                write_disk('pp.xlsx', overwrite = TRUE))
}
```

C) Using the `readxl` package you can open the saved file.
```{r}
pp.tb <- readxl::read_excel('pp.xlsx')
pp.tb

# A tibble: 33 x 13
   Study `Categorize d.v… `dependent vari… `Quoted Predict…
   <chr> <chr>            <chr>            <chr>           
 1 Alle… 3                number of pretz… We hypothesized…
 2 Arne… 3                Position of cha… Posture, as it …
 3 Bohn… 3                pain control     Experiment 1 te…
 4 Bohn… 3                pain control     Specifically, w…
 5 Brin… 2                self-evalaution  In this experim…
 6 Carn… 3                hormones and ri… We hypothesized…
 7 Carn… 3                hormones and ri… We hypothesized…
 8 Cesa… 3                gambling         If embodied eff…
 9 Cesa… 3                gambling         Study 2 manipul…
10 Cudd… 3                Evaluated perfo… Specifically, t…
# ... with 23 more rows, and 9 more variables: `Study
#   Design` <chr>, `Key Statistical Result` <chr>, `Quoted
#   Results` <chr>, Results <chr>, `Quoted Robustness
#   Results` <chr>, `Robustness Results` <chr>, X__1 <chr>,
#   `Quoted Feelings Of Power` <chr>, `Feelings Of Power
#   Results` <chr>
```




