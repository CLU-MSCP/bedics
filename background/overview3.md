---
layout: page
title: DSUR2
permalink: /background
---

## Summary: The chapter covers a lot of diverse material.  Here's how you can make sense of it all.

- [R History and Setup](setup)

- [Importing Data into R](#import)

- [Data Wrangling](#wrangle)


**General tip**: Ignore anything and everything to do with R Commander.  We will *never* use that software.

## Background: 

The majority of time when we use R we are working with data that have been entered or created in other software packages such as Excel (.xls, .xlsx), tabular spreadsheets (.csv, .dat), SPPS (.sav), STATA (.dta) and others.  In the old days, and still today, we would enter data by hand into Excel or SPSS.  Nowadays, it's more common to use Qualtrics (at CLU) or Survey Monkey to electronically collect data.  The data from these services is then easily exported into a tabular file like Excel, .csv (Dr. Bedics' favorite), or SPSS.

Your most likely familiar with Excel and SPSS from your prior training.  In this sense, you've been to that should be able to _see_ and _touch_ data.  Further, there tends to be some comfort with that ability to visually see and touch the data.  Consequently, it can be actually be a bit unsettling to _not_ see the data.  

Although comforting, you might not have considered the dangers with some of that comfort in seeing and touching the data.  If you can see and touch data, that makes you vulnerable in at least a couple of ways.  First, it's much easier to begin altering the data by error or even with the best intentions.  Regardless of intention, you might start altering the original data in ways that are not documented, cannot be reversed, and become invisible to others. Worse yet, you do what Dr. Bedics has done which is created files such as 'data.sav', 'data2.sav', 'final_clean_data.sav', 'really_final_data.sav'.  Nobody could tell you the difference between those files nor could, honestly, Dr. Bedics after he's put the data away for several months. Such a process is not reproducible (nobody else can do it) nor is transparent (it's all happening in one person's mind).

Traditionally, statistics courses in psychology are focused +90% on data modeling in order to make predictions and inferences.  In reality, statisticians and data scientists spend the bulk of their time managing their data commonly referred to as **data wrangling** (more commonly used) or **data munging**.  All the things you can _do_ to data, we write code to do rather than CTRL+C and CTRL-V.  Unfortunately, this can take a lot of time and we can spend 80% of our time wrangling the data, once we get it in, and then it's relatively straightforward from there to run and interpret your model with the help of a good book.  


## Importing Data with R (Sections 3.5 & 3.7) {#import}




## Wrangling Data {#wrangle}
