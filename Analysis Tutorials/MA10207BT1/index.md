---
title: "Analysis 1B — Tutorial 1"
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
      download: [["Tutorial1.html", "HTML page"], ["Tutorial1.pdf","Standard print PDF"], ["Tutorial1Clear.pdf","Clear print PDF"], ["Tutorial1Large.pdf","Large print PDF"], ["Tutorial1.docx","Accessible Word document"], ["Tutorial1.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
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
Here is the material to accompany the 1st Analysis 1B Tutorial on the 6th February. Alternative formats can be downloaded by clicking the download icon at the top of the page. Please send any comments or corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Lecture Recap
This is somewhat a disingenuous title, as there haven't been any lectures for this unit yet! Instead, we are going to recap some of the material from last semester, which will come in handy for the content you'll see over the next eleven weeks. The material here is quite terse, but should hopefully provide a useful summary of some of the main results. For more details, see the Analysis 1A files from Semester 1.

## Sequences and Convergence

### Definition of Convergence
To begin, we recall the definition of a sequence:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Sequence) </strong></span><div>A sequence of real numbers is a function
\begin{align*}
    a:\; &\mathbb{N} \longrightarrow \mathbb{R},\\
    &n \longmapsto a_n.
\end{align*}</div></div>\EndKnitrBlock{definition}
As you saw last semester, this notation can get pretty annoying, so instead we write a sequence as $(a_n)_{n\in\mathbb{N}}$. If it's clear from the context what set we're indexing over, we can even just write $(a_n)_n$.

Since the natural numbers forms a countably infinite set, a sequence gives us a countably infinite list of real numbers. Sometimes it's interesting to look at the 'long-term' behaviour of this list which leads on to the idea of convergence:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Sequence Convergence) </strong></span><div>A sequence $(a_n)_{n\in\mathbb{N}}$ converges to a real number $L$ as $n \longrightarrow \infty$, written as either $a_n \longrightarrow L$, or $\lim_{n \to \infty}a_n = L$ if $$\forall \epsilon > 0, \; \exists N = N(\epsilon) \in \mathbb{N}, \; \text{such that} \; \forall n \geq N, \; \lvert a_n - L \rvert < \epsilon.$$</div></div>\EndKnitrBlock{definition}
Loosely speaking, this says that no matter how close you want the sequence to get to $L$, you will always be able to find some point in the sequence after which all points in the sequence will be as close to $L$ as desired.

### Tests for Convergence
Using the definition to prove sequence convergence (or otherwise) for every possible sequence is incredibly tedious. So what we really want is some criteria or tests which make these proofs much easier. You'll find some of these tests below.

The first test is the *sandwich* (or *pinching* or *squeeze*) theorem:
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1)  (Sandwich Theorem) </strong></span><p>Suppose that $(a_n)_{n\in\mathbb{N}}\, , \, (b_n)_{n\in\mathbb{N}}\, , \, (c_n)_{n\in\mathbb{N}}$ are real sequences. If $a_n \leq b_n \leq c_n \quad \forall n \in \mathbb{N}$, and $\exists L \in \mathbb{R}$ such that
\begin{align*}
    \lim_{n \to \infty} a_n = L = \lim_{n \to \infty} c_n,
\end{align*}
then $\lim_{n \to \infty}b_n = L$.</p></div>\EndKnitrBlock{theorem}
In words, this says that if you can 'trap' a sequence between two other sequences converging to a common limit, then all three sequences involved will converge to the same limit.

The second test is known as the *Growth Factor Test*, and aims to determine convergence by comparing the ratio of successive terms in a sequence:
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Growth Factor Test) </strong></span><p>Let $(a_n)_{n\in\mathbb{N}}$ be a real sequence with $a_n>0 \; \forall n\in\mathbb{N}$, and with $$\lim_{n\to\infty} \frac{a_{n+1}}{a_n} = r.$$ Then:
  
* If $r < 1$, $a_n \to 0$ as $n \to \infty$.
* If $r > 1$, $a_n \to \infty$ as $n \to \infty$.
* If $r = 1$, the test is inconclusive.
</p></div>\EndKnitrBlock{theorem}
Note that this test won't work if the terms of the sequence $(a_n)_n$ are given by rational functions (i.e. ratios of polynomials). Can you see/prove why?

### Subsequences
The two tests above are great at proving convergence, but is there a quick way of proving non-convergence? As you've seen before, we can do this using subsequences:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong>(\#def:def3)  (Subsequence) </strong></span><div>Let $(a_n)_{n \in \mathbb{N}}$ be a real sequence, and let $(n_k)_{k\in\mathbb{N}}$ be a strictly increasing sequence. Then $(a_{n_k})_{k\in\mathbb{N}}$ is called a subsequence of $(a_n)_{n\in\mathbb{N}}$.</div></div>\EndKnitrBlock{definition}

Using these subsequences to prove non-convergence relies on the contrapositive of the following proposition:
\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1) </strong></span><p>If a real sequence $(a_n)_n$ converges to a limit $L$, then all subsequences $(a_{n_k})_k$ of $(a_n)_n$ also converge to $L$.</p></div>\EndKnitrBlock{proposition}
Namely, **if there exists two subsequences converging to different limits**, then the **original sequence does not converge**!

