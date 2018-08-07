---
title: Chapter 2
layout: page
permalink: /dsurch2
---



## Why is my evil lecturer forcing me to learn statistics?
#### **Everything you need to know *and more* from DSUR**


1. [##](#dsur2_1)
2. [##](#dsur2_2)
3. [##](#dsur2_3)

*****


### 3. Null Hypothesis Significance Testing (NHST) {#dsur1_3}

At the very end of this chapter, in section 1.7.4 & 1.7.5, the author begins a discussion of sampling distributions. We spend a lot of time talking about NHST in class and in Research Ethics.  We discuss its strengths, limits, and possible solutions to those limits.  There is nothing inherently bad about NHST, the problem is that it's widely misunderstood and misapplied.  As we will see, NHST, as a procedure for establishing the meaningfulness of our results, as become highly ritualized.  In fact, this ritual is mostly used in ways that are inconsistent with how the original founders of statistical testing would have endorsed.  

**What is NHST and the P-value?**

The correct definition of a p-value is as follows:

> *The probability that the observed data is consistent (or more extreme) than the null hypothesis distribution assuming additional study assumptions are met.*

Here is what a p value does not tell us:

  * The probability that the null is true
  * The probability that your hypothesis is true (wouldn't that be nice to say?)
  * A p value less than .05 does not tell us that the null should be rejected. It just means your results are odd. We do not know why it's odd. It could not fit the null distribution or some other study assumption could've been violated
  * A p value greater than .05 does not tell us that the null should be accepted (same as above but other direction)
  * A p value less than .05 does not mean that what we found is important.
  * A p value greater than .05 does not mean that there was no effect found. 
  * The p value is not the chance of our data occurring given the null.  It's what we observed and *more extreme*, again, given other study assumptions are met.
  * The p value is not the chance of a Type I error (false positive).  The 5% is how often you would be wrong over many studies, given all assumptions are met, including the null. 


<strong><center>Advanced Resources</center></strong>

    Gigerenzer, G. (2004). Mindless statistics. The Journal of Socio-Economics,33(5), 587-606. doi:10.1016/j.socec.2004.09.033
    
    Greenland, S., Senn, S. J., Rothman, K. J., Carlin, J. B., Poole, C., Goodman, S. N., & Altman, D. G. (2016). Statistical tests, P values, confidence intervals, and power: a guide to misinterpretations. European Journal of Epidemiology,31(4), 337-350. doi:10.1007/s10654-016-0149-3
    
    
