---
title: "Cauchy Condensation Example"
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
  clavertondown::html_clav:
    toc: true
    pandoc_args: --default-image-extension=svg
  clavertondown::gitbook_clav:
    split_by: section
    keep_md: true
    config:
      download: [["Cauchy.html", "HTML page"], ["Cauchy.pdf","Standard print PDF"], ["CauchyClear.pdf","Clear print PDF"], ["CauchyLarge.pdf","Large print PDF"], ["Cauchy.docx","Accessible Word document"], ["Cauchy.epub","Accessible EPub book" ]]
      sharing: no
    pandoc_args: --default-image-extension=svg
header-includes:
  - \newcommand{\BOO}{BOO}
---

\newpage
\pagenumbering{arabic}

# Example involving logarithms

\BeginKnitrBlock{example}<div class="bookdown-example" custom-style="ExampleStyle" id="exm:ex1"><span class="exm:ex1" custom-style="NameStyle"><strong><span id="exm:ex1"></span>Example 1.1  </strong></span><div>Prove that $$\sum_{n=4}^{\infty} \frac{1}{n\ln(n)\ln(\ln(n))}$$ diverges.</div></div>\EndKnitrBlock{example}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyle"><strong>Solution. </strong></span> <p>For $n\geq4$, define $$a_n = \frac{1}{n\ln(n)\ln(\ln(n))},$$ and for $k\geq 2$, define $$b_k := 2^{k}a_{2^k} = \frac{2^k}{2^k\ln(2^k)\ln(\ln(2^k))}.$$ Then, by properties of logarithms,
$$\begin{align*}
b_k = \frac{1}{k\ln(2)\ln(k\ln(2))} = \frac{1}{k\ln(2)[\ln(k) + \ln(\ln(2))]}.
\end{align*}$$
Also, for $k\geq 2$, we know that (under the assumption that $\ln : (0,\infty) \to \mathbb{R}$ is an increasing function), $$\ln(k) \geq \ln(2) \geq \ln(\ln(2))).$$ Hence $$b_k \geq \frac{1}{2\ln(2)k\ln(k)} =: c_k.$$ From lectures (or by applying the Cauchy condensation test again to $c_k$), we know that $\sum_{k=2}^{\infty}c_k$ diverges. Hence, by comparison (as $c_k \geq 0$), we find that $\sum_{k=2}^{\infty} b_k$ diverges. Finally, by the Cauchy condensation test, we conclude that $$\sum_{n=4}^{\infty} a_n = \sum_{n=4}^{\infty} \frac{1}{n\ln(n)\ln(\ln(n))} \quad \text{diverges.}$$</p></div>\EndKnitrBlock{solution}
It turns out that this example is a special case of what is known as a *generalised Bertrand series*, and it's quite surprising how general we can make this example! See [here](https://en.wikipedia.org/wiki/Cauchy_condensation_test#Examples) for details!

