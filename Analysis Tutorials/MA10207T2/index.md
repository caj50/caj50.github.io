---
title: "Analysis 1A — Tutorial 2"
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
      download: [["Tutorial2.html", "HTML page"], ["Tutorial2.pdf","Standard print PDF"], ["Tutorial2Clear.pdf","Clear print PDF"], ["Tutorial2Large.pdf","Large print PDF"], ["Tutorial2.docx","Accessible Word document"], ["Tutorial2.epub","Accessible EPub book" ]]
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
Here is the material to accompany the 2nd Analysis Tutorial in Week 2. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk). To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Lecture Recap

## Induction
This week first involves a little bit more about statements, namely those that involve the natural numbers $\mathbb{N}$. Suppose we have a statement $P(n)$ which depends on a natural number $n$. If we want to prove this true for all natural numbers, we use the principle of *mathematical induction*.

Firstly, let $\Lambda \subseteq \mathbb{N}$ be the set of all $n \in \mathbb{N}$ such that $P(n)$ is true. Then, to prove something by induction, we use the following procedure:

1. Show $1 \in \Lambda$.
2. Assume $k \in \Lambda$ for some $k \in \mathbb{N}$. Prove $k + 1 \in \Lambda$.

If these two steps are satisfied, then $\Lambda = \mathbb{N}$, and $P(n)$ holds for all natural numbers $n$. You may come across different styles of inductive proofs from different lecturers at Bath, but as long as you write everything logically, these are fine for this course too!

## Axioms[^1]

### Field Axioms
As you might know from experience, natural numbers won't get us very far in maths. So instead, we turn to studying the real numbers ($\mathbb{R}$). But before we do, we need to know how these numbers behave under certain operations. This is where the *field axioms* come in. There's a long list of them in Section 3.1 of the lecture notes , so they're not repeated here in full. However, we can summarise[^2] them as follows:

* **Addition**: On $\mathbb{R}$, addition is *associative* and *commutative*, an *additive identity* exists, and *additive inverses* exist.
* **Multiplication**: On $\mathbb{R}\setminus \lbrace 0 \rbrace$, multiplication is *associative* and *commutative*, a *multiplicative identity* exists, and *multiplicative inverses* exist.
* Multiplication *distributes* over addition.

Try matching the properties here to the numbered axioms in the lecture notes!

[^1]: Or Axiomata, if you're into your archaic English.
[^2]: Once you've learned some group theory, we can obscure everything behind more definitions. The first two bullet points can be stated as: $(\mathbb{R},+)$ and $(\mathbb{R}\setminus\lbrace0\rbrace, \cdot)$ are abelian groups. The third bullet point remains the same.

### Order Axioms
As if the first 9 field axioms weren't enough, there are 5 *order axioms* you need to know. As these are useful for the problem sheet, they are presented below.
\BeginKnitrBlock{Order Axioms}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Order Axioms" custom-style="TheoremStyle" id="Order Axioms:unnamed-chunk-2"><span class="Order Axioms" custom-style="NameStyle"><strong> Order Axioms: </strong></span><p>For $x,y,z \in \mathbb{R}$:
  
* $x \leq y$ or $y \leq x$.
* If $x\leq y$ and $y \leq x$, then $x = y$.
* If $x \leq y$ and $y \leq z$, then $x \leq z$.
* If $x \leq y$, then $x + z \leq y + z$.
* If $x\leq y$ and $z\geq0$, then $xz\leq yz$.
</p></div>\EndKnitrBlock{Order Axioms}

