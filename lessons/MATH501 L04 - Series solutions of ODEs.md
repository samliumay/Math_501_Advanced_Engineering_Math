---
course: MATH 501 Advanced Engineering Mathematics
lecture: 4
title: Series solutions of ODEs
tags: [math501, lecture]
slides: lectures/lecture_04/Math501 Chapter 4.pdf
full_notes: lecture_notes/lecture_04/MATH501_Lecture_04_Series_Solutions.pdf
---
# MATH 501 · Lecture 4 · Series solutions of ODEs

> [!summary] In short
> - Linear ODEs with variable coefficients often have no closed form solution. A power series solution still works.
> - Ordinary point: put $y=\sum a_nx^n$ in, shift every sum to $x^n$, set each coefficient to zero. This gives a recurrence relation.
> - Singular point ($P(x_0)=0$): regular if $(x-x_0)Q/P$ and $(x-x_0)^2R/P$ are analytic, otherwise irregular.
> - Regular singular point: Frobenius series $y=\sum a_nx^{n+r}$. The lowest power gives the indicial equation for $r$.
> - The difference $r_1-r_2$ decides the shape of the second solution (second series, or with $\ln x$).

The slide numbers below are the pages of the Chapter 4 PDF (page 1 is printed page 65).

## 1. Power series, analytic functions, Maclaurin series (slides 1-2)
![[math501_lecture_04_math501_chapter_4_p001.jpg]]

**Notes.** A **power series** about $x_0$ is $\sum_{n=0}^\infty a_n(x-x_0)^n$. The numbers $a_n$ are the coefficients and $x_0$ is the center. A function is **analytic** at $x_0$ if it equals such a series on some interval around $x_0$. Then $a_n=\dfrac{f^{(n)}(x_0)}{n!}$.

The six Maclaurin series ($x_0=0$) to know. The last three are at the top of slide 2.

| Function | Series | Valid for |
|---|---|---|
| $\dfrac{1}{1-x}$ | $\sum_{n\ge0}x^n$ | $\lvert x\rvert<1$ |
| $e^x$ | $\sum_{n\ge0}\dfrac{x^n}{n!}$ | all $x$ |
| $\sin x$ | $\sum_{n\ge0}\dfrac{(-1)^nx^{2n+1}}{(2n+1)!}$ | all $x$ |
| $\cos x$ | $\sum_{n\ge0}\dfrac{(-1)^nx^{2n}}{(2n)!}$ | all $x$ |
| $\arctan x$ | $\sum_{n\ge0}\dfrac{(-1)^nx^{2n+1}}{2n+1}$ | $\lvert x\rvert\le1$ |
| $\ln(1+x)$ | $\sum_{n\ge1}\dfrac{(-1)^{n-1}x^n}{n}$ | $-1<x\le1$ |

> [!warning] Watch out
> Analytic is much stronger than continuous. $|x|$ is continuous at 0 but has no power series about 0.

## 2. Ordinary points and the power series method (slides 2-3)
![[math501_lecture_04_math501_chapter_4_p002.jpg]]
![[math501_lecture_04_math501_chapter_4_p003.jpg]]

**Notes.** $x_0$ is an **ordinary point** of $y''+p(x)y'+q(x)y=f(x)$ if $p$, $q$, $f$ are analytic at $x_0$. Then the IVP at $x_0$ has a unique solution, and that solution is analytic at $x_0$. The same holds for $y'+p(x)y=f(x)$.

Method (about $x_0=0$):
1. Write $y=\sum_{n\ge0}a_nx^n$, $y'=\sum_{n\ge1}na_nx^{n-1}$, $y''=\sum_{n\ge2}n(n-1)a_nx^{n-2}$.
2. Substitute. Expand the right side as a series too.
3. Shift indices so that every sum has $x^n$.
4. Pull out the first terms so that all sums start at the same $n$.
5. Set the coefficient of each power to zero: first coefficients plus a **recurrence relation**.
6. Compute the coefficients. $a_0$ (and $a_1$ for second order) stay free.

> [!example] Slide example (first order)
> $y'+2xy=\dfrac{1}{1-x}$. Coefficient of $x^0$: $a_1=1$. Recurrence: $a_{n+1}=\dfrac{1-2a_{n-1}}{n+1}$, $n\ge1$.
> $$y=a_0+x+\left(\tfrac12-a_0\right)x^2-\tfrac13x^3+\tfrac{a_0}{2}x^4+\tfrac13x^5+\left(\tfrac16-\tfrac{a_0}{6}\right)x^6+\tfrac{1}{21}x^7+\cdots$$

