---
title: "Analysis 1A — Tutorial 10"
author: 'Christian Jones: University of Bath'
date: 'December 2022'
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
      download: [["Tutorial10.html", "HTML page"], ["Tutorial10.pdf","Standard print PDF"], ["Tutorial10Clear.pdf","Clear print PDF"], ["Tutorial10Large.pdf","Large print PDF"], ["Tutorial10.docx","Accessible Word document"], ["Tutorial10.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
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
header-includes:
  - \newcommand{\BOO}{BOO}
---
<!-- This is needed since I am working with svg files from mathcha.io. It converts the graphics files to something that can be used in the pdf files. Code taken from https://stackoverflow.com/questions/50165404/how-to-make-a-pdf-using-bookdown-including-svg-images/56044642#56044642 -->

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the 10th Analysis Tutorial on the 12th December. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk).

# Lecture Recap

## Nested Intervals Theorem

### Intervals
Over the last semester, we first studied sequences of numbers, and then we used that theory to study sequences of sums. Now it's time to focus on sequences of sets. In particular, we are going to look at sequences of *intervals*, which are defined as follows:

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Interval) </strong></span><div>Let $S \subseteq \mathbb{R}$. Then $S$ is an interval if $\forall x,y \in S$ with $x \leq y$, and $\forall z \in \mathbb{R}$, $x < z < y$ implies that $z \in S$.</div></div>\EndKnitrBlock{definition}
This definition looks pretty complicated, so we could do with some examples. Firstly, we could construct an interval by taking two real numbers $a$ and $b$ with $a \leq b$, and considering the set $$S_1 = \lbrace s \in \mathbb{R}\; \lvert\; a \leq s \leq b \rbrace.$$ Similarly, since all quantities involved in the definition are real numbers, we also find that $S_2 = \mathbb{R}$ defines an interval. Quite bizarrely, we see via *vacuous reasoning*[^1] that $S_3 = \emptyset$ is also an interval! 

Conversely, sets such as $S_4 = \lbrace 0 \rbrace \cup \lbrace 1 \rbrace$ and $$\mathbb{R}\setminus S_1 = \lbrace s \;\lvert\; s < a \;\; \text{or}\;\; s > b\;\rbrace$$ are not intervals.

### The Theorem!
It turns out that if we have a sequence of intervals $(I_n)_{n\in\mathbb{N}}$ which are nested --- so that $I_{n+1} \subseteq I_n$ for all $n\in\mathbb{N}$ --- we can construct some major theorems in analysis! To do so; however, requires the following result:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1)  (Nested Intervals Theorem) </strong></span><p>Let $(a_n)_{n\in\mathbb{N}}$ and $(b_n)_{n\in\mathbb{N}}$ be real sequences with $a_n \leq b_n$ for all $n\in\mathbb{N}$. Suppose also that for all $n\in\mathbb{N},$ $[a_{n+1},b_{n+1}] \subseteq [a_{n},b_{n}]$. Then $$\bigcap_{n\in\mathbb{N}}[a_n,b_n] \neq \emptyset.$$ Moreover, $$b_n - a_n \to 0 \;\;\text{as $n \to \infty$} \Longrightarrow \exists!\; z \in \bigcap_{n\in\mathbb{N}}[a_n,b_n].$$</p></div>\EndKnitrBlock{theorem}
In words, this theorem says that if we have a sequence of closed[^2], bounded, non-empty, nested intervals of decreasing length, then their intersection is non-empty. If the length of these intervals decreases to zero, then there is a unique[^3] element in this intersection. As you can see, there's a lot of hypotheses for this theorem; Homework Question 1 this week has you going through these hypotheses, and exploring what happens when you remove them.

[^1]: Vacuous reasoning is best summed up with an example. Suppose you were looking into an empty room, and you said that "everybody in that room was staring at their mobile phone". As there were no people in the room to begin with, this ends up being a completely true statement.

[^2]: You may not have seen the definitions of open and closed sets before, so these have been added to a section at the end of this document.

