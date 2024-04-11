---
title: "Vectors, Vector Calculus and Mechanics — Past Paper 2017"
author: 'Christian Jones: University of Bath'
date: 'April 2024'
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
      download: [["MA10236Paper2017.html", "HTML page"], ["MA10236Paper2017.pdf","Standard print PDF"], ["MA10236Paper2017.pdf","Clear print PDF"], ["MA10236Paper2017.pdf","Large print PDF"], ["MA10236Paper2017.docx","Accessible Word document"], ["MA10236Paper2017.epub","Accessible EPub book" ]]
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
Here are the solutions to the past paper discussed in the revision session on XXth May 2024. This is designed as a guide to how much to write in the exam, and how you might want to style your solutions. To return to the homepage, click [here](http://caj50.github.io/tutoring.html).

# Section A {-}

## Question 1 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-2"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>In the triangle $OAB,$ we set $\overrightarrow{OA} = \mathbf{a}$ and $\overrightarrow{OB} = \mathbf{b}.$ The point $C$ is located at the midpoint of the side $AB.$ The point $D$ divides the side $OB$ in the ratio $2:1,$ i.e. $OD = \frac23 OB.$
  
The lines $AD$ and $OC$ cross at $X.$ Using vectors, show that $AX = \frac35 AD$ and find the ratio in which the point $X$ divides $OC.$\hspace{4cm}
</p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
TBD
</p></div>\EndKnitrBlock{solution}

## Question 2 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-4"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>Let $\mathbf{a} = \mathbf{i} + 3\mathbf{j}$ and $\mathbf{b} = 2\mathbf{i}-\mathbf{k}.$
  
  a)  Find the lengths of $\mathbf{a}$ and $\mathbf{b}.$
  
  b)  Find the cosine of the acute angle between $\mathbf{a}$ and $\mathbf{b}.$
  
  c)  Find a unit vector $\hat{\mathbf{c}}$ which is orthogonal to both $\mathbf{a}$ and $\mathbf{b},$ such that $\mathbf{a},\mathbf{b},\hat{\mathbf{c}}$ form a right-handed system.
</p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
TBD
</p></div>\EndKnitrBlock{solution}

## Question 3 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-6"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>State the expansion formula for the vector triple product $\mathbf{a}\times\left(\mathbf{b}\times\mathbf{c}\right).$ Use it to prove that $$\left(\mathbf{a}\times\mathbf{b}\right)\cdot\left\lbrace\left(\mathbf{b}\times\mathbf{c}\right)\times\left(\mathbf{c}\times\mathbf{a}\right)\right\rbrace = \left[\mathbf{a},\mathbf{b},\mathbf{c}\right]^2,$$ where $\left[\mathbf{a},\mathbf{b},\mathbf{c}\right]$ is the scalar triple product.

State, but do not prove, the results of vector algebra which you use.
  </p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
TBD
</p></div>\EndKnitrBlock{solution}

## Question 4 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-8"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>a)  Let $T(x,y)$ be a differentiable function of $x$ and $y$, and let $(a,b)$ be a point on the $xy$-plane. Define the gradient vector $\nabla T(a,b),$ and prove that the rate of change of $T(x,y)$ at $(a,b)$ in the direction of the unit vector $\mathbf{u}$ is given by $$D_{\mathbf{u}}T(a,b) = \mathbf{u}\cdot\nabla T(a,b).$$
  
b)  Find the gradient vector of the function $$T(x,y) = 3x^2 + 2y^2 + 6$$ at the point $(2,1),$ and find the equation of the tangent plane to the 3D surface $z=T(x,y)$ at the point $(2,1,c)$ where $c = T(2,1).$
  </p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
TBD</p></div>\EndKnitrBlock{solution}

## Question 5 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-10"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>In planar polar coordinates $(r.\theta),$ the position vector of a particle at time $t$ can be written as $$\mathbf{x}(t) = r\cos(\theta)\mathbf{i} + r\sin(\theta)\mathbf{j}$$ where $r,\theta$ are functions of $t.$
  
  a)  Express the radial and angular unit vectors $\mathbf{e}_r,\mathbf{e}_{\theta}$ in terms of $\mathbf{i},\mathbf{j}.$ Derive expressions for $\dot{\mathbf{e}}_r$ and $\dot{\mathbf{e}}_{\theta},$ and hence show that $$\dot{\mathbf{x}} = \dot{r}\mathbf{e}_r + r\dot{\theta}\mathbf{e}_{\theta}$$ and $$\ddot{\mathbf{x}} = \left(\ddot{r} - r\dot{\theta}^2\right)\mathbf{e}_r + \left(2\dot{r}\dot{\theta} + r\ddot{\theta}\right)\mathbf{e}_{\theta}.$$
    
  b) Find the acceleration vector of a particle which travels in a circular orbit of radius $a,$ at a constant angular speed $\omega.$
  </p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
