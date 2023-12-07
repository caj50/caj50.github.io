---
title: "Analysis 1A — Tutorial 10"
author: 'Christian Jones: University of Bath'
date: 'December 2023'
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
      download: [["Tutorial10.html", "HTML page"], ["Tutorial10.pdf","Standard print PDF"], ["Tutorial10Clear.pdf","Clear print PDF"], ["Tutorial19Large.pdf","Large print PDF"], ["Tutorial10.docx","Accessible Word document"], ["Tutorial10.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
  clavertondown::html_clav:
    toc: true
    pandoc_args: --default-image-extension=svg
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
    pandoc_args: --default-image-extension=svg
  clavertondown::pdf_clav:
    latex_engine: pdflatex
    keep_tex: true
    fig_caption: true
    toc: true
    extra_dependencies: ["float"]
    pandoc_args: --default-image-extension=pdf
  clavertondown::epub_clav:
    toc: false
    pandoc_args: --default-image-extension=svg
header-includes:
  - \newcommand{\BOO}{BOO}
  - \usepackage {hyperref}
  - \hypersetup {colorlinks = true, linkcolor = blue, urlcolor = blue}
---

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the Analysis Tutorial in Week 10. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Lecture Recap

## Two More Convergence Tests
So far, we've seen two tests which allow us (under certain conditions) to determine whether a series is convergent or not. These were the comparison test and d'Alembert's ratio test. There's two more tests to cover here. The first is yet another thing named after Cauchy! The second concerns series which have *alternating terms*. This is due to Leibniz, who --- depending on your point of view --- is considered to be the inventor of calculus.

### Cauchy Condensation Test
This test is very good when the terms of a series involve logarithms, and can also be used to show that $$\sum_{n = 1}^{\infty} \frac{1}{n^{\alpha}} \;\;\text{converges} \Longleftrightarrow \alpha > 1.$$

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1)  (Cauchy) </strong></span><p>Assume $(a_n)_n$ satisfies $a_n \geq 0 \; \forall n \in \mathbb{N}$, and is a decreasing sequence. For $k \in \mathbb{N}$, define $b_k := 2^ka_{2^k}$. Then $$\sum_{n = 1}^{\infty} a_n \;\; \text{converges}\; \Longleftrightarrow\; \sum_{k = 1}^{\infty} b_k \;\; \text{converges}.$$</p></div>\EndKnitrBlock{theorem}

We conclude this (rather short) subsection with a [link](https://math.stackexchange.com/questions/2071016/does-sum-infty-3-fracn2lnlnnlnn-converge?rq=1) to an example of the Cauchy condensation test in practice. It's highly unlikely you'll ever get something like this in the exam, but the numbers involved are so ridiculous it's worth including here nonetheless!

### Leibniz Alternating Series Test
We've stated in tutorials that the series $$\sum_{i=1}^{\infty}\frac{(-1)^n}{n}$$ is conditionally convergent --- that is, that this sum converges, but $$\sum_{i=1}^{\infty}\left\lvert\frac{(-1)^n}{n}\right\rvert = \sum_{i=1}^{\infty}\frac{1}{n}$$ does not. But how do we prove this? The answer to this lies within the following convergence test:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Leibniz Alternating Series Test) </strong></span><p>Suppose $(a_n)_{n\in\mathbb{N}}$ is a decreasing sequence tending to $0$ as $n \to \infty$. Then $$\sum_{n=1}^{\infty} (-1)^n a_n$$ is a convergent series. </p></div>\EndKnitrBlock{theorem}
Moreover, since the sequence $(a_n)_n$ is decreasing towards $0$, we can say that the value of this sum lies in between $-a_1$ and $a_2 - a_1$.

## Multiplying Series
Recall the statement of the Algebra of Series:
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong>(\#thm:thm3)  (Algebra of Series) </strong></span><p>Let $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$ be convergent series, and let $\alpha, \beta \in \mathbb{R}$. Then $$\sum_{n=1}^{\infty}(\alpha a_n + \beta b_n) = \alpha\sum_{n=1}^{\infty}a_n + \beta\sum_{n=1}^{\infty}b_n.$$</p></div>\EndKnitrBlock{theorem}
Now, compare this to the statement of the Algebra of Limits. Notice that we've suspiciously omitted any mention about multiplying infinite series together. This is because while for convergent sequences $(x_n)_n$ and $(y_n)_n$, $$\lim_{n\to\infty}(x_ny_n) = \lim_{n\to\infty}x_n \cdot \lim_{n\to\infty}y_n,$$ it does **not** follow that for convergent series $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$, $$\sum_{n=1}^{\infty} a_nb_n = \left(\sum_{n=1}^{\infty}a_n\right)\left(\sum_{n=1}^{\infty}b_n\right).$$

If you're not convinced, we can try this with $a_n = b_n =  \frac{(-1)^{n}}{\sqrt{n}}$. Using the Leibniz test, we can see that both $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$ converge, but $$\sum_{n=1}^{\infty} a_nb_n = \sum_{n=1}^{\infty}\frac{1}{n} = \infty.$$ So, the next question we need to ask is whether a formula for multiplying convergent series exists, and if so, which series can we apply it to. This question was answered by Cauchy[^2], and is summarised in the below theorem:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong>(\#thm:thm4)  (Cauchy Multiplication Theorem) </strong></span><p>Assume that the real series $\sum_{n=0}^{\infty}a_n$ and $\sum_{n=0}^{\infty}b_n$ converge absolutely, and for $n \in \mathbb{N}$, define $$c_n:=\sum_{j=0}^{n}a_j b_{n - j}.$$ Then $\sum_{n=0}^{\infty} c_n$ converges absolutely, and $$\sum_{n=0}^{\infty} c_n = \left(\sum_{n=0}^{\infty}a_n\right)\left(\sum_{n=0}^{\infty}b_n\right).$$</p></div>\EndKnitrBlock{theorem}
Note that we index the sums starting at $n=0$ here. This is purely for convenience, and you could equally formulate this theorem for sums starting at $n=1$ (or any other value of $n$ for that matter). Furthermore, we require the condition that the two individual sums are *absolutely convergent*. As you've seen in lectures, the Cauchy Multiplication Theorem will fail if the series involved are only conditionally convergent.



[^2]: If you're keeping track, this is the third time Cauchy has appeared in this course.

# Hints
As per usual, here’s where you’ll find the problem sheet hints!

1.  In this one, remember what we did in tutorials. One uses Leibniz, one can be done with Leibniz (but its quicker not to), and one diverges. Make sure you check the hypotheses of any test you use!
2.  a)  Work out an expression for $\frac{a_{n+1}}{a_n}$ (this will depend on whether $n$ is odd or even).
    b) Check whether $(a_n)$ is an increasing or decreasing sequence first: this will help you calculate the $\limsup$.
3.  To begin here, you've seen a similar trick for the square roots in previous problem sheets. Think about your tests for convergence again on this one!
4.  Use the alternative characterisation of suprema (Theorem 3.2 in the lecture notes).


<!--chapter:end:index.Rmd-->

