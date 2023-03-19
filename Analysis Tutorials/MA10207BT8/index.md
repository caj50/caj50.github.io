---
title: "Analysis 1B — Tutorial 8"
author: 'Christian Jones: University of Bath'
date: 'March 2023'
site: bookdown::bookdown_site
language: en
documentclass: article
classoption: a4paper
fontsize: 10pt
geometry: margin=2.5cm
output:
  clavertondown::gitbook_clav:
    split_by: section
    keep_md: true
    config:
      download: [["Tutorial8.html", "HTML page"], ["Tutorial8.pdf","Standard print PDF"], ["Tutorial8Clear.pdf","Clear print PDF"], ["Tutorial8Large.pdf","Large print PDF"], ["Tutorial8.docx","Accessible Word document"], ["Tutorial8.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
  clavertondown::epub_clav:
    toc: false
    pandoc_args: --default-image-extension=svg
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
    pandoc_args: --default-image-extension=svg
  clavertondown::html_clav:
    toc: true
    pandoc_args: --default-image-extension=svg
  clavertondown::pdf_clav:
    latex_engine: pdflatex
    keep_tex: true
    fig_caption: true
    toc: true
    extra_dependencies: ["float"]
    pandoc_args: --default-image-extension=pdf
header-includes:
  - \newcommand{\BOO}{BOO}
  - \usepackage {hyperref}
  - \hypersetup {colorlinks = true, linkcolor = blue, urlcolor = blue}
---
<!-- This is needed since I am working with svg files from mathcha.io. It converts the graphics files to something that can be used in the pdf files. Code taken from https://stackoverflow.com/questions/50165404/how-to-make-a-pdf-using-bookdown-including-svg-images/56044642#56044642 -->

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the 8th Analysis 1B Tutorial on the 27th March. Alternative formats can be downloaded by clicking the download icon at the top of the page. Please send any comments or corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

<!--<details open>
<summary>Want to ruin the surprise?</summary>
<br>
Well, you asked for it!
</details>-->

# Lecture Recap
This week, we look at some of the consequences of the Mean Value Theorem! These include a method of calculating limits (L'Hôpital's Rule) and a method of approximating functions (Taylor's Theorem). Throughout all of this, we are going to need functions which are at least twice differentiable, and along the way, we will develop some conditions to classify extrema.

## L'Hôpital's Rule [^1]
When calculating limits of one function divided by another, it is very tempting to apply the algebra of limits, and move on. However, if we look at $f(x)/g(x)$, and take $x \to c$, say, then a naïve application of the algebra of limits may result in an object of the form $$\frac{0}{0}, \; \text{or} \; \frac{\infty}{\infty}.$$ These are known as *indeterminate forms*, named as such because we can't assign a value to them. But in cases such as $$\lim_{x \to 3} \frac{x^2 - 9}{x - 3}$$, we know the limit exists ($=6$), despite the fact that blindly applying AoL gives us $0/0$. Luckily for us, there is a method which can help us find limits in the cases where an indeterminate form arises. This is known as L'Hôpital's rule:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1)  (L'Hôpital's Rule) </strong></span><p>Let $c \in \mathbb{R}$ and let $f,g: I \to \mathbb{R}$ be differentiable on an open interval $I$ containing $c$. Furthermore, suppose that:
  
  * $\lim_{x \to c} f(x) = 0  = \lim_{x \to c} g(x)$
  
  * $g'(x) \neq  0 \;\; \forall x \in I\setminus\lbrace c \rbrace,$ and
  
  * $\lim_{x \to c} \frac{f'(x)}{g'(x)}$ exists.

Then $\lim_{x \to c} \frac{f(x)}{g(x)} = \lim_{x \to c} \frac{f'(x)}{g'(x)}.$
  </p></div>\EndKnitrBlock{theorem}

[^1]: Or if you prefer your 17th Century French, de L'Hospital's rule.

# Hints
As per usual, here's where you'll find the problem sheet hints!

1) Remember that $\lvert x - 1\rvert$ is not differentiable at $x = 1$. So I would suggest splitting the domain up first to account for this. After doing this, there's an example in the lecture notes that may come in useful.
2) Try adapting the solutions to 'Problem Sheet 6, Tutorial Q1'.
3) Some of the ideas used in `Problem Sheet 7, Tutorial Q1' will be helpful here. Just remember to make sure that the hypotheses are satisfied when applying the Mean Value Theorem!

 

<!--chapter:end:index.Rmd-->