> [!warning] Watch out
> When shifting an index, change both the power and the starting value: $\sum_{n\ge1}na_nx^{n-1}=\sum_{n\ge0}(n+1)a_{n+1}x^n$.

## 3. Second order examples and an IVP (slides 3-6)
![[math501_lecture_04_math501_chapter_4_p004.jpg]]
![[math501_lecture_04_math501_chapter_4_p005.jpg]]
![[math501_lecture_04_math501_chapter_4_p006.jpg]]

**Notes.** Same method with two free coefficients $a_0$, $a_1$. For an IVP at 0: $a_0=y(0)$ and $a_1=y'(0)$.

> [!example] Slide examples
> - $(1-x)y''-xy'=e^x$ (starts on slide 3): $a_2=\tfrac12$, $a_{n+2}=\dfrac{n(n+1)a_{n+1}+na_n+\frac{1}{n!}}{(n+2)(n+1)}$.
>   $y=a_0+a_1x+\tfrac12x^2+\left(\tfrac13+\tfrac{a_1}{6}\right)x^3+\left(\tfrac{7}{24}+\tfrac{a_1}{12}\right)x^4+\left(\tfrac{7}{30}+\tfrac{3a_1}{40}\right)x^5+\cdots$
> - $y''-xy=0$: $a_2=0$, $a_{n+2}=\dfrac{a_{n-1}}{(n+2)(n+1)}$ (jumps by three).
>   $y_1=1+\tfrac16x^3+\tfrac{1}{180}x^6+\tfrac{1}{12960}x^9+\cdots$, $\ y_2=x+\tfrac{1}{12}x^4+\tfrac{1}{504}x^7+\tfrac{1}{45360}x^{10}+\cdots$
> - $(x^2-1)y''+3xy'+xy=0$, $y(0)=4$, $y'(0)=6$: $a_2=0$, $a_3=\tfrac{a_0}{6}+\tfrac{a_1}{2}$, $a_{n+2}=\dfrac{a_{n-1}+n(n+2)a_n}{(n+2)(n+1)}$ for $n\ge2$.
>   $y=4+6x+\tfrac{11}{3}x^3+\tfrac12x^4+\tfrac{11}{4}x^5+\cdots$

The **general solution** is the whole family $a_0y_1+a_1y_2$. **Two linearly independent solutions** are the two members $y_1$ ($a_0=1$, $a_1=0$) and $y_2$ ($a_0=0$, $a_1=1$).

## 4. Singular points, Frobenius' theorem, indicial equation (slides 7-9)
![[math501_lecture_04_math501_chapter_4_p007.jpg]]
![[math501_lecture_04_math501_chapter_4_p008.jpg]]
![[math501_lecture_04_math501_chapter_4_p009.jpg]]

**Notes.** For $P(x)y''+Q(x)y'+R(x)y=0$, $x_0$ is a **singular point** if $P(x_0)=0$. It is **regular** if both

$$(x-x_0)\frac{Q(x)}{P(x)}\quad\text{and}\quad(x-x_0)^2\frac{R(x)}{P(x)}$$

are analytic at $x_0$. Otherwise it is **irregular**.

**Frobenius' theorem.** At a regular singular point there is at least one solution $y=\sum_{n\ge0}a_n(x-x_0)^{n+r}$ with $a_0\neq0$.

**Indicial equation** (for $x_0=0$): with $c_0=\lim_{x\to0}x\,Q/P$ and $d_0=\lim_{x\to0}x^2R/P$,

$$r(r-1)+c_0r+d_0=0 .$$

Let its real roots be $r_1\ge r_2$, and $y_1=\sum a_nx^{n+r_1}$.

| $r_1-r_2$ | Second solution |
|---|---|
| not an integer | $y_2=\sum_{n\ge0}a_n^*x^{n+r_2}$ |
| $0$ | $y_2=y_1\ln x+\sum_{n\ge1}a_n^*x^{n+r_1}$ |
| positive integer | $y_2=k\,y_1\ln x+\sum_{n\ge0}a_n^*x^{n+r_2}$ ($k$ may be 0) |