## Set Bounds
You might be interested to know that at this stage, despite the fact we have specified 14 axioms, these still aren't unique to the real numbers! For example, the exact same axioms also apply to the set of rational numbers $\mathbb{Q}$. Luckily, we only need one more axiom to complete our description of the real numbers. Unfortunately, there are a few definitions we need first...

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def1"><span class="def:def1" custom-style="NameStyle"><strong>(\#def:def1)  (Upper Bound) </strong></span><div>Let $S \subseteq \mathbb{R}$. Then $M \in \mathbb{R}$ is an upper bound for $S$ if for all $x \in S$, $x \leq M$. In this case, we say $S$ is bounded above.</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def2"><span class="def:def2" custom-style="NameStyle"><strong>(\#def:def2)  (Lower Bound) </strong></span><div>Let $S \subseteq \mathbb{R}$. Then $m \in \mathbb{R}$ is a lower bound for $S$ if for all $x \in S$, $x \geq m$. In this case, we say that $S$ is bounded below.</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def3"><span class="def:def3" custom-style="NameStyle"><strong>(\#def:def3)  (Bounded Set) </strong></span><div>A set $S$ is bounded if it is both bounded above and below. Equivalently, $S$ is bounded if there exists $m, M \in \mathbb{R}$ such that for all $x \in S$, $m\leq x \leq M$.</div></div>\EndKnitrBlock{definition}
We can go one step further with the definition of a bounded set. Namely, we can say that $S$ is bounded if $\exists M^{*}\geq0$ such that $\lvert x \rvert \leq M$ for all members $x$ of $S$. The link here is that $M^{*} = \max\left\lbrace \lvert m \rvert, \lvert M \rvert \right\rbrace$.

Thinking of upper bounds for a moment, if we have one, we could ask if there is a smaller number which also bounds the set from above. You might also be tempted to ask what the 'best' upper bound on a set could be, such that no smaller number will bound the set from above. This leads to the ideas of suprema and infima:

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def4"><span class="def:def4" custom-style="NameStyle"><strong>(\#def:def4)  (Supremum) </strong></span><div>Let $S \in \mathbb{R}$. A number $T \in \mathbb{R}$ is said to be the supremum of $S$ if it is an upper bound for $S$, and for any other upper bound $M$, $T \leq M$. Here, we write $T = \sup(S)$.</div></div>\EndKnitrBlock{definition}

\BeginKnitrBlock{definition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-definition" custom-style="DefinitionStyle" id="def:def5"><span class="def:def5" custom-style="NameStyle"><strong>(\#def:def5)  (Infimum) </strong></span><div>Let $S \in \mathbb{R}$. A number $t \in \mathbb{R}$ is said to be the infimum of $S$ if it is a lower bound for $S$, and for any other lower bound $m$, $t\geq m$. Here, we write $t = \inf(S)$.</div></div>\EndKnitrBlock{definition}

For example, if we consider the set $S = (-1,2] = \lbrace x \lvert -1<x\leq2\rbrace$, we can see that possible upper and lower bounds are $M = 3$ and $m = -2$ respectively, so the set is bounded. Its supremum and infimum are $\sup(S) = 2$ and $\inf(S) = -1$. However, note that the supremum lies inside $S$, whereas the infimum does not lie inside $S$. This also tells us that the maximum element of $S$ is $2$, whereas $S$ has no minimum element!

### The Completeness Axiom
Finally, we are ready to state the required $15^{th}$ axiom! As the title suggests, this is known as the *Completeness Axiom*.

\BeginKnitrBlock{Completeness Axiom}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Completeness Axiom" custom-style="TheoremStyle" id="Completeness Axiom:unnamed-chunk-3"><span class="Completeness Axiom" custom-style="NameStyle"><strong> Completeness Axiom: </strong></span><p>Every non-empty set $S$ in $\mathbb{R}$ that is bounded above has a supremum[^3].</p></div>\EndKnitrBlock{Completeness Axiom}

Loosely, this axiom ensures that there are no 'gaps' in the real number line. For some more (precise) information, see [this link.](https://en.wikipedia.org/wiki/Completeness_of_the_real_numbers)

[^3]:In the lecture notes, it also states that 'Every non-empty set of real numbers that is bounded below has an infimum.' But you can deduce this from the supremum result by considering the set $-S:=\lbrace -x \lvert x \in S\rbrace.$

### The Archimedian Postulate
To finish, we mention one result which will become very useful when studying sequences in the next few weeks. This is the *Archimedian Postulate*, and says that the set of natural numbers is unbounded above. In maths terms:

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1)  (Archimedian Postulate) </strong></span><p>We have that $\forall x \in \mathbb{R}, \exists N \in \mathbb{N}$ such that $N > x.$</p></div>\EndKnitrBlock{proposition}


# Hints
As per last week, here's the hints section of this document.

* [H1.] Recall that a number $N$ is a multiple of 3 if there exists $j \in \mathbb{Z}$ such that $N = 3j$. The proof is then similar to tutorial question 1.
* [H2.] Try and get the problems into the form of one of the order axioms. Make sure to state each axiom you use, when you use it!
* [H3.] The induction should be straightforward. To find the formula you need to prove, have you seen a way of rewriting $\begin{pmatrix}
    n\\
    10
    \end{pmatrix}$ recently? (Have a look at the proof of the binomial theorem).
* [H4.] In both cases, your contradiction will come from the fact that one number is found to be strictly less than itself.
* [H5.] Think back to the definitions, and use them to construct your proof of this result.
* [H6.] The method here is very similar to that used in proving the infimum result from Tutorial Question 5.

<!--chapter:end:index.Rmd-->

