---
title: "Analysis 1B — Supplementary Paper 2020"
author: 'Christian Jones: University of Bath'
date: 'May 2023'
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
      download: [["MA10207Paper2020.html", "HTML page"], ["MA10207Paper2020.pdf","Standard print PDF"], ["MA10207Paper2020Clear.pdf","Clear print PDF"], ["MA10207Paper2020Large.pdf","Large print PDF"], ["MA10207Paper2020.docx","Accessible Word document"], ["MA10207Paper2020.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
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
Here are the solutions to the past paper discussed in the revision session on 9th May 2023. This is designed as a guide to how much to write in the exam, and how you might want to style your solutions. To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Question 1 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-2"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>Let $f:\mathbb{R}\to\mathbb{R}$ be given by $$f(x) = \frac{2x^2 - 2}{x^2 + x + 2}.$$
  
  a)  Using the $\epsilon-\delta$ definition, prove that $$\lim_{x\to 0}f(x) = -1.$$
  b)  Using the *Algebra of Limits* and the *Sequential Characterisation of Limits*, show that $$\lim_{x \to \pm 1} f(x) = 0.$$
</p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
a)  Fix $\epsilon > 0$ and suppose $0 < \lvert x - 0 \rvert < \delta$ for some $\delta > 0$ to be chosen later. Then
\begin{align*}
\lvert f(x) - (-1)\rvert &= \left\lvert \frac{2x^2 - 2}{x^2 + x + 2} - (-1) \right\rvert,\\
&= \frac{\lvert x \rvert\lvert 3x + 1\rvert}{\lvert x^2 + x + 2\rvert}.
\end{align*}
Now,
\begin{align*}
\lvert 3x + 1\rvert &\leq 3\lvert x \rvert + 1 \;\;&&\text{(by the triangle ineq.)},\\
&< 4 \;\; &&\text{(if $\delta < 1$)}.
\end{align*}
Also,
\begin{align*}
\lvert x^2 + x + 2\rvert &= \lvert 2 - (-x-x^2)\rvert,\\
&\geq 2 - \lvert x + x^2 \rvert,\;\; &&\text{(by the reverse triangle ineq.)},\\
&\geq 2 - \lvert x \rvert - \lvert x \rvert^2,\;\; &&\text{(by the triangle ineq.)},\\
&> \frac{5}{4}.\;\; &&\text{(if $\delta < \frac{1}{2}$)}.
\end{align*}
So, if $\delta \leq \min\lbrace 1/2,1\rbrace$, we find that
\begin{align*}
\lvert f(x) - (-1)\rvert < \frac{4\lvert x \rvert}{5/4} = \frac{16\lvert x \rvert}{5} < \frac{16\delta}{5}.
\end{align*}
Hence, if $\delta = \min\lbrace 1/2, 5\epsilon/16\rbrace, we get that 0<\lvert x - 0 \rvert < \delta implies that $\lvert f(x) - (-1) \rvert < \epsilon.$ Since $\epsilon > 0 $ was arbitrary, we conclude that $$\lim_{x\to 0}f(x) = -1.$$
  
b)  Consider the limit as we approach $x = 1.$ Let $(x_n)_n$ be a sequence in $\mathbb{R}\setminus\lbrace 1 \rbrace$ with $x_n \to 1$ as $n \to \infty.$ Then, as $n\to\infty$ the algebra of limits says that $$f(x_n) = \frac{2x_n^2 - 2}{x_n^2 + x_n+ 2} \to \frac{2(1)^2 - 2}{(1)^2 + 1 + 2} = \frac{0}{4} = 0.$$ Since the sequence $(x_n)_n$ was arbitrary, we find that $$\lim_{x \to  1} f(x) = 0$$ by the sequential characterisation of limits. Similar arguments[^1] also show that $$\lim_{x \to - 1} f(x) = 0.$$</p></div>\EndKnitrBlock{solution}

[^1]: If you've got time in the exam, I'd advise you do this calculation in full.

