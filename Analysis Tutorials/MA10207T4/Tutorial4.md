---
title: "Analysis 1A — Tutorial 4"
author: 'Christian Jones: University of Bath'
date: 'October 2023'
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
  clavertondown::epub_clav:
    toc: false
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
  clavertondown::gitbook_clav:
    split_by: section
    keep_md: true
    config:
      download: [["Tutorial4.html", "HTML page"], ["Tutorial4.pdf","Standard print PDF"], ["Tutorial4Clear.pdf","Clear print PDF"], ["Tutorial4Large.pdf","Large print PDF"], ["Tutorial4.docx","Accessible Word document"], ["Tutorial4.epub","Accessible EPub book" ]]
      sharing: no
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
Here is the material to accompany the Analysis Tutorial in Week 4. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Lecture Recap

## Suprema and Infima
Hopefully by now you're getting more familiar with the ideas of set bounds, especially the idea of suprema/infima! It also turns out that there's an alternative characterisation of suprema and infima which can be very useful, especially if the members of a set aren't indexed by natural numbers. Technically, this is something that came up in last week's lectures, but is more relevant to this week's problem sheet (see Tutorial Question 1).

\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong><span id="prp:prop1"></span>Proposition 1.1  </strong></span><p>Let $S\subseteq\mathbb{R}$. Then a number $T\in\mathbb{R}$ is the supremum of $S$, denoted $\sup(S)$ if: $$\forall \epsilon > 0, \exists s \in S\; \text{such that} \; s > T - \epsilon.$$</p></div>\EndKnitrBlock{proposition}

\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop2"><span class="prp:prop2" custom-style="NameStyle"><strong><span id="prp:prop2"></span>Proposition 1.2  </strong></span><p>Let $S\subseteq\mathbb{R}$. Then a number $t\in\mathbb{R}$ is the infimum of $S$, denoted $\inf(S)$ if: $$\forall \epsilon > 0, \exists s \in S\; \text{such that} \; s < t + \epsilon.$$</p></div>\EndKnitrBlock{proposition}
As an example, take the set $S = (-1,2] = \lbrace x \, \lvert\, -1 < x \leq 2\rbrace$, and fix some $\epsilon > 0$. Then, if we take $s_1 = 2 - \epsilon/2$ and $s_2 = -1 + \epsilon/2$, we see that

* $s_1$ and $s_2$ are in the set $S$,
* $s_1 > 2 - \epsilon$, and
* $s_2 < -1 + \epsilon$.

Hence, as $\epsilon$ was arbitrary, the alternative characterisation of suprema and infima says that $\sup(S) = 2$ and $\inf(S) = -1$.

## Complex Numbers
Up until this point, we have only looked at numbers which are subsets of the real numbers ($\mathbb{R}$) However, to steal an archetypal example, how do we solve an equation like $x^2 + 1 = 0$? We can't do this in the reals, so we 'invent' a solution by defining $i:=\sqrt{-1}.$ This gives us a new set of numbers, namely $$\mathbb{C}:= \lbrace a + ib \;\lvert\; a,b\in\mathbb{R}\rbrace,$$ and call members of this set **complex numbers**. There is a ton of theory on these numbers, which is left for the lecture notes.[^1] Instead, we just repeat a list of important definitions, and one important result.

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def0"><span class="def:def0" custom-style="NameStyle"><strong><span id="def:def0"></span>Definition 1.1   (Complex Numbers) </strong></span><div>Given a complex number $z = a + ib,$ we define the following quantities:
  
  i) The real part of $z$ is $\mathcal{R}(z) := a.$
  ii) The imaginary part of $z$ is $\mathcal{I}(z) := b.$
  iii) The complex conjugate of $z$ is $\bar{z}:= a - ib.$
  iv) The modulus of $z$ is defined to be $\lvert z \rvert := \sqrt{a^2 + b^2}.$
</div></div>\EndKnitrBlock{definition}
Just like the absolute value on the real numbers, the modulus defines a *distance* on the complex numbers.[^2] In particular for complex numbers $z_1$ and $z_2$, the quantity $\lvert z_1 - z_2 \rvert$ tells us how 'far apart' the two numbers are. Plotting these numbers on an Argand diagram, we see that $\lvert z_1 - z_2 \rvert$ gives us the distance of the straight line joining $z_1$ and $z_2.$

