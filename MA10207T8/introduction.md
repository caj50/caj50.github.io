---
title: "Analysis 1A — Tutorial 8"
author: 'Christian Jones: University of Bath'
date: 'November 2022'
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
      download: [["Notes.html", "HTML page"], ["Notes.pdf","Standard print PDF"], ["NotesClear.pdf","Clear print PDF"], ["NotesLarge.pdf","Large print PDF"], ["Notes.docx","Accessible Word document"], ["Notes.epub","Accessible EPub book" ]]
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
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
    pandoc_args: --default-image-extension=svg
  clavertondown::epub_clav:
    toc: false
    pandoc_args: --default-image-extension=svg
header-includes:
  - \newcommand{\BOO}{BOO}
---

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the 8th Analysis Tutorial on the 28th November. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk)

# Lecture Recap

## Series Convergence
Recall from last week that we can define the convergence of an infinite sum/series as follows:

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Series Convergence and Partial Sums) </strong></span><div>Let $(a_n)_{n \in \mathbb{N}}$ be a real sequence. Then $\sum_{n = 1}^{\infty} a_n$ converges if and only if the sequence $(S_N)_{N \in \mathbb{N}}$ converges, where $$S_N:= \sum_{n = 1}^{N} a_n$$ is the $N$\textsuperscript{th} partial sum. If $S_N \to \ell$ as $N \to \infty$, we define $$\ell = \sum_{n = 1}^{\infty}a_n.$$</div></div>\EndKnitrBlock{definition}
Much like with proving sequence convergence, using the definition each time you want to `evaluate' a series can get tedious really quickly. Therefore, we really want a couple of tests which can prove convergence without too much hassle. Before we discuss these tests though, we need to introduce the ideas of *absolute and conditional convergence*.

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Absolute Convergence) </strong></span><div>A real series $\sum_{n = 1}^{\infty} a_n$ is absolutely convergent if $\sum_{n = 1}^{\infty} \lvert a_n \rvert$ converges.</div></div>\EndKnitrBlock{definition}
For example, if we consider the series $\sum_{n = 1}^{\infty} a_n$, where $a_n$ is given by $$a_n = \frac{(-1)^n}{n^2},$$ we find that $$\sum_{n = 1}^{\infty} \lvert a_n \rvert = \sum_{n=1}^{\infty} \frac{1}{n^2},$$ which we know converges from lectures[^1]. Hence $\sum_{n = 1}^{\infty} a_n$ is absolutely convergent. Have we learnt anything about the convergence of $\sum_{n=1}^{\infty}a_n$ here? Turns out the answer is yes, and this is because of the following result.

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1) </strong></span><p>If a real series $\sum_{n = 1}^{\infty} a_n$ is absolutely convergent, then it is convergent.</p></div>\EndKnitrBlock{proposition}
At this stage, we can introduce the idea of conditional convergence too.

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong>(\#def:def3)  (Conditional Convergence) </strong></span><div>Let $\sum_{n = 1}^{\infty} a_n$ be a real series. If $\sum_{n = 1}^{\infty} a_n$ is convergent, but $\sum_{n = 1}^{\infty} \lvert a_n \rvert$ is not, then $\sum_{n = 1}^{\infty} a_n$ is said to be conditionally convergent.</div></div>\EndKnitrBlock{definition}

[^1]: If you take the *Vector Calculus and PDEs* module next year, you'll show that this sum equals $\frac{\pi^2}{6}$.

### Series Rearrangement
So, what can we do with absolutely convergent series?
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1) </strong></span><p>Suppose $\sum_{n = 1}^{\infty} a_n$ is an absolutely convergent series, and that $\sigma: \mathbb{N} \to \mathbb{N}$ is a bijection. Then $\sum_{n = 1}^{\infty} a_{\sigma(n)}$ is also an absolutely convergent series, and $$\sum_{n = 1}^{\infty} a_n = \sum_{n = 1}^{\infty} a_{\sigma(n)}.$$</p></div>\EndKnitrBlock{theorem}
This theorem tells us that for an absolutely convergent series, we can order the terms any way we like, and still reach the same value for the series. At this point, you might be interested to know what happens if we don't have absolute convergence. Long story short, weird things can happen, as is seen in the following theorem.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Riemann Rearrangement Theorem) </strong></span><p>Suppose $\sum_{n = 1}^{\infty} a_n$ is conditionally convergent. Then, for any $\alpha \in \mathbb{R}$, or $\alpha = \pm\infty$, there exists a bijection $\sigma:\mathbb{N} \to \mathbb{N}$ such that $$\sum_{n = 1}^{\infty} a_{\sigma(n)} = \alpha.$$</p></div>\EndKnitrBlock{theorem}
So what we see here is that we really need to be careful in which order we sum up the terms of a conditionally convergent series!

## Tests for Convergence
Now that we have the idea of absolute convergence, we can state some convergence tests applicable to series.

### Comparison Test
The first of these tests involves comparing the sizes of two series, and is aptly known as the comparison test.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong>(\#thm:thm3)  (Comparison Test) </strong></span><p>Let $(a_n)_n$ and $(b_n)_n$ be real sequences, and suppose that there exists a $M \in \mathbb{N}$ such that $\lvert a_n \rvert \leq b_n \;\forall n \geq M.$
Then, if $\sum_{n = 1}^{\infty} b_n$ is convergent, $\sum_{n = 1}^{\infty} a_n$ is convergent.</p></div>\EndKnitrBlock{theorem}
Naturally, using this, we can also build a test for divergence to $\infty$ out of the comparison test too.

\BeginKnitrBlock{corollary}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-corollary" custom-style="TheoremStyle" id="cor:corol1"><span class="cor:corol1" custom-style="NameStyle"><strong>(\#cor:corol1) </strong></span><p>Let $(a_n)_n$ and $(b_n)_n$ be real sequences. If there exists a $M \in \mathbb{N}$ such that $0 \leq a_n \leq b_n \; \forall n \geq M$, and $\sum_{n = 1}^{\infty} a_n$ diverges, then $\sum_{n = 1}^{\infty} b_n$ diverges.</p></div>\EndKnitrBlock{corollary}
Here, we require the $a_n$ values to be non-negative to force any divergence of $\sum_{n = 1}^{\infty} a_n$ to be to $\infty$. If we allowed, say, $a_n = (-1)^nn$, then $\sum_{n = 1}^{\infty} a_n$ would diverge without limit, making this divergence test useless.

### D'Alembert's Ratio Test
This one is quite similar to the growth factor test for sequences, except that due to the idea of absolute convergence (and Proposition \@ref(prp:prop1)), the terms of the series only have to be non-zero:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong>(\#thm:thm4)  (D'Alembert's Ratio Test) </strong></span><p>Let $(a_n)_n$ be a real sequence with $a_n \neq 0 \; \forall n \in \mathbb{N}$. Suppose $$\lim_{n\to\infty}\frac{\lvert a_{n+1}\rvert}{\lvert a_n\rvert} = r.$$ Then:
  
* If $0 \leq r < 1$, $\sum_{n = 1}^{\infty} a_n$ converges.
* If $r > 1$, then $\sum_{n = 1}^{\infty} a_n$ diverges.
* If $r = 1$, the test is inconclusive.
</p></div>\EndKnitrBlock{theorem}
To see why the test fails for $r = 1$, consider the three series: $$\sum_{n = 1}^{\infty} \frac{(-1)^{n+1}}{n^2}, \quad \sum_{n = 1}^{\infty} \frac{(-1)^{n+1}}{n} \;\; \text{and} \;\; \sum_{n = 1}^{\infty} (-1)^{n+1}.$$ The first is absolutely convergent, the second is conditionally convergent and the third diverges without any limit at all!

### Cauchy Condensation Test
The final test we're going to look at here is yet another thing named after Cauchy! This one is very good when the terms of a series involve logarithms, and can also be used to show that $$\sum_{n = 1}^{\infty} \frac{1}{n^{\alpha}} \;\;\text{converges} \Longleftrightarrow \alpha > 1.$$

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm5"><span class="thm:thm5" custom-style="NameStyle"><strong>(\#thm:thm5)  (Cauchy) </strong></span><p>Assume $(a_n)_n$ satisfies $a_n \geq 0 \; \forall n \in \mathbb{N}$, and is a decreasing sequence. For $k \in \mathbb{N}$, define $b_k := 2^ka_{2^k}$. Then $$\sum_{n = 1}^{\infty} a_n \;\; \text{converges}\; \Longleftrightarrow\; \sum_{k = 1}^{\infty} b_k \;\; \text{converges}.$$</p></div>\EndKnitrBlock{theorem}

We conclude here with a [link](https://math.stackexchange.com/questions/2071016/does-sum-infty-3-fracn2lnlnnlnn-converge?rq=1) to an example of the Cauchy condensation test in practice. It's highly unlikely you'll ever get something like this in the exam, but the numbers involved are so ridiculous it's worth including here nonetheless!

# Hints
As per usual, here's where you'll find the problem sheet hints!

* [H1.] Think about all the methods you know for proving whether a series converges. Some of the methods from the tutorial may come in handy...
* [H2.] Pretty much the same as homework question 1. However...
    * [H2b.] I've got a few pointers for this one. Make sure you know how the binomial coefficient is defined. Also, try to avoid expanding any unnecessary brackets — if you're writing $n^3, n^4$ etc. in your solutions, you're putting in more effort than needed!
* [H3.] This one is only slightly more involved. Know your definitions, and again, think of possible convergence tests to apply.