# Question 2 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-4"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>a)  Let $f: \mathbb{R} \to \mathbb{R}$ be given by $$f(x) = 3x^2 - 5x -1.$$ Using the *Algebra of Limits*, prove that $f$ is continuous everywhere on $\mathbb{R}$.
b)  Let the function $g:\mathbb{R} \to \mathbb{R}$ be given by $$g(x) = x^5 -3x^4+2x^3-x^2-2x+1.$$ Show that there exists three points $c_1,c_2$ and $c_3$ such that $g(c_1)=g(c_2)=g(c_3)=0.$ (You may assume results from the course without proof). [*Hint: Compute $g(0)$ and $g(1).$*]
</p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
a) Fix $c \in \mathbb{R}$, and let $(x_n)_n$ be a sequence in $\mathbb{R}$ with $x_n \to c$ as $n \to \infty.$ Then, by the algebra of limits, we find that as $n \to \infty$: $$f(x_n) = 3x_n^2 - 5x_n -1 \to 3(c)^2 - 5(c) - 1 = f(c).$$ Since the sequence $(x_n)_n$ was arbitrary, the sequential characterisation of continuity says that $f$ is continuous at $c$. Since $c$ was also arbitrary, $f$ is continuous everywhere on $\mathbb{R}.$

b) Firstly, as $g$ is a polynomial, it is continuous on $\mathbb{R}$, and is so too on any subinterval of $\mathbb{R}$. Considering $g$ restricted to $[0,1]$, we have since $$g(0) = 1 > 0 > -2 = g(1),$$ the Intermediate Value Theorem says that $\exists c_2 \in [0,1]$ such that $g(c_2) = 0.$ Now, note further that $$g(-1000) < 0 < 1 = g(0),$$ so by the IVT again, there exists $c_1 \in [-1000,0]$ with $g(c_1) = 0.$ Finally, as $$g(1) = -2 < 0 < g(1000),$$ a third application of the IVT gives that there exists $c_3 \in [1,1000],$ with $g(c_3) = 0,$ as required.

</p></div>\EndKnitrBlock{solution}

# Question 3 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-6"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>a)  Let $f: \mathbb{R} \to \mathbb{R}$ be defined by $$f(x) = \begin{cases} 0 \;\; \text{if $x \leq 0$},\\
x \;\; \text{if $x > 0$}.\end{cases}$$ Find all points where $f$ is differentiable.
b)  Give an example of a continuous function $f:\mathbb{R} \to \mathbb{R}$ which is differentiable in $\mathbb{R}\setminus\lbrace 0,1\rbrace$ and not differentiable at $0$ and $1$.
c) Let $f: \mathbb{R} \to \mathbb{R}$ be defined by $$f(x) = (x^3 - 9x^2 + 29x - 35)\mathrm{e}^x.$$ On what intervals is the function $f$ increasing? [*Hint: $x=1$ is a critical point of $f$.*]
d) Let $f:[0,1] \to \mathbb{R}$ be continuous and differentiable in $(0,1).$ Assume that $f(0) = 0$ and that $f'$ is increasing in $(0,1).$ Prove that $g:(0,1) \to \mathbb{R}$ defined by $g(x) = \frac{f(x)}{x}$ is increasing in $(0,1).$ [*Hint: Use the Mean Value Theorem.*]