### Limits Superior and Inferior
It is not always the case that the limit of a sequence exists — take for example the sequence $\left((-1)^n\right)_{n\in\mathbb{N}}.$ But there are two 'limiting' objects which we can still talk about. These are the *limit superior* and *limit inferior* of a sequence, and can be thought of as 'eventual' bounds on a sequence:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def100"><span class="def:def100" custom-style="NameStyle"><strong>(\#def:def100)  (Limits Superior and Inferior) </strong></span><div>For a sequence $(a_n)_{n\in\mathbb{N}}$, we define the limits superior and inferior to be $$\limsup_{n \to \infty} a_n := \lim_{k\to\infty}\sup_{n\geq k}a_n \;\, \text{and} \;\, \liminf_{n \to \infty} a_n := \lim_{k\to\infty}\inf_{n\geq k}a_n.$$ If the sequence $(a_n)_{n\in\mathbb{N}}$ is unbounded above, we say that $\limsup_{n \to \infty} a_n = +\infty$. If $(a_n)_{n\in\mathbb{N}}$ is unbounded below, we set $\liminf_{n \to \infty} a_n = -\infty.$</div></div>\EndKnitrBlock{definition}
Alternatively, we can think of $\limsup_{n\to\infty} a_n$ and $\liminf_{n \to \infty}a_n$ as being the largest and smallest possible limits of any subsequence of $(a_n)_{n\in\mathbb{N}}$ respectively.

## Series and Convergence

### Definitions
The mathematics in this section is nothing new either --- it's really just sequences in disguise. Given a sequence, one thing we can do is add up all the terms and see what happens. This results in the idea of an (infinite) series:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def4"><span class="def:def4" custom-style="NameStyle"><strong>(\#def:def4)  (Series) </strong></span><div>Let $(a_n)_{n \in \mathbb{N}}$ be a real sequence. Then $$\sum_{n = 1}^{\infty} a_n$$ is called a series for $(a_n)_{n\in\mathbb{N}}$.</div></div>\EndKnitrBlock{definition}
So when does this series converge? In other words, when is the object in Definition \@ref(def:def4) a real number? To answer these questions, we have the following definition:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def5"><span class="def:def5" custom-style="NameStyle"><strong>(\#def:def5)  (Series Convergence and Partial Sums) </strong></span><div>Let $(a_n)_{n \in \mathbb{N}}$ be a real sequence. Then $\sum_{n = 1}^{\infty} a_n$ converges if and only if the sequence $(S_N)_{N \in \mathbb{N}}$ converges, where $$S_N:= \sum_{n = 1}^{N} a_n$$ is the $N^{\text{th}}$ partial sum. If $S_N \to \ell$ as $N \to \infty$, we define $$\ell = \sum_{n = 1}^{\infty}a_n.$$</div></div>\EndKnitrBlock{definition}