[^3]: This is what the symbol $\exists!$ is referring to --- the exclamation point indicates the unique part of this statement. It is definitely *not* $\exists! = \exists(\exists-1)\ldots(2)(1).$

## Real Functions {#sec1}

### Sequential Continuity
We've finally reached some of the main results in the course, and certainly ones that will carry you into semester two! Until now, you may have thought of a function being *continuous* if you can draw it without taking your pencil off the page, but we can formalise this idea in the below definition:

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Sequential Continuity) </strong></span><div>Let $I \subseteq \mathbb{R}$ and $x_0 \in I$. A function $f: I \to \mathbb{R}$ is sequentially continuous at $x_0$ if for all sequences $(x_n)_{n\in\mathbb{N}}$ in $I$ such that $x_n \to x_0$ as $n \to \infty$, we have that $f(x_n) \to f(x_0)$ as $n \to \infty$.</div></div>\EndKnitrBlock{definition}
This definition looks pretty horrible, but it really amounts to saying that for all convergent sequences in the domain tending to $x_0$, $$\lim_{n\to\infty}f(x_n) = f\left(\lim_{n\to\infty}x_n\right).$$ The main point here is that you need to prove we can swap the limits **for all** sequences converging to $x_0.$ You can't just test it for a specific sequence. This is shown graphically in Figure \@ref(fig:seqcnt).

