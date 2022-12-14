---
title: "Analysis 1A — Tutorial 9"
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

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the 9th Analysis Tutorial on the 5th December. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk).

# Lecture Recap

## Two More Series Results

### Leibniz Alternating Series Test
So far, we've seen three tests which allow us (under certain conditions) to determine whether a series is convergent or not. These were the comparison test, d'Alembert's ratio test and the Cauchy condensation test. There's one more test to cover here, and this concerns series which have *alternating terms*. This is due to Leibniz, who --- depending on your point of view --- is considered to be the inventor of calculus.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1)  (Leibniz Alternating Series Test) </strong></span><p>Suppose $(a_n)_{n\in\mathbb{N}}$ is a decreasing sequence tending to $0$ as $n \to \infty$. Then $$\sum_{n=1}^{\infty} (-1)^n a_n$$ is a convergent series. </p></div>\EndKnitrBlock{theorem}
Moreover, since the sequence $(a_n)_n$ is decreasing towards $0$, we can say that the value of this sum lies in between $-a_1$ and $a_2 - a_1$.

### Multiplying Series
Recall the statement of the Algebra of Series:
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Algebra of Series) </strong></span><p>Let $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$ be convergent series, and let $\alpha, \beta \in \mathbb{R}$. Then $$\sum_{n=1}^{\infty}(\alpha a_n + \beta b_n) = \alpha\sum_{n=1}^{\infty}a_n + \beta\sum_{n=1}^{\infty}b_n.$$</p></div>\EndKnitrBlock{theorem}
Now, compare this to the statement of the Algebra of Limits. Notice that we've suspiciously omitted any mention about multiplying infinite series together. This is because while for convergent sequences $(x_n)_n$ and $(y_n)_n$, $$\lim_{n\to\infty}(x_ny_n) = \lim_{n\to\infty}x_n \cdot \lim_{n\to\infty}y_n,$$ it does **not** follow that for convergent series $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$, $$\sum_{n=1}^{\infty} a_nb_n = \left(\sum_{n=1}^{\infty}a_n\right)\left(\sum_{n=1}^{\infty}b_n\right).$$

If you're not convinced, we can try this with $a_n = b_n =  \frac{(-1)^{n}}{\sqrt{n}}$. Using the Leibniz test, we can see that both $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$ converge, but $$\sum_{n=1}^{\infty} a_nb_n = \sum_{n=1}^{\infty}\frac{1}{n} = \infty.$$ So, the next question we need to ask is whether a formula for multiplying convergent series exists, and if so, which series can we apply it to. This question was answered by Cauchy[^2], and is summarised in the below theorem:

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong>(\#thm:thm3)  (Cauchy Multiplication Theorem) </strong></span><p>Assume that the real series $\sum_{n=0}^{\infty}a_n$ and $\sum_{n=0}^{\infty}b_n$ converge absolutely, and for $n \in \mathbb{N}$, define $$c_n:=\sum_{j=0}^{n}a_j b_{n - j}.$$ Then $\sum_{n=0}^{\infty} c_n$ converges absolutely, and $$\sum_{n=0}^{\infty} c_n = \left(\sum_{n=0}^{\infty}a_n\right)\left(\sum_{n=0}^{\infty}b_n\right).$$</p></div>\EndKnitrBlock{theorem}
Note that we index the sums starting at $n=0$ here. This is purely for convenience, and you could equally formulate this theorem for sums starting at $n=1$ (or any other value of $n$ for that matter). Furthermore, we require the condition that the two individual sums are *absolutely convergent*. As you've seen in lectures, the Cauchy Multiplication Theorem will fail if the series involved are only conditionally convergent.



[^2]: If you're keeping track, this is the third time Cauchy has appeared in this course. And we're not done yet!

## Power Series
To complete our look at series, we're going to consider a special type of series which may depend on some parameter $x$. These are known as *power series*, and are defined as follows:

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Power Series) </strong></span><div>A power series is a real series of the form $\sum_{n = 0}^{\infty} a_n x^n$, where $a_n \in \mathbb{R}$.</div></div>\EndKnitrBlock{definition}
Note that compared to many of the series we have seen so far, we have started indexing the sum at $n = 0$. This is just convention, and will make no difference to the overall convergence properties of these series. Speaking of, we could do with knowing for which values of $x$ these power series converge (or diverge).

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1) </strong></span><p>For a power series $\sum_{n = 0}^{\infty} a_n x^n$, let $$R:= \sup\lbrace r \geq 0 \lvert \left(\lvert a_n \rvert r^n\right)_{n \in \mathbb{N}} \; \text{is bounded}\rbrace.$$ Then $$\sum_{n = 0}^{\infty} a_n x^n \begin{cases}
\text{diverges for}\;\lvert x \rvert > R,\\
\text{converges absolutely for}\; \lvert x \rvert < R. 
\end{cases}$$</p></div>\EndKnitrBlock{proposition}
Here, $R$ is known as the *radius of convergence* of the power series. Now, if $R \neq +\infty$, what happens if $x = \pm R$? Unfortunately, we need to check the convergence at these points separately, but in doing so, we determine the *interval of convergence*, which is the set of all $x$ for which the power series converges.

