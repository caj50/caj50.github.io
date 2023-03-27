---
title: "Analysis 1B — Tutorial 9"
author: 'Christian Jones: University of Bath'
date: 'April 2023'
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
      download: [["Tutorial9.html", "HTML page"], ["Tutorial9.pdf","Standard print PDF"], ["Tutorial9Clear.pdf","Clear print PDF"], ["Tutorial9Large.pdf","Large print PDF"], ["Tutorial9.docx","Accessible Word document"], ["Tutorial9.epub","Accessible EPub book" ]]
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
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
    pandoc_args: --default-image-extension=svg
  clavertondown::html_clav:
    toc: true
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
Here is the material to accompany the 9th Analysis 1B Tutorial on the 17th April. Alternative formats can be downloaded by clicking the download icon at the top of the page. Please send any comments or corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

<!--<details open>
<summary>Want to ruin the surprise?</summary>
<br>
Well, you asked for it!
</details>-->

# Lecture Recap
This week, we begin the final section of this course, and it's all about integration! Unfortunately, in order to actually define what the (Riemann) integral of a function is, we're going to need a whole lot of definitions...

## Fundamentals of Integration

Just as we used derivatives to find how fast a function is changing at a given point, we may also be interested in how much area lies between a function and its domain. For example, if we extend an elastic spring by a distance $x$, and consider the corresponding force to do so, $F(x)$, then the area under a graph of $F(x)$ tells us how much (elastic) energy is stored in the spring.

But how do we find this area mathematically? The idea is to look at the domain of the function, split it up, and over/underestimate the area using rectangles. The hope is then that as the division of the domain becomes finer and finer, the estimates converge to the true area under the graph of our function.

In all of what follows, we are going to need a bounded function $f : [a,b] \to \mathbb{R}$. This is so its supremum and infimum exist.

### Subdivisions and Riemann Sums

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Subdivision) </strong></span><div>A *subdivision* (or partition or dissection) of $[a,b]$ is a finite set $P = \lbrace x_0, x_1, \ldots, x_n \rbrace$ with $$a = x_0 < x_1 < \ldots < x_n = b.$$
</div></div>\EndKnitrBlock{definition}

