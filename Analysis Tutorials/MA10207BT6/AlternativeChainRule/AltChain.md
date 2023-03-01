---
title: "Alternative Chain Rule Proof"
author: 'Christian Jones: University of Bath'
date: 'March 2023'
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
  clavertondown::pdf_clav:
    latex_engine: pdflatex
    keep_tex: true
    fig_caption: true
    toc: true
    extra_dependencies: ["float"]
    pandoc_args: --default-image-extension=pdf
  clavertondown::gitbook_clav:
    split_by: section
    keep_md: true
    config:
      download: [["AltChain.html", "HTML page"], ["AltChain.pdf","Standard print PDF"], ["AltChainClear.pdf","Clear print PDF"], ["AltChainLarge.pdf","Large print PDF"], ["AltChain.docx","Accessible Word document"], ["AltChain.epub","Accessible EPub book" ]]
      sharing: no
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
<!-- This is needed since I am working with svg files from mathcha.io. It converts the graphics files to something that can be used in the pdf files. Code taken from https://stackoverflow.com/questions/50165404/how-to-make-a-pdf-using-bookdown-including-svg-images/56044642#56044642 -->

\newpage
\pagenumbering{arabic}

# Introduction {-}
Here is an alternative proof of the chain rule which uses the $\epsilon$-$\delta$ definition of the limit. It's quite involved, but its a great example if you want more practice with these types of arguments. The typed version here is based off of one presented by Adrian Hill, who previously lectured this course.

# The Chain Rule {-}
\BeginKnitrBlock{theorem}<div class="bookdown-theorem" custom-style="TheoremStyleUpright" id="thm:thm1"><span class="thm:thm1" custom-style="NameStyle"><strong><span id="thm:thm1"></span>Theorem 1   (Chain Rule) </strong></span><p>Let $g:(a,b) \to \mathbb{R}$ and $f:(A,B) \to \mathbb{R}$ be such that $g\left((a,b)\right) \subseteq (A,B).$ Assume that $g$ is differentiable at $c$ and $f$ is differentiable at $g(c)$. Then the composition $f\circ g$ is differentiable at $c$ with $$\left(f\circ g\right)'(c) = f'\left(g(c)\right)g'(c).$$</p></div>\EndKnitrBlock{theorem}

\BeginKnitrBlock{proof}<div class="bookdown-proof" custom-style="ProofStyle"><span class="proof" custom-style="NameStyle"><strong>Proof. </strong></span> <p>Firstly, note that using the definition of limit, we can recast this problem into the following form: given $\epsilon > 0$, we seek $\delta > 0$ such that
$$\begin{align}
\lvert x - c \rvert < \delta \Rightarrow \left\lvert (f\circ g)(x) - \left[(f\circ g)(c) + f'(g(c))g'(c)(x-c)\right]\right\rvert\leq \epsilon\lvert x - c \rvert \tag{*}
\end{align}$$

Now, fix $\epsilon > 0$, and let $\eta_1, \eta_2 > 0$ be determined later. As $f$ is differentiable at $g(c)$, $\exists \theta_1>0$ such that
$$\begin{align}
\lvert y - g(c) \rvert < \theta_1 \Rightarrow \left\lvert f(y) - \left[f(g(c)) + f'(g(c))(y - g(c))\right]\right\rvert \leq \eta_1\lvert y - g(c)\rvert \tag{1}
\end{align}$$

Also, as $g$ is differentiable at $c$, $\exists \theta_2 > 0$ such that
$$\begin{align}
\lvert x - c \rvert < \theta_2 &\Rightarrow \left\lvert g(x) - \left[g(c) + g'(c)(x - c)\right]\right\rvert \leq \eta_2\lvert x - c\rvert, \tag{2}\\
&\Rightarrow \lvert g(x) - g(c) \rvert \leq \left(\eta_2 + \lvert g'(c) \rvert\right)\lvert x - c \rvert. \tag{3}
\end{align}$$

So, if $\lvert x - c \rvert < \delta$ for
$$\begin{align}
\delta = \min\left\lbrace \theta_2, \frac{\theta_1}{\eta_2 + \lvert g'(c)\rvert}\right\rbrace, \tag{4}
\end{align}$$
then using (3), we find that

$$\begin{align*}
\lvert x - c \rvert < \delta \Rightarrow \lvert g(x) - g(c) \rvert < \left(\eta_2 + \lvert g'(c) \rvert\right)\delta \leq \theta_1.
\end{align*}$$

Substituting $y = g(x)$ into (1) then gives for $\lvert x - c \rvert < \delta$,
$$\begin{align*}
\left\lvert f(g(x)) - \left[f(g(c)) + f'(g(c))(g(x) - g(c))\right]\right\rvert \leq \eta_1\lvert g(x) - g(c) \rvert
\end{align*}$$

Adding and subtracting $f'(g(c))g'(c)(x-c)$ yields
$$\begin{align*}
\left\lvert f(g(x)) - \left[f(g(c))+f'(g(c))g'(c)(x-c)\right] - f'(g(c))\left[g(x) - g(c) - g'(c)(x-c)\right]\right\rvert \leq \eta_1\lvert g(x) - g(c) \rvert.
\end{align*}$$

Applying the reverse triangle inequality and rearranging,
$$\begin{align}
\left\lvert f(g(x)) - \left[f(g(c))+f'(g(c))g'(c)(x-c)\right]\right\rvert &\leq \left\lvert f'(g(c)) \right\rvert \lvert g(x) - g(c) - g'(c)(x-c)\rvert \nonumber \\
&\;\;+ \eta_1\lvert g(x) - g(c)\rvert, \nonumber \\
&\leq \eta_2\left\lvert f'(g(c))\right\rvert\lvert x - c \rvert + \eta_1(\eta_2 + \lvert g'(c)\rvert)\lvert x - c \rvert.\nonumber
\end{align}$$

So, if $$\eta_2 = \frac{\epsilon}{2\left(\lvert f'(g(c))\rvert + 1\right)}\;\;\;\text{and}\;\;\eta_1 = \frac{\epsilon}{2\left(\eta_2 + \lvert g'(c) \rvert\right)},$$ then this final inequality implies that for $\lvert x - c \rvert < \delta$,
$$\begin{align*}
\left\lvert (f\circ g)(x) - \left[(f\circ g)(c) + f'(g(c))g'(c)(x-c)\right]\right\rvert\leq \left(\frac{\epsilon}{2} + \frac{\epsilon}{2}\right)\lvert x - c \rvert = \epsilon\lvert x - c \rvert
\end{align*}$$

Hence, provided $\theta_1$ and $\theta_2$ are respectively defined for $\eta_1$ and $\eta_2$ by (1) and (2), and $\delta$ is defined by (4), we find that (*) is satisfied, and the result follows.</p><p>&squ;</p></div>\EndKnitrBlock{proof}

<!--<details open>
<summary>Want to ruin the surprise?</summary>
<br>
Well, you asked for it!
</details>-->

<!--chapter:end:index.Rmd-->