> [!example] Slide example
> $x^3(x-2)^2y''+5(x^2-4)y'+3x^2y=0$: singular points 0 and 2. At 0: $x\,Q/P=\dfrac{5(x+2)}{x^2(x-2)}$ is not analytic, so 0 is irregular. At 2: $\dfrac{5(x+2)}{x^3}$ and $\dfrac3x$ are analytic, so 2 is regular.

> [!warning] Watch out
> - The theorem promises one Frobenius series, not two.
> - $\ln x$ and $x^r$ with non-integer $r$ need $x>0$.
> - The top of slide 7 holds the exercise of the previous section.

## 5. Frobenius example: roots not differing by an integer (slides 10-12)
![[math501_lecture_04_math501_chapter_4_p010.jpg]]
![[math501_lecture_04_math501_chapter_4_p011.jpg]]

**Notes.** $x^2y''+\left(2x^2+\tfrac x2\right)y'+\left(x-\tfrac12\right)y=0$ about 0.

- $x\,Q/P=2x+\tfrac12$ and $x^2R/P=x-\tfrac12$ are analytic: 0 is a regular singular point, $c_0=\tfrac12$, $d_0=-\tfrac12$.
- Indicial equation: $r^2-\tfrac12r-\tfrac12=(r-1)(r+\tfrac12)=0$, so $r_1=1$, $r_2=-\tfrac12$.
- Recurrence: $\left[(n+r)(n+r-\tfrac12)-\tfrac12\right]a_n+(2n+2r-1)a_{n-1}=0$.
- $r=1$: $a_n=-\dfrac{(2n+1)a_{n-1}}{n(n+\frac32)}$, so $y_1=x-\tfrac65x^2+\tfrac67x^3-\tfrac49x^4+\tfrac{2}{11}x^5+\cdots$
- $r=-\tfrac12$: $a_n^*=-\dfrac{(2n-2)a_{n-1}^*}{n(n-\frac32)}$. For $n=1$ the numerator is 0, so all $a_n^*=0$ for $n\ge1$ and $y_2=\dfrac{1}{\sqrt x}$ (top of slide 12).

## 6. Frobenius example: repeated root (slides 12-15)
![[math501_lecture_04_math501_chapter_4_p012.jpg]]
![[math501_lecture_04_math501_chapter_4_p013.jpg]]
![[math501_lecture_04_math501_chapter_4_p014.jpg]]
![[math501_lecture_04_math501_chapter_4_p015.jpg]]

**Notes.** $x^2y''+5xy'+(x+4)y=0$ about 0.

- $c_0=5$, $d_0=4$. Indicial equation: $r^2+4r+4=(r+2)^2=0$, repeated root $r=-2$.
- Recurrence with $r=-2$: $a_n=-\dfrac{a_{n-1}}{n^2}$, so $a_n=\dfrac{(-1)^na_0}{(n!)^2}$.

$$y_1=\sum_{n\ge0}\frac{(-1)^n}{(n!)^2}x^{n-2}=\frac{1}{x^2}-\frac1x+\frac14-\frac{1}{36}x+\frac{1}{576}x^2-\cdots$$

- Second solution: $y_2=y_1\ln x+\sum_{n\ge1}a_n^*x^{n-2}$. Substituting and using that $y_1$ solves the ODE gives $a_1^*=2$ and a recurrence for $n\ge2$: $a_2^*=-\tfrac34$, $a_3^*=\tfrac{11}{108}$, $a_4^*=-\tfrac{25}{3456}$, $a_5^*=\tfrac{137}{432000}$.

$$y_2=y_1\ln x+\frac2x-\frac34+\frac{11}{108}x-\frac{25}{3456}x^2+\frac{137}{432000}x^3+\cdots$$

> [!warning] Errors on the slides
> - Slide 15 prints the last term as $\tfrac{137}{432000}x^2$. The power is $x^3$ ($a_5^*$ goes with $x^{5-2}$).
> - Slide 12 has a slip "$y'=y=\sum\dots$" at the start of this example. It should read $y'=\sum(n+r)a_nx^{n+r-1}$.

