---
title: Chapter 1
layout: page
permalink: /dsurch1
---



## Why is my evil lecturer forcing me to learn statistics?
#### **Everything you need to know *and more* from DSUR**


1. [Thoery and Hypotheses](#dsur1_1)
2. [Measurement Scales](#dsur1_2)
3. [Null-Hypothesis Statistical Testing](#dsur1_3)

*****


### 1. Theory, hypothesis, and operational definitions. {#dsur1_1}

> *"Theories are nets cast to catch what we call the 'world': to rationalize, to explain, and to master it. We endeavor to make the mesh ever finer and finer."* - Karl Popper

Theory is the story or narrative we apply to better understand the world. Theories are a blend of intuition and empirical data.  In popular culture, it is common to hear someone say "Oh, that's just theory" and wave a dismissing hand. In dosing so, they are suggesting that theory is simply philosophy with no empirical data and thus of little value.  Instead, theory is best understood as a blend of intuition and data.  Data and philosophy have a reciprocal relationship.  Data inform our thoughts and our thoughts inform how we search and interpret our data.  Data can come from all sources including personal experience, case studies, qualitative narrative, field experiments, surveys, or experimentation.  

*****

**Get to know a Theory**

Researchers often feel pressure to come up with a novel and exciting new idea.  There can be a sense of pressure to be unique and to say something new.  Contrary to this idea, much of science involves the testing of theory which, for the most part, has already been laid out for the researcher.  Simply knowing and caring about theory will provide any researcher with enough questions to study for a lifetime.  For example, there are likely many branches of the theory that are either unexplored or underexplored.  If you know a theory then the hypotheses and your future work will reveal themselves.


A great book on the topic of theory was written by Thomas Kuhn called "The Structure of Scientific Revolutions."
<img src="https://raw.githubusercontent.com/CLU-MSCP/bedics/master/public/kuhn.jpg" alt="kuhn" align="right" style="width: 20%; height: 20%; margin:8px">

In this book he reviews the topic of "normal science" as problem solving and how impactful a community can be on our data analytic decisions.  Another book of interest was written by the Nobel Prize winning psychologist Daniel Kahneman that chronicles his work with Amos Tversky.  In this book Kahneman discusses the importance of our natural thinking styles as they influence how we interpret and collect data. 

<img src="https://raw.githubusercontent.com/CLU-MSCP/bedics/master/public/dk.jpg" alt="dk" align="right" style="width: 20%; height: 20%; margin:8px">



*****

**Theory as Motivation**

Working with a specific theory can be exciting and motivational.  It's fun to believe in something, identify with it, and attempt to challenge it by conducting research and contributing to a larger body of knowledge.  It also places an emphasis on knowing the *truth* rather than simply looking for, and likely finding, associations that require post-hoc explanations.  The *random* search for findings based on underdeveloped thought has been referred to as [dustbowl empiricism](https://dictionary.apa.org/dustbowl-empiricism).

As a undergraduate and graduate student, I (Jamie) was motivated not only by my advisor but the pursuit of understanding a theory.

<img src="https://raw.githubusercontent.com/CLU-MSCP/bedics/master/public/HSS.png" alt="HSS" align="right" style="width: 20%; height: 20%; margin:8px">

I spent most of my years walking around campus with the work of Harry Stack Sullivan in my back pocket.  I appreciated is focus on close relationships consistent with object relations and his human approach to schizoprhenia.  However, it wasn't until I read the work of Lorna Smith Benjamin that allowed me to see clear ways of testing concepts related to his theory and specifically those related to personality disorders.

<img src="https://raw.githubusercontent.com/CLU-MSCP/bedics/master/public/LSB.png" alt="HSS" align="left" style="width: 20%; height: 20%; margin:8px">

I never felt at a loss for questions to answer because I knew the theory well enough to know that many of the branches were unexplored or greatly in need of replication.  There was no pressure to come up with a new idea or be unique.  The focus was on the truth of the theory more than anything else.  In addition, such a commitment also connected me with a professional community filled with people to share my ideas and present my work. 


<br>
<br>
<br>

*****

**The components of a theory**

The phenomena we refer to are called *hypothetical constructs*.  The constructs can have an infinite number of specific definitions called *operational definitions*.  For example, depression is a construct and can be defined using the DSM, self-report measure, etc. 

*Reliability* speaks to the stability or internal consistency for each operational definition.  *Validity* speaks to how well operational definitions relate to  each other when they are expected, or not expected, to be associated.  

<strong><center>Advanced Resources</center></strong>

    Meehl, P. E. (1967). Theory-testing in psychology and physics: A methodological paradox. Philosophy of Science, 34, 103-115.
    
    Wampold, B. E., Davis, B., & Gould, R. H. (1990). Hypothesis validity of clinical research. Journal of Consulting and Clinical Psychology, 58, 360-367

*****

### 2. Measurement Scales {#dsur1_2}

The distinction between nominal, ordinal, interval, ratio scales in scales of measurement is something you learned quite early in your education.  However, the importance of these scales is rarely made clear.  The reason why these scales are important is that they will impact how you summarize, visualize, and model (run statistics) your data.  

At the same time, the **scale of measurement is inherently limiting**.  It will force you to think about a problem or concept in a particular way. A good exercise is to think about the variables in your study and consider how you might assess the same constructs on a different scale.

**2a. Arbitrary Metrics**

You should consider and review the concept of *arbitrary metrics* as discussed by Alan Kazdin in the 2006 article cited below.  He raises the point that many of our measurements have no real, pracical, or "non-arbitrary" meaning.  A non-arbitrary **ecological validity**.    

As an example, people don't often appreciate a 5-point change on, for example, a self-report measure of depression.  Instead, they often appreciate fewer days of unemployment, having a job or not having a job, number of social events attended, number of days out of bed, etc.  

In summary, it is best to consider both arbitrary and non-arbitrary metrics.  The point being that hypothetical constructs are inexhaustible entities that can be defined in a variety, in fact infinite, number of ways.  If you care about the variables that you are measuring then in makes sense to assess them as exhaustively as possible and include both arbitrary and non-arbitrary metrics.


<strong><center>Advanced Resources</center></strong>

    Kazdin, A. E. (2006). Arbitrary Metrics: Implications for Identifying Evidence-Based Treatments. American Psychologist,61(1), 42-49. doi:10.1037/0003-066X.61.1.42
    
    Baumeister, R. F., Vohs, K. D. & Funder, D. C. (2007).  Psychology as the science of self-reports and finger movements: Whatever happened to actual behavior? Perspectives on Psychological Science, 2, 396-403. 

*****

### 3. Null Hypothesis Significance Testing (NHST) {#dsur1_3}

At the very end of this chapter, in section 1.7.4 & 1.7.5, the author begins a discussion of sampling distributions similar to our in-class discussion using the binomial distribution.  The basic idea being that there are expected frequencies of outcomes and these outcomes can have assigned probabilities.  Many of our variables fall along a normal distribution, many do not.  If we know the distribution of outcomes, then we can guess the probability of those outcomes occuring given all assumptions are met. Every time we have a new outcome (e.g., test statistic), we can see how consistent or inconsistent our data is with the established frequency table and their corresponding probabilities.

Although perhaps odd to think about, the tables in the back of your statistics textbooks are nothing more than expected outcomes of test statistics (t-test, chi-square, F-test, etc.) for different sample sizes and their corresponding probability of occurring.   You compare *your* results (i.e., test statistic) with the probability of it occurring in the table.  Lastly, the tables are the frequency/probabilities of outcomes when you'd expect no relationship/no effect.  It's called the **null hypothesis distribution**.

We spend *a lot* of time talking about NHST.  We discuss its strengths, limits, and possible solutions to those limits.  There is nothing inherently bad about NHST, the problem is that it's widely misunderstood and misapplied.  As we will see, NHST, as a procedure for establishing the meaningfulness of our results, as become highly ritualized.  In fact, this ritual is mostly used in ways that are inconsistent with how the original founders of NHST would have endorsed.  

**What is NHST and the P-value?**

Correct definition of a p-value is as follows:

> *The probability that the observed data is consistent (or more extreme) than the null hypothesis distribution assuming additional study assumptions are met*

Here is what a p value does not tell us:

  * The probability that the null is true
  * The probability that your hypothesis is true (wouldn't that be nice to say? Go Bayesian stats!)
  * A p value less than .05 does not tell us that the null should be rejected. It just means your results are odd. We do not know why it's odd. It could not fit the null distribution or some other study assumption could've been violated
  * A p value greater than .05 does not tell us that the null should be accepted (same as above but other direction)
  * A p value less than .05 does not mean that what we found is important.
  * A p value greater than .05 does not mean that there was no effect found. 
  * The p value is not the chance of our data occurring given the null.  It's what we observed and *more extreme*, again, given other study assumptions are met.
  * The p value is not the chance of a Type I error (false positive).  The 5% is how often you would be wrong over many studies, given all assumptions are met, including the null. 


<strong><center>Advanced Resources</center></strong>

    Gigerenzer, G. (2004). Mindless statistics. The Journal of Socio-Economics,33(5), 587-606. doi:10.1016/j.socec.2004.09.033
    
    Greenland, S., Senn, S. J., Rothman, K. J., Carlin, J. B., Poole, C., Goodman, S. N., & Altman, D. G. (2016). Statistical tests, P values, confidence intervals, and power: a guide to misinterpretations. European Journal of Epidemiology,31(4), 337-350. doi:10.1007/s10654-016-0149-3
    
    
