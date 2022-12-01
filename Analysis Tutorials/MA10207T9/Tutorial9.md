---
title: "Analysis 1A — Tutorial 9"
author: 'Christian Jones: University of Bath'
date: 'November 2022'
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
  clavertondown::gitbook_clav:
    split_by: section
    keep_md: true
    config:
      download: [["Tutorial9.html", "HTML page"], ["Tutorial9.pdf","Standard print PDF"], ["Tutorial9Clear.pdf","Clear print PDF"], ["Tutorial9Large.pdf","Large print PDF"], ["Tutorial9.docx","Accessible Word document"], ["Tutorial9.epub","Accessible EPub book" ]]
      sharing: no
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
---

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the 9th Analysis Tutorial on the 4th December. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk).

# Lecture Recap

## Two More Series Results

### Leibniz Alternating Series Test
So far, we've seen three tests which allow us (under certain conditions) to determine whether a series is convergent or not. These were the comparison test, d'Alembert's ratio test and the Cauchy condensation test. There's one more test to cover here, and this concerns series which have *alternating terms*. This is due to Leibniz, who --- depending on your point of view --- is considered to be the inventor of calculus.

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong><span id="thm:thm1"></span>Theorem 1.1   (Leibniz Alternating Series Test) </strong></span><p>Suppose $(a_n)_{n\in\mathbb{N}}$ is a decreasing sequence tending to $0$ as $n \to \infty$. Then $$\sum_{n=1}^{\infty} (-1)^n a_n$$ is a convergent series. </p></div>\EndKnitrBlock{theorem}
Moreover, since the sequence $(a_n)_n$ is decreasing towards $0$, we can say that the value of this sum lies in between $-a_1$ and $a_2 - a_1$.

### Multiplying Series
Recall the statement of the Algebra of Series:
\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong><span id="thm:thm2"></span>Theorem 1.2   (Algebra of Series) </strong></span><p>Let $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$ be convergent series, and let $\alpha, \beta \in \mathbb{R}$. Then $$\sum_{n=1}^{\infty}(\alpha a_n + \beta b_n) = \alpha\sum_{n=1}^{\infty}a_n + \beta\sum_{n=1}^{\infty}b_n.$$</p></div>\EndKnitrBlock{theorem}
Now, compare this to the statement of the Algebra of Limits. Notice that we've suspiciously omitted any mention about multiplying infinite series together. This is because while for convergent sequences $(x_n)_n$ and $(y_n)_n$, $$\lim_{n\to\infty}(x_ny_n) = \lim_{n\to\infty}x_n \cdot \lim_{n\to\infty}y_n,$$ it does **not** follow that for convergent series $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$ that $$\sum_{n=1}^{\infty} a_nb_n = \left(\sum_{n=1}^{\infty}a_n\right)\left(\sum_{n=1}^{\infty}b_n\right).$$

If you're not convinced, try this with $a_n = \frac{1}{n^2}$ and $b_n = 1$! So, the next question we need to ask is whether a formula for multiplying convergent series exists, and if so, which series can we apply it to. This question was answered by Cauchy[^1], and is summarised in the below theorem:

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm3"><span class="thm:thm3" custom-style="NameStyle"><strong><span id="thm:thm3"></span>Theorem 1.3   (Cauchy Multiplication Theorem) </strong></span><p>Assume that the real series $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$ converge absolutely, and for $n \in \mathbb{N}$, define $$c_n:=\sum_{j=1}^{n}a_j b_{n+1 - j}.$$ Then $\sum_{n=1}^{\infty} c_n$ converges absolutely, and $$\sum_{n=1}^{\infty} c_n = \left(\sum_{n=1}^{\infty}a_n\right)\left(\sum_{n=1}^{\infty}b_n\right).$$</p></div>\EndKnitrBlock{theorem}
Note that we require the condition that the two individual sums are *absolutely convergent*. To see why, consider the following example:

\BeginKnitrBlock{example}<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong><span id="exm:ex1"></span>Example 1.1  </strong></span><div>For $n\in\mathbb{N}$, define $a_n = b_n = \frac{(-1)^n}{\sqrt{n}}$, so that $\sum_{n=1}^{\infty}a_n$ and $\sum_{n=1}^{\infty}b_n$ are conditionally convergent. We can calculate $c_n$ as $$c_n = \sum_{j = 1}^{n} \frac{(-1)^{(n+1)}}{\sqrt{j}\sqrt{n+1-j}},$$ from which (as $1 \leq \sqrt{j} \leq \sqrt{n}$ and $1 \leq \sqrt{n+1-j} \leq \sqrt{n}$), $$\lvert c_n \rvert \geq \sum_{j=1}^{n} \frac{1}{n} = n.$$ This tells us that $c_n \not\to 0$ as $n\to\infty$, so $\sum_{n=1}^{\infty} c_n$ must diverge. Hence, the Cauchy Multiplication Theorem fails in this case.</div></div>\EndKnitrBlock{example}

