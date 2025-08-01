---
title: "Analysis 1B — Further Integral Examples"
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
      download: [["ExtraExamples.html", "HTML page"], ["ExtraExamples.pdf","Standard print PDF"], ["ExtraExamplesClear.pdf","Clear print PDF"], ["ExtraExamplesLarge.pdf","Large print PDF"], ["ExtraExamples.docx","Accessible Word document"], ["ExtraExamples.epub","Accessible EPub book" ]]
      sharing: no
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
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
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
Hi everyone! Since Problem Sheet 11 is being covered in Revision Week, I thought it might be more useful for you to have a few extra questions (and solutions) related to those on the sheet. As usual, alternative formats can be downloaded by clicking the download icon at the top of the page. Please send any comments or corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

<!--<details open>
<summary>Want to ruin the surprise?</summary>
<br>
Well, you asked for it!
</details>-->

# Example 1

\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong>(\#exm:ex1) </strong></span><div>Let $f:[-1,1] \to \mathbb{R}$ be defined by
\begin{align*}
    f(x) = \begin{cases}
    0 &\quad \text{if} \quad -1\leq x <0,\\
    1 &\quad \text{if} \quad\quad\; 0\leq x \leq1.
    \end{cases}
\end{align*}
Using the Cauchy criterion, prove that $f$ is integrable.
</div></div>\EndKnitrBlock{example}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>If you weren't asked to use the Cauchy criterion, the easy way of doing this is by using the theorem that says that a monotone function is integrable. Here's how you would do it via the Cauchy criterion:

For some $\delta \in (0,1]$, consider the subdivision $$P_{\delta} = \lbrace -1, -\delta,\delta,1\rbrace = \lbrace x_0,x_1,x_2,x_3\rbrace.$$ Then,
\begin{align*}
    L(f,P_{\delta}) &= \sum_{i=1}^3 \inf_{[x_{i-1},x_{i}]} f(x) \cdot (x_{i} - x_{i-1}),\\
    &=0(-\delta - -1) + 0(\delta - - \delta) + 1(1-\delta),\\
    &= 1 - \delta.
\end{align*}
Also,
\begin{align*}
    U(f,P_{\delta}) &= \sum_{i=1}^3 \sup_{[x_{i-1},x_{i}]} f(x) \cdot (x_{i} - x_{i-1}),\\
    &= 0(-\delta - - 1) + 1(\delta - - \delta) + 1(1-\delta),\\
    &= 1 + \delta.
\end{align*}
Hence,
\begin{align*}
U(f,P_{\delta}) - L(f,P_{\delta}) = 1 + \delta - (1 - \delta) = 2\delta.
\end{align*}
Now, fix $\epsilon >0$. We have that $2\delta < \epsilon$ when $\delta < \epsilon/2$. So, taking $\delta = \epsilon/4$, for example, we find that $$P_{\delta} = \left\lbrace -1, -\frac{\epsilon}{4}, \frac{\epsilon}{4},1\right\rbrace$$ is such that $U(f,P_{\delta}) - L(f, P_{\delta}) <\epsilon$. Therefore, by the Cauchy criterion, $f$ is integrable.

</p></div>\EndKnitrBlock{solution}
*This idea of `cutting out the discontinuity' by introducing a $\delta$ comes in really handy in a few areas of maths. It's also really handy for dealing with improper integrals, for example $$\int_0^1 \frac{1}{\sqrt{x}}\, dx$$*

# Example 2

\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex2"><span class="exm:ex2" custom-style="NameStyle"><strong>(\#exm:ex2) </strong></span><div>Consider $f:[1,4] \to \mathbb{R}$ given by $f(x) = \frac{1}{2\sqrt{x}}$. Find $\int_1^4 f$ by using the Fundamental Theorem of Calculus.</div></div>\EndKnitrBlock{example}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>Let $F:(0,5) \to \mathbb{R}$ be defined by $F(x) = \sqrt{x}$. We know that $F$ is differentiable on $(0,5)$, and $\forall x \in [1,4]$: $$F'(x) = \frac{1}{2\sqrt{x}} = f(x).$$ Hence, $F$ is a primitive for $f$. Moreover, $f$ is continuous on $[1,4]$, so it is integrable. Hence, by the FTC:
\begin{align*}
    \int_1^4 f = F(4) - F(1) = \sqrt{4} - \sqrt{1} = 1.
\end{align*}

</p></div>\EndKnitrBlock{solution}

# Example 3

\BeginKnitrBlock{example}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex3"><span class="exm:ex3" custom-style="NameStyle"><strong>(\#exm:ex3) </strong></span><div>Let $f:[0,\pi/2] \to \mathbb{R}$ be defined by $f(t) = \mathrm{e}^{-t^2}$, and let $b:(0,\pi/2) \to (0,\pi/2)$ be defined by $b(x) = x\sin(x)$. Find $$\frac{d}{dx}\int_0^{b(x)} f(t)\, dt.$$
  </div></div>\EndKnitrBlock{example}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>First, let $$G(b) = \int_0^b f(t)\, dt,$$ where $b = b(x) = x\sin(x)$. By the second Fundamental Theorem of Calculus, as $f$ is continuous on $[0,\pi/2]$, then $G$ is a primitive for $f$ in terms of $b$, with $$f(b(x)) = \frac{dG}{db}(b(x)) \quad \forall x \in (0,\pi/2).$$ Hence, by the chain rule:
\begin{align*}
    \frac{d}{dx}\int_0^{b(x)} f(t)\, dt &= \frac{dG}{db}\bigg\rvert_{b = b(x)}\frac{db}{dx},\\
    &= f(b(x))b'(x) \quad \text{(by second FTC)},\\
    &= \exp\left(-x^2\sin^2(x)\right)(x\sin(x))'.
\end{align*}
Finally, by the product rule, we obtain for any $x \in (0,\pi/2)$
\begin{align*}
    \frac{d}{dx}\int_0^{b(x)} f(t)\, dt = \left(\sin(x) + x\cos(x)\right)\exp\left(-x^2\sin^2(x)\right).
\end{align*}

</p></div>\EndKnitrBlock{solution}

<!--chapter:end:index.Rmd-->