Now that we have our subdivision of the domain, we need to define our under- and overestimates of the area below $f$. These are defined mathematically below, but can be seen geometrically in Figure \@ref(fig:Riemann).

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Lower Riemann Sum) </strong></span><div>The *lower Riemann sum* of $f$ on a subdivision $P$ is $$L(f,P) = \sum_{i=1}^{n} m_i (x_i - x_{i-1}),$$ where $$m_i = \inf_{[x_{i-1},x_i]}f(x) := \inf\lbrace f(x) \lvert x \in [x_{i-1},x_i]\rbrace.$$</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong>(\#def:def3)  (Upper Riemann Sum) </strong></span><div>The *upper Riemann sum* of $f$ on a subdivision $P$ is $$U(f,P) = \sum_{i=1}^{n} M_i (x_i - x_{i-1}),$$ where $$M_i = \sup_{[x_{i-1},x_i]}f(x) := \sup\lbrace f(x) \lvert x \in [x_{i-1},x_i]\rbrace.$$</div></div>\EndKnitrBlock{definition}


<div class="figure" style="text-align: center">
<img src="riemannsums.svg" alt="A diagram illustrating Taylor's Theorem"  />
<p class="caption">(\#fig:Riemann)The upper and lower Riemann sums for a function $f:[a,b] \to \mathbb{R}$ defined on a subdivision $P = \lbrace x_0,x_1,x_2,x_3 \rbrace$ of $[a,b]$. The lower Riemann sum is the total area of the green rectangles, and the upper Riemann sum is the total area of the green and orange rectangles.</p>
</div>

### Refinements
At this stage, given a bounded function $f:[a,b] \to \mathbb{R}$, we have a way of subdividing the domain and a way of estimating the area under $f$. We'd now like to consider what happens to the estimates as we make our subdivision finer. This leads on to the idea of a refinement:

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def4"><span class="def:def4" custom-style="NameStyle"><strong>(\#def:def4)  (Refinement) </strong></span><div>Let $P = \lbrace x_0, x_1, \ldots, x_n \rbrace$ and $Q = \lbrace y_0, y_1, \ldots, y_m \rbrace$ be subdivisions of $[a,b].$ Then $Q$ is a *refinement* of $P$ if $P\subseteq Q$.</div></div>\EndKnitrBlock{definition}
Note that under this definition, $P$ is a refinement of itself!

## Useful Results for Subdivisions
If we refine our subdivisions, what happens to the corresponding lower and upper Riemann sums? Luckily we have a set of results that tell us!

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1) </strong></span><p>Let $f:[a,b] \to \mathbb{R}$ be bounded, and let $P$ be a subdivision of $[a,b].$ Then:
  
  * $L(f,P) \leq U(f,P)$
  * If $Q$ is a refinement of $P$, $$L(f,P) \leq L(f,Q)\;\; \text{and} \;\; U(f,Q) \leq U(f,P).$$
  * If $R$ is **any** other subdivision, $$L(f,P) \leq U(f,R).$$ (This says that every lower Riemann sum is smaller than every upper Riemann sum.)
</p></div>\EndKnitrBlock{proposition}

## The Definition!
We're almost ready to define the (Riemann) integral! Since the set of all lower sums is bounded above, and the set of all upper sums is bounded below, we can talk about their supremum and infimum respectively. These have special names, and are correspondingly known as *lower and upper Riemann integrals*.

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def5"><span class="def:def5" custom-style="NameStyle"><strong>(\#def:def5)  (Lower and Upper Riemann Integrals) </strong></span><div>Let $f:[a,b] \to \mathbb{R}$ be bounded. Then:
  
  * The *lower Riemann integral* is $$\underline{\int_a^b} f := \sup\left\lbrace L(f,P) \bigg\lvert\; \text{$P$ is a subdivision of $[a.b]$}\right\rbrace.$$
  * The *upper Riemann integral* is $$\overline{\int_a^b} f := \inf\left\lbrace U(f,P) \bigg\lvert\; \text{$P$ is a subdivision of $[a.b]$}\right\rbrace.$$
  </div></div>\EndKnitrBlock{definition}

And now, after much ado, we can finally say what it means for a function to be Riemann integrable!

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def6"><span class="def:def6" custom-style="NameStyle"><strong>(\#def:def6)  (Riemann Integral) </strong></span><div>Let $f:[a,b] \to \mathbb{R}$ be bounded. Then $f$ is *Riemann integrable* if $$\underline{\int_a^b} f = \overline{\int_a^b} f.$$ If this happens, then the (Riemann) integral of $f$ is defined to be the common value, and given the notation $\int_{a}^b f.$</div></div>\EndKnitrBlock{definition}

# Hints
As per usual, here's where you'll find the problem sheet hints!

1) Have a look back at the example we did in tutorials — this one is pretty similar! Calculate both the lower and upper Riemann sums, and make sure to justify the main steps of your argument. Another thing, feel free to quote the values of $$\sum_{i=1}^{n} i^{k}, \quad k=0,1,2,\ldots$$ as 'standard results', although being able to prove them is good practice too!
2) First of all, this is an 'if and only if', so there are two things to prove! The '$\Leftarrow$' direction should be fairly straightforward. For the '$\Rightarrow$' direction, what do you get from considering $U(f,P) - L(f,P)$?
3) Try the function $$h:[0,1] \to \mathbb{R}, \quad h(x) = xf(x),$$ where $f$ is as given in the question. Make sure to prove continuity at zero first. To prove that $h$ is not integrable, show that the lower and upper Riemann integrals cannot be the same. For any subdivision $P$, finding $L(h,P)$ should be OK. For $U(h,P)$, try and compare it to an upper Riemann sum of a function that you know the integral of.
 

<!--chapter:end:index.Rmd-->

