---
title: "Analysis 1A — Tutorial 3"
author: 'Christian Jones: University of Bath'
date: 'October 2022'
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
      download: [["Tutorial3.html", "HTML page"], ["Tutorial3.pdf","Standard print PDF"], ["Tutorial3Clear.pdf","Clear print PDF"], ["Tutorial3Large.pdf","Large print PDF"], ["Tutorial3.docx","Accessible Word document"], ["Tutorial3.epub","Accessible EPub book" ]]
      sharing: no
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
  clavertondown::html_clav:
    toc: true
    pandoc_args: --default-image-extension=svg
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
    pandoc_args: --default-image-extension=svg
header-includes:
  - \newcommand{\BOO}{BOO}
  - \usepackage {hyperref}
  - \hypersetup {colorlinks = true, linkcolor = blue, urlcolor = blue}
---
<!-- This is needed since I am working with svg files from mathcha.io. It converts the graphics files to something that can be used in the pdf files. Code taken from https://stackoverflow.com/questions/50165404/how-to-make-a-pdf-using-bookdown-including-svg-images/56044642#56044642 -->

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the 3rd Analysis Tutorial on the 24th October. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk).

# Lecture Recap

## Suprema and Infima
There's still a little bit of material to cover regarding the supremum and infimum of a set. To begin, we re-cover the definitions from last week.
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Supremum) </strong></span><div>Let $S \in \mathbb{R}$. A number $T \in \mathbb{R}$ is said to be the supremum of $S$ if it is an upper bound for $S$, and for any other upper bound $M$, $T \leq M$. Here, we write $T = \sup(S)$.</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Infimum) </strong></span><div>Let $S \in \mathbb{R}$. A number $t \in \mathbb{R}$ is said to be the infimum of $S$ if it is a lower bound for $S$, and for any other lower bound $m$, $t\geq m$. Here, we write $t = \inf(S)$.</div></div>\EndKnitrBlock{definition}
It also turns out that there's an alternative characterisation of suprema and infima which turns out to be very useful, especially if the members of a set aren't indexed by natural numbers.

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1) </strong></span><p>Let $S\subseteq\mathbb{R}$. Then a number $T\in\mathbb{R}$ is the \emph{supremum} of $S$, denoted $\sup(S)$ if: $$\forall \epsilon > 0, \exists s \in S\; \text{such that} \; s > T - \epsilon.$$</p></div>\EndKnitrBlock{proposition}

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop2"><span class="prp:prop2" custom-style="NameStyle"><strong>(\#prp:prop2) </strong></span><p>Let $S\subseteq\mathbb{R}$. Then a number $t\in\mathbb{R}$ is the \emph{infimum} of $S$, denoted $\inf(S)$ if: $$\forall \epsilon > 0, \exists s \in S\; \text{such that} \; s < t + \epsilon.$$</p></div>\EndKnitrBlock{proposition}
As an example, take the set $S = (-1,2] = \lbrace x \, \lvert\, -1 < x \leq 2\rbrace$, and fix some $\epsilon > 0$. Then, if we take $s_1 = 2 - \epsilon/2$ and $s_2 = -1 + \epsilon/2$, we see that

* $s_1$ and $s_2$ are in the set $S$,
* $s_1 > 2 - \epsilon$, and
* $s_2 < -1 + \epsilon$.

Hence, as $\epsilon$ was arbitrary, the alternative characterisation of suprema and infima says that $\sup(S) = 2$ and $\inf(S) = -1$.

## Inequalities
Inequalities come up everywhere in maths! For example, they can be used in statistics for estimation (Markov/Chebyshev inequalities), they can be used as constraints in optimisation problems (see Section 3.1 of [this Wikipedia link.](https://en.wikipedia.org/wiki/Linear_programming)), and quite famously appear in Quantum Mechanics. In this latter case, we have the [Heisenberg Uncertainty Principle](http://hyperphysics.phy-astr.gsu.edu/hbase/uncer.html), and this inequality states that you can't simultaneously know the position and momentum of a quantum particle, such as an electron.

Most of the inequalities in this course will be based on the absolute value, which is defined as follows:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong>(\#def:def3)  (Absolute Value) </strong></span><div>For $x \in \mathbb{R}$, the absolute value of $x$ is given by \begin{align*}
    \lvert x \rvert = \begin{cases}
    x \quad &\text{if} \; x \geq 0,\\
    -x \quad &\text{if} \; x < 0
    \end{cases}\;\; = \max\lbrace x, -x \rbrace.
\end{align*}</div></div>\EndKnitrBlock{definition}

The absolute value has the following properties:
\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop3"><span class="prp:prop3" custom-style="NameStyle"><strong>(\#prp:prop3) </strong></span><p>For $x,y \in \mathbb{R}$:
\begin{gather*}
   x \leq \lvert x \rvert,\quad -x \leq \lvert x \rvert,\quad \lvert -x \rvert = \lvert x \rvert\quad \text{and}\quad \lvert x y \rvert = \lvert x \rvert \lvert y \rvert.
\end{gather*}</p></div>\EndKnitrBlock{proposition}
Now we come on to what I consider to be the most important thing in this course.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong>(\#thm:thm4)  (Triangle Inequalities) </strong></span><p>For $x,y\in\mathbb{R}$:
  
  * $\lvert x + y \rvert \leq \lvert x \rvert + \lvert y \rvert$, and
  * $\left\lvert \lvert x \rvert - \lvert y \rvert \right\rvert \leq \lvert x - y \rvert.$
  </p></div>\EndKnitrBlock{theorem}
The first of these is known as the **Triangle Inequality**, and the second is the **Reverse Triangle Inequality**. Why do I think this is so important? This will come up in almost any course you take at university that uses analysis! If you're studying vector calculus, fluid mechanics, statistics, probability, or anything that's not abstract algebra, there's guaranteed to be a proof or technique which involves an inequality of this form! So if you only learn one result from Analysis 1, make it this one.

Finally, there's one more inequality to mention — the binomial inequality.
\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop4"><span class="prp:prop4" custom-style="NameStyle"><strong>(\#prp:prop4)  (Binomial Inequality) </strong></span><p>We have $\forall n \in \mathbb{N}_0$ (i.e. all the natural numbers with $0$), and $\forall x \geq -1$, $$(1 + x)^n \geq 1 + nx.$$</p></div>\EndKnitrBlock{proposition}

# Hints
As per usual, here's where you'll find the problem sheet hints!

* [H1.] Take cases on $x$.
* [H2.] You should only need the definitions given in lectures to solve this question. Make sure to write things logically! 
* [H3.] Without loss of generality (WLOG), consider $x \geq y$ (otherwise you can just swap them), and consider $\lvert \sqrt{x} - \sqrt{y} \rvert^2$. On expanding, try and find a bound for the `middle' term.
* [H4.] Solve the modulus equation, and then use your solutions to formulate simultaneous equations for $c$ and $r$.
