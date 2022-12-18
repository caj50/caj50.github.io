---
title: "Analysis 1A — Tutorial 5"
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
      download: [["Tutorial5.html", "HTML page"], ["Tutorial5.pdf","Standard print PDF"], ["Tutorial5Clear.pdf","Clear print PDF"], ["Tutorial5Large.pdf","Large print PDF"], ["Tutorial5.docx","Accessible Word document"], ["Tutorial5.epub","Accessible EPub book" ]]
      sharing: no
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
Here is the material to accompany the 5th Analysis Tutorial on the 7th November. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](caj50.github.io/tutoring.html).

# Infinite Limits
Before we cover any material from this week, its worth discussing the use of $\infty$ as a limit, especially when applying the Algebra of Limits. The main thing to note is that expressions such as $\infty - \infty$ and $\frac{\infty}{\infty}$ don't really make a lot of sense, for example:

\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong>(\#exm:ex1) </strong></span><div>Give examples of sequences $(a_n)_{n\in\mathbb{N}}$ and $(b_n)_{n\in\mathbb{N}}$, both diverging to $\infty$ for which:
  
  1. $(a_n - b_n)_{n\in\mathbb{N}}$ diverges to $\infty$,
  2. $(a_n - b_n)_{n\in\mathbb{N}}$ diverges to $-\infty$, and
  3. $(a_n - b_n)_{n\in\mathbb{N}}$ converges to $0$.
  </div></div>\EndKnitrBlock{example}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>The idea here is to look for fairly simple sequences. With that in mind:
  
1. If we take $a_n = 2n$ and $b_n = n$, we see that $a_n - b_n = n$, and $(n)_{n\in\mathbb{N}}$ diverges to $\infty$. But if we tried to apply the algebra of limits to this result, it would suggest that $\infty - \infty = \infty$.
2. If we take $a_n = n$ and $b_n = 2n$, we see that $a_n - b_n = -n$, and $(-n)_{n\in\mathbb{N}}$ diverges to $\infty$. But, again, if we tried to apply AoL to this result, it would suggest that $\infty - \infty = -\infty$. Immediately this conflicts with the answer to part 1)!
3. Finally, if we take $a_n = b_n = n$, we see that $a_n - b_n = 0$, and $(0)_{n \in \mathbb{N}}$ is a convergent sequence — it converges to $0$. Attempting to apply AoL to this result suggests that $\infty - \infty = 0$.
</p></div>\EndKnitrBlock{solution}
What parts 1), 2) and 3) demonstrate is that you can't consistently define $\infty - \infty$. (Note: if you take the same sequences from 1), 2) and 3) and divide them, you can see why $\frac{\infty}{\infty}$ isn't consistently define-able either).

# Lecture Recap

## Monotonic Subsequences
In reverse order to how it was discussed in tutorials, we begin with some special types of sequences. First, we need to define what these sequences are. This definition might look long, but it's really just five concepts grouped together.
\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Monotonic Sequences) </strong></span><div>Let $(a_n)_{n\in\mathbb{N}}$ be a real sequence. Then if $\forall n \in \mathbb{N}$:
  
  * $a_{n+1} \geq a_n,\;$ $(a_n)_{n\in\mathbb{N}}$ is increasing, 
  * $a_{n+1} > a_n,\;$ $(a_n)_{n\in\mathbb{N}}$ is strictly increasing,
  * $a_{n+1} \leq a_n,\;$ $(a_n)_{n\in\mathbb{N}}$ is decreasing,
  * $a_{n+1} < a_n,\;$ $(a_n)_{n\in\mathbb{N}}$ is strictly decreasing.

If the sequence has any one of these properties, it is called monotone, or a monotonic sequence.</div></div>\EndKnitrBlock{definition}
For a given sequence $(a_n)$, the two main ways of checking monotonicity are by considering $a_{n+1} - a_n$ and/or $\frac{a_{n+1}}{a_n}$, and comparing these objects to $0$ and $1$ respectively. The second of these methods is especially useful when you're dealing with powers of $n$, such as for the sequence $(b_n)$ in Exercise Sheet 5, Question 2.

A useful theorem for these sequences is the following[^1]:
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1) </strong></span><p>Let $(a_n)_{n\in\mathbb{N}}$ be a bounded, monotone sequence. Then $(a_n)_{n\in\mathbb{N}}$ is convergent. </p></div>\EndKnitrBlock{theorem}
In fact, if a sequence $(a_n)_{n \in \mathbb{N}}$ is increasing, then it converges to the supremum of the set of $a_n$ values, and if it is decreasing, then it converges to the infimum of the set of $a_n$ values.

[^1]:If you're interested, this statement is completely equivalent to the completeness axiom from Section 2 of the lecture notes. In fact, back in the prehistoric times of 2016 --- when I took the course --- this result was stated as the completeness axiom.