</p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>a)  Firstly, as polynomials are differentiable, we know that $f$ is differentiable on $\mathbb{R}\setminus\lbrace 0 \rbrace,$ with $$f'(x) = \begin{cases} 0 \;\; \text{if $x < 0$},\\
1 \;\; \text{if $x > 0$}.\end{cases}$$ However, $f$ is not differentiable at $0.$ To see this, first consider for $x>0.$ $$\frac{f(x) - f(0)}{x - 0} = \frac{x}{x} = 1 \to 1 \;\;\text{as $x \to 0^{+}$}.$$ However, for $x < 0$, $$\frac{f(x) - f(0)}{x - 0} = 0 \to 0 \;\;\text{as $x \to 0^{-}$}.$$ Hence, as $$\lim_{x\to 0^{-}}\frac{f(x) - f(0)}{x - 0} \neq \lim_{x\to 0^{+}}\frac{f(x) - f(0)}{x - 0},$$ $f$ is not differentiable at $0.$ So $f$ is differentiable only on $\mathbb{R}\setminus\lbrace 0 \rbrace.$
b)  Consider $f:\mathbb{R} \to \mathbb{R}$ given by $$f(x) = \lvert x \rvert + \lvert x - 1 \rvert = \begin{cases} 1 - 2x \;\; \text{if $x \leq 0$},\\
1\;\;\quad\quad\; \text{if $0 < x \leq 1$},\\
2x - 1\;\; \text{if $x > 1$}.\end{cases}$$ Since $f$ is a composition of continuous functions on $\mathbb{R}$, it is continuous on $\mathbb{R}.$ It is also differentiable on $\mathbb{R}\setminus\lbrace 0,1\rbrace$, with $$f'(x) = \begin{cases} - 2 \;\; \text{if $x < 0$},\\
0\;\;\; \text{if $0 < x < 1$},\\
2 \;\;\;\; \text{if $x > 1$}.\end{cases}$$ However, at $x=0$ (similarly for $x=1$), we find that $$\lim_{x \to 0^{-}}\frac{f(x) - f(0)}{x - 0} = -2 \neq 0 = \lim_{x \to 0^{+}}\frac{f(x) - f(0)}{x - 0},$$ so $f$ is not differentiable at $0$ or $1$.
c)  As $f$ is a product of a polynomial and the exponential function, it is differentiable on $\mathbb{R}$ by the product rule, with derivative function $$f(x) = (3x^2-18x+29)\mathrm{e}^x + (x^3 - 9x^2 +29x -35)\mathrm{e}^x = (x^3 - 6x^2 + 11x -6)\mathrm{e}^x.$$ Using the hint (and that the exponential is positive for all $x$), we can factorise this as
\begin{align*}
f'(x) = (x-1)(x^2-5x-6)\mathrm{e}^x = (x-1)(x-2)(x-3)\mathrm{e}^x.
\end{align*}
Now, note that $f'(x) > 0$ when either $1 < x < 2$ or $x > 3$. By a theorem from lectures, this says that $f$ is increasing on the intervals $[1,2]$ and $[3,\infty).$
d) Fix $x,y$ in $(0,1)$, and suppose WLOG that $x < y$. By the algebra of continuity and the quotient rule, $g$ is continuous on $[x,y]$ and differentiable on $(x,y).$ Hence, by the Mean Value Theorem, $\exists \chi \in (x,y)$ such that $$\frac{g(y) - g(x)}{y - x} = g'(\chi).$$ Now, $$g'(\chi) = \frac{f'(\chi)}{\chi} - \frac{f(\chi)}{\chi^2},$$ so to prove $g(y) \geq g(x),$ we need the following implication to hold:
\begin{align*}
g'(\chi) \geq 0 &\Leftrightarrow \frac{f'(\chi)}{\chi} - \frac{f(\chi)}{\chi^2} \geq 0,\\
&\Leftrightarrow f'(\chi) \geq \frac{f(\chi)}{\chi}.
\end{align*}
Now, applying the MVT to $f$ on the interval $[0,\chi]$, we find that there exists $c \in (0,\chi)$ such that $$\frac{f(\chi)}{\chi} = \frac{f(\chi) - f(0)}{x - 0} = f'(c).$$ Since $f'$ is increasing on $(0,1)$, $$\frac{f(\chi)}{\chi} = f'(c) \leq f'(\chi),$$ which proves that $g(y) \geq g(x).$ Since $x,y$ were arbitrary, $g$ is increasing on $(0,1),$ as required.

</p></div>\EndKnitrBlock{solution}


# Question 4 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-8"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>a)  Give an example of a function $f:\mathbb{R} \to \mathbb{R}$ which is differentiable on $\mathbb{R}$, twice differentiable on $\mathbb{R}\setminus\lbrace 0 \rbrace$ and not twice differentiable at $0$.
b) What theorem from the lectures is natural to use to answer the following question?
  *Find a polynomial p(x) with rational coefficients such that $$\lvert \sin(x) - p(x)\rvert \leq 10^{-6}\;\;\forall x \; \text{in}\;[0,1].$$* Explain your reasoning.
c) There exists a twice differentiable function $f:\mathbb{R} \to \mathbb{R}$ such that $$f(x) + \mathrm{e}^{f(x)} = \cos\left(\frac{x}{3}\right) + \frac{x}{3\sqrt{2}}.$$ 
Find all critical points of $f$ and determine whether they are local maxima, local minima or none of these.