Since the modulus defines a distance on $\mathbb{C},$ it had better obey the triangle inequality. Luckily for us, it does!

\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop3"><span class="prp:prop3" custom-style="NameStyle"><strong><span id="prp:prop3"></span>Proposition 1.3   (Triangle Inequality) </strong></span><p>For $z_1,z_2 \in \mathbb{C}$,
$$\begin{align*}
\lvert z_1 + z_2 \rvert \leq \lvert z_1 \rvert + \lvert z_2 \rvert.
\end{align*}</p></div>\EndKnitrBlock{proposition}


[^1]: We could even spend the entire semester studying complex analysis instead of real analysis, but that adds a whole other layer of --- for want of a better word --- complexity. Having two dimensions to deal with instead of one causes a whole raft of issues!
[^2]: The more technical term is that the modulus defines a *metric* on $\mathbb{C}.$ You'll see more of this next year, but if you're interested, see the section on metrics in this document!

## Sequences and Convergence
We're finally onto the first main topic of this course! To discuss anything from this point, we need to introduce the idea of a sequence.
\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong><span id="def:def1"></span>Definition 1.2   (Sequence) </strong></span><div>A sequence of real/complex numbers is a function
$$\begin{align*}
    a:\; &\mathbb{N} \longrightarrow X,\\
    &n \longmapsto a_n,
\end{align*}$$
where $X$ is either $\mathbb{R}$ or $\mathbb{C}$ respectively.</div></div>\EndKnitrBlock{definition}
Since this notation can get kind of annoying, we instead denote a sequence by $(a_n)_{n\in\mathbb{N}}$. If it's clear from the context what set we're indexing over, we can even just simply write a sequence as $(a_n)_n$.

Now, this gives us an infinitely long list of real numbers, and sometimes its interesting to look at the 'long-term' behaviour of these lists. This gives rise to the idea of convergence.

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong><span id="def:def2"></span>Definition 1.3   (Sequence Convergence) </strong></span><div>A sequence $(a_n)_{n\in\mathbb{N}}$ converges to a real number $L$ as $n \longrightarrow \infty$, written as either $a_n \longrightarrow L$, or $\lim_{n \to \infty}a_n = L$ if $$\forall \epsilon > 0, \; \exists N = N(\epsilon) \in \mathbb{N}, \; \text{such that} \; \forall n \geq N, \; \lvert a_n - L \rvert < \epsilon.$$</div></div>\EndKnitrBlock{definition}
Loosely speaking, this says that no matter how close you want the sequence to get to $L$, you will always be able to find some point in the sequence after which all points in the sequence will be as close to $L$ as you wanted. For an example of this, have a look at this [Desmos link](https://www.desmos.com/calculator/dfkjgg0wzj). For $\epsilon = 0.5$ and $L = 3$, you can see that every member of the sequence after the $11^{th}$ lies within a strip of width $2\epsilon$ around $L$. Have a go at messing with the value of $\epsilon$!

Something else we can mention for the definition is its *negation*. Specifically, a sequence $(a_n)_n$ does not converge to $L$ if
$$\begin{align*}
    \exists\; \epsilon_0 > 0, \; \text{such that} \; \forall N \in \mathbb{N}, \exists n \geq N \; \text{such that} \; \lvert a_n - L \rvert \geq \epsilon_0.
\end{align*}$$

We can say the exact same things for the convergence of complex sequences without much effort too. We just need to remember to change the distance from the absolute value to the modulus!

### Useful Sequences
Since there's no point in having a definition without using it, it's a great idea to obtain some (straightforward) results:

* As $n \longrightarrow \infty$: $$\frac{1}{n} \longrightarrow 0.$$
* For a real number $c$: as $n \longrightarrow \infty$, $$c \longrightarrow c.$$
* For $q \in \mathbb{R}$ with $\lvert q \rvert < 1$: as $n \longrightarrow \infty$ $$q^n \longrightarrow 0.$$

## Metric Spaces (Non-examinable)
Have you noticed that both the absolute value on the real numbers and the modulus on the complex numbers behave suspiciously alike? They even have the same notation! This is because they're both examples of *metrics* on a set:

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong><span id="def:def3"></span>Definition 1.4   (Metric Space) </strong></span><div>A metric space $(X,d)$ consists of a set $X$ together with a function $d: X\times X \to \mathbb{R}$ satisfying $\forall x,y,z \in X:$ 
  
i) Non-negativity: $d(x,y) \geq 0,$
ii) $d(x,y) = 0 \; \Leftrightarrow x = y,$
iii) Symmetry: $d(x,y) = d(y,x),$
iv) Triangle Inequality: $d(x,z) \leq d(x,y) + d(y,z).$
  </div></div>\EndKnitrBlock{definition}

