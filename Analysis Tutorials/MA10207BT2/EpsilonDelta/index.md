---
title: "Analysis 1B — Epsilon-Delta Example"
author: 'Christian Jones: University of Bath'
date: 'February 2023'
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
      download: [["EpsilonDelta.html", "HTML page"], ["EpsilonDelta.pdf","Standard print PDF"], ["EpsilonDeltaClear.pdf","Clear print PDF"], ["EpsilonDeltaLarge.pdf","Large print PDF"], ["EpsilonDelta.docx","Accessible Word document"], ["EpsilonDelta.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
  clavertondown::html_clav:
    toc: true
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

# Introduction {-}
Here is an extra example of finding the limit of a function using the definition. This should hopefully give you a guide to the techniques required, and how much detail you should put in your solutions.

# Worked Example
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-2"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>Let $f : \mathbb{R} \to \mathbb{R}$ be defined by $$f(x) = \begin{cases}
\frac{1}{x^2}\;\;\text{if}\;\;x\in\mathbb{R}\setminus\lbrace 0\rbrace,\\
0 \;\;\;\;\text{if}\;\;x=0.\end{cases}$$ Prove that $\lim_{x\to 1} f(x) = 1.$</p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>Fix $\epsilon>0$, and suppose that $0<\lvert x - 1 \rvert < \delta$ for some $\delta > 0$ to be chosen later. Without loss of generality, suppose that $\delta \leq 1$. Then 
\begin{align*}
\lvert f(x) - 1 \rvert &= \bigg\lvert \frac{1}{x^2} - 1 \bigg\rvert,\\
&= \bigg\lvert \frac{1 - x^2}{x^2} \bigg\rvert,\\
&= \frac{\lvert x - 1 \rvert \lvert x + 1\rvert}{\lvert x \rvert ^2}.
\end{align*}

Now, by the triangle inequality, we have that $$\lvert x + 1 \rvert = \lvert x - 1 + 2 \rvert \leq \lvert x - 1 \rvert + 2.$$ Also, by the reverse triangle inequality, $$\lvert x \rvert = \lvert x - 1 + 1 \rvert \geq 1 - \lvert x - 1 \rvert.$$ So, if $\delta \leq \frac{1}{2}$, we obtain $\lvert x + 1 \rvert < \frac{5}{2}$, $\lvert x \rvert > \frac{1}{2}$, and
\begin{align*}
\lvert f(x) - 1 \rvert < \frac{5/2 \lvert x - 1 \rvert}{\left(1/2\right)^2} = 10\lvert x - 1 \rvert < 10\delta.
\end{align*}

Hence, if $\delta = \min\lbrace 1 , 1/2, \epsilon/10\rbrace$, we find that
\begin{align*}
0<\lvert x - 1 \rvert < \delta \Longrightarrow \lvert f(x) - 1 \rvert < \epsilon
\end{align*}

Finally, since $\epsilon$ was arbitrary, we conclude that $\lim_{x\to 1} f(x) = 1,$ as required.
</p></div>\EndKnitrBlock{solution}

<!--chapter:end:index.Rmd-->