### Tests for Convergence
Much like with proving sequence convergence, using the definition each time you want to 'evaluate' a series can get tedious really quickly. Therefore, we really want a couple of tests which can prove convergence without too much hassle. The first of these tests involves comparing the sizes of two series, and is aptly known as the comparison test.
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong>(\#thm:thm4)  (Comparison Test) </strong></span><p>Let $(a_n)_n$ and $(b_n)_n$ be real sequences, and suppose that there exists a $M \in \mathbb{N}$ such that $\lvert a_n \rvert \leq b_n \;\forall n \geq M.$
Then, if $\sum_{n = 1}^{\infty} b_n$ is convergent, $\sum_{n = 1}^{\infty} a_n$ is convergent.</p></div>\EndKnitrBlock{theorem}
Naturally, using this, we can also build a test for divergence to $\infty$ out of the comparison test too.

\BeginKnitrBlock{corollary}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-corollary" custom-style="TheoremStyle" id="cor:corol1"><span class="cor:corol1" custom-style="NameStyle"><strong>(\#cor:corol1) </strong></span><p>Let $(a_n)_n$ and $(b_n)_n$ be real sequences. If there exists a $M \in \mathbb{N}$ such that $0 \leq a_n \leq b_n \; \forall n \geq M$, and $\sum_{n = 1}^{\infty} a_n$ diverges, then $\sum_{n = 1}^{\infty} b_n$ diverges.</p></div>\EndKnitrBlock{corollary}

The second test we look at here is similar to the Growth Factor test (Theorem \@ref(thm:thm2)), in that it assesses convergence of a series by examining the ratio of successive terms:
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm5"><span class="thm:thm5" custom-style="NameStyle"><strong>(\#thm:thm5)  (D'Alembert's Ratio Test) </strong></span><p>Let $(a_n)_n$ be a real sequence with $a_n \neq 0 \; \forall n \in \mathbb{N}$. Suppose $$\lim_{n\to\infty}\frac{\lvert a_{n+1}\rvert}{\lvert a_n\rvert} = r.$$ Then:
  
* If $0 \leq r < 1$, $\sum_{n = 1}^{\infty} a_n$ converges.
* If $r > 1$, then $\sum_{n = 1}^{\infty} a_n$ diverges.
* If $r = 1$, the test is inconclusive.
</p></div>\EndKnitrBlock{theorem}
Like the Growth Factor Test, d'Alembert's test fails if the terms of the series are formed of ratios of polynomials.

The final test presented here is applicable when the terms of the series alternate in sign:
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm6"><span class="thm:thm6" custom-style="NameStyle"><strong>(\#thm:thm6)  (Leibniz Alternating Series Test) </strong></span><p>Suppose $(a_n)_{n\in\mathbb{N}}$ is a decreasing sequence tending to $0$ as $n \to \infty$. Then $$\sum_{n=1}^{\infty} (-1)^n a_n$$ is a convergent series. Further, the value of this series lies between $-a_1$ and $a_2 - a_1$.</p></div>\EndKnitrBlock{theorem}


## Sets and Bounds

### Upper and Lower Bounds
The final topic we are going to re-cover here involves sets of real numbers, and deciding on whether we can 'trap' these sets between an upper bound --- which no member of the set can lie above --- and a lower bound --- which no member of the set can lie below. To do this requires a few defintions, which are presented below:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def6"><span class="def:def6" custom-style="NameStyle"><strong>(\#def:def6)  (Upper Bound) </strong></span><div>Let $S \subseteq \mathbb{R}$. Then $M \in \mathbb{R}$ is an upper bound for $S$ if for all $x \in S$, $x \leq M$. In this case, we say $S$ is bounded above.</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def7"><span class="def:def7" custom-style="NameStyle"><strong>(\#def:def7)  (Lower Bound) </strong></span><div>Let $S \subseteq \mathbb{R}$. Then $m \in \mathbb{R}$ is a lower bound for $S$ if for all $x \in S$, $x \geq m$. In this case, we say that $S$ is bounded below.</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def8"><span class="def:def8" custom-style="NameStyle"><strong>(\#def:def8)  (Bounded Set) </strong></span><div>A set $S$ is bounded if it is both bounded above and below. Equivalently, $S$ is bounded if there exists $m, M \in \mathbb{R}$ such that for all $x \in S$, $m\leq x \leq M$.</div></div>\EndKnitrBlock{definition}

### Suprema and Infima
Think about upper bounds for a moment: if we have one, we could ask if there is a smaller number that also bounds the set from above. You might also be tempted to ask what the 'best' upper bound on a set could be, such that no smaller number will bound the set from above. This leads to the ideas of suprema and, analogously for lower bounds, infima:

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def9"><span class="def:def9" custom-style="NameStyle"><strong>(\#def:def9)  (Supremum) </strong></span><div>Let $S \in \mathbb{R}$. A number $T \in \mathbb{R}$ is said to be the supremum of $S$ if it is an upper bound for $S$, and for any other upper bound $M$, $T \leq M$. Here, we write $T = \sup(S)$.</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def10"><span class="def:def10" custom-style="NameStyle"><strong>(\#def:def10)  (Infimum) </strong></span><div>Let $S \in \mathbb{R}$. A number $t \in \mathbb{R}$ is said to be the infimum of $S$ if it is a lower bound for $S$, and for any other lower bound $m$, $t\geq m$. Here, we write $t = \inf(S)$.</div></div>\EndKnitrBlock{definition}

Finally, we state an alternative characterisation of the supremum/infimum of a set.
\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop2"><span class="prp:prop2" custom-style="NameStyle"><strong>(\#prp:prop2) </strong></span><p>Let $S\subseteq\mathbb{R}$. Then a number $T\in\mathbb{R}$ is the supremum of $S$, denoted $\sup(S)$ if: $$\forall \epsilon > 0, \exists s \in S\; \text{such that} \; s > T - \epsilon.$$</p></div>\EndKnitrBlock{proposition}

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop3"><span class="prp:prop3" custom-style="NameStyle"><strong>(\#prp:prop3) </strong></span><p>Let $S\subseteq\mathbb{R}$. Then a number $t\in\mathbb{R}$ is the infimum of $S$, denoted $\inf(S)$ if: $$\forall \epsilon > 0, \exists s \in S\; \text{such that} \; s < t + \epsilon.$$</p></div>\EndKnitrBlock{proposition}

# Hints
In this section, you'll find hints for the current week's problem sheet. Try and have a go without them first, but hopefully these will help you solve the problems.

1) This question is all about sequences!
    a) This one requires you to use the definition, so you can't use any of the tests! 
        i) Remember, if you make the denominator of a fraction smaller, you make the overall fraction larger.
        ii) $\sqrt[4]{n} = \sqrt{\sqrt{n}}$.
    b) Think about which tests you can apply for convergence. As a further hint, one of these sequences converges, and one doesn't.
2) This question is all about series! Think about all the tests you've seen for series convergence, and also, think about some of the series you calculated last semester.
3) This questions is all about sets and bounds!
    a) Before you start calculating the $\sup$,$\inf$, etc., draw a graph --- it'll help you rewrite this set.
    b) Try writing out the first few components of the infinite union, this might suggest whether the set is bounded or not. 
 

<!--chapter:end:index.Rmd-->

