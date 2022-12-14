---
title: "Analysis 1A — Tutorial 1"
author: 'Christian Jones: University of Bath'
date: 'October 2022'
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
      download: [["Tutorial1.html", "HTML page"], ["Tutorial1.pdf","Standard print PDF"], ["Tutorial1Clear.pdf","Clear print PDF"], ["Tutorial1Large.pdf","Large print PDF"], ["Tutorial1.docx","Accessible Word document"], ["Tutorial1.epub","Accessible EPub book" ]]
      sharing: no
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
  clavertondown::word_clav:
    toc: true
    number_sections: true
    keep_md: true
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
Here is the material to accompany the 1st Analysis Tutorial on the 10th October. Alternative formats can be downloaded by clicking the download icon at the top of the page. As usual, send comments and corrections to [Christian Jones (caj50)](mailto:caj50@bath.ac.uk).

# Lecture Recap

## Statements
This week has been all about logic, and is pretty much the foundation of most of maths! To begin, we need some 'building blocks', and these come in the form of *statements* — sentences which are either true or false. For example, \color{blue} 'The sky is blue' \color{black} is a statement, whereas \color{red} 'Why is the sky blue?' \color{black} is not. In this course, statements are denoted by capital letters (usually $P,Q,R,\ldots$)[^1]

Now that we have some statements, it makes sense to see if we can build something more complicated using them, and this is where the idea of \emph{logical operations} come in. Suppose $P$ and $Q$ are statements. Then, there are four main ones you should be aware of:

* **Conjunction** ($P \wedge Q$): Said '$P$ and $Q$', this is true if both $P$ and $Q$ are true; it is false otherwise.
* **Disjunction** ($P \;\vee\; Q$): Said '$P$ or $Q$', this is true when *at least* one of $P$ or $Q$ is true.
* **Negation** ($\neg P$): Said 'not $P$', this is true when $P$ is false, and vice versa.
* **Implication** ($P\Rightarrow Q$): We have that '$P$ implies $Q$' is true, except when $P$ is true and $Q$ is false.[^2] If you're still unsure as to what this statement means, there's a good example [here](https://simple.wikipedia.org/wiki/Implication_(logic)).

One way we can represent these statements is via a *truth table*. Below is a (combined) truth table for $P \Rightarrow Q$ and $\neg P \;\vee Q$:


   $P$   $Q$   $P \Rightarrow Q$   $\neg P$   $\neg P \; \vee Q$
  :-----: :-----: :-------------------: :----------: :--------------------:
   $T$   $T$          $T$            $F$             $T$
   $T$   $F$          $F$            $F$             $F$
   $F$   $T$          $T$            $T$             $T$
   $F$   $F$          $T$            $T$             $T$

Note that in this table, the 'simple' statements are on the left, and the 'compound' statements are written afterwards.[^3] Also, what we can see is that the truth table columns for both $P \Rightarrow Q$ and $\neg P \;\vee Q$ are identical. This means that both statements are *equivalent*, leading to a fifth logical operation:

* Equivalence ($P \Leftrightarrow Q$): Two statements are equivalent if they're both simultaneously true or simultaneously false. This can also be written $(P \Rightarrow Q) \wedge (Q \Rightarrow P)$.

In regards to statements, there are two more types which we can discuss. Firstly, if a statement is always true, it is known as a *tautology*. Similarly, if a statement is always false, it is known as a *contradiction*.

[^1]: You can use any capital letter you want; I can only presume we start at $P$ because of the word 'proposition'.
[^2]: In case it comes up in anything you read, we can also say that $P$ is *sufficient* for $Q$ and also that $Q$ is necessary for $P$.
[^3]: Ideally, you'd separate the simple statements from the compound ones by use of a double vertical line. However, due to Markdown's apparent lack of syntax for adding a double line, you'll just have to imagine one there.

## Some Useful Laws
In the previous section, we combined statements via logical operations. There is nothing stopping us combining these new statements too! We just need to know how to do it systematically. This relies on *distributive laws* and *De Morgan's laws*. Here, $P,Q,R$ are statements.

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop1"><span class="prp:prop1" custom-style="NameStyle"><strong>(\#prp:prop1)  (Distributive Laws) </strong></span><p>\begin{align*}
    P \wedge (Q \; \vee R) &\Leftrightarrow (P \wedge Q)\; \vee (P \wedge R),\\
    P \; \vee (Q \wedge R) &\Leftrightarrow (P \; \vee Q) \wedge (P \, \vee R).
\end{align*}</p></div>\EndKnitrBlock{proposition}

\BeginKnitrBlock{proposition}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="bookdown-proposition" custom-style="TheoremStyle" id="prp:prop2"><span class="prp:prop2" custom-style="NameStyle"><strong>(\#prp:prop2)  (De Morgan's Laws) </strong></span><p>\begin{align*}
    \neg (P \, \vee Q) &\Leftrightarrow (\neg P) \wedge (\neg Q),\\
    \neg (P \wedge Q) &\Leftrightarrow (\neg P) \, \vee (\neg Q).
\end{align*}</p></div>\EndKnitrBlock{proposition}
If you're ever in a situation where you need to prove these laws, use truth tables! They're also really helpful when writing complex statements in simpler forms (see, for example, Homework Questions 2 \& 3).

## Quantifiers
Put simply, these are just ways of making your life easier, so that you have fewer words to write out when doing maths. There are two quantifiers you'll come across in common usage:

* Firstly, the phrase 'for all' can be represented by $\forall$.
* Secondly, the phrase 'there exists' can be represented by $\exists$.

For example, consider the statements
\begin{align*}
    (\forall x \in \mathbb{R})(x > 2),\\
    (\exists x \in \mathbb{R})(x > 2).
\end{align*}
The first one says 'for all real numbers $x$, $x$ is greater than 2', whereas the second says 'there exists a real number $x$ such that $x$ is greater than 2'. Hopefully you can see that the choice of quantifier can make a huge difference to the truth of a statement! Naturally, for a statement $P$, these can be negated too in the following ways:
\begin{align*}
    \neg(\forall x \; P) &\Leftrightarrow \exists x \; \neg P,\\
    \neg(\exists x \; P) &\Leftrightarrow \forall x\;  \neg P.
\end{align*}
As a final note, if you have statements in which both quantifiers appear, don't swap them! For example, suppose $S \subseteq \mathbb{R}$ is a non-empty set, and consider the two statements
\begin{align*}
    (\forall x \in S)(\exists y \in S)(x < y),\\
    (\exists y \in S)(\forall x \in S)(x < y).
\end{align*}
The first of these says that $S$ has no largest element, and is a perfectly valid statement. However, if we choose $x$ to be equal to $y$ in the second statement, we can see that this version of the statement is totally impossible!


# Hints
Each week, I'll send out a list of hints for the homework questions. Try and have a go without them, but if you need them, you'll usually find them in a document like this one. Anyway, without further ado...

* [H1.] You've got a few examples of truth tables from lectures, and we just about managed to do tutorial question 1a) in the physical tutorial, so look back over these. Also, recall what it means for two statements to be equivalent.
* [H2.] Recall the definition of a tautology. If you're content writing truth tables out, then this question is similar to H1. Alternatively, you could try applying the different laws from Section 1.2 to simplify the statement.
* [H3.] This is similar to the previous two questions.
* [H4.] We did an example in tutorials similar to this one — try some values from the sets $A$ and $B$! For the negation, just take it one step at a time, and apply the rules you've learnt this week.
