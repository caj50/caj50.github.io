---
title: "Analysis 1A — Tutorial 4"
author: 'Christian Jones: University of Bath'
date: 'October 2022'
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
      download: [["Tutorial4.html", "HTML page"], ["Tutorial4.pdf","Standard print PDF"], ["Tutorial4Clear.pdf","Clear print PDF"], ["Tutorial4Large.pdf","Large print PDF"], ["Tutorial4.docx","Accessible Word document"], ["Tutorial4.epub","Accessible EPub book" ]]
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
header-includes:
  - \newcommand{\BOO}{BOO}
  - \usepackage {hyperref}
  - \hypersetup {colorlinks = true, linkcolor = blue, urlcolor = blue}
---
<!-- This is needed since I am working with svg files from mathcha.io. It converts the graphics files to something that can be used in the pdf files. Code taken from https://stackoverflow.com/questions/50165404/how-to-make-a-pdf-using-bookdown-including-svg-images/56044642#56044642 -->

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the 4th Analysis Tutorial on the 31st October. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk).

# Lecture Recap

## Sequences and Convergence
Firstly, to discuss anything this week, we need to introduce the idea of a sequence.
\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong><span id="def:def1"></span>Definition 1.1   (Sequence) </strong></span><div>A sequence of real numbers is a function
$$\begin{align*}
    a:\; &\mathbb{N} \longrightarrow \mathbb{R},\\
    &n \longmapsto a_n.
\end{align*}</div></div>\EndKnitrBlock{definition}
Since this notation can get kind of annoying, we instead denote a sequence by $(a_n)_{n\in\mathbb{N}}$. If it's clear from the context what set we're indexing over, we can even just simply write a sequence as $(a_n)_n$.

