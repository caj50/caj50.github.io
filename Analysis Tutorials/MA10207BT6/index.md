---
title: "Analysis 1B — Tutorial 6"
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
      download: [["Tutorial6.html", "HTML page"], ["Tutorial6.pdf","Standard print PDF"], ["Tutorial6Clear.pdf","Clear print PDF"], ["Tutorial6Large.pdf","Large print PDF"], ["Tutorial6.docx","Accessible Word document"], ["Tutorial6.epub","Accessible EPub book" ]]
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
Here is the material to accompany the 6th Analysis 1B Tutorial on the 13th March. Alternative formats can be downloaded by clicking the download icon at the top of the page. Please send any comments or corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

<!--<details open>
<summary>Want to ruin the surprise?</summary>
<br>
Well, you asked for it!
</details>-->

# Lecture Recap
This week, we're starting to look at the derivative of a function. Along the way, we'll see some tricks for making differentiation easier, and we'll cover a way of finding the derivative of inverse functions.

## Differentiation
While functions are very good at describing physical quantities such as temperature, density or momentum we can usually gain more insight into these variables by studying how fast they change at a given position or time. Mathematically, we study rates of change using derivatives, which again relies on the ideas behind limits!

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Derivative) </strong></span><div>Let $f: D \to \mathbb{R}$, where $D \subseteq \mathbb{R}$ is an open set, and let $c \in D$. Then, if $\exists L \in \mathbb{R}$ such that $$\lim_{h \to 0}\frac{f(c+h) - f(c)}{h} = L,$$ we say that $f$ is differentiable at $c$, and call $L$ the derivative of $f$ at $c$.</div></div>\EndKnitrBlock{definition}
We can note a few things here:

*  Firstly, if this $L$ exists, we write it as $f'(c)$ to make it clear that its a derivative.
*  We require $D$ to be open, so that we can actually take limits! If, for example, $D = [-1,2]$, we could attempt to define the derivative at any point in the interior of $D$, $D^{\circ} = (-1,2)$, but we couldn't define the derivative at $x = -1$ or $x = 2$.[^4]
*  Substituting $x = c+h$ into the definition gives us an equivalent formulation: $f$ is differentiable at $c$ if there exists $L\in\mathbb{R}$ such that $$\lim_{x \to c}\frac{f(x) - f(c)}{x - c} = L.$$

One quick result we obtain from this definition is the following:
\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1) </strong></span><p>If a function $f:D \to \mathbb{R}$ is differentiable at a point $c$, then it is continuous at $c$.</p></div>\EndKnitrBlock{proposition}
The contrapositive of this is very useful for ruling functions out: if a function is **not** continuous, it is not differentiable. As a further remark, or warning, **continuity does not imply differentiability**! To see this, think of either $f(x) = \lvert x \rvert$ at $x = 0$, or look up the [Weierstrass function](https://en.wikipedia.org/wiki/Weierstrass_function). 

[^4]: There is nothing stopping us; however, trying to define *left* and *right derivatives* at these points, i.e. we could search for $$\lim_{x \to -1^{+}}\frac{f(-1+h) - f(-1)}{h}\;\;\text{or}\;\;\lim_{x \to 2^{-}}\frac{f(2+h) - f(2)}{h}.$$

## Rules of Differentiation {#diff}
Since everything inside the limit defining the derivative is just a function (of either $h$ or $x$), we can apply the algebra of limits to deduce a few familiar rules of differentiation:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1a"><span class="thm:thm1a" custom-style="NameStyle"><strong>(\#thm:thm1a)  (Algebra of Derivatives 1) </strong></span><p>Let $D\subseteq\mathbb{R}$ be an open set, and let $f,g:D \to \mathbb{R}$ be differentiable at $c\in D.$ Then the following functions are differentiable at $c$:
  
  1. $f+g$, with $$(f+g)'(c) = f'(c) + g'(c),$$
  2. $Kf$ for any $K\in\mathbb{R}$, with $$(Kf)'(c) = Kf'(c),$$
  
  </p></div>\EndKnitrBlock{theorem}

Using these two rules we can show that the set of functions $f:D\to\mathbb{R}$ which are differentiable at $c$ form a vector space. In fact, since differentiability implies continuity, and the zero function $0:D \to \mathbb{R}$ given by $0(x) = 0$ is also differentiable at $c$, this set forms a vector subspace of the set of functions $f:D \to \mathbb{R}$ which are continuous at $c$.

There are three further rules which make up the Algebra of Derivatives:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1b"><span class="thm:thm1b" custom-style="NameStyle"><strong>(\#thm:thm1b)  (Algebra of Derivatives 2) </strong></span><p>Let $D\subseteq\mathbb{R}$ be an open set, and let $f,g:D \to \mathbb{R}$ be differentiable at $c\in D.$ Then the following functions are differentiable at $c$:
  
  3. (Product rule) $fg$, with $$(fg)'(c) = f'(c)g(c) + f(c)g'(c),$$
  4. For $g(c)\neq0$, $1/g$, with $$\left(\frac{1}{g}\right)'(c) = \frac{-g'(c)}{g(c)^2}.$$
  5. (Quotient rule) For $g(c)\neq0$, $f/g$ with $$\left(\frac{f}{g}\right)'(c) = \frac{f'(c)g(c)-f(c)g'(c)}{g(c)^2}.$$
  
  </p></div>\EndKnitrBlock{theorem}

