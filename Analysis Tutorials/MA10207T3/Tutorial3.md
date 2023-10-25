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
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
    pandoc_args: --default-image-extension=svg
  clavertondown::gitbook_clav:
    split_by: section
    keep_md: true
    config:
      download: [["Tutorial3.html", "HTML page"], ["Tutorial3.pdf","Standard print PDF"], ["Tutorial3Clear.pdf","Clear print PDF"], ["Tutorial3Large.pdf","Large print PDF"], ["Tutorial3.docx","Accessible Word document"], ["Tutorial3.epub","Accessible EPub book" ]]
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
  clavertondown::html_clav:
    toc: true
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
Here is the material to accompany the Analysis Tutorial in Week 3. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Lecture Recap

## Suprema and Infima
There's still a bit of material to cover regarding the supremum and infimum of a set. To begin, we re-cover the definitions from last week.
\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong><span id="def:def1"></span>Definition 1.1   (Supremum) </strong></span><div>Let $S \in \mathbb{R}$. A number $T \in \mathbb{R}$ is said to be the supremum of $S$ if it is an upper bound for $S$, and for any other upper bound $M$, $T \leq M$. Here, we write $T = \sup(S)$.</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong><span id="def:def2"></span>Definition 1.2   (Infimum) </strong></span><div>Let $S \in \mathbb{R}$. A number $t \in \mathbb{R}$ is said to be the infimum of $S$ if it is a lower bound for $S$, and for any other lower bound $m$, $t\geq m$. Here, we write $t = \inf(S)$.</div></div>\EndKnitrBlock{definition}
There's also two results from last week's notes that you didn't reach in lectures either, so we (re)state these below too.
\BeginKnitrBlock{Completeness Axiom}<div class="Completeness Axiom" custom-style="TheoremStyleUpright" id="CA:unnamed-chunk-2"><span class="Completeness Axiom" custom-style="NameStyle"><strong> Completeness Axiom: </strong></span><p>Every non-empty set $S$ in $\mathbb{R}$ that is bounded above has a supremum.</p></div>\EndKnitrBlock{Completeness Axiom}
 
\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong><span id="prp:prop1"></span>Proposition 1.1   (Archimedian Postulate) </strong></span><p>We have that $\forall x \in \mathbb{R}, \exists N \in \mathbb{N}$ such that $N > x.$ In other words, the set of natural numbers $\mathbb{N}$ is unbounded above.</p></div>\EndKnitrBlock{proposition}
As mentioned in last week's notes, the completeness axiom assumes that there are no 'gaps' in the real number line (and allows us to solve equations such as $x^2-2=0$, for example.) It's also worth mentioning how useful Archimedes' Postulate is --- this is usually the result you will contradict when showing a set is not bounded.

## Inequalities
Inequalities come up everywhere in maths! For example, they can be used in statistics for estimation (Markov/Chebyshev inequalities), they can be used as constraints in optimisation problems (see Section 3.1 of [this Wikipedia link.](https://en.wikipedia.org/wiki/Linear_programming)), and quite famously appear in Quantum Mechanics. In this latter case, we have the [Heisenberg Uncertainty Principle](http://hyperphysics.phy-astr.gsu.edu/hbase/uncer.html), and this inequality states that you can't simultaneously know the position and momentum of a quantum particle, such as an electron.

Most of the inequalities in this course will be based on the absolute value, which is defined as follows:
\BeginKnitrBlock{definition}<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong><span id="def:def3"></span>Definition 1.3   (Absolute Value) </strong></span><div>For $x \in \mathbb{R}$, the absolute value of $x$ is given by \begin{align*}
    \lvert x \rvert = \begin{cases}
    x \quad &\text{if} \; x \geq 0,\\
    -x \quad &\text{if} \; x < 0
    \end{cases}\;\; = \max\lbrace x, -x \rbrace.
\end{align*}</div></div>\EndKnitrBlock{definition}

The absolute value has the following properties:
\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop4"><span class="prp:prop4" custom-style="NameStyle"><strong><span id="prp:prop4"></span>Proposition 1.2  </strong></span><p>For $x,y \in \mathbb{R}$:
$$\begin{gather*}
   x \leq \lvert x \rvert,\quad -x \leq \lvert x \rvert,\quad \lvert -x \rvert = \lvert x \rvert\quad \text{and}\quad \lvert x y \rvert = \lvert x \rvert \lvert y \rvert.
\end{gather*}</p></div>\EndKnitrBlock{proposition}
Now we come on to what I consider to be the most important thing in this course.

\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm4"><span class="thm:thm4" custom-style="NameStyle"><strong><span id="thm:thm4"></span>Theorem 1.3   (Triangle Inequalities) </strong></span><p>For $x,y\in\mathbb{R}$:
  
  * $\lvert x + y \rvert \leq \lvert x \rvert + \lvert y \rvert$, and
  * $\left\lvert \lvert x \rvert - \lvert y \rvert \right\rvert \leq \lvert x - y \rvert.$
  </p></div>\EndKnitrBlock{theorem}
The first of these is known as the **Triangle Inequality**, and the second is the **Reverse Triangle Inequality**. Why do I think this is so important? This will come up in almost any course you take at university that uses analysis! If you're studying vector calculus, fluid mechanics, statistics, probability, or anything that's not abstract algebra, there's guaranteed to be a proof or technique which involves an inequality of this form! So if you only learn one result from Analysis 1A, make it this one.

Finally, there's one more inequality to mention — the binomial inequality.
\BeginKnitrBlock{proposition}<div class="bookdown-proposition" custom-style="TheoremStyleUpright" id="prp:prop5"><span class="prp:prop5" custom-style="NameStyle"><strong><span id="prp:prop5"></span>Proposition 1.4   (Binomial Inequality) </strong></span><p>We have $\forall n \in \mathbb{N}_0$ (i.e. all the natural numbers with $0$), and $\forall x \geq -1$, $$(1 + x)^n \geq 1 + nx.$$</p></div>\EndKnitrBlock{proposition}

# Hints
As per usual, here's where you'll find the problem sheet hints!

1. The techniques involved in this one are similar to those used in Tutorial Question 1 (and there were some questions on this last week too!)
2.
    i) Firstly, note that this is an **if and only if** statement, so there are two things to prove! You can get most of the way between both statements by completing the square on the polynomial. For the "$\Rightarrow$" direction, remember square numbers are non-negative. For the "$\Leftarrow$" direction, make a specific choice of $x$.
    ii) Follow the hint here, and be careful when collecting terms together.
3. Take cases on $x$.
4. Without loss of generality (WLOG), consider $x \geq y$ (otherwise you can just swap them), and consider $\lvert \sqrt{x} - \sqrt{y} \rvert^2$. On expanding, try and find a bound for the 'middle' term.
5. Solve the modulus equation, and then use your solutions to formulate simultaneous equations for $c$ and $r$.
6. You should only need the definitions given in lectures to solve this question. Make sure to write things logically!

<!--chapter:end:index.Rmd-->

