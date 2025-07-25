---
title: "Analysis 1A — Supremum Example"
author: 'Christian Jones: University of Bath'
date: 'October 2023'
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
      download: [["OldPS2.html", "HTML page"], ["OldPS2.pdf","Standard print PDF"], ["OldPS2Clear.pdf","Clear print PDF"], ["OldPS2Large.pdf","Large print PDF"], ["OldPS2.docx","Accessible Word document"], ["OldPS2.epub","Accessible EPub book" ]]
      sharing: no
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
<!-- This is needed since I am working with svg files from mathcha.io. It converts the graphics files to something that can be used in the pdf files. Code taken from https://stackoverflow.com/questions/50165404/how-to-make-a-pdf-using-bookdown-including-svg-images/56044642#56044642 -->

\newpage
\pagenumbering{arabic}

# Question {-}
Here is an example of finding the supremum of a set taken from an old problem sheet, together with three possible methods to find it.
\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:unnamed-chunk-2"><span class="exm:unnamed-chunk-2" custom-style="NameStyle"><strong>(\#exm:unnamed-chunk-2) </strong></span><div>Let $$B = \left\lbrace \frac{2n-1}{n+1} \lvert n \in \mathbb{N}\right\rbrace.$$ Show that $B$ is bounded above and find $\sup(B).$</div></div>\EndKnitrBlock{example}

## Method 1 --- Contradiction {-}
\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>First, note for $n\in\mathbb{N}$: $$\frac{2n-1}{n+1} = \frac{2n+2-3}{n+1} = 2 - \frac{3}{n+1} < 2.$$ Hence $B$ is bounded above by $2$. Therefore, by the completeness axiom, as $B \neq \emptyset,$ $\sup(B)$ exists and $\sup(B) \leq 2.$

Next, suppose for contradiction that $\sup(B) < 2$. Now, for any $x < 2,$ $$2 - \frac{3}{n+1} > x \Leftrightarrow n+1 > \frac{3}{2-x} \Leftrightarrow n > \frac{3}{2-x} - 1.$$ Taking $x = \sup(B)$ and applying Archimedes Postulate, $\exists N \in \mathbb{N}$ such that
\begin{align*}
N &> \frac{3}{2-\sup(B)} - 1,\\
\Leftrightarrow 2 - \frac{3}{N+1} &> \sup(B),
\end{align*}
which is a contradiction as $2 - \frac{3}{N+1} \in B.$ Hence $\sup(B) \geq 2$, and by combining our found inequalities, $\sup(B)=2$.</p></div>\EndKnitrBlock{solution}

## Method 2 --- Alternative Characterisation of Suprema {-}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>First, note for $n\in\mathbb{N}$: $$\frac{2n-1}{n+1} = \frac{2n+2-3}{n+1} = 2 - \frac{3}{n+1} < 2.$$ Hence $B$ is bounded above by $2$. Therefore as $B \neq \emptyset,$ the completeness axiom says that $\sup(B)$ exists.

We claim that $\sup(B) = 2.$ Fix $\epsilon > 0.$ Then, for $n \in \mathbb{N}:$
\begin{align*}
2 - \frac{3}{n+1} &> 2-\epsilon,\\
\Leftrightarrow \epsilon &> \frac{3}{n+1},\\
\Leftrightarrow n\epsilon &> 3 - \epsilon,\\
\Leftrightarrow n &> \frac{3-\epsilon}{\epsilon}.
\end{align*}
Now, by Archimedes Postulate, $\exists N \in \mathbb{N}$ such that $N > \frac{3-\epsilon}{\epsilon}$, from which $$2 - \frac{3}{N+1} > 2- \epsilon.$$ At this stage, take $b = 2 - \frac{3}{N+1} \in B$. Since $\epsilon > 0$ was arbitrary, we have that $\forall \epsilon > 0, \exists b \in B$ such that $b > 2-\epsilon.$ So, by the alternative characterisation of suprema (Theorem 3.2), $\sup(B) = 2.$</p></div>\EndKnitrBlock{solution}

## Method 3 --- Limits {-}
Note that this doesn't work in general, but it might be quicker when you can use it. It relies on the following theorem (which we'll eventually cover):
\BeginKnitrBlock{theorem}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-theorem" custom-style="TheoremStyle" id="thm:unnamed-chunk-5"><span class="thm:unnamed-chunk-5" custom-style="NameStyle"><strong>(\#thm:unnamed-chunk-5) </strong></span><p>A bounded, increasing sequence $(b_n)_{n \in \mathbb{N}}$ is convergent, and its limit is given by $$\lim_{n \to \infty} b_n = \sup\lbrace b_n \,\lvert\, n \in \mathbb{N} \rbrace.$$</p></div>\EndKnitrBlock{theorem}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>Define $b_n = \frac{2n - 1}{n+1}$ for $n \in \mathbb{N}$.

**Step 1 --- Show $(b_n)_n$ is bounded above**:
  
First, note for $n\in\mathbb{N}$: $$b_n = \frac{2n+2-3}{n+1} = 2 - \frac{3}{n+1} < 2.$$ Hence $B$ is bounded above by $2$. Therefore, as $B \neq \emptyset,$ the completeness axiom says that $\sup(B)$ exists.

**Step 2 --- Show $(b_n)_n$ is increasing (i.e. show $b_{n+1} \geq b_n \; \forall n \in \mathbb{N}$)**:
  
We have for $n \in \mathbb{N}$,
\begin{align*}
b_{n+1} - b_{n} &= 2 - \frac{3}{n+2} - \left(2 - \frac{3}{n+1}\right),\\
&= \frac{3(n+2)-3(n+1)}{(n+1)(n+2)},\\
&= \frac{3}{(n+1)(n+2)},\\
&\geq 0.
\end{align*}
So $(b_n)$ is increasing. Hence, by the above theorem, $(b_n)$ converges, and by the *Algebra of Limits*, $$\sup(B) = \lim_{n \to \infty} b_n = \lim_{n \to \infty} \left(2 - \frac{\frac{3}{n}}{1 + \frac{1}{n}}\right) = 2,$$
as expected!
  
  </p></div>\EndKnitrBlock{solution}

<!--chapter:end:index.Rmd-->