<div class="figure">
<img src="Seqcnt.svg" alt="A diagram illustrating sequential continuity. As the sequence in the domain converges, so too do the corresponding sequence of function values."  />
<p class="caption">(\#fig:seqcnt)A diagram showing the idea of sequential continuity. Note that as the values of $x_n$ get closer to the limiting value $x_0$, the corresponding values of $f(x_n)$ get closer to a limiting value $f(x_0)$. This property has to hold for all sequences in the domain converging to $x_0$.</p>
</div>


Now, having a definition is all well and good, but how do we use it?
\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong>(\#exm:ex1) </strong></span><div>Prove that the function $f: \mathbb{R} \to \mathbb{R}$ given by $$f(x) = x^{27} - 4x^6 + \frac{3}{x^2 +1}$$ is sequentially continuous at any $x_0 \in \mathbb{R}$.</div></div>\EndKnitrBlock{example}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>First take *any* sequence $(x_n)_{n\in\mathbb{N}}$ in $\mathbb{R}$ such that $x_n \to x_0$ as $n \to \infty$. Then by the Algebra of Limits

\begin{align*}
f(x_n) &= x_n^{27} - 4x_n^{6} + \frac{3}{x_n^2 +1}\\
&\to x_0^{27} - 4x_0^6 + \frac{3}{x_0^2 + 1}\; \; \text{as $n \to \infty$}\\
& = f(x_0) 
\end{align*}
Hence, as the chosen convergent sequence, and $x_0$ was arbitrary, $f$ is sequentially continuous at any $x_0$ in $\mathbb{R}$.</p></div>\EndKnitrBlock{solution}

It's also useful to know how to prove a function isn't sequentially continuous at a point. To this end, we conclude this section with a rather interesting example.
\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex2"><span class="exm:ex2" custom-style="NameStyle"><strong>(\#exm:ex2) </strong></span><div>Prove that the function $g: \mathbb{R} \to \mathbb{R}$ given by $$g(x) = \begin{cases}
0 \quad \text{if} \; x \in \mathbb{R}\setminus\mathbb{Q},\\
1 \quad \text{if} \; x \in \mathbb{Q}.
\end{cases}$$ is not sequentially continuous anywhere on $\mathbb{R}$.</div></div>\EndKnitrBlock{example}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>Fix $x_0 \in \mathbb{R}$. Our aim is to find two sequences $(x_n)_{n\in\mathbb{N}}$ and $(y_n)_{n\in\mathbb{N}}$ converging to $x_0$, such that $\left(g(x_n)\right)_{n\in\mathbb{N}}$ and $\left(g(y_n)\right)_{n\in\mathbb{N}}$ approach different limits. Since both the rational and the irrational numbers are dense in the real numbers, we take $$(x_n)_{n\in\mathbb{N}}\;\; \text{in}\;\; \mathbb{R}\setminus\mathbb{Q} \;\; \text{such that} \;\; x_n \to x_0 \;\; \text{as}\;\; n \to \infty,$$ and $$(y_n)_{n\in\mathbb{N}}\;\; \text{in}\;\; \mathbb{Q} \;\; \text{such that} \;\; y_n \to x_0 \;\; \text{as}\;\; n \to \infty.$$ Now, note that as $n \to \infty,$  $$g(x_n) = 0 \to 0, \quad \text{and} \quad g(y_n) = 1 \to 1.$$ So, no matter the value of $g(x_0)$, we have found a sequence --- either $(x_n)_n$ or $(y_n)_n$ --- such that one of $\left(g(x_n)\right)_n$ or $\left(g(y_n)\right)_n$ does not tend to $g(x_0)$. Hence, $g$ is not sequentially continuous anywhere!</p></div>\EndKnitrBlock{solution}

### Intermediate Value Theorem
Here's the main reason why we needed the Nested Intervals Theorem!

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Intermediate Value Theorem (IVT)) </strong></span><p>Suppose $a,b \in \mathbb{R}$ with $a < b$, and that $f:[a,b] \to \mathbb{R}$ is sequentially continuous. Then, if $y \in \mathbb{R}$ is such that either $f(a) \leq y \leq f(b)$, or $f(b) \leq y \leq f(a)$, then $\exists c \in [a,b]$ such that $f(c) = y$.</p></div>\EndKnitrBlock{theorem}
Diagrammatically, we might be in a situation like in Figure \@ref(fig:ivt). Note that there may be more than one $c$ that fulfills the conclusion of this theorem. Also, the theorem doesn't tell you what this $c$ is; it only says that a $c$ must exist.

<div class="figure">
<img src="ivt.svg" alt="A diagram showing how the intermediate value theorem applies to a sequentially continuous function"  />
<p class="caption">(\#fig:ivt)This function is sequentially continuous on $[a,b]$, and for $y$ as in the diagram, $y$ lies between $f(a)$ and $f(b)$. Hence the IVT applies, and so there exists $c$ in the interval $[a,b]$ such that $f(c)=y$. In this scenario, $c$ can be any one of $c_1,c_2$ or $c_3$.</p>
</div>

The IVT is very good for proving existence of square roots (and roots of any degree!), proving that functions have zeros, and proving that at any given point in time, there exists two points on the equator with exactly the same temperature[^4].

[^4]: On an idealised Earth, anyway.

# Hints
As per usual, here’s where you’ll find the problem sheet hints! There's no official hand in this week, but I'll still mark anything handed in by Friday. The questions on this problem sheet are sort of split into two groups. The first two questions are all about theorem hypotheses (and are definitely worth thinking about!) In a way, the third question is about theorem hypotheses too. Question 4 is a more standard example, mainly to check you can perform power series calculations.

* [H1.] Primarily, the idea is to think of an interval that fits the given description, and explain why the conclusion of the theorem doesn't hold. A word of warning, the empty set $\emptyset$ is a closed set.
* [H2.] Pretty much the same idea as H1. The examples required won't necessarily be complicated functions. My best advice is to just play around with this question.
* [H3.] Check the hypotheses of the Intermediate Value Theorem are satisfied by the given function.
* [H4.] Look back over the examples from last week, or the first tutorial question from this week.

# Sets
This week, we've been exposed to a fair few definitions regarding sets, some of which come up a fair bit on the problem sheet. The precise definitions of open and closed sets are non-examinable, but you'll need to be aware of some examples for the exam.  

## Dense Sets
We begin with the concept of a *dense set*.
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong>(\#def:def3)  (Dense Set) </strong></span><div>Let $S \subseteq \mathbb{R}$. A subset $T$ of $S$ is dense in $S$ if $$\forall s \in S \;\;\text{and}\;\; \forall \epsilon > 0,\; \exists t \in T \;\; \text{such that}\;\; \lvert s - t \rvert < \epsilon.$$</div></div>\EndKnitrBlock{definition}
Loosely, this says that we can approximate members of $S$ pretty well by using members of $T$ instead. For example, you've seen in lectures that the rational numbers $\mathbb{Q}$ are dense in the real numbers $\mathbb{R}$. Equally, we can use this to show that the irrational numbers $\mathbb{R}\setminus\mathbb{Q}$ are dense in $\mathbb{R}$ too! A useful proposition arising from this is the following:

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1) </strong></span><p>Let $T \subseteq S$ be dense in $S$. Then, for all $x_0 \in S$, there exists a sequence $(x_n)_n$ in $T$ such that $(x_n)_n$ converges to $x_0$ in $S$.</p></div>\EndKnitrBlock{proposition}
This is the property that we used in Example \@ref(exm:ex2) of Section \@ref(sec1) to generate our convergent sequences! Note that the convergence has to be in $S$, since $x_0$ may not be in $T$ (take for example the sequence $1, 1.4, 1.41,\ldots$ in $\mathbb{Q}$ converging to $\sqrt{2}$.)

## Open and Closed Sets
The next two concepts we discuss here go hand-in-hand, and are quite important for the Nested Intervals Theorem (Theorem \@ref(thm:thm1)) and the Intermediate Value Theorem (Theorem \@ref(thm:thm2)). We first discuss *open sets*.

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def4"><span class="def:def4" custom-style="NameStyle"><strong>(\#def:def4)  (Open Set) </strong></span><div>Let $S \subseteq \mathbb{R}$. Then $S$ is open if $$\forall s \in S, \exists \epsilon > 0 \;\; \text{such that} \;\; (s-\epsilon,s+\epsilon) \subseteq S.$$</div></div>\EndKnitrBlock{definition}
Some examples here would be useful. Working in $\mathbb{R}$:

* For any $a,b \in \mathbb{R}$ with $a < b$ the interval $(a,b) = \lbrace x \;\lvert\; a < x < b \rbrace$ is open, because for any $s \in (a,b)$, taking $\epsilon = \min\left\lbrace s-a, b-s\right\rbrace$, we find that $(s-\epsilon, s + \epsilon) \subseteq (a,b)$.
* Intervals of the form $(a, \infty)$ or $(-\infty, a)$ are open.
* $\mathbb{R}$ is open.
* The empty set $\emptyset$ is open (!!)

The last of these is vacuously true — since there's no elements in the empty set, the statement is automatically true. We can use the concept of an open set to define a closed set[^5].

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def5"><span class="def:def5" custom-style="NameStyle"><strong>(\#def:def5)  (Closed Set) </strong></span><div>Let $S \subseteq \mathbb{R}$. Then $S$ is closed if its complement $\mathbb{R}\setminus S$ is open. </div></div>\EndKnitrBlock{definition}
Again, some examples are in order. Working in $\mathbb{R}$:

* For any $a,b \in \mathbb{R}$ with $a < b$ the interval $[a,b] = \lbrace x \;\lvert\; a \leq x \leq b \rbrace$ is closed. This is because $$\mathbb{R}\setminus[a,b] = (-\infty,a)\cup(b,\infty),$$ which is a union of open sets, hence open.
* Intervals of the form $[a, \infty)$ or $(-\infty, a]$ are closed.
* $\mathbb{R}$ is closed.
* The empty set $\emptyset$ is closed.

#### Warnings! {-}
These next few words are hardly inventive, but we need to mention it: **sets are not doors**! If a set is not open, we can't automatically conclude that it is closed (and vice versa). Similarly, sets can be both open and closed simultaneously. We finish on some examples to illustrate this:

For any $a,b \in \mathbb{R}$ with $a < b$:

* the interval $(a,b)$ is open, but *not* closed.
* the interval $[a,b]$ is closed, but *not* open.
* the intervals $(a,b]$ and $[a,b)$ are neither open or closed.
* the sets $\emptyset$ and $\mathbb{R}$ are both open and closed.


[^5]: We could instead define 'closed-ness' in terms of sequences, but for brevity we defer this to Analysis 2A.