[^1]: If you're keeping track, this is the third time Cauchy has appeared in this course. And we're not done yet!

## Power Series
To complete our look at series, we're going to consider a special type of series which may depend on some parameter $x$. These are known as *power series*, and are defined as follows:

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong><span id="def:def1"></span>Definition 1.1   (Power Series) </strong></span><div>A power series is a real series of the form $\sum_{n = 0}^{\infty} a_n x^n$, where $a_n \in \mathbb{R}$.</div></div>\EndKnitrBlock{definition}
Note that compared to many of the series we have seen so far, we have started indexing the sum at $n = 0$. This is just convention, and will make no difference to the overall convergence properties of these series. Speaking of, we could do with knowing for which values of $x$ these power series converge (or diverge) for.

\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong><span id="prp:prop1"></span>Proposition 1.1  </strong></span><p>For a power series $\sum_{n = 0}^{\infty} a_n x^n$, let $$R:= \sup\lbrace r \geq 0 \lvert \left(\lvert a_n \rvert r^n\right)_{n \in \mathbb{N}} \; \text{is bounded}\rbrace.$$ Then $$\sum_{n = 0}^{\infty} a_n x^n \begin{cases}
\text{diverges for}\;\lvert x \rvert > R,\\
\text{converges absolutely for}\; \lvert x \rvert < R. 
\end{cases}$$</p></div>\EndKnitrBlock{proposition}
Here, $R$ is known as the *radius of convergence* of the power series. Now, if $R \neq +\infty$, what happens if $x = \pm R$? Unfortunately, we need to check the convergence at these points separately, but in doing so, we determine the *interval of convergence*, which is the set of all $x$ for which the power series converges.

### How do we find $R$?
Good question. Luckily, there's two[^2] methods of finding $R$. The first one is a result of d'Alembert's ratio test.

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong><span id="thm:thm4"></span>Theorem 1.4  </strong></span><p>Suppose $\sum_{n = 0}^{\infty} a_n x^n$ is a power series. If $$\lim_{n \to \infty} \frac{\lvert a_n \rvert}{\lvert a_{n+1}\rvert}$$ exists, then the radius of convergence $R$ is the value of this limit.</p></div>\EndKnitrBlock{theorem}
There's something to be aware of here. In this test, $a_n$ is on the top of the fraction, and $a_{n+1}$ is on the bottom. This is the **other way round** to d'Alembert's ratio test, so be careful when applying this test! Also, note that if you have infinitely many $a_n$ equal to zero, then you won't be able to define the fraction in the first place!

The second method doesn't look as nice, but it's very useful if the values of $a_n$ involve powers of $n$, or if there's infinitely many of them equal to zero. And it's also another result due to Cauchy![^3]

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm5"><span class="thm:thm5" custom-style="NameStyle"><strong><span id="thm:thm5"></span>Theorem 1.5   (Cauchy-Hadamard) </strong></span><p>Suppose $\sum_{n = 0}^{\infty} a_n x^n$ is a power series. Then $$R = \left(\limsup_{n\to\infty}\lvert a_n \rvert^{\frac{1}{n}}\right)^{-1},$$ where we define $R = \infty$ if $\frac{1}{R} = 0$, and $R = 0$ if $\frac{1}{R} = \infty$.</p></div>\EndKnitrBlock{theorem}
This test is also known as the *root test*. It is also a good point to mention a particular limit, as it often comes up when applying Cauchy-Hadamard.

\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop2"><span class="prp:prop2" custom-style="NameStyle"><strong><span id="prp:prop2"></span>Proposition 1.2  </strong></span><p>We have $\lim_{n \to \infty} n^{\frac{1}{n}} = 1$.</p></div>\EndKnitrBlock{proposition}
Try proving this using a similar argument to that on *Exercise Sheet 5, Question 1* (but using the binomial theorem instead of just the binomial inequality).

As a final comment here, there is much more that we can say about power series (in regards to differentiability, integrability, etc.), and we can even extend them to complex $x$. If you're interested, you'll find these results in  [Analysis 2A](https://www.bath.ac.uk/catalogues/2022-2023/ma/MA20218.html) in Year 2!

[^2]:Technically, there's three, but the third is basically by using both versions of the comparison test to compare the power series to something which you know converges/diverges.
[^3]: This is result number four named after Cauchy!

# Hints
As per usual, here’s where you’ll find the problem sheet hints!

* [H1.] In this one, remember what we did in tutorials. One uses Leibniz, one can be done with Leibniz (but its quicker not to), and one diverges. Make sure you check the hypotheses of any test you use!
* [H2.] The radius of convergence, $R$, should be alright — have a look at the theory in lectures/tutorials. For the interval of convergence, remember that if $R \neq \infty$, you need to test for convergence at $\pm R$. However...
     * [H2a).] For this one, you might want to make a variable substitution first.
* [H3.] This one is only slightly more involved. Know your definitions, and again, think of possible convergence tests to apply.
