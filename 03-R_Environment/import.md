---
layout: page
title: Chapter 3 The R Environment
permalink: /import
---


1. [Looking at Relationships](#dsur6_3)
#. [Importing Data](#import)




### Looking at Relationships {#dsur6_3}




## Importing Data with R (Sections 3.5 & 3.7) {#import}

[RStudio Data Import Cheatsheet](https://rawgit.com/rstudio/cheatsheets/master/data-import.pdf)


1. Get data from GitHub

The data is here is from the crowdsourcing study on soccer red cards.  Accessible introductions can be found here [Nature](https://www.nature.com/news/crowdsourced-research-many-hands-make-tight-work-1.18508) and in Andrew Gelman's [blog](http://andrewgelman.com/2015/01/27/crowdsourcing-data-analysis-soccer-referees-give-red-cards-dark-skin-toned-players/) can be found here.

A GitHub user has put the data up using a `.csv` file.  Here's the [URL](https://github.com/cgonza12/Soccer/blob/master/data.csv).  However, this is not the URL you need to import.  Click on "View Raw" and the following URL will appear along with some unsightly data 'https://raw.githubusercontent.com/cgonza12/Soccer/master/data.csv'.  This is your link to get the data. Follow the steps


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

2. Get data from Open Science Framework

Here we'll get data used to conduct the P-curve analysis for the Power Poses discussed at [Data Colada](http://datacolada.org/37) by the authors and also in [Slate](http://www.slate.com/articles/health_and_science/science/2016/01/amy_cuddy_s_power_pose_research_is_the_latest_example_of_scientific_overreach.html) article by Andrew Gelman.


A) `httr` package is need for the `GET` command. Install and load.
```r
library(httr) 
```

B) Here you need: 1) The name of the file and in this case it's an `.xlsx` file. 2) The URL followed by `/?action=download` and saved as `data` 3) Our file is in `data` and we'll call it `pp.xlsx` to preserve the original extension.  The names `data` and `pp` are irrelevant.

```
if (!file.exists('p-curve disclosure table for Power Posing review - 2016 09 26.xlsx')) {
    data <- GET('osf.io/2fq9c//?action=download',
                write_disk('pp.xlsx', overwrite = TRUE))
}
```

C) Using the `readxl` package you can open the saved file.
```r
pp.tb <- read_excel('pp.xlsx')
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




