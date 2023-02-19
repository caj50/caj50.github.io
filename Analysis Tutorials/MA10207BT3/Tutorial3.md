---
title: "Analysis 1B — Tutorial 3"
author: 'Christian Jones: University of Bath'
date: 'February 2023'
site: bookdown::bookdown_site
language: en
documentclass: article
classoption: a4paper
fontsize: 10pt
geometry: margin=2.5cm
output:
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
    pandoc_args: --default-image-extension=svg
  clavertondown::gitbook_clav:
    split_by: section
    keep_md: true
    config:
      download: [["Tutorial3.html", "HTML page"], ["Tutorial3.pdf","Standard print PDF"], ["Tutorial3Clear.pdf","Clear print PDF"], ["Tutorial3Large.pdf","Large print PDF"], ["Tutorial3.docx","Accessible Word document"], ["Tutorial3.epub","Accessible EPub book" ]]
      sharing: no
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
  clavertondown::epub_clav:
    toc: false
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
Here is the material to accompany the 3rd Analysis 1B Tutorial on the 20th February. Alternative formats can be downloaded by clicking the download icon at the top of the page. Please send any comments or corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Lecture Recap

## Algebra of Limits for Functions
From last week, recall that we showed that we can characterise the limit of a function at a point in terms of sequences. This was brilliant, as it allowed us to apply the theory we derived in Semester 1 directly to functions. In particular, this gives us an easy way of finding the limits of sums and products of functions:

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong><span id="thm:thm1"></span>Theorem 1.1   (Algebra of Limits) </strong></span><p>Let $c, L, M, \lambda \in \mathbb{R}$, and let $f,g: D \to \mathbb{R}$, where $D$ is a punctured neighbourhood of $c$. Suppose $\lim_{x \to c}f(x) = L$, and $\lim_{x \to c}g(x) = M$. Then:
  
  1. $\lim_{x\to c}\left(f \pm g\right)(x) = L \pm M,$
  
  2. $\lim_{x \to c}\lambda f(x) = \lambda L,$
  
  3. $\lim_{x \to c}(fg)(x) = LM,$
  
  4. If $g(x) \neq 0 \;\;\forall x \in D$, and $M \neq 0$, then $$\lim_{x \to c}\left(\frac{f}{g}\right)(x) = \frac{L}{M}.$$
  </p></div>\EndKnitrBlock{theorem}

Note that here, we define the *product* of $f$ and $g$ by $(fg)(x) = f(x)g(x)$ --- don't get this confused with the composition $(f \circ g)(x) = f(g(x))$!

## Left and Right Limits
When finding the limit of a function $f$ at a point $c$ in the interior of its domain, we are free to approach $c$ from whichever direction we like. However, we could equally restrict ourselves to approaching $c$ only from the left or the right, and observing how the function values respond. This gives rise to the idea of *left and right hand limits*.

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong><span id="def:def1"></span>Definition 1.1   (Left and Right Hand Limits) </strong></span><div>Let $c, L, M \in \mathbb{R}$, and let $f: D \to \mathbb{R}$.
  
  1. Suppose $\exists \delta_0 > 0$ such that $(c, c + \delta_0) \subseteq D$. Then $\lim_{x \to c^{+}}f(x) = L$ means that $$\forall \epsilon >0\;\;\exists \delta>0\;\;\text{s.t}\;\; \forall x \in D,\;\; 0 < x - c < \delta \Rightarrow \lvert f(x) - L \rvert < \epsilon.$$ This is the *right-hand limit* at $c$.
  2. Suppose $\exists \delta_0 > 0$ such that $(c - \delta_0, c) \subseteq D$. Then $\lim_{x \to c^{-}}f(x) = M$ means that $$\forall \epsilon >0\;\;\exists \delta>0\;\;\text{s.t}\;\; \forall x \in D,\;\; 0 < x - c < \delta \Rightarrow \lvert f(x) - M \rvert < \epsilon.$$ This is the *left-hand limit* at $c$.
</div></div>\EndKnitrBlock{definition}

As the names suggest, we approach $c$ from the left when calculating the left-hand limit, and we approach $c$ from the right when calculating the right-hand limit. It also turns out that these objects can be very useful in calculating function limits, especially when the function is defined piecewise:

\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong><span id="prp:prop1"></span>Proposition 1.2  </strong></span><p>Let $c \in \mathbb{R}$, and let $f: D \to \mathbb{R}$, where $D$ is a punctured neighbourhood of $c$. Then $\lim_{x \to c}f(x)$ exists if and only if both the left and right hand limits exist, and are equal.</p></div>\EndKnitrBlock{proposition}

Finally, note that if we had a function on a domain such as $D = [-1,2]$, we could only search for the right hand limit at $c = -1$, and the left hand limit at $c = 2$. This is because there is no way we could approach these elements of the domain from the left or right respectively.

## Continuity
A stronger statement than requiring a function to have a limit at a value $c$ is for that function to be continuous. Up until now, you may have thought of a continuous function as one that can be drawn without taking your pen off the page. We can make that idea more precise in the following definition:

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong><span id="def:def2"></span>Definition 1.2   (Continuity) </strong></span><div>Let $D \subseteq \mathbb{R}$, and $f: D \to \mathbb{R}$. Then $f$ is continuous at a point $c$ if $$\forall \epsilon > 0\;\;\exists \delta > 0\;\;\text{s.t.}\;\;\forall x \in D,\;\; \lvert x - c \rvert < \delta \Rightarrow \lvert f(x) - f(c) \rvert < \epsilon.$$</div></div>\EndKnitrBlock{definition}

A graphical example of this definition can be seen in Figure <a href="#fig:cont">1.1</a>.

![Figure 1.1: A diagram illustrating the definition of a continuous function at a point $c$ (left). Compare this to a function which only approaches a limit $L$ as $x \to c$ (right).](Continuity.svg)

You might be thinking that this looks remarkably like the definition of a limit from last week, and you would be right. In fact: $$f\;\;\text{is continuous at}\;\; c \Longleftrightarrow \lim_{x \to c}f(x) = f(c).$$ However, note that we require $f$ to be defined at $c$ for $f$ to be continuous; in the limit definition, we didn't care whether or not $f(c)$ existed.

# Hints
As per usual, here's where you'll find the problem sheet hints!

1) Part a) is all about using the epsilon-delta definition of limit. Firstly, note that there are two things to prove here because of the `if and only if'. Think about how you can substitute variables to move from the definition of one limit to the definition of the other.  For part b), think about using a step function for $f$.
2) Again, this is all about manipulating an unfamiliar definition, and again, there are two things to prove! Pretty much the same idea applies here too — try and rewrite one definition so it starts to look like the other, then use that to make a choice of $\delta$ and/or $M$ (depending on which implication you are proving).
3) This is quite similar to the example we did in tutorials. Note that you'll have to take cases on $x$ when evaluating $\lvert f(x) - f(0)\rvert$, but in both cases, you'll end up with the same bound in terms of $\delta$.
 

<!--chapter:end:index.Rmd-->

