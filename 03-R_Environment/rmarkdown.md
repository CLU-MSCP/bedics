---
layout: page
title: Chapter 3 The R Environment
permalink: /rmarkdown
---


# R Mardown

*****

## Table of Contents

1. [Setup](#setup)
2. [Page Break](#break)
3. [Equations](#equations)
4. [Quotations](#quotations)
5. [Table of Contents](#toc)

*****

### 1. Setup {#setup}

a. Control the options for every chunk all at once 

```{r}
{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE, message = FALSE, warning = FALSE)
```
This chunk pops up for _every_ `.Rmd` you open.  It will control the options that appear in from **all** of the chunks in your document. If you want to set rules for all the chunks, then you can modify the controls in this section.  

In this particular setup chunk, it's call the `opts_chunk$set` function from the `knitr` library. In this example, I'll never see warnings or messages but I _will_ see code because `echo = True`.  I will also see results if I do any data analysis.   

- Notice `include=FALSE` will including _nothing_ from the chunk in the output rendering that chunk invisible in your output.  

b. Control the options for a single chunk

The key options for our work include:
1. `message = FALSE`
2. `warning = FALSE`
3. `echo = FALSE`

In this chunk, for example, I will not see any messages, warning, or code:

```{r}
{r, message = FALSE, warning = FALSE, echo=FALSE}
plot(mpg)
```

Further chunk options can be found at the following **[site](https://yihui.name/knitr/options)**.

*****

### 2. Page Break {#break}

You can use the following functions when you want to create a new page for a new section in your document.  These work for PDF and WORD documents.  It's the same as adding a "page break" in word when, for example, you want to start your method section on a new page when writing a research paper.  Othertimes, it's simply more aesthetically pleasing to start on a new page.  The following instructions tell you how to do this in R Studio for PDF and WORD outputs.

a. Create a page break when you render using `.pdf`

You can add a line break, a new separate page on a .pdf if you add the `\break` command.  This does not work for .html or for .docx.  Add it to any part of the document _outside_ of a chunk

```{r}
\break
```

b. Create a page break when you render using `.docx` 
If you want to do so for .docx the instructions are pretty straightforward and can be found at this website:
[https://datascienceplus.com/r-markdown-how-to-insert-page-breaks-in-a-ms-word-document/](https://datascienceplus.com/r-markdown-how-to-insert-page-breaks-in-a-ms-word-document/)

The steps can be broken down as follows:

1. Render a word doc and save is as something like "rmarkdown_template.docx" and save in the **same** folder as your code.

2. Open the new word file and change the style template as noted on the website.  There are several steps.

3. Save the template.

4. In the YAML  (the code at the very top with you name), remove the `default` and add the following under word_document: 
  reference_docx: rmarkdown_template.docx

Notice the number formmating comes out nicely above but we can use bullets too:

- Render a word doc and save is as something like "rmarkdown_template.docx" and save in the **same** folder as your code.

- Open the new word file and change the style template as noted on the website.  There are several steps.

- Save the template.

- In the YAML  (the code at the very top with you name), remove the `default` and add the following under     
    - word_document: 
        
        reference_docx: rmarkdown_template.docx

*****

### 3. Equations {#equations}

You can get fancy with equations:

```r
$$\begin{array}{ccc}
x_{11} & x_{12} & x_{13} \\
x_{21} & x_{22} & x_{23}
\end{array}$$
```

$$\begin{array}{ccc}
x_{11} & x_{12} & x_{13} \\
x_{21} & x_{22} & x_{23}
\end{array}$$

*****

### 4. Quotations {#quotations}

Sometimes in describing your results you might want to quote a famous person for inspiration:

```r
> "Today is only one day in all the days that will ever be. But what will happen in all the other days that ever come can depend on what you do today."
>
> --- Ernest Hemingway, _From Whom the Bell Tolls_
```

> "Today is only one day in all the days that will ever be. But what will happen in all the other days that ever come can depend on what you do today."
>
> --- Ernest Hemingway, _From Whom the Bell Tolls_

*****

### 5. Table of Contents {#toc}

Notice in the YAML, that under `.html` there is a `toc=true` and there is no `default` statement like there is for word and pdf.  Knit html and .doc and compare.

What's the difference?

Change to the `toc=` to `toc_float = true` under html. What happens?  This only works for `html`.

Additional tips on `html` can be found **[here](https://rmarkdown.rstudio.com/html_document_format)** at R Studio.

*****

<a href="#">Go to top</a>