Now, this gives us an infinitely long list of real numbers, and sometimes its interesting to look at the 'long-term' behaviour of these lists. This gives rise to the idea of convergence.

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong><span id="def:def2"></span>Definition 1.2   (Sequence Convergence) </strong></span><div>A sequence $(a_n)_{n\in\mathbb{N}}$ converges to a real number $L$ as $n \longrightarrow \infty$, written as either $a_n \longrightarrow L$, or $\lim_{n \to \infty}a_n = L$ if $$\forall \epsilon > 0, \; \exists N = N(\epsilon) \in \mathbb{N}, \; \text{such that} \; \forall n \geq N, \; \lvert a_n - L \rvert < \epsilon.$$</div></div>\EndKnitrBlock{definition}
Loosely speaking, this says that no matter how close you want the sequence to get to $L$, you will always be able to find some point in the sequence after which all points in the sequence will be as close to $L$ as you wanted. For an example of this, have a look at this [Desmos link](https://www.desmos.com/calculator/dfkjgg0wzj). For $\epsilon = 0.5$ and $L = 3$, you can see that every member of the sequence after the $11^{th}$ lies within a strip of width $2\epsilon$ around $L$. Have a go at messing with the value of $\epsilon$!

Something else we can mention for the definition is its *negation*. Specifically, a sequence $(a_n)_n$ does not converge to $L$ if
$$\begin{align*}
    \exists\; \epsilon_0 > 0, \; \text{such that} \; \forall N \in \mathbb{N}, \exists n \geq N \; \text{such that} \; \lvert a_n - L \rvert \geq \epsilon_0.
\end{align*}$$

### Useful Sequences
Some (straightforward) results from using the definition include

* As $n \longrightarrow \infty$: $$\frac{1}{n} \longrightarrow 0.$$
* For a real number $c$: as $n \longrightarrow \infty$, $$c \longrightarrow c.$$
* For $q \in \mathbb{R}$ with $\lvert q \rvert < 1$: as $n \longrightarrow \infty$ $$q^n \longrightarrow 0.$$

### Two Useful Theorems
\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong><span id="thm:thm1"></span>Theorem 1.1   (Preservation of Non-Strict Inequalities) </strong></span><p>Let $(a_n)_{n\in\mathbb{N}}$ and $(b_n)_{n\in\mathbb{N}}$ be sequences and let $L,M \in \mathbb{R}$ be such that $a_n \to L$ and $b_n \to L$ as $n \to \infty$. If $a_n \leq b_n \; \forall n \in \mathbb{N}$, then $L \leq M$.</p></div>\EndKnitrBlock{theorem}
There are two good uses for this theorem. The first says that non-negative sequences should have non-negative limits (which is something you might expect). Before we state the second, we mention one more thing, which is **not true**:
\BeginKnitrBlock{Non-theorem}<div class="Non-theorem" custom-style="ExampleStyle" id="Non:unnamed-chunk-2"><span class="Non-theorem" custom-style="NameStyle"><strong> Non-theorem: </strong></span><p> Let $(a_n)_{n\in\mathbb{N}}$ and $(b_n)_{n\in\mathbb{N}}$ be sequences and let $L,M \in \mathbb{R}$ be such that $a_n \to L$ and $b_n \to L$ as $n \to \infty$. If $a_n < b_n \; \forall n \in \mathbb{N}$, then $L < M$.</p></div>\EndKnitrBlock{Non-theorem}
To see why this is false, consider the sequences defined by $a_n = 1 - \frac{1}{n}$ and $b_n = 1$. We note that each $a_n$ is strictly less than each corresponding $b_n$, but we find that $$\lim_{n \to \infty} a_n = 1 = \lim_{n \to \infty} b_n.$$

The second reason why Theorem <a href="#thm:thm1">1.1</a> is so important, is that it gives us this second theorem[^1]:
\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong><span id="thm:thm2"></span>Theorem 1.2   (Uniqueness of Limits) </strong></span><p>If $(a_n)_{n\in\mathbb{N}}$ is convergent with $a_n \to L$ and $a_n \to M$ as $n \to \infty$, then $L = M$.</p></div>\EndKnitrBlock{theorem}

[^1]: Feel free to ignore this footnote, but there are areas of maths where limits are not unique. This is usually in the realm of topology, which you can take in Year 3 [(MA30055)](https://www.bath.ac.uk/catalogues/2022-2023/ma/MA30055.html). Luckily for us, everything behaves nicely, and our limits are unique.

### Bounded Sequences
Much like we have done with sets, we can formulate a definition which allows us to `trap' sequences.

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong><span id="def:def3"></span>Definition 1.3   (Bounded Sequence) </strong></span><div>A sequence $(a_n)$ is bounded if there exists $M \in \mathbb{R}$ such that $\lvert a_n \rvert \leq M$.</div></div>\EndKnitrBlock{definition}
If you prefer to think diagramatically, this says we can trap the sequence within a strip of width $2M$ around $0$. More importantly, this leads to the idea that *all convergent sequences are bounded*. Note that this is equivalent to saying that if a sequence is not bounded, then it is not convergent.

### Algebra of Limits
Using the definition to prove all limits would be an incredibly boring way to go through this course. Luckily, there are a few general results we can prove which make our lives so much easier. This is known as the *algebra of limits* (AoL).

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong><span id="thm:thm4"></span>Theorem 1.3   (Algebra of Limits) </strong></span><p>Let $A,B,c \in \mathbb{R}$ and let $(a_n)$ and $(b_n)$ be sequences with $a_n \to A$ and $b_n \to B$ as $n \to \infty$. Then:

1. $\lim_{n \to \infty} (a_n + b_n) = A + B$,
2. $\lim_{n \to \infty} (ca_n) = cA$,
3. $\lim_{n \to \infty} (a_n b_n) = AB$,
4. If $b_n \neq 0 \; \forall n \in \mathbb{N}$ and $B \neq 0$, $\lim_{n \to \infty} \frac{a_n}{b_n} = \frac{A}{B}$.
</p></div>\EndKnitrBlock{theorem}


# Hints
As per usual, here's where you'll find the problem sheet hints!

* [H1.] Use the definition! Try and follow a similar format to what we did in tutorials. Make sure to write things logically, and ensure that you've satisfied each part of the definition.
* [H2i).] The hint on the sheet will certainly help (can you see the difference of two squares trick here?) The definition is probably the best way to go here. Remember that making a positive denominator smaller will also make the fraction bigger too!
* [H2ii).] Feel free to use AoL here, but make sure to justify why you can use it!
* [H3.] This one is a bit tricky. Firstly, what do you get if you factorise $x^3 - y^3$? Next, you'll want to use the fact that $\lim_{n \to \infty} a_n = 1$ twice — once to introduce an $\epsilon$ into the problem, and again to find a point in the sequence after which all of the $a_n$ are positive. Combining all this information should help you prove the required result.