One thing to note here is that we can obtain the quotient rule by applying the product rule to the functions $f$ and $1/g$, which saves you having to learn the proof!

### Chain Rule
The one thing we've said nothing about so far is whether a composition of functions is differentiable. This result is what is known as the (familiar) chain rule:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Chain Rule) </strong></span><p>Let $g:(a,b) \to \mathbb{R}$ and $f:(A,B) \to \mathbb{R}$ be such that $g\left((a,b)\right) \subseteq (A,B).$ Assume that $g$ is differentiable at $c$ and $f$ is differentiable at $g(c)$. Then the composition $f\circ g$ is differentiable at $c$ with $$\left(f\circ g\right)'(c) = f'\left(g(c)\right)g'(c).$$</p></div>\EndKnitrBlock{theorem}

## Inverse Functions
Another thing we might want to know is whether we can differentiate the inverse of a differentiable function. For example, the exponential function $\exp$ and the trigonometric functions $\sin, \cos$ have nice series definitions, and this makes it fairly straightforward to calculate their derivatives. But what if we're interested in their inverses ($\ln, \arcsin, \arccos$)? Luckily, we have a theorem which tells us what the values of their derivatives are!

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong>(\#thm:thm3)  (Inverse Function Theorem) </strong></span><p>Let $f: (a,b) \to (A, B)$ be bijective, and let $c \in (a,b).$ Assume that $f$ is differentiable at $c$, $f'(c) \neq 0$, and $f^{-1}$ is continuous at $f(c).$ Then $f^{-1}$ is differentiable at $y_0 = f(c)$ and $$\left(f^{-1}\right)'(y_0) = \frac{1}{f'\left(f^{-1}(y_0)\right)} = \frac{1}{f'(c)}.$$
  </p></div>\EndKnitrBlock{theorem}

\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong>(\#exm:ex1) </strong></span><div>Returning to our exponential example from last week, we know that from lectures $\exp: \mathbb{R} \to (0,\infty)$ is differentiable for all $c \in \mathbb{R}$, and since $\exp'(x) = \exp(x)$, $\exp'(c) \neq 0$ for any $c$. Last week, we showed that the inverse function $\ln: (0,\infty) \to \mathbb{R}$ is continuous at any $\exp(c) \in (0,\infty)$, so by Theorem \@ref(thm:thm3), $\ln$ is differentiable on $(0,\infty)$, with $$\ln'(y_0) = \frac{1}{\exp'(\ln(y_0))} = \frac{1}{\exp(\ln(y_0))} = \frac{1}{y_0}.$$ Graphically, we can see the result of this theorem by comparing the gradient of the associated tangent lines:

  ADD GRAPH</div></div>\EndKnitrBlock{example}

We can use the results of Example \@ref(exm:ex1) and the rules of differentiation from Section \@ref(diff) to calculate the derivatives of some more complicated functions:
\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex2"><span class="exm:ex2" custom-style="NameStyle"><strong>(\#exm:ex2) </strong></span><div>Consider the function $h:(0,\infty) \to (0,\infty)$ given by $h(x) = x^x.$ Since $$h(x) = \exp(\ln(x^x)) = \exp(x\ln(x)),$$ we can rewrite $h$ as a composition of differentiable functions $h = f \circ g$, where $f:\mathbb{R} \to (0,\infty)$ is defined by $f(x) = \exp(x)$, and $g: (0,\infty) \to \mathbb{R}$ is defined by $g(x) = x\ln(x).$
  
From lectures, we know that $f$ is differentiable on $\mathbb{R}$ with $f'(x) = \exp(x).$ Furthermore, by Example \@ref(exm:ex1) and the product rule, we know that $g$ is differentiable on $(0,\infty)$, with $g'(x) = \ln(x) + 1.$ Hence, by the chain rule, $h$ is differentiable on $(0,\infty)$ with $$h'(x) = f'(g(x))g'(x) = \exp(x\ln(x))\left(\ln(x) + 1\right) = x^x\left(\ln(x) + 1\right)$$

</div></div>\EndKnitrBlock{example}
Theorem \@ref(thm:thm3) will come in handy if you ever need to perform coordinate transforms, in particular when evaluating integrals by substitution. You may have also come across the multivariate version of this theorem in MA10230 (Multivariable Calculus and Differential Equations) when calculating the Jacobian for a transformation from Cartesian to polar coordinates (or vice versa).

# Hints
As per usual, here's where you'll find the problem sheet hints!

1) We did some examples similar to this in the tutorial today. Specify the domain of each function, and use the results you've seen in the course to justify differentiability on each domain. In regards to computing the derivatives, I don't think you'll have too much trouble, but let me know if you run into problems.
2)  The following formula may come in handy:$$\max(f(x),g(x)) = \frac{1}{2}\left(\lvert f(x) - g(x) \rvert + f(x) + g(x)\right).$$
    For the function examples, try and find $f,g$ such that $$\max(f(x),g(x)) = \lvert x \rvert.$$
3) Using $p(x) = (x-a)q(x)$, what does $p'(x)$ give you?

 

<!--chapter:end:index.Rmd-->