## Key formulas and terms
| Term | Meaning / formula |
|---|---|
| Analytic at $x_0$ | Equal to a power series near $x_0$, $a_n=f^{(n)}(x_0)/n!$ |
| Ordinary point | $p$, $q$, $f$ analytic at $x_0$: solution is a power series |
| Recurrence relation | Formula giving $a_{n+1}$ or $a_{n+2}$ from earlier coefficients |
| Singular point | $P(x_0)=0$ in $Py''+Qy'+Ry=0$ |
| Regular singular point | $(x-x_0)Q/P$ and $(x-x_0)^2R/P$ analytic at $x_0$ |
| Frobenius series | $y=\sum_{n\ge0}a_nx^{n+r}$, $a_0\neq0$ |
| Indicial equation | $r(r-1)+c_0r+d_0=0$ |
| Repeated root | $y_2=y_1\ln x+\sum_{n\ge1}a_n^*x^{n+r_1}$ |

## Check yourself
> [!question]- 1. Write the first four nonzero terms of $\dfrac{1}{1+x^2}$ for $\lvert x\rvert<1$.
> Put $u=-x^2$ in $\dfrac{1}{1-u}=1+u+u^2+u^3+\cdots$.
> Answer: $1-x^2+x^4-x^6+\cdots$

> [!question]- 2. Solve $y'-xy=1-x$ as a power series about 0.
> After shifting: $\sum_{n\ge0}(n+1)a_{n+1}x^n-\sum_{n\ge1}a_{n-1}x^n=1-x$.
> $x^0$: $a_1=1$. $x^1$: $a_2=\tfrac{a_0-1}{2}$. $n\ge2$: $a_{n+1}=\tfrac{a_{n-1}}{n+1}$.
> $y=a_0+x+\tfrac{a_0-1}{2}x^2+\tfrac13x^3+\tfrac{a_0-1}{8}x^4+\tfrac{1}{15}x^5+\cdots$

> [!question]- 3. First six nonzero terms of the solution of $y''-xy'-y=0$, $y(0)=1$, $y'(0)=0$.
> Recurrence: $a_{n+2}=\dfrac{a_n}{n+2}$. $a_0=1$, $a_1=0$, so all odd coefficients are 0.
> $y=1+\tfrac12x^2+\tfrac18x^4+\tfrac{1}{48}x^6+\tfrac{1}{384}x^8+\tfrac{1}{3840}x^{10}+\cdots$

> [!question]- 4. Find and classify the singular points of $x(x-1)^2y''+3y'+xy=0$.
> $P=0$ at $x=0$ and $x=1$. At 0: $\dfrac{3}{(x-1)^2}$ and $\dfrac{x^2}{(x-1)^2}$ are analytic, regular.
> At 1: $(x-1)\dfrac QP=\dfrac{3}{x(x-1)}$ is not analytic, irregular.

> [!question]- 5. Find the indicial roots of $2x^2y''-xy'+(1+x)y=0$ at 0.
> $c_0=-\tfrac12$, $d_0=\tfrac12$: $r(r-1)-\tfrac12r+\tfrac12=0$, so $2r^2-3r+1=(2r-1)(r-1)=0$.
> $r_1=1$, $r_2=\tfrac12$. The difference is not an integer: two Frobenius series.

> [!question]- 6. Find two independent series solutions of $x^2y''+x^2y'-2y=0$ about 0.
> $r^2-r-2=0$: $r_1=2$, $r_2=-1$, difference 3. Recurrence: $[(n+r)(n+r-1)-2]a_n+(n+r-1)a_{n-1}=0$.
> $r=2$: $a_n=-\dfrac{(n+1)a_{n-1}}{n(n+3)}$, $y_1=x^2-\tfrac12x^3+\tfrac{3}{20}x^4-\tfrac{1}{30}x^5+\cdots$
> $r=-1$: $a_1^*=-\tfrac12$, $a_2^*=0$, and $n=3$ reads $0=0$, so no logarithm is needed: $y_2=\dfrac1x-\dfrac12$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L03 - The Laplace transform]]. Next: [[MATH501 L05 - Matrices and determinants]]
- Full step-by-step notes (PDF): [MATH501_Lecture_04_Series_Solutions.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_04/MATH501_Lecture_04_Series_Solutions.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_04/MATH501_Lecture_04_Series_Solutions.pdf`
- Original chapter notes (PDF): [Math501 Chapter 4.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_04/Math501%20Chapter%204.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_04/Math501 Chapter 4.pdf`

Slides not embedded: none.
