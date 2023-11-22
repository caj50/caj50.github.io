---
title: "Further Examples — Limits Inferior and Superior"
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
      download: [["Liminfsup.html", "HTML page"], ["Liminfsup.pdf","Standard print PDF"], ["LiminfsupClear.pdf","Clear print PDF"], ["LiminfsupLarge.pdf","Large print PDF"], ["Liminfsup.docx","Accessible Word document"], ["Liminfsup.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
  clavertondown::epub_clav:
    toc: false
    pandoc_args: --default-image-extension=svg
  clavertondown::html_clav:
    toc: true
    pandoc_args: --default-image-extension=svg
header-includes:
  - \newcommand{\BOO}{BOO}
---

\newpage
\pagenumbering{arabic}

# Overview {-}
In this document, you'll find three different examples of finding the limit superior ($\limsup$) and limit inferior ($\liminf$) of a sequence, with different methods used in each case.

## Example 1 {-}
\BeginKnitrBlock{example}<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong><span id="exm:ex1"></span>Example 1  </strong></span><div>Consider the sequence $(a_n)_{n}$ defined by $$a_n = (-1)^n\frac{2n}{1+3n}.$$ Find $\limsup_{n \to \infty} a_n$ and $\liminf_{n \to \infty} a_n$.</div></div>\EndKnitrBlock{example}

**Solution**
Firstly, note that we can rewrite each $a_n$ as $$a_n = (-1)^n \frac{2}{3}\frac{1}{\frac{1}{3n} + 1}.$$ Splitting into odd and even cases, we obtain $$a_n = \begin{cases} \frac{2}{3}\frac{1}{\frac{1}{3n} + 1} &\quad \text{for $n$ even},\\
\frac{2}{3}\frac{-1}{\frac{1}{3n} + 1} &\quad \text{for $n$ odd}.\end{cases}$$ Note that for $j \in \mathbb{N}$, $a_{2j-1} \leq 0 \leq a_{2j}$. Also note that $(a_{2j-1})_j$ is a decreasing sequence and $(a_{2j})_{j}$ is an increasing sequence [Try showing these!] Moreover, $\lvert a_n \rvert \leq \frac{2}{3} \; \forall n\in\mathbb{N}$, so $(a_n)_n$ is bounded.

Now, fix $k \in \mathbb{N}$. We have:
$$\begin{align*}
\sup_{k\geq n}a_n &= \sup_{2j \geq k} a_{2j}, \; \; &&\text{(since only even elements are non-negative.)}\\
&= \lim_{j \to \infty} a_{2j}, \; \; &&\text{(since $(a_{2j})_j$ is a bounded increasing sequence)},\\
&= \frac{2}{3}. \; \; \quad &&\text{(by algebra of limits)}
\end{align*}$$
Hence, taking $k \to \infty$, we find that $\sup_{n \geq k} a_n \to \frac{2}{3}$. So, $\limsup_{n \to \infty} a_n = \frac{2}{3}$.

Similarly, fixing $k \in \mathbb{N}$ again:
$$\begin{align*}
\inf_{k\geq n}a_n &= \inf_{2j \geq k} a_{2j-1}, \; \; &&\text{(since only odd elements are non-positive.)}\\
&= \lim_{j \to \infty} a_{2j-1}, \; \; &&\text{(since $(a_{2j-1})_j$ is a bounded decreasing sequence)},\\
&= \lim_{j \to \infty}-\frac{4-\frac{2}{j}}{6 - \frac{2}{j}}, \; \; \quad &&\text{(by sequence definition)}\\
&= -\frac{2}{3}. \; \; \quad &&\text{(by algebra of limits)}.
\end{align*}$$

Hence, taking $k \to \infty$, we find that $\inf_{n \geq k} a_n \to -\frac{2}{3}$. So, $\liminf_{n \to \infty} a_n = -\frac{2}{3}$.

## Example 2 {-}
\BeginKnitrBlock{example}<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex2"><span class="exm:ex2" custom-style="NameStyle"><strong><span id="exm:ex2"></span>Example 2  </strong></span><div>Consider the sequence $(a_n)_{n}$ defined by $$a_n = \frac{1}{n^2} - (-1)^n + 2.$$ Find $\limsup_{n \to \infty} a_n$ and $\liminf_{n \to \infty} a_n$.</div></div>\EndKnitrBlock{example}

**Solution**
First, note that for any $j\in\mathbb{N}$, $a_{2j} \leq 2 \leq a_{2j-1}$. But this time, we find that both $(a_{2j})_j$ and $(a_{2j-1})_j$ are decreasing sequences! In this case, the argument used in Example <a href="#exm:ex1">1</a> will only work for $\liminf_{n\to\infty} a_n.$ Try using that argument to show that $$\liminf_{n\to\infty}a_n = 1.$$ For $\limsup_{n\to\infty} a_n$, we have to look towards the start of the sequence. To this end, fix $k \in \mathbb{N}$. Then,
$$\begin{align*}
\sup_{n\geq k}a_n &= \sup_{2j-1 \geq k} a_{2j - 1} \; \; &&\text{(since only the odd elements are $\geq 2$)}\\
&=\begin{cases}
a_k \; \text{if $k$ is odd},\\
a_{k+1} \; \text{if $k$ is even}\end{cases} \; \; &&\text{(because $(a_{2j-1})_j$ is a decreasing sequence)}\\
&=\begin{cases}
\frac{1}{k^2} + 3 \; \text{if $k$ is odd},\\
\frac{1}{(k+1)^2} + 3 \; \text{if $k$ is even}\end{cases}
\end{align*}$$

In both cases, as $k \to \infty$, $\sup_{n\geq k }a_n \to 3$, so $\limsup_{n \to \infty} a_n = 3$.

## Example 3 {-}
\BeginKnitrBlock{example}<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex3"><span class="exm:ex3" custom-style="NameStyle"><strong><span id="exm:ex3"></span>Example 3  </strong></span><div>Consider the sequence $(a_n)_{n}$ defined by $$a_n = \cos\left(\frac{n\pi}{3}\right) + \frac{(-1)^n}{n}.$$ Find $\limsup_{n \to \infty} a_n$ and $\liminf_{n \to \infty} a_n$.</div></div>\EndKnitrBlock{example}
Note that this time, you can't split $(a_n)_n$ up into two monotonic subsequences, so neither of the two methods in the previous examples work. So, we need to be crafty.

It's always handy to have an idea of what the $\liminf$ and $\limsup$ might be. Since $\left\lvert\cos\left(\frac{n\pi}{3}\right)\right\rvert \leq 1$ for all $n \in \mathbb{N}$, and $\frac{(-1)^n}{n} \to 0$ as $n \to \infty$, we (hopefully) would guess that $$\liminf_{n\to\infty}a_n = -1, \quad \text{and} \quad \limsup_{n \to \infty} a_n = -1.$$ So how do we go about showing these?

**Solution**
Firstly, recall that the $\limsup$ is the largest limit of any subsequence of $(a_n)_n$. Take $n_j = 6j$, then $$a_{n_j} = \cos\left(\frac{6j\pi}{3}\right) + \frac{(-1)^{6j}}{6j} = 1 + \frac{1}{6j} \to 1, \; \text{as} \; j \to \infty.$$

So, $\lim_{j \to \infty} a_{n_j} = 1$, hence $\limsup_{n \to \infty} a_n \geq 1$.

To show that $\limsup_{n \to \infty} a_n \leq 1$, recall that for sequences $(b_n)_n$ and $(c_n)_n$, $$\limsup_{n \to \infty}(b_n + c_n) \leq \limsup_{n \to \infty}b_n + \limsup_{n \to \infty}c_n.$$ Taking $$b_n = \cos\left(\frac{n\pi}{3}\right), \; \text{and} \; c_n = \frac{(-1)^n}{n},$$ we have that $$\limsup_{n \to \infty} b_n = 1, \; \text{and}$$ $$\limsup_{n \to \infty} c_n = 0 \quad \text{(as $(c_n)_n$ converges to $0$)}.$$ Hence,
$$\limsup_{n \to \infty} a_n = \limsup_{n \to \infty}(b_n + c_n) \leq 1 + 0 = 1.$$

Combining the two inequalities we have found allows us to conclude that $\limsup_{n \to \infty} a_n = 1.$

Have a go at proving that $\liminf_{n \to \infty} a_n = -1$. You'll need:

* $\liminf$ is the smallest limit of any subsequence of $(a_n)_n$.
* $\liminf_{n \to \infty}(b_n + c_n) \geq \liminf_{n \to \infty}b_n + \liminf_{n \to \infty}c_n.$

<!--chapter:end:index.Rmd-->

