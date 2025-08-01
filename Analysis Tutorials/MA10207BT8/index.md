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
Suppose we want to calculate the limit $$\lim_{x \to 3} \frac{x^2 - 9}{x - 3} = L.$$ Using sequences, say, we can easily show that $L = 6$, but why don't we use the algebra of limits? After all, we formulated AoL to make our lives easier, and both $\lim_{x \to 3} x^2 - 9$ and $\lim_{x \to 3} x - 3$ exist. The issue is that if we naïvely apply AoL, we end up running into an *indeterminate form*. This is an object of the form $$\frac{0}{0} \; \text{or} \; \frac{\infty}{\infty},$$ and is named as such because we cannot assign a value to it. For more complicated limits, we could really use a method which can help us in the cases where an indeterminate form arises. Such a method exists, and is known as L'Hôpital's rule[^2]:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1)  (L'Hôpital's Rule) </strong></span><p>Let $c, L \in \mathbb{R}$, $\eta > 0$, $D = (c-\eta, c + \eta)\setminus\lbrace c \rbrace,$ and let $f,g: D \to \mathbb{R}$ be differentiable on $D$. Furthermore, suppose that:
  
  * $\lim_{x \to c} f(x) = 0  = \lim_{x \to c} g(x)$
  
  * $g'(x) \neq  0 \;\; \forall x \in D,$ and
  
  * $\lim_{x \to c} \frac{f'(x)}{g'(x)}$ exists.

Then $\lim_{x \to c} \frac{f(x)}{g(x)} = \lim_{x \to c} \frac{f'(x)}{g'(x)}.$

</p></div>\EndKnitrBlock{theorem}

[^1]: Or if you prefer your 17th Century French, de L'Hospital's rule.
[^2]: It's worth mentioning that there are many different statements of this rule. The one given here combines Theorem 2.32 from the lecture notes (which is L'Hôpital for right-handed limits) with a corresponding statement for left-handed limits.

## Higher Order Derivatives

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Higher Order Derivatives) </strong></span><div>Let $a,b \in \mathbb{R}$ with $a < b$, and $f:(a,b) \to \mathbb{R}$. We say that $f$ is $n$-times differentiable at $c \in (a,b)$ if:
  
  * $n=1$: $\lim_{x \to c}\frac{f(x) - f(c)}{x - c}$ exists.

  * $n>1$: There exists $\delta \in (0, b-a)$ such that $f$ is $(n-1)$-times differentiable on $(c - \delta, c + \delta)$ and the $(n-1)$-th derivative function of $f$, $f^{(n-1)}: (c - \delta, c + \delta) \to \mathbb{R}$ is differentiable at $c$.
</div></div>\EndKnitrBlock{definition}
In terms of notation, we have that $$f^{(n)}(x) = \left(f^{(n-1)}\right)'(x) =  f^{\hspace{-0.2cm}\overbrace{\,'\cdots'\,}^{n\; \text{primes}}}\hspace{-0.25cm}(x).$$ The inclusion of brackets here to specify a derivative is really important, as omitting them just gives us $f^n$, which is the product of $f$ with itself $n$ times!

As you've seen, polynomials, $\sin$, $\cos$ and $\exp$ are $n$-times differentiable on $\mathbb{R}$ for all $n \in \mathbb{N}$. These functions are known as smooth. As a result, the function $f:\mathbb{R} \to \mathbb{R}$ given by $$f(x) = \lvert x \rvert \frac{x^n}{(n+1)!}$$ can be differentiated infinitely many times on $\mathbb{R}\setminus\lbrace 0 \rbrace$, but only $n$ times at $x = 0$.

### Conditions for Extrema
Second order derivatives in particular can be quite useful when looking at the extrema of functions. Given a set of candidate extrema (critical points and interval endpoints), we can use the second derivatives to establish some selection criteria to determine whether they are local max or local min points. 

Here, we present the results for local max points of a function $f$ only, as corresponding results for local min points can be deduced by considering $-f$.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Necessary Conditions for Local Maxima) </strong></span><p>Let $a,b \in \mathbb{R}$ with $a<b$. Also, let $p \in (a,b)$, and let $f: (a,b) \to \mathbb{R}$ be differentiable on $(a,b)$ and twice differentiable at $p$. If $p$ is a local max point of $f$, then $f'(p) = 0$, and $f''(p) \leq 0$. 
</p></div>\EndKnitrBlock{theorem}
One thing to note here is that this theorem allows you to discount points from being local maxima --- you cannot use it to say that a point is a local maximum point! To do that, you need the converse of this theorem to hold true, and by considering the function $f:(-1,1) \to \mathbb{R}$, $f(x) = x^3$ at $p=0$, we see that the converse does not hold. 

