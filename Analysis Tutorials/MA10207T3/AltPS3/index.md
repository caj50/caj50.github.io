---
title: "Analysis 1A — Tutorial 3"
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
      download: [["AltPS3.html", "HTML page"], ["AltPS3.pdf","Standard print PDF"], ["AltPS3Clear.pdf","Clear print PDF"], ["AltPS3Large.pdf","Large print PDF"], ["AltPS3.docx","Accessible Word document"], ["AltPS3.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
  clavertondown::epub_clav:
    toc: false
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
header-includes:
  - \newcommand{\BOO}{BOO}
  - \usepackage {hyperref}
  - \hypersetup {colorlinks = true, linkcolor = blue, urlcolor = blue}
---
<!-- This is needed since I am working with svg files from mathcha.io. It converts the graphics files to something that can be used in the pdf files. Code taken from https://stackoverflow.com/questions/50165404/how-to-make-a-pdf-using-bookdown-including-svg-images/56044642#56044642 -->

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is a version of Tutorial Question 4 off of Problem Sheet 3 with an alternative solution for part c). Parts a) and b) are included for completeness.

\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong>(\#exm:ex1)  (PS3 Question 4) </strong></span><div>a)  Show that $$ 2xy \leq x^2 + y^2, \;\; \forall x,y \in \mathbb{R},$$ and that equality holds only if $x = y$.
b)  Show that $$\sqrt{\frac{x}{2}} + \sqrt{\frac{y}{2}} \leq \sqrt{x + y} \leq \sqrt{x} + \sqrt{y}, \;\; \forall x,y > 0.$$
c)  Prove that $$\lvert \sqrt{1 + x^2} - \sqrt{1 + y^2} \rvert \leq \lvert x - y \rvert \;\; \forall x,y \in \mathbb{R}.$$</div></div>\EndKnitrBlock{example}

## Part a) {-}
\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>We have that for any $x,y\in\mathbb{R},$ $$ 0 \leq (x-y)^2 = x^2 - 2xy + y^2,$$ from which rearranging gives $$2xy \leq x^2 + y^2.$$ Now, $$2xy = x^2 + y^2\; \Leftrightarrow\; 0 = (x-y)^2 \;\Leftrightarrow \;x-y = 0 \;\Leftrightarrow\; x=y.$$ So equality holds *if and only if* $x = y.$</p></div>\EndKnitrBlock{solution}

## Part b) {-}
\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>Consider the second inequality first. Note that since $x,y > 0$, $\sqrt{x}, \sqrt{y} > 0$, and so $$x + y \leq x + 2\sqrt{x}\sqrt{y} + y = (\sqrt{x} + \sqrt{y})^2.$$ Square rooting this result gives us that $$\sqrt{x + y} \leq \sqrt{x} + \sqrt{y}.$$ Next, we have that
\begin{align*}
\left(\sqrt{\frac{x}{2}} + \sqrt{\frac{y}{2}}\right)^2 &= \frac{x}{2} + 2\sqrt{\frac{x}{2}}\sqrt{\frac{y}{2}} + \frac{y}{2},\\
&\leq \frac{x}{2} + 2\left(\frac{x}{2} + \frac{y}{2}\right) + \frac{y}{2} \;\;\; \text{(by part a)},\\
&= x + y.
\end{align*}
Again, square rooting gives us that $$\sqrt{\frac{x}{2}} + \sqrt{\frac{y}{2}} \leq \sqrt{x + y}.$$</p></div>\EndKnitrBlock{solution}

## Part c) {-}
\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>Firstly for $x = -y$, $$\lvert \sqrt{1 + x^2} - \sqrt{1 + y^2}\rvert = 0 \leq \lvert -2y \rvert = \lvert x - y \rvert.$$ For $x \neq -y$, we have
\begin{align}
\lvert \sqrt{1 + x^2} - \sqrt{1 + y^2}\rvert &= \frac{\lvert 1 + x^2 - (1 + y^2) \rvert}{\sqrt{1 + x^2} + \sqrt{1 + y^2}},\tag{*}\\
&= \frac{\lvert x^2 - y^2 \rvert}{\sqrt{1 + x^2} + \sqrt{1 + y^2}},\nonumber\\
&= \frac{\lvert x + y \rvert \lvert x - y \rvert}{\sqrt{1 + x^2} + \sqrt{1 + y^2}}.\nonumber
\end{align}
Now, $$\lvert x \rvert \leq \sqrt{1 + x^2}, \;\;\text{and}\;\; \lvert y \rvert \leq \sqrt{1 + y^2}.$$ (This can be seen by squaring both sides of each inequality)

So,
\begin{align*}
\lvert x + y \rvert &\leq \lvert x \rvert + \lvert y \rvert \;\;\; \text{(by the triangle inequality)}\\
&\leq \sqrt{1 + x^2} + \sqrt{1 + y^2},\\
\Leftrightarrow \frac{1}{\lvert x + y \rvert} &\geq \frac{1}{\sqrt{1 + x^2} + \sqrt{1 + y^2}}.
\end{align*}
Therefore,
\begin{align}
\lvert \sqrt{1 + x^2} - \sqrt{1 + y^2}\rvert &= \frac{\lvert x + y \rvert \lvert x - y \rvert}{\sqrt{1 + x^2} + \sqrt{1 + y^2}},\nonumber\\
&\leq \frac{\lvert x - y \rvert\lvert x + y \rvert}{\lvert x + y \rvert},\tag{**}\\
&= \lvert x - y \rvert,\nonumber
\end{align}
as required!</p></div>\EndKnitrBlock{solution}
You might have a few questions about this:

**Q1)**  Why is 4c) done in this way?

A1)  It's an alternative way to the one in the model solutions, but I think it's good because it uses some techniques that are useful for the sequences part of the course (e.g. the triangle inequality and step (\*)).

**Q2)**  Where on Earth did the case $x = -y$ come from?

A2)  If you look at (\*\*), this expression doesn't work if $x = -y$, so you need to consider this separately. It's not an obvious case until you actually reach (\*\*), but once you realise it, it's an easy thing to add to the start of your solution.

**Q3)**  What about (\*)? Where does this come from?

A3)  Recall for $a,b \in \mathbb{R}$, $$(a-b)(a+b) = a^2 - b^2.$$ Taking $a = \sqrt{1 + x^2}, \;\; \text{and} \;\; b = \sqrt{1 + y^2},$ we have that $$\sqrt{1 + x^2} - \sqrt{1 + y^2} = \frac{(1+x^2)-(1+y^2)}{\sqrt{1 + x^2} + \sqrt{1 + y^2}}.$$

<!--chapter:end:index.Rmd-->