## The Sandwich/Pinching/Squeeze Theorem[^2]
This is a way of finding the limit of a sequence if you can find two other sequences to `trap' it with. It's quite a good method for rational functions and proving statements about $n$-th roots.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Sandwich Theorem) </strong></span><p>Suppose that $(a_n)_{n\in\mathbb{N}}\, , \, (b_n)_{n\in\mathbb{N}}\, , \, (c_n)_{n\in\mathbb{N}}$ are real sequences. If $a_n \leq b_n \leq c_n \quad \forall n \in \mathbb{N}$, and $\exists L \in \mathbb{R}$ such that
\begin{align*}
    \lim_{n \to \infty} a_n = L = \lim_{n \to \infty} c_n,
\end{align*}
then $\lim_{n \to \infty}b_n = L$.</p></div>\EndKnitrBlock{theorem}
There's also a slight modification to this theorem, called the 'Bitten Sandwich Theorem'.
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong>(\#thm:thm3)  (Bitten Sandwich Theorem) </strong></span><p>Suppose that $(a_n)_{n\in\mathbb{N}}\, , \, (b_n)_{n\in\mathbb{N}}\, , \, (c_n)_{n\in\mathbb{N}}$ are real sequences. If $\exists N \in \mathbb{N}$ such that $a_n \leq b_n \leq c_n \; \forall n \geq N$, and $\exists L \in \mathbb{R}$ such that
\begin{align*}
    \lim_{n \to \infty} a_n = L = \lim_{n \to \infty} c_n,
\end{align*}
then $\lim_{n \to \infty}b_n = L$.</p></div>\EndKnitrBlock{theorem}
This just says that as long as after some $N \in \mathbb{N}$, $(b_n)_n$ is trapped between sequences $(a_n)_n$ and $(c_n)_n$ that share a common limit, then all three sequences will share that common limit. 

It is worth noting that adaptations of theorems in this way exist all across analysis. This is because when studying convergence, we don't really care about what is happening at the start of the sequence. We only care about the "long term" behaviour.

[^2]: Other names for this theorem must surely exist. If you find one out in the wild, tell me, and I'll add it to the name of this section.

## More on Infinite Limits
We can also make the idea of a sequence getting increasingly more positive (or more negative) more precise via the idea of divergence to $\pm\infty$. We present the definition for 'positive' $\infty$ here.

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Divergence to Infinity) </strong></span><div>A real sequence $(a_n)_{n\in\mathbb{N}}$ diverges to $\infty$ if $$\forall M \in \mathbb{R}, \; \exists N \in \mathbb{N} \; \text{such that}\; \forall n \geq N, \; a_n > M.$$</div></div>\EndKnitrBlock{definition}

There is also a corresponding version of the 'algebra of limits' for divergence to $\pm\infty$ (see \@ref(thm:thm4)). This version has been stolen and adapted from an old set of lecture notes (ones from 2016 to be precise!), so some of these results may not appear in the current lecture notes. Consequently, you won't have seen the proofs for these results, so you can't use them in Tutorial Question 4, Exercise Sheet Five.[^3]

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong>(\#thm:thm4)  (Algebra of Infinite Limits) </strong></span><p>Let $(a_n)_{n\in\mathbb{N}}$ and $(b_n)_{n\in\mathbb{N}}$ be real sequences.

1. If $a_n \to \infty$ and $y_n \to \infty$ as $n \to \infty$, then $a_n + b_n \to \infty$ as $n\to\infty$.
2. If $a_n \to \infty$ and $c > 0$, then $ca_n \to \infty$ as $n \to \infty$.
3. If $a_n \to \infty$ and $y_n \to \infty$ as $n \to \infty$, then $a_nb_n \to \infty$ as $n\to\infty$.
4. We have $a_n \to \infty$ as $n \to \infty$ if and only if $-a_n \to -\infty$ as $n \to \infty$.
5. For $a_n \neq 0\; \forall n \in \mathbb{N}$, if $a_n \to \infty$ as $n \to \infty$, then $\frac{1}{a_n} \to 0$ as $n \to \infty$.
6. If If $a_n \to 0$ as $n\to\infty$ and $a_n > 0\; \forall n \in \mathbb{N}$, then $\frac{1}{a_n} \to \infty$ as $n \to \infty$.
</p></div>\EndKnitrBlock{theorem}

[^3]: This question asks you to prove parts of this theorem, so using the theorem to prove the theorem is purely circular reasoning, and should absolutely be avoided.

# Hints
As per usual, here's where you'll find the problem sheet hints!

* [H1.] Try applying one of the tests for monotonicity. For the limit, if you need to use any theorems anywhere, state them!
* [H2.] If $a_n \neq 0 \, \; \forall n \in \mathbb{N}$, then this would just be an application of the algebra of (infinite) limits! Since you don't know if this is the case, you'll need to use the definition again for this question. You'll end up with an inequality of the form $a_n^2 > g(\epsilon)$, where $g$ is a rational function of $\epsilon$, at some point in your solution. Take cases on the sign of the numerator of $g(\epsilon)$ to find the required $N$ in the definition of limit.
* [H3.] This is similar to the supremum question we did in tutorials. If you need a refresher on the argument involved, look in the solutions to Exercise Sheet 4. Try adapting this for infima!
* [H4.] This is similar to tutorial question 3 off Exercise Sheet 5. Try a few terms of the sequence to get a feel for what's happening first. Note that you're not explicitly told to find the limit, but it's really worth doing if you can!

<!--chapter:end:index.Rmd-->

