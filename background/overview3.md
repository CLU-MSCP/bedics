---
layout: page
title: Chapter 2 DSUR: The R Environment
permalink: /background
---

Summary: The chapter covers a lot of diverse material.  Here's how you can make sense of it all.

- [R History and Setup](setup)

- [Importing Data into R](#import)

- [Data Wrangling](#wrangle)


**General tip**: Ignore anything and everything to do with R Commander.  We will *never* use that software.

## Background: 

The majority of time when we use R we are working with data that have been entered or created in other software packages such as Excel (.xls, .xlsx), tabular spreadsheets (.csv, .dat), SPSS (.sav), STATA (.dta) and others.  In the old days, and still today, we would enter data by hand into Excel or SPSS.  Nowadays, it's more common to use Qualtrics (at CLU) or Survey Monkey to electronically collect data.  The data from these services are then easily exported into a tabular file like Excel, .csv (Dr. Bedics' favorite), or SPSS.

You're most likely familiar with Excel and SPSS from your prior training.  In this sense, you've been to taught that you should be able to visually _see_ and physically _touch_ data.  Further, there tends to be some comfort when you have such a direct connection to the data itself.  Consequently, it can be actually be a bit unsettling to _not_ see the data so easily as in a framework like R.

Although comforting, you might not have considered the dangers when you have such a close relationship with the data. First, it's much easier to slip and make a mistake once the data is entered.  Numbers can change accidentally.  Second, you could make well-intentioned and thoughtful changes on the spreadsheet itself.  Although often innocuous and necessary, these subtle changes are often not documented by researchers.  If another researcher were to attempt to replicate the study they might get stuck or make errors inconsistent with the original study because there was a lack of transparency in the data analysis. The changes the original researcher made, although likely justified, are invisible to others.

There are likley two outcomes to the above errors. A new researcher will be entirely naive to your research process and fail to replicate and extend the area of research.  Money and time is wasted.  Alternatively, you do what Dr. Bedics has done and create files such as 'data.sav', 'data2.sav', 'final_clean_data.sav', 'really_final_data.sav'.  Nobody could tell the difference between those files nor could, honestly, Dr. Bedics after he's put the data away for several months. Such a process is not reproducible (nobody else can do it) nor is transparent (it's all happening in one person's mind).

Traditionally, statistics courses in psychology are focused 90%+ on data modeling in order to make predictions and inferences.  Students learn the family of linear models and learn about statistical significance testing.  In reality, statisticians and data scientists spend the bulk of their time (80%+ is the popular saying) managing their data commonly referred to as **data wrangling** (more commonly used) or **data munging**.  All the things you can _do_ to data, we write code to do rather than CTRL+C and CTRL-V or manual changes.  Unfortunately, this can take a lot of time wrangling the data as it will become completely apparent to you that there are about a billion to infinite ways that people make a spreadsheet. It's fascinating but for full-time data scientists it's crazy making. 

Before you take you first step towards reproducibility, you have to get data into R.  We will then review data wrangling.

## Importing Data with R (Sections 3.5 & 3.7) {#import}




## Wrangling Data {#wrangle}