As we've seen, $(\mathbb{R}, \lvert \cdot \rvert)$ and $(\mathbb{C}, \lvert \cdot \rvert)$ both define metric spaces. The existence of this definition suggests that we can define the distance between two members of a set in different ways! For example, thinking about the complex numbers $X = \mathbb{C},$ with complex numbers $z_1 = a_1 + ib_1$ and $z_2 = a_2 + ib_2,$ we could instead look at:

*  The discrete metric $$d(z_1,z_2) = \begin{cases} 1 \quad \text{if $z_1=z_2$},\\
0 \quad \text{otherwise}\end{cases}$$
*  The $p$-norm: $$d(z_1,z_2) = \left(\lvert a_1-a_2\rvert^p + \lvert b_1-b_2\rvert ^p\right)^{1/p},\;\; 1\leq p < \infty.$$
*  The $\infty$-norm: $$d(z_1,z_2) = \max\left\lbrace \lvert a_1 - a_2 \rvert, \lvert b_1 - b_2 \rvert\right\rbrace.$$

These last two are called norms because they satisfy some additional properties, but don't worry about these until next year! It's an interesting thing to look at what the unit circle looks like under the $1$-norm (blue), $2$-norm (red) and $\infty$-norm (green). The complex numbers used here are $z_1 = x + iy$ and $z_2$=0:

<!--<iframe src="https://www.desmos.com/calculator/vy8zsbn3kr?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>-->
![](unitcircle.png)

We can even look at defining distances on other sets. For example, consider the set $X =  C^{0}([a,b])$, which is the set of all continuous functions $f:[a,b] \to \mathbb{R}.$[^3] One way we can define the distance between two functions $f$ and $g$ is to consider evaluating them at all members of the domain, and finding what the maximum deviation between the two are. This gives rise to a metric $d:X\times X \to \mathbb{R},$ namely $$d(f,g) := \max_{x \in [a,b]} \lvert f(x) - g(x) \rvert.$$ Have a go at proving that this is a metric!

### Convergence
In a similar way, have you noticed that the definitions of convergence for a real/complex sequence are pretty much identical? Again, this is because we can generalise the definition of convergence to metric spaces!

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def4"><span class="def:def4" custom-style="NameStyle"><strong><span id="def:def4"></span>Definition 1.5   (Convergence) </strong></span><div>Let $(X,d)$ be a metric space, let $a \in X$ and let $(a_n)_{n\in\mathbb{N}}$ be a sequence in $X$. Then $(a_n)_{n\in\mathbb{N}}$ converges to $a$ if $$\forall \epsilon > 0, \; \exists N = N(\epsilon) \in \mathbb{N}, \; \text{such that} \; \forall n \geq N, \; d(a_n,a) < \epsilon.$$</div></div>\EndKnitrBlock{definition}

This is a huge generalisation of Definition <a href="#def:def2">1.3</a>, and you'll meet it properly in Analysis 2A next year! 

[^3]: For the time being, think of these functions as ones that you can draw without lifting your pen off the page.






# Hints
As per usual, here's where you'll find the problem sheet hints!

1. Use the definition! Try and follow a similar format to what we did in tutorials. Make sure to write things logically, and ensure that you've satisfied each part of the definition.
2. Again, this is an exercise in using the definition of convergence. 
3. Without loss of generality, assume that $\lvert z_1 \rvert  \geq \lvert z_2 \rvert.$ The advice here is that if you ever get stuck in Analysis, either add $0$, or multiply by $1$ in a clever way. Try and do one of these tricks to allow you to apply the triangle inequality.
4. a) This is an *if and only if* statement, so there are two things to prove! Try and manipulate the definition of convergence for one side of the $\Leftrightarrow$ statement to resemble the other.
   b) Recall what it means for a complex number to be in modulus-argument form.
   c) Definition again, and follow the hint on the sheet.
   d) I'll leave this to you! Think simple!
5. For a) and b), De Moivre's Theorem will come in handy! For c), when bounding, remember that if you make a denominator smaller, the whole fraction will get bigger.

<!--chapter:end:index.Rmd-->