TBD</p></div>\EndKnitrBlock{solution}

# Section B {-}

## Question 6 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-12"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>a)  Prove that the shortest distance from a point $A$ with position vector $\mathbf{a},$ to the plane $\Pi$ defined by $\mathbf{r}\cdot\mathbf{n} = d$ is $$h = \frac{\lvert d - \mathbf{a}\cdot\mathbf{n}\rvert}{\lVert\mathbf{n}\rVert},$$ and find the position vector of the point on $\Pi$ which achieves this distance.

b)  Let $\mathbf{a},\mathbf{b},\mathbf{l},\mathbf{m}$ be given vectors, and let $\mathbf{r} = \mathbf{a} + \lambda\mathbf{l}$ and $\mathbf{r} = \mathbf{b} + \mu\mathbf{m}$ be two non-parallel and non-intersecting lines $L_1$ and $L_2$ respectively.

    i)  Find the vector equations of two parallel planes $\Pi_1$ and $\Pi_2,$ such that $\Pi_1$ contains $L_1$ and $\Pi_2$ contains $L_2.$
  
    ii)  Find the distance between the two planes $\Pi_1$ and $\Pi_2.$
  </p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
TBD</p></div>\EndKnitrBlock{solution}

## Question 7 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-14"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>a) By either finding the Complementary Function and Particular Integral, or using the Integrating Factor method, solve the vector differential equation $$\ddot{\mathbf{x}} + k\dot{\mathbf{x}} = \mathbf{h}, \quad \mathbf{x}(0) = \mathbf{x}_0, \quad \dot{\mathbf{x}}(0) = \mathbf{0}$$ where $k$ is a non-zero scalar and $\mathbf{h}$ is a constant vector. Show that the solution can be written as $$\mathbf{x}  = \mathbf{x}_0 + \frac{1}{k^2}\left(\mathrm{e}^{-kt} + kt - 1\right)\mathbf{h}.$$
  
b) A food parcel of mass $m$ is dropped from a helicopter hovering at a height $D$ directly above a target on horizontal ground. There is a constant horizontal crosswind of velocity $u,$ and the air resistance is proportional to the relative velocity of the parcel with respect to the wind, with coefficient $\mu.$ Derive the vector differential equation of motion of the parcel, and hence find its position vector $\mathbf{x}(t).$
  
c) How far away from the target will the food parcel land?
  </p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
TBD</p></div>\EndKnitrBlock{solution}

## Question 8 {-}
\BeginKnitrBlock{Question}BEGINSORTNAMEOUTMARKER-ENDSORTNAMEOUTMARKER<div class="Question" custom-style="TheoremStyle" id="Question:unnamed-chunk-16"><span class="Question" custom-style="NameStyle"><strong> Question: </strong></span><p>A particle of mass $m$ moves under the action of a central "planetary" force $$\mathbf{F} = -\mu m \lVert \dot{\mathbf{x}}\rVert^2\frac{\mathbf{x}}{r^2}$$ where $r = \lVert\mathbf{x}\rVert$ and $\mu > 0$ is a constant.

a)  Prove that the motion takes place in a plane.

b)  Using polar coordinates $(r,\theta)$ on the plane, show that the equations of motion are $$r^2\dot{\theta} = h, \quad \ddot{r} + (\mu-1)\frac{h^2}{r^3} + \mu\frac{\dot{r}^2}{r} = 0,$$ where $h$ is a constant. 

    Note: You may use without proof the formulae for velocity and acceleration in polar coordinates, given in Question 5(a).
    
c) The particle is projected radially outwards from the surface of a "planet" of radius $R,$ with initial speed $v_0.$ Show that $h=0$ in part (b).

    Integrate the second equation of motion in part (b) to obtain $$\ln(\dot{r}) = -\mu \ln(r) + c$$ where $c$ is a constant of integration. Hence deduce that for all $v_0 > 0$ the particle will never fall back to the "planet".
    
    Hint: $\frac{d}{dr}\left(\ln(r)\right) = \frac{1}{r}\frac{dr}{dt}.$
  </p></div>\EndKnitrBlock{Question}

\BeginKnitrBlock{solution}<div class="bookdown-solution" custom-style="ProofStyle"><span class="solution" custom-style="NameStyleItalics"><strong>Solution. </strong></span> <p>
TBD</p></div>\EndKnitrBlock{solution}

<!--chapter:end:index.Rmd-->

