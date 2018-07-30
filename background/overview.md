---
title: Chapter 2
layout: page
permalink: /overview
---

## Everything you want to know about statistics (well, sort of)
#### **Everything you need to know *and more* from DSUR**


Summary: The chapter covers a lot of diverse material.  Here's how you can make sense of it all.

- [R History and Setup](https://clu-mscp.github.io/bedics/setup) 

- [Importing Data into R](#import)

- [Data Wrangling](#wrangle)


**General tip**: Ignore anything and everything to do with R Commander.  We will *never* use that software.

## Importing Data with R {#import}

The majority of time when we use R we are working with data that have been entered or created in other software packages such as Excel (.xls, .xlsx), tabular spreadsheets (.csv, .dat), SPSS (.sav), STATA (.dta) and others.  In the old days, and still today, we would enter data by hand into Excel or SPSS.  Nowadays, it's more common to use Qualtrics (at CLU) or Survey Monkey to electronically collect data.  The data from these services are then easily exported into a tabular file like Excel, .csv (Dr. Bedics' favorite), or SPSS.

You're most likely familiar with Excel and SPSS from your prior training.  In this sense, you've been to taught that you should be able to visually _see_ and physically _touch_ data. Further, there tends to be some comfort when you have such a direct connection to the data itself. It can be soothing to see the numbers all lined up and, given the size of dataframe, you might also get a could sense of the data itself.  In light of this comfort and prior training, it can actually be a unsettling to _not_ see the data so easily as in a framework like R.

Although comforting, you might not have considered the dangers of having such a close relationship with the data.  

  1. It's much easier to slip and make a mistake to original data.  Numbers can change accidentally.  
    
  2. Researchers often make well-intentioned and thoughtful changes on the spreadsheet itself but not document how the changes were made.

There are likley two outcomes to the above errors. A new researcher will be entirely naive to your research process and fail to replicate and extend the area of research.  Money and time is wasted.  Alternatively, you do what Dr. Bedics has done and create files such as 'data.sav', 'data2.sav', 'final_clean_data.sav', 'really_final_data.sav'.  Nobody could tell the difference between these files.  In fact, Dr. Bedics wouldn't be able to do after putting the data aside for a month or two. Such a process is not reproducible (nobody else can do it) nor is transparent (it's all happening in one person's mind).

## Wrangling Data with R {#wrangle}

Traditionally, statistics courses in psychology are focused 90%+ on data modeling in order to make predictions and inferences.  Students learn the family of linear models and learn about statistical significance testing (i.e., p<.05 is good).  

In reality, statisticians and data scientists spend the bulk of their time (80%+ is the popular saying) managing their data.  These skills are commonly referred to as *data wrangling* or *data munging* (3.5 & 3.9).  These include summarizing, transforming, arranging, and any other data manipulation.

In order to be fully reproducible, we want to write R code for all our data management.  By doing this we, again, never touch our raw data.  We bring the data in (import), untouched, then manipulate the data. 
