---
title: "Further Examples — Limits Inferior and Superior"
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
      download: [["Liminfsup.html", "HTML page"], ["Liminfsup.pdf","Standard print PDF"], ["Liminfsup.pdf","Clear print PDF"], ["Liminfsup.pdf","Large print PDF"], ["Liminfsup.docx","Accessible Word document"], ["Liminfsup.epub","Accessible EPub book" ]]
      sharing: no
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
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
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

## Example 1
\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong>(\#exm:ex1) </strong></span><div>Consider the sequence $(a_n)_{n}$ defined by $$a_n = (-1)^n\frac{2n}{1+3n}.$$ Find $\limsup_{n \to \infty} a_n$ and $\liminf_{n \to \infty} a_n$.</div></div>\EndKnitrBlock{example}

**Solution**
Firstly, note that we can rewrite each $a_n$ as $$a_n = (-1)^n \frac{2}{3}\frac{1}{\frac{1}{3n} + 1}.$$ Splitting into odd and even cases, we obtain $$a_n = \begin{cases} \frac{2}{3}\frac{1}{\frac{1}{3n} + 1} &\quad \text{for $n$ even},\\
\frac{2}{3}\frac{-1}{\frac{1}{3n} + 1} &\quad \text{for $n$ odd}.\end{cases}$$ Note that for $j \in \mathbb{N}$, $a_{2j-1} \leq 0 \leq a_{2j}$. Also note that $(a_{2j-1})_j$ is a decreasing sequence and $(a_{2j})_{j}$ is an increasing sequence [Try showing these!] Moreover, $\lvert a_n \rvert \leq \frac{2}{3} \; \forall n\in\mathbb{N}$, so $(a_n)_n$ is bounded.

Now, fix $k \in \mathbb{N}$. We have:
\begin{align*}
\sup_{k\geq n}a_n &= \sup_{2j \geq k} a_{2j}, \; \; &&\text{(since only 'even' elements are non-negative.)}\\
&= \lim_{j \to \infty} a_{2j}, \; \; &&\text{(since $(a_{2j})_j$ is a bounded increasing sequence)},\\
&= \frac{2}{3} \; \; \quad &&\text{(by algebra of limits)}
\end{align*}

## Series
It might look like we're done with sequences, but in the grand scheme of things, we're only really getting started. Since with each sequence $(a_n)_{n\in\mathbb{N}}$, we have an infinite list of real numbers, we might consider trying to manipulate them in some way. One way we can do this is by adding them together, which leads to the notion of a *series*.

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Series) </strong></span><div>Let $(a_n)_{n \in \mathbb{N}}$ be a real sequence. Then $$\sum_{n = 1}^{\infty} a_n$$ is called a series for $(a_n)_{n\in\mathbb{N}}$.</div></div>\EndKnitrBlock{definition}

Much like with sequences, we have an analogous version of convergence for a series:
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Series Convergence and Partial Sums) </strong></span><div>Let $(a_n)_{n \in \mathbb{N}}$ be a real sequence. Then $\sum_{n = 1}^{\infty} a_n$ converges if and only if the sequence $(S_N)_{N \in \mathbb{N}}$ converges, where $$S_N:= \sum_{n = 1}^{N} a_n$$ is the $N$\textsuperscript{th} partial sum. If $S_N \to \ell$ as $N \to \infty$, we define $$\ell = \sum_{n = 1}^{\infty}a_n.$$</div></div>\EndKnitrBlock{definition}
If $(S_N)_{N\in\mathbb{N}}$ diverges to $\pm\infty$, we say that the corresponding series $$\sum_{n=1}^{\infty} a_n = \pm\infty.$$ Finally, if $(S_N)_{N\in\mathbb{N}}$ doesn't converge to a limit, we say that the series diverges without limit.

### Algebra of Series
By applying the algebra of limits to the sequences of partial sums, we can deduce some handy results.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong>(\#thm:thm3)  (Algebra of Series) </strong></span><p>Let $\sum_{n=1}^{\infty} a_n$ and $\sum_{n=1}^{\infty} b_n$ be convergent series, and let $\alpha,\beta \in \mathbb{R}$. Then $$\sum_{n = 1}^{\infty} (\alpha a_n + \beta b_n) = \alpha\sum_{n=1}^{\infty} a_n + \beta\sum_{n=1}^{\infty} b_n.$$</p></div>\EndKnitrBlock{theorem}

### Some Other Useful Results
Firstly, we can relate the size of the terms of a series to the overall sum.

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1) </strong></span><p>Let $\sum_{n=1}^{\infty} a_n$ and $\sum_{n=1}^{\infty} b_n$ be real series. If $a_n \leq b_n \, \forall n\in\mathbb{N}$, then $$\sum_{n=1}^{\infty} a_n \leq \sum_{n=1}^{\infty} b_n.$$</p></div>\EndKnitrBlock{proposition}

Secondly, we have a *necessary* condition for convergence of a series.

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop2"><span class="prp:prop2" custom-style="NameStyle"><strong>(\#prp:prop2) </strong></span><p>Let $\sum_{n=1}^{\infty} a_n$ be a convergent series. Then $a_n \to 0$ as $n \to \infty$.</p></div>\EndKnitrBlock{proposition}
Note that the converse of this theorem *does not* hold (think of the sum $\sum_{n=1}^{\infty} \frac{1}{n}$). However, the contrapositive is very good at showing that a series does not converge!

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop3"><span class="prp:prop3" custom-style="NameStyle"><strong>(\#prp:prop3) </strong></span><p>Let $\sum_{n=1}^{\infty} a_n$ be a series. If $a_n \not\to 0$ as $n \to \infty$, then $\sum_{n=1}^{\infty} a_n$ does not converge.</p></div>\EndKnitrBlock{proposition}

# Hints
As per usual, here's where you'll find the problem sheet hints!

* [H1.] Try using a similar argument to the one used in tutorial question 1 (i.e. use the fact that the sequence can be split into odd and even cases to your advantage)
* [H2.] For this question, think about what it means for a series to be convergent. You'll also want to split the terms of the series up in some way. (Think of tutorial question 3a.) 
* [H3.] For the first part, think induction. The only other thing I'll say is to make sure you state all the main results you use!