However, all hope is not lost! A partial converse does hold, which we can use to determine whether a point is a local maximum:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong>(\#thm:thm3)  (Sufficient Conditions for Local Maxima) </strong></span><p>Let $a,b \in \mathbb{R}$ with $a<b$. Also, let $p \in (a,b)$, and let $f: (a,b) \to \mathbb{R}$ be differentiable on $(a,b)$ and twice differentiable at $p$. If $f'(p) = 0$, and $f''(p) < 0$, then $p$ is a local max point of $f$. 
</p></div>\EndKnitrBlock{theorem}

## Taylor's Theorem
This next theorem is quite possibly the most useful[^3] theorem that you'll learn in this course. Simply put, it gives you a way of approximating a complicated function by a polynomial. In maths terms, we have the following:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong>(\#thm:thm4)  (Taylor's Theorem) </strong></span><p>Let $n \in \mathbb{N}$ and $x_0,x \in \mathbb{R}.$ Let $I \subseteq \mathbb{R}$ be an open interval containing $[x_0,x].$ Let $f:I\to\mathbb{R}$ be $(n+1)$-times differentiable on $I$. Then, $\exists c \in (x_0,x)$ such that $$f(x) = \sum_{k = 0}^{n} \frac{f^{(k)}(x_0)}{k!}(x - x_0)^k + R_n,$$ where $$R_n = \frac{f^{(n+1)}(c)}{(n+1)!}(x - x_0)^{n+1}.$$
</p></div>\EndKnitrBlock{theorem}
Here, $R_n$ is a remainder term, and the form above is known as the *Lagrange form* of the remainder[^4]. As an example, we can plot successive Taylor approximations to $\sin$, as is seen in Figure \@ref(fig:sinapx) (Taken from [Wikipedia](By IkamusumeFan - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27865201)). What we find is that even small term Taylor approximations can be quite accurate!

<div class="figure" style="text-align: center">
<img src="sinapx.svg" alt="A diagram illustrating Taylor's Theorem" width="50%" />
<p class="caption">(\#fig:sinapx)Taylor approximations to $\sin(x)$ at $x=0$ of degree 1 (red), 3 (orange), 5 (yellow), 7 (green), 9 (blue), 11 (purple) and 13 (pink).</p>
</div>

So, why is this theorem so useful? Firstly, it allows computers to work with complicated, non-linear functions such as $\exp$ and $\sin$ without losing too much by way of accuracy. Secondly, Taylor's theorem allows us to actually do some analysis on physical systems.


\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong>(\#exm:ex1) </strong></span><div>Consider a pendulum consisting of a mass $m$ connected to a string (under tension) of length $\ell$.

![](./bob.svg)

If you've seen it in MA10236 (Vectors, Vector Calculus and Mechanics), the equation of motion for this system is given by $$\theta'' + \frac{g}{\ell}\sin(\theta) = 0.$$ This is a non-linear differential equation, which we need to solve numerically. However, if we make a 'small angle' approximation, then by Taylor's theorem, $\sin(\theta) \approx \theta$, and the equation becomes $$\theta'' + \frac{g}{\ell}\theta= 0.$$ This is analytically tractable, and --- subject to suitable initial conditions --- we can write down a solution!</div></div>\EndKnitrBlock{example}
Finally, we can also use the expansion in Taylor's Theorem to define differentiation in more than one dimension! If you're interested in how this is done, take [MA20219](https://people.bath.ac.uk/mo221/MA20219/notes.bho/lecturenotes.pdf) (Analysis 2B) next year![^5]   
 
[^3]: In a practical sense, anyway.
[^4]: There is another form, which you may not be surprised to learn is named after Cauchy.
[^5]: The link here will take you to some lecture notes; see Chapter 1 for details.


# Hints
As per usual, here's where you'll find the problem sheet hints!

1) Proof by induction comes to mind here. Make sure you justify the important steps in the proof using course results too!
2) ‘Tutorial Question 2’ from this week’s tutorial should help. I think there might be an example in the lecture notes as well.
3) Since integration has been banned, you’ll have to find another way to relate $g$ to its first and second derivatives. There’s a theorem from this week that’ll certainly help!

 

<!--chapter:end:index.Rmd-->

