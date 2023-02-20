---
title: "Analysis 1B — Tutorial 4"
author: 'Christian Jones: University of Bath'
date: 'February 2023'
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
      download: [["Tutorial4.html", "HTML page"], ["Tutorial4.pdf","Standard print PDF"], ["Tutorial4Clear.pdf","Clear print PDF"], ["Tutorial4Large.pdf","Large print PDF"], ["Tutorial4.docx","Accessible Word document"], ["Tutorial4.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
  clavertondown::pdf_clav:
    latex_engine: pdflatex
    keep_tex: true
    fig_caption: true
    toc: true
    extra_dependencies: ["float"]
    pandoc_args: --default-image-extension=pdf
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
    pandoc_args: --default-image-extension=svg
  clavertondown::html_clav:
    toc: true
    pandoc_args: --default-image-extension=svg
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
Here is the material to accompany the 4th Analysis 1B Tutorial on the 27th February. Alternative formats can be downloaded by clicking the download icon at the top of the page. Please send any comments or corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

<!--<details open>
<summary>Want to ruin the surprise?</summary>
<br>
Well, you asked for it!
</details>-->

# Lecture Recap

## Sequential Continuity
Recall the definition of function continuity from last week:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Continuity) </strong></span><div>Let $D \subseteq \mathbb{R}$, and $f: D \to \mathbb{R}$. Then $f$ is continuous at a point $c$ if $$\forall \epsilon > 0\;\;\exists \delta > 0\;\;\text{s.t.}\;\;\forall x \in D,\;\; \lvert x - c \rvert < \delta \Rightarrow \lvert f(x) - f(c) \rvert < \epsilon.$$</div></div>\EndKnitrBlock{definition}
Much like we did with limits, we can characterise continuity in terms of sequences. A bit of déjà vu here is completely normal, as this is something that was covered in Semester 1:

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Sequential Continuity) </strong></span><div>Let $D \subseteq \mathbb{R}$, and $f: D \to \mathbb{R}$. Then $f$ is sequentially continuous at a point $c$ if for all sequences $(x_n)_n$ in $D$ converging to $c$, we have that $\lim_{n \to \infty}f(x_n) = f(c).$</div></div>\EndKnitrBlock{definition}

A comparison between the two definitions is seen in Figure \@ref(fig:seqcnt). Remarkably, we can show that these two definitions are equivalent to each other:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1)  (Sequential Characterisation of Continuity) </strong></span><p>Let $D \subseteq \mathbb{R}$, and $f: D \to \mathbb{R}$. Then $f$ is continuous at a point $c$ if and only if it is sequentially continuous at $c$.</p></div>\EndKnitrBlock{theorem}
So why is this theorem useful? Basically, it says that you can use all the theory you learnt about sequences last semester to continuous functions. For example, last semester you showed that $\sin$, $cos$ and the exponential function $\exp$ were sequentially continuous on $\mathbb{R}$. Now you know they are continuous without doing any extra work! Also, this allows you to deduce the *Intermediate Value Theorem* for continuous functions too --- see later for more details.