</p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>a) Consider $f:\mathbb{R} \to \mathbb{R}$ given by $$f(x) = \frac{x\lvert x \rvert}{2} = \begin{cases}
-\frac{x^2}{2} \quad \text{if $x < 0$},\\
\;\;\;\frac{x^2}{2} \quad \text{if $x \geq 0$}.\end{cases}$$ Since $f$ is defined piecewise by polynomials, we know $f$ is differentiable on $\mathbb{R}\setminus\lbrace 0 \rbrace$ with $$f'(x) =\begin{cases}
-x \quad \text{if $x < 0$},\\
\;\;\;x \quad \text{if $x > 0$}.\end{cases}$$ Also, we have that as $x \to 0$: $$\left\lvert\frac{f(x) - f(0)}{x - 0} \right\rvert = \lvert x \rvert \to 0,$$ which implies that $f'(0)$ exists and is equal to $0$. Therefore $f$ is once differentiable on $\mathbb{R}$ with $$f'(x) = \lvert x \rvert.$$ From lectures, we know that $f'$ is differentiable only on $\mathbb{R}\setminus\lbrace 0 \rbrace$, which means that $f$ is twice differentiable on $\mathbb{R}\setminus\lbrace 0 \rbrace$ and not twice differentiable at $0$, as required.
b) It is natural to use Taylor's theorem. ADD JUSTIFICATION
c) By the chain rule, as $f$, $\exp$ and $\cos$ are twice differentiable, each term in the equation is twice differentiable. In particular, differentiating once, we find that $$f'(x) + f'(x)\mathrm{e}^{f(x)} = -\frac{1}{3}\sin\left(\frac{x}{3}\right) + \frac{1}{3\sqrt{2}}.$$ At critical points, $f'(x) = 0$, so critical points satisfy
\begin{align*}
&\quad 0 = -\frac{1}{3}\sin\left(\frac{x}{3}\right) + \frac{1}{3\sqrt{2}},\\
&\Leftrightarrow \sin\left(\frac{x}{3}\right) = \frac{1}{\sqrt{2}},\\
&\Leftrightarrow \frac{x}{3} = \frac{\pi}{4} + 2k\pi, \;\; \text{or} \;\; \frac{x}{3} = \frac{3\pi}{4} + 2k\pi,\;\;\text{for $k \in \mathbb{Z}$},\\
&\Leftrightarrow x = \frac{3\pi}{4} + 6k\pi\;\; \text{or} \;\; x = \frac{9\pi}{4} + 6k\pi,\;\;\text{for $k \in \mathbb{Z}$},\\
\end{align*}
These are the required critical points. Now, differentiating our equation again yields
\begin{align*}
f''(x) + f''(x)\mathrm{e}^{f(x)} + f'(x)^2\mathrm{e}^{f(x)} = -\frac{1}{9}\cos\left(\frac{x}{3}\right).
\end{align*}
Evaluating at $x = \frac{3\pi}{4} + 6k\pi$, we find that
\begin{align*}
&\quad f''(x)\left(1 + \mathrm{e}^{f(x)}\right) = -\frac{1}{9}\cos\left(\frac{\pi}{4}+2k\pi\right),\\
&\Leftrightarrow f''(x)\left(1 + \mathrm{e}^{f(x)}\right) = -\frac{1}{9\sqrt{2}},\\
&\Rightarrow f''(x) < 0.
\end{align*}
This means that the critical points $x = \frac{3\pi}{4} + 6k\pi$ with $k \in \mathbb{Z}$ correspond to local maxima. Evaluating at $x = \frac{9\pi}{4} + 6k\pi$, we find that
\begin{align*}
&\quad f''(x)\left(1 + \mathrm{e}^{f(x)}\right) = -\frac{1}{9}\cos\left(\frac{3\pi}{4}+2k\pi\right),\\
&\Leftrightarrow f''(x)\left(1 + \mathrm{e}^{f(x)}\right) = \frac{1}{9\sqrt{2}},\\
&\Rightarrow f''(x) > 0.
\end{align*}
This means that the critical points $x = \frac{9\pi}{4} + 6k\pi$ with $k \in \mathbb{Z}$ correspond to local minima.

</p></div>\EndKnitrBlock{solution}

<!--chapter:end:index.Rmd-->