### How do we find $R$?
Good question. Luckily, there's two[^3] methods of finding $R$. The first one is a result of d'Alembert's ratio test.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong>(\#thm:thm4) </strong></span><p>Suppose $\sum_{n = 0}^{\infty} a_n x^n$ is a power series. If $$\lim_{n \to \infty} \frac{\lvert a_n \rvert}{\lvert a_{n+1}\rvert}$$ exists, then the radius of convergence $R$ is the value of this limit.</p></div>\EndKnitrBlock{theorem}
There's something to be aware of here. In this test, $a_n$ is on the top of the fraction, and $a_{n+1}$ is on the bottom. This is the **other way round** to d'Alembert's ratio test, so be careful when applying this test! Also, note that if you have infinitely many $a_n$ equal to zero, then you won't be able to define the fraction in the first place!

The second method doesn't look as nice, but it's very useful if the values of $a_n$ involve powers of $n$, or if there's infinitely many of them equal to zero. And it's also another result due to Cauchy![^4]

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm5"><span class="thm:thm5" custom-style="NameStyle"><strong>(\#thm:thm5)  (Cauchy-Hadamard) </strong></span><p>Suppose $\sum_{n = 0}^{\infty} a_n x^n$ is a power series. Then $$R = \left(\limsup_{n\to\infty}\lvert a_n \rvert^{\frac{1}{n}}\right)^{-1},$$ where we define $R = \infty$ if $\frac{1}{R} = 0$, and $R = 0$ if $\frac{1}{R} = \infty$.</p></div>\EndKnitrBlock{theorem}
This test is also known as the *root test*. It is also a good point to mention a particular limit, as it often comes up when applying Cauchy-Hadamard.

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop2"><span class="prp:prop2" custom-style="NameStyle"><strong>(\#prp:prop2) </strong></span><p>We have $\lim_{n \to \infty} n^{\frac{1}{n}} = 1$.</p></div>\EndKnitrBlock{proposition}
Try proving this using a similar argument to that on *Exercise Sheet 5, Question 1* (but using the binomial theorem instead of just the binomial inequality). Now that we have this result, we can cover a more unusual power series example:

\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex2"><span class="exm:ex2" custom-style="NameStyle"><strong>(\#exm:ex2) </strong></span><div>Consider the power series $\sum_{n=1}^{\infty}a_n x^n$, where $a_n$ is given by $$a_n = \begin{cases}
n \quad \text{if $n$ is prime},\\
0 \quad \text{otherwise}.
\end{cases}$$
What is the radius of convergence, $R$?</div></div>\EndKnitrBlock{example}
**Solution:**
Since zero occurs as a value of $a_n$ infinitely often, we resort to using the Cauchy-Hadamard test. As each term of $(a_n)_n$ is non-negative and we can split it up into two monotonic increasing sequences --- one consisting of all zeroes, and one consisting of the prime numbers --- we find that $$\limsup_{n\to\infty}\lvert a_n \rvert^{\frac{1}{n}} = \lim_{n \to \infty} n^{\frac{1}{n}} = 1.$$ Taking the reciprocal of this answer gives us that the radius of convergence is $R = 1$.  

As a final comment here, there is much more that we can say about power series (in regards to differentiability, integrability, etc.), and we can even extend them to complex $x$. If you're interested, you'll find these results in  [Analysis 2A](https://www.bath.ac.uk/catalogues/2022-2023/ma/MA20218.html) in Year 2!

[^3]:Technically, there's three, but the third is basically by using both versions of the comparison test to compare the power series to something which you know converges/diverges.
[^4]: This is result number four named after Cauchy!

# Hints
As per usual, here’s where you’ll find the problem sheet hints!

* [H1.] In this one, remember what we did in tutorials. One uses Leibniz, one can be done with Leibniz (but its quicker not to), and one diverges. Make sure you check the hypotheses of any test you use!
* [H2.] The radius of convergence, $R$, should be alright — have a look at the theory in lectures/tutorials. For the interval of convergence, remember that if $R \neq \infty$, you need to test for convergence at $\pm R$. However...
     * [H2a).] For this one, you might want to make a variable substitution first.
* [H3.] To begin here, you've seen a similar trick for the square roots in previous problem sheets (e.g. Sheet 4/Sheet 8). Think about your tests for convergence again on this one!

