---
title: "Analysis 1A — Tutorial 9"
author: 'Christian Jones: University of Bath'
date: 'November 2023'
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
  clavertondown::html_clav:
    toc: true
    pandoc_args: --default-image-extension=svg
header-includes:
  - \newcommand{\BOO}{BOO}
  - \usepackage {hyperref}
  - \hypersetup {colorlinks = true, linkcolor = blue, urlcolor = blue}
---

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the Analysis Tutorial in Week 9. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Lecture Recap

## Series Convergence
Recall from last week that we can define the convergence of an infinite sum/series as follows:

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong><span id="def:def1"></span>Definition 1.1   (Series Convergence and Partial Sums) </strong></span><div>Let $(a_n)_{n \in \mathbb{N}}$ be a real sequence. Then $\sum_{n = 1}^{\infty} a_n$ converges if and only if the sequence $(S_N)_{N \in \mathbb{N}}$ converges, where $$S_N:= \sum_{n = 1}^{N} a_n$$ is the $N^{\text{th}}$ partial sum. If $S_N \to \ell$ as $N \to \infty$, we define $$\ell = \sum_{n = 1}^{\infty}a_n.$$</div></div>\EndKnitrBlock{definition}
Much like with proving sequence convergence, using the definition each time you want to `evaluate' a series can get tedious really quickly. Therefore, we really want a couple of tests which can prove convergence without too much hassle. Before we discuss these tests though, we need to introduce the ideas of *absolute and conditional convergence*.

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong><span id="def:def2"></span>Definition 1.2   (Absolute Convergence) </strong></span><div>A real series $\sum_{n = 1}^{\infty} a_n$ is absolutely convergent if $\sum_{n = 1}^{\infty} \lvert a_n \rvert$ converges.</div></div>\EndKnitrBlock{definition}
For example, if we consider the series $\sum_{n = 1}^{\infty} a_n$, where $a_n$ is given by $$a_n = \frac{(-1)^n}{n^2},$$ we find that $$\sum_{n = 1}^{\infty} \lvert a_n \rvert = \sum_{n=1}^{\infty} \frac{1}{n^2},$$ which we know converges from lectures[^1]. Hence $\sum_{n = 1}^{\infty} a_n$ is absolutely convergent. Have we learnt anything about the convergence of $\sum_{n=1}^{\infty}a_n$ here? Turns out the answer is yes, and this is because of the following result.

\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong><span id="prp:prop1"></span>Proposition 1.1  </strong></span><p>If a real series $\sum_{n = 1}^{\infty} a_n$ is absolutely convergent, then it is convergent.</p></div>\EndKnitrBlock{proposition}
At this stage, we can introduce the idea of conditional convergence too.

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong><span id="def:def3"></span>Definition 1.3   (Conditional Convergence) </strong></span><div>Let $\sum_{n = 1}^{\infty} a_n$ be a real series. If $\sum_{n = 1}^{\infty} a_n$ is convergent, but $\sum_{n = 1}^{\infty} \lvert a_n \rvert$ is not, then $\sum_{n = 1}^{\infty} a_n$ is said to be conditionally convergent.</div></div>\EndKnitrBlock{definition}

[^1]: If you take the *Vector Calculus and PDEs* module next year, you'll show that this sum equals $\frac{\pi^2}{6}$.

### Series Rearrangement
So, what can we do with absolutely convergent series?
\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong><span id="thm:thm1"></span>Theorem 1.2  </strong></span><p>Suppose $\sum_{n = 1}^{\infty} a_n$ is an absolutely convergent series, and that $\sigma: \mathbb{N} \to \mathbb{N}$ is a bijection. Then $\sum_{n = 1}^{\infty} a_{\sigma(n)}$ is also an absolutely convergent series, and $$\sum_{n = 1}^{\infty} a_n = \sum_{n = 1}^{\infty} a_{\sigma(n)}.$$</p></div>\EndKnitrBlock{theorem}
This theorem tells us that for an absolutely convergent series, we can order the terms any way we like, and still reach the same value for the series. At this point, you might be interested to know what happens if we don't have absolute convergence. Long story short, weird things can happen, as is seen in the following theorem.

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong><span id="thm:thm2"></span>Theorem 1.3   (Riemann Rearrangement Theorem) </strong></span><p>Suppose $\sum_{n = 1}^{\infty} a_n$ is conditionally convergent. Then, for any $\alpha \in \mathbb{R}$, or $\alpha = \pm\infty$, there exists a bijection $\sigma:\mathbb{N} \to \mathbb{N}$ such that $$\sum_{n = 1}^{\infty} a_{\sigma(n)} = \alpha.$$</p></div>\EndKnitrBlock{theorem}
So what we see here is that we really need to be careful in which order we sum up the terms of a conditionally convergent series!

## Tests for Convergence
Now that we have the idea of absolute convergence, we can state some convergence tests applicable to series.

### Comparison Test
The first of these tests involves comparing the sizes of two series, and is aptly known as the comparison test.

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong><span id="thm:thm3"></span>Theorem 1.4   (Comparison Test) </strong></span><p>Let $(a_n)_n$ and $(b_n)_n$ be real sequences, and suppose that there exists a $M \in \mathbb{N}$ such that $\lvert a_n \rvert \leq b_n \;\forall n \geq M.$
Then, if $\sum_{n = 1}^{\infty} b_n$ is convergent, $\sum_{n = 1}^{\infty} a_n$ is convergent.</p></div>\EndKnitrBlock{theorem}
Naturally, using this, we can also build a test for divergence to $\infty$ out of the comparison test too.

\BeginKnitrBlock{corollary}<div class="bookdown-corollary" custom-style="TheoremStyleUpright" id="cor:corol1"><span class="cor:corol1" custom-style="NameStyle"><strong><span id="cor:corol1"></span>Corollary 1.1  </strong></span><p>Let $(a_n)_n$ and $(b_n)_n$ be real sequences. If there exists a $M \in \mathbb{N}$ such that $0 \leq a_n \leq b_n \; \forall n \geq M$, and $\sum_{n = 1}^{\infty} a_n$ diverges, then $\sum_{n = 1}^{\infty} b_n$ diverges.</p></div>\EndKnitrBlock{corollary}
Here, we require the $a_n$ values to be non-negative to force any divergence of $\sum_{n = 1}^{\infty} a_n$ to be to $\infty$. If we allowed, say, $a_n = (-1)^nn$, then $\sum_{n = 1}^{\infty} a_n$ would diverge without limit, making this divergence test useless.

### D'Alembert's Ratio Test
This one is quite similar to the growth factor test for sequences, except that due to the idea of absolute convergence (and Proposition <a href="#prp:prop1">1.1</a>), the terms of the series only have to be non-zero:

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong><span id="thm:thm4"></span>Theorem 1.5   (D'Alembert's Ratio Test) </strong></span><p>Let $(a_n)_n$ be a real sequence with $a_n \neq 0 \; \forall n \in \mathbb{N}$. Suppose $$\lim_{n\to\infty}\frac{\lvert a_{n+1}\rvert}{\lvert a_n\rvert} = r.$$ Then:
  
* If $0 \leq r < 1$, $\sum_{n = 1}^{\infty} a_n$ converges.
* If $r > 1$, then $\sum_{n = 1}^{\infty} a_n$ diverges.
* If $r = 1$, the test is inconclusive.
</p></div>\EndKnitrBlock{theorem}
To see why the test fails for $r = 1$, consider the three series: $$\sum_{n = 1}^{\infty} \frac{(-1)^{n+1}}{n^2}, \quad \sum_{n = 1}^{\infty} \frac{(-1)^{n+1}}{n} \;\; \text{and} \;\; \sum_{n = 1}^{\infty} (-1)^{n+1}.$$ The first is absolutely convergent, the second is conditionally convergent and the third diverges without any limit at all!

# Hints
As per usual, here's where you'll find the problem sheet hints!

1.  Think about all the methods you know for proving whether a series converges. Some of the methods from the tutorial may come in handy...
2.  Pretty much the same as homework question 1. However, for part...
    b)  I've got a few pointers for this one. Make sure you know how the binomial coefficient is defined. Also, try to avoid expanding any unnecessary brackets — if you're writing $n^3, n^4$ etc. in your solutions, you're putting in more effort than needed!
3.  This one is only slightly more involved. Know your definitions, and again, think of possible convergence tests to apply.
4.  i) For this part, use the convergence definition with a specific $\epsilon$ alongside the pinching theorem.
    ii) Use part i) --- for reference, this is a special case of what is known as the **root test** for series.
5.  This is similar to Tutorial Question 4.

<!--chapter:end:index.Rmd-->

