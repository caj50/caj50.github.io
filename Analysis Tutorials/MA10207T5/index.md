---
title: "Analysis 1A — Tutorial 5"
author: 'Christian Jones: University of Bath'
date: 'November 2023'
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
  - \usepackage {hyperref}
  - \hypersetup {colorlinks = true, linkcolor = blue, urlcolor = blue}
---
<!-- This is needed since I am working with svg files from mathcha.io. It converts the graphics files to something that can be used in the pdf files. Code taken from https://stackoverflow.com/questions/50165404/how-to-make-a-pdf-using-bookdown-including-svg-images/56044642#56044642 -->

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is the material to accompany the Analysis Tutorial in Week 5. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Lecture Recap

## Sequences

### Two Useful Theorems
Last week, we were introduced to the idea of sequences and what it means for a sequence to *converge*. The definition of this is repeated below.

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Sequence Convergence) </strong></span><div>A sequence $(a_n)_{n\in\mathbb{N}}$ converges to a real number $L$ as $n \longrightarrow \infty$, written as either $a_n \longrightarrow L$, or $\lim_{n \to \infty}a_n = L$ if $$\forall \epsilon > 0, \; \exists N = N(\epsilon) \in \mathbb{N}, \; \text{such that} \; \forall n \geq N, \; \lvert a_n - L \rvert < \epsilon.$$</div></div>\EndKnitrBlock{definition}

Using this definition, we can establish two theorems which will really help us when looking for further results about sequences.

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong>(\#thm:thm1)  (Preservation of Non-Strict Inequalities) </strong></span><p>Let $(a_n)_{n\in\mathbb{N}}$ and $(b_n)_{n\in\mathbb{N}}$ be sequences and let $L,M \in \mathbb{R}$ be such that $a_n \to L$ and $b_n \to L$ as $n \to \infty$. If $a_n \leq b_n \; \forall n \in \mathbb{N}$, then $L \leq M$.</p></div>\EndKnitrBlock{theorem}
There are two good uses for this theorem. The first says that non-negative sequences should have non-negative limits (which is something you might expect). Before we state the second, we mention one more thing, which is **not true**:
\BeginKnitrBlock{Non-theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Non-theorem" custom-style="TheoremStyle" id="Non-theorem:unnamed-chunk-2"><span class="Non-theorem" custom-style="NameStyle"><strong> Non-theorem: </strong></span><p> Let $(a_n)_{n\in\mathbb{N}}$ and $(b_n)_{n\in\mathbb{N}}$ be sequences and let $L,M \in \mathbb{R}$ be such that $a_n \to L$ and $b_n \to L$ as $n \to \infty$. If $a_n < b_n \; \forall n \in \mathbb{N}$, then $L < M$.</p></div>\EndKnitrBlock{Non-theorem}
To see why this is false, consider the sequences defined by $a_n = 1 - \frac{1}{n}$ and $b_n = 1$. We note that each $a_n$ is strictly less than each corresponding $b_n$, but we find that $$\lim_{n \to \infty} a_n = 1 = \lim_{n \to \infty} b_n.$$

The second reason why Theorem \@ref(thm:thm1) is so important, is that it gives us this second theorem[^1]:
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm2"><span class="thm:thm2" custom-style="NameStyle"><strong>(\#thm:thm2)  (Uniqueness of Limits) </strong></span><p>If $(a_n)_{n\in\mathbb{N}}$ is convergent with $a_n \to L$ and $a_n \to M$ as $n \to \infty$, then $L = M$.</p></div>\EndKnitrBlock{theorem}

[^1]: Feel free to ignore this footnote, but there are areas of maths where limits are not unique. This is usually in the realm of topology, which you can take in Year 3 [(MA30055)](https://www.bath.ac.uk/catalogues/2023-2024/ma/MA30055.html). Luckily for us, everything behaves nicely, and our limits are unique.

### Bounded Sequences
Much like we have done with sets, we can formulate a definition which allows us to 'trap' sequences.

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Bounded Sequence) </strong></span><div>A sequence $(a_n)$ is bounded if there exists $M \in \mathbb{R}$ such that $\lvert a_n \rvert \leq M$.</div></div>\EndKnitrBlock{definition}
If you prefer to think diagramatically, this says we can trap the sequence within a strip of width $2M$ centred round $0$. More importantly, this leads to the idea that *all convergent sequences are bounded*. Note that this is equivalent to saying that if a sequence is not bounded, then it is not convergent.

### Algebra of Limits
Using the definition to prove all limits would be an incredibly boring way to go through this course. Luckily, there are a few general results we can prove which make our lives so much easier. This is known as the *algebra of limits* (AoL).

\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong>(\#thm:thm4)  (Algebra of Limits) </strong></span><p>Let $A,B,c \in \mathbb{R}$ and let $(a_n)$ and $(b_n)$ be sequences with $a_n \to A$ and $b_n \to B$ as $n \to \infty$. Then:

1. $\lim_{n \to \infty} (a_n + b_n) = A + B$,
2. $\lim_{n \to \infty} (ca_n) = cA$,
3. $\lim_{n \to \infty} (a_n b_n) = AB$,
4. If $b_n \neq 0 \; \forall n \in \mathbb{N}$ and $B \neq 0$, $\lim_{n \to \infty} \frac{a_n}{b_n} = \frac{A}{B}$.
</p></div>\EndKnitrBlock{theorem}

# Hints
As per usual, here's where you'll find the problem sheet hints!

1.  i) At this stage of the course, you'll have to use the definition of convergence. Apply this, and follow the hint on the sheet.
    ii) This one you can apply AoL! However, you should explain why you can use AoL, namely: which convergence results from lectures are you applying?
2.  Again, this is one you have to use the definition on (for the time being, at least). Remember, if you make the denominator of a fraction smaller, you'll make the overall fraction bigger.
3.  For the first bit, you can use AoL! For the second, you'll have to use the definition, making a **specific** choice of $\epsilon.$
4. This is very similar to the first question from tutorials, so here's a few (vague-ish) hints:
    i) Try and find expressions to simplify the sums.
    ii) Again, you'll want to find an explicit expression for the sum of square numbers.
    iii) Firstly, what do you get if you factorise $a^3 - b^3$? The result of Tutorial Question 2 will also be useful here.
    iv) Evaluate $\cos(2n\pi).$
    v) Simplify the expression first.
    vi) You'll have to use the definition again here.
5. This is another definition question. Use the knowledge that $(a_n)$ converges (i.e. what does this mean explicitly?) to conclude something about the convergence of $(b_n)$.

<!--chapter:end:index.Rmd-->