<div class="figure">
<img src="Sequential Continuity.svg" alt="A diagram illustrating the difference between continuity and sequential continuity at a point $c$ in the domain of a function $f$."  />
<p class="caption">(\#fig:seqcnt)A diagram illustrating the definitions of continuity at a point $c$ (left), and sequential continuity at a point $c$ (right), for a function $f$. It turns out that these definitions are completely equivalent!</p>
</div>

Before we move on, Theorem \@ref(thm:thm1) also gives us a way of proving that a function is *not* continuous. We show this through an example, which extends Tutorial Question 2 on Problem Sheet 4.

\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong>(\#exm:ex1) </strong></span><div>Let $f:\mathbb{R} \to \mathbb{R}$ be defined by $$f(x) = \begin{cases}
1 \;\;\text{if}\;\;x\in\mathbb{Q},\\
0 \;\;\text{if}\;\;x\in\mathbb{R}\setminus\mathbb{Q}.\end{cases}$$ Further, define $h:\mathbb{R} \to \mathbb{R}$ by $h(x) = xf(x)$. Determine all points where $h$ is continuous.</div></div>\EndKnitrBlock{example}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>Firstly, in tutorial question 2, you showed that $f$ is discontinuous at all points in $\mathbb{R}$. But does this extend to $h$? In fact, $h$ is continuous at exactly one point --- zero.

To prove $h$ is continuous at $0$, fix $\epsilon > 0$, and suppose $\lvert x \rvert < \delta$ for some $\delta > 0$ to be chosen later. Then
\begin{align*}
\lvert h(x) - h(0) \rvert = \lvert x f(x) \rvert \leq \lvert x \rvert < \delta.
\end{align*}
Hence, taking $\delta = \epsilon$ gives that
\begin{align*}
\lvert x \rvert < \delta \Longrightarrow \lvert h(x) - h(0) \rvert < \epsilon.
\end{align*}
As $\epsilon$ was arbitrary, we have shown $h$ is continuous at $0$.

To prove $h$ is discontinuous everywhere else, fix $c \in \mathbb{R}\setminus \lbrace 0 \rbrace.$ Since both the rational numbers ($\mathbb{Q}$) and irrational numbers ($\mathbb{R}\setminus\mathbb{Q}$) are dense in $\mathbb{R}$, we can choose sequences $(x_n)_n$ and $(y_n)_n$ in $\mathbb{R}$ such that

1.  $\lim_{n \to \infty} x_n = c = \lim_{n \to \infty} y_n$,
2.  $x_n \in \mathbb{Q}\;\;\forall n \in \mathbb{N},$ and
3.  $y_n \in \mathbb{R}\setminus\mathbb{Q}\;\;\forall n \in \mathbb{N}.$
  
Now, $$h(x_n) = x_n f(x_n) = x_n \to c \;\;\text{as}\;\; n \to \infty,$$ and $$h(y_n) = y_n f(y_n) = 0 \to 0 \;\;\text{as}\;\; n \to \infty.$$ So, if $c$ is rational, we have shown that $h(y_n)\not\to h(c)$. If $c$ is irrational, we have shown that $h(x_n)\not\to h(c)$. Therefore, $h$ cannot be continuous at $c$ by Theorem \@ref(thm:thm1).

</p></div>\EndKnitrBlock{solution}

<details closed>
<summary>**Extension!**</summary>
\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex2"><span class="exm:ex2" custom-style="NameStyle"><strong>(\#exm:ex2) </strong></span><div>We can even use this example to produce a function defined on $\mathbb{R}$ which is only continuous on $\mathbb{Z}$! Using the $h$ from Example \@ref(exm:ex1), we can define $k(x) = h(x)$ if $x \in (-1/2, 1/2]$, and otherwise set $k(x + 1) = k(x).$ This periodicity condition ensures that since $h$ is only continuous at $0$, $k$ must be continuous only at each integer value.</div></div>\EndKnitrBlock{example}
</details>

## Building Continuous Functions
Another thing that the sequential characterisation of continuity gives you is an 'algebra of continuity'. In other words, continuous functions behave as you'd expect them to:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Algebra of Continuity) </strong></span><p>Let $c, \lambda \in \mathbb{R}$, and let $f,g: D \to \mathbb{R}$ Suppose $f$ and $g$ are continuous at $c \in D$. Then the following functions are continuous at $c$:
  
  1. $f + g$.
  
  2. $\lambda f$
  
  3. $fg$ (where $(fg)(x) = f(x)g(x)$)
  
  4. $\frac{f}{g}$ (when $g(c) \neq 0.$)
  </p></div>\EndKnitrBlock{theorem}
However, one thing that we can do with functions that we couldn't do with sequences is compose them. The following result tells us exactly when the composition $f\circ g$ is continuous!

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1)  (Continuity of Composition) </strong></span><p>Let $f: D \to \mathbb{R}$ and $g: E \to \mathbb{R}$, with $g(x) \in D \;\; \forall x \in E.$ Then, if $g$ is continuous at $c \in E$, and $f$ is continuous at $g(c) \in D$, then the composition $f\circ g : E \to \mathbb{R}$ is continuous at $c$.</p></div>\EndKnitrBlock{proposition}
A similar statement for limits also holds, but in that case, the continuity of $f$ is crucial --- see Problem Sheet 4 for more details!

## Intermediate Value Theorem
Here's one of the main theorems from last semester!

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong>(\#thm:thm3)  (Intermediate Value Theorem (IVT)) </strong></span><p>Suppose $a,b \in \mathbb{R}$ with $a < b$, and that $f:[a,b] \to \mathbb{R}$ is continuous[^1]. Then, if $y \in \mathbb{R}$ is such that $f(a) \leq y \leq f(b)$, then $\exists c \in [a,b]$ such that $f(c) = y$.</p></div>\EndKnitrBlock{theorem}
Diagrammatically, we might be in a situation like in Figure \@ref(fig:ivt). Note that there may be more than one $c$ that fulfills the conclusion of this theorem. Also, the theorem doesn't tell you what this $c$ is; it only says that a $c$ must exist.

<div class="figure">
<img src="ivt.svg" alt="A diagram showing how the intermediate value theorem applies to a continuous function"  />
<p class="caption">(\#fig:ivt)This function is continuous on $[a,b]$, and for $y$ as in the diagram, $y$ lies between $f(a)$ and $f(b)$. Hence the IVT applies, and so there exists $c$ in the interval $[a,b]$ such that $f(c)=y$. In this scenario, $c$ can be any one of $c_1,c_2$ or $c_3$.</p>
</div>

The IVT is very good for proving existence of square roots (and roots of any degree!), proving that functions have zeros, and proving that at any given point in time, there exists two points on the equator with exactly the same temperature[^2].

[^1]: If you like your notation, you can say that $f \in C^0([a,b]),$ which is the set of continuous functions on $[a,b]$.
[^2]: On an idealised Earth, anyway.
 
# Hints
As per usual, here's where you'll find the problem sheet hints!

1) These two examples are largely similar to the ones we did in tutorials (and I think there's a couple of examples in the lecture notes). Just make sure to explain fully why the function is/isn't continuous at a given point. And for once, there's no $\epsilon-\delta$ argument in sight!
2)  There's an example of how to solve this type of problem in the lecture notes. I'd also recommend looking at 'Problem Sheet Week 10' from last semester too, if you want another example along these lines. In regards to your solution, make it explicit that all hypotheses of the IVT are satisfied!
3) For the first part (i.e. proving the given result), use the sequential characterisation of limits and continuity. For the second part, try and find functions $f,g: \mathbb{R} \to \mathbb{R}$ which satisfy
\begin{align*}
g(f(x)) = \begin{cases}
1 \quad x\leq 0,\\
0 \quad x > 0.
\end{cases}
\end{align*}
*(Googling 'ramp function' might help with choosing one of $f$ or $g$.)*

 

<!--chapter:end:index.Rmd-->

