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

> [!info] Radius of convergence and the ratio test (beyond the slides)
> The slide says a power series represents $f$ "in some interval $(x_0-h,x_0+h)$". The largest such $h$ is the **radius of convergence** $R$. The series converges for $\lvert x-x_0\rvert<R$ and diverges for $\lvert x-x_0\rvert>R$.
> **Ratio test.** Call the $n$-th term $u_n=a_n(x-x_0)^n$ and compute
> $$L=\lim_{n\to\infty}\left\lvert\frac{u_{n+1}}{u_n}\right\rvert=\lvert x-x_0\rvert\cdot\lim_{n\to\infty}\left\lvert\frac{a_{n+1}}{a_n}\right\rvert .$$
> The series converges if $L<1$ and diverges if $L>1$. So $R=\lim_{n\to\infty}\left\lvert\dfrac{a_n}{a_{n+1}}\right\rvert$ when this limit exists.
> Example: for $\sum x^n$ all $a_n=1$, so $R=1$. This is the "$\lvert x\rvert<1$" of series 1) on the slide. For $e^x$: $\dfrac{a_n}{a_{n+1}}=\dfrac{(n+1)!}{n!}=n+1\to\infty$, so $R=\infty$ ("$x\in\mathbb R$").
> Inside the interval of convergence a power series may be differentiated term by term. The power series method uses this in every example.

> [!question]- Check (slide 1, coefficient formula): Use $a_n=\dfrac{f^{(n)}(x_0)}{n!}$ to find the first four terms of the power series of $f(x)=e^{2x}$ about $x_0=1$.
> Derivatives: $f(x)=e^{2x}$, $f'(x)=2e^{2x}$, $f''(x)=4e^{2x}$, $f'''(x)=8e^{2x}$. In general $f^{(n)}(x)=2^ne^{2x}$.
> At $x_0=1$: $f(1)=e^2$, $f'(1)=2e^2$, $f''(1)=4e^2$, $f'''(1)=8e^2$.
> Coefficients:
> - $a_0=\dfrac{e^2}{0!}=e^2$
> - $a_1=\dfrac{2e^2}{1!}=2e^2$
> - $a_2=\dfrac{4e^2}{2!}=2e^2$
> - $a_3=\dfrac{8e^2}{3!}=\dfrac{4e^2}{3}$
>
> $$e^{2x}=e^2+2e^2(x-1)+2e^2(x-1)^2+\frac{4e^2}{3}(x-1)^3+\cdots$$
> The center is $x_0=1$, so the powers are powers of $(x-1)$, not of $x$.

> [!question]- Check (slide 1, radius of convergence): Find the radius of convergence of $\sum_{n\ge1}\dfrac{n}{3^n}x^n$ with the ratio test (beyond the slides, see the box above). Does the series converge at $x=3$?
> Here $a_n=\dfrac{n}{3^n}$ and $a_{n+1}=\dfrac{n+1}{3^{n+1}}$.
> Ratio of two neighbouring terms:
> $$\left\lvert\frac{a_{n+1}x^{n+1}}{a_nx^n}\right\rvert=\frac{n+1}{3^{n+1}}\cdot\frac{3^n}{n}\cdot\lvert x\rvert=\frac{n+1}{n}\cdot\frac{\lvert x\rvert}{3}$$
> Limit: $\dfrac{n+1}{n}=1+\dfrac1n\to1$, so $L=\dfrac{\lvert x\rvert}{3}$.
> Converges if $L<1$: $\dfrac{\lvert x\rvert}{3}<1$, so $\lvert x\rvert<3$. Diverges if $\lvert x\rvert>3$. So $R=3$.
> At $x=3$ the terms are $\dfrac{n}{3^n}\cdot3^n=n$. They do not go to 0, so the series diverges at $x=3$. (The ratio test gives $L=1$ there and decides nothing. The endpoints must be checked separately.)

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

> [!info] How far does the series solution converge? (beyond the slides)
> The theorem on slide 2 says the solution is analytic at $x_0$, but not on which interval. The standard result: if $x_0$ is an ordinary point, the series solution about $x_0$ converges at least for $\lvert x-x_0\rvert<\rho$, where $\rho$ is the distance from $x_0$ to the nearest point where $p$, $q$ or $f$ is not analytic.
> The distance is measured in the complex plane. Complex singular points count too. The distance from a real $x_0$ to $a+bi$ is $\sqrt{(x_0-a)^2+b^2}$.
> Example on the slide: $f(x)=\dfrac{1}{1-x}$ is not analytic at $x=1$, and $p(x)=2x$ is analytic everywhere. About $x_0=0$ the distance is 1. This is why the slide writes "for $-1<x<1$".

> [!question]- Check (slide 2, Maclaurin series): Differentiate series 6), $\ln(1+x)=\sum_{n\ge1}\dfrac{(-1)^{n-1}x^n}{n}$, term by term. Shift the index so that the sum has $x^n$. Which known series do you get?
> Differentiate each term: $\dfrac{d}{dx}\dfrac{(-1)^{n-1}x^n}{n}=\dfrac{(-1)^{n-1}\,n\,x^{n-1}}{n}=(-1)^{n-1}x^{n-1}$.
> $$\frac{d}{dx}\ln(1+x)=\sum_{n\ge1}(-1)^{n-1}x^{n-1}$$
> Shift: put $k=n-1$, so $n=k+1$. When $n=1$, $k=0$. The power $x^{n-1}$ becomes $x^k$ and $(-1)^{n-1}$ becomes $(-1)^k$:
> $$\sum_{k\ge0}(-1)^kx^k=1-x+x^2-x^3+\cdots$$
> Rename $k$ as $n$: $\sum_{n\ge0}(-x)^n$. This is series 1) with $x$ replaced by $-x$: $\dfrac{1}{1-(-x)}=\dfrac{1}{1+x}$, valid for $\lvert x\rvert<1$.
> Check: $\dfrac{d}{dx}\ln(1+x)=\dfrac{1}{1+x}$. Correct.

> [!question]- Check (slide 2, ordinary point): Is $x_0=0$ an ordinary point of $(x^2+4)y''+xy'+y=0$? For which $x$ is a power series solution about 0 guaranteed to converge (beyond the slides, see the box above)? What changes for a series about $x_0=1$?
> Standard form (divide by $x^2+4$): $y''+\dfrac{x}{x^2+4}y'+\dfrac{1}{x^2+4}y=0$, so $p(x)=\dfrac{x}{x^2+4}$, $q(x)=\dfrac{1}{x^2+4}$, $f(x)=0$.
> At $x=0$ the denominator is $0^2+4=4\neq0$. So $p$, $q$, $f$ are analytic at 0 and $x_0=0$ is an ordinary point.
> $p$ and $q$ fail to be analytic where $x^2+4=0$: $x^2=-4$, $x=\pm2i$. These points are complex.
> Distance from $0$ to $\pm2i$: $\sqrt{(0-0)^2+2^2}=2$. The series about 0 converges at least for $\lvert x\rvert<2$.
> About $x_0=1$: distance from $1$ to $\pm2i$ is $\sqrt{(1-0)^2+2^2}=\sqrt5\approx2.24$. The series in powers of $(x-1)$ converges at least for $\lvert x-1\rvert<\sqrt5$.
> There is no real singular point, but the radius is still finite. The complex points decide it.

> [!question]- Check (slides 2-3): Solve $y'-2xy=0$ as a power series about 0 with the method of the slide example. Find the coefficients up to $a_6$ and recognise the function.
> **Type of point.** $p(x)=-2x$ and $f(x)=0$ are analytic at 0, so 0 is an ordinary point. **Method:** power series $y=\sum_{n\ge0}a_nx^n$.
> **Step 1, series.** $y=\sum_{n\ge0}a_nx^n$, $y'=\sum_{n\ge1}na_nx^{n-1}$.
> **Step 2, substitute.**
> $$\sum_{n\ge1}na_nx^{n-1}-2x\sum_{n\ge0}a_nx^n=0\quad\Rightarrow\quad\sum_{n\ge1}na_nx^{n-1}-\sum_{n\ge0}2a_nx^{n+1}=0$$
> **Step 3, shift to $x^n$.** First sum: replace $n$ by $n+1$, it starts at $n=0$: $\sum_{n\ge0}(n+1)a_{n+1}x^n$. Second sum: replace $n$ by $n-1$, it starts at $n=1$: $\sum_{n\ge1}2a_{n-1}x^n$.
> $$\sum_{n\ge0}(n+1)a_{n+1}x^n-\sum_{n\ge1}2a_{n-1}x^n=0$$
> **Step 4, same start.** Pull out the $n=0$ term of the first sum, which is $a_1$:
> $$a_1+\sum_{n\ge1}\left[(n+1)a_{n+1}-2a_{n-1}\right]x^n=0$$
> **Step 5, coefficients.** $x^0$: $a_1=0$. $x^n$ for $n\ge1$: $(n+1)a_{n+1}-2a_{n-1}=0$, so
> $$a_{n+1}=\frac{2a_{n-1}}{n+1},\qquad n=1,2,3,\dots$$
> **Step 6, compute.**
> - $n=1$: $a_2=\dfrac{2a_0}{2}=a_0$
> - $n=2$: $a_3=\dfrac{2a_1}{3}=0$
> - $n=3$: $a_4=\dfrac{2a_2}{4}=\dfrac{a_0}{2}$
> - $n=4$: $a_5=\dfrac{2a_3}{5}=0$
> - $n=5$: $a_6=\dfrac{2a_4}{6}=\dfrac{a_0}{6}$
>
> $$y=a_0\left(1+x^2+\frac{x^4}{2}+\frac{x^6}{6}+\cdots\right)$$
> **Recognise.** $e^u=1+u+\dfrac{u^2}{2!}+\dfrac{u^3}{3!}+\cdots$ with $u=x^2$ gives exactly this. So $y=a_0e^{x^2}$.
> **Check.** $y'=a_0\cdot2x\,e^{x^2}=2xy$, so $y'-2xy=0$. With the series: $y'=a_0(2x+2x^3+x^5+\cdots)$ and $2xy=a_0(2x+2x^3+x^5+\cdots)$. Equal.

> [!question]- Check (slide 3, index shift): In the example at the bottom of slide 3, the term $-x\,y''$ gives $-\sum_{n\ge2}n(n-1)a_nx^{n-1}$, and the next line writes it as $-\sum_{n\ge1}n(n+1)a_{n+1}x^n$. Show this shift step by step. Why does the new sum start at $n=1$ and not at $n=0$?
> Start: $x\,y''=x\sum_{n\ge2}n(n-1)a_nx^{n-2}=\sum_{n\ge2}n(n-1)a_nx^{n-1}$ (the factor $x$ raises the power by one).
> The power is $x^{n-1}$. Put $k=n-1$, so $n=k+1$. Replace every $n$:
> - $n(n-1)$ becomes $(k+1)k$
> - $a_n$ becomes $a_{k+1}$
> - $x^{n-1}$ becomes $x^k$
> - the start $n=2$ becomes $k=2-1=1$
>
> $$\sum_{n\ge2}n(n-1)a_nx^{n-1}=\sum_{k\ge1}(k+1)k\,a_{k+1}x^k$$
> Rename $k$ as $n$: $\sum_{n\ge1}n(n+1)a_{n+1}x^n$.
> It starts at $n=1$ because the lowest power in the old sum is $x^{2-1}=x^1$. There is no $x^0$ term.
> Check with the first term. Old sum, $n=2$: $2\cdot1\cdot a_2x^1=2a_2x$. New sum, $n=1$: $1\cdot2\cdot a_2x^1=2a_2x$. Equal.

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

> [!question]- Check (slide 4): Find the general solution of $y''+y=e^x$ as a power series about 0, up to $x^5$. Then recognise the functions that multiply $a_0$ and $a_1$.
> **Type of point.** $p=0$, $q=1$, $f=e^x$ are analytic at 0: ordinary point. **Method:** power series, with the right side expanded too.
> **Step 1, series.** $y=\sum_{n\ge0}a_nx^n$, $y'=\sum_{n\ge1}na_nx^{n-1}$, $y''=\sum_{n\ge2}n(n-1)a_nx^{n-2}$, and $e^x=\sum_{n\ge0}\dfrac{x^n}{n!}$.
> **Step 2, substitute.**
> $$\sum_{n\ge2}n(n-1)a_nx^{n-2}+\sum_{n\ge0}a_nx^n-\sum_{n\ge0}\frac{x^n}{n!}=0$$
> **Step 3, shift.** In the first sum replace $n$ by $n+2$. It starts at $n=0$: $\sum_{n\ge0}(n+2)(n+1)a_{n+2}x^n$.
> **Step 4.** All three sums start at $n=0$. Nothing to pull out.
> $$\sum_{n\ge0}\left[(n+2)(n+1)a_{n+2}+a_n-\frac{1}{n!}\right]x^n=0$$
> **Step 5, recurrence.**
> $$a_{n+2}=\frac{\frac{1}{n!}-a_n}{(n+2)(n+1)},\qquad n=0,1,2,\dots$$
> **Step 6, compute.**
> - $n=0$: $a_2=\dfrac{1-a_0}{2}$
> - $n=1$: $a_3=\dfrac{1-a_1}{6}$
> - $n=2$: $a_4=\dfrac{\frac12-a_2}{12}=\dfrac{\frac12-\frac12+\frac{a_0}{2}}{12}=\dfrac{a_0}{24}$
> - $n=3$: $a_5=\dfrac{\frac16-a_3}{20}=\dfrac{\frac16-\frac16+\frac{a_1}{6}}{20}=\dfrac{a_1}{120}$
>
> $$y=a_0+a_1x+\frac{1-a_0}{2}x^2+\frac{1-a_1}{6}x^3+\frac{a_0}{24}x^4+\frac{a_1}{120}x^5+\cdots$$
> **Recognise.** Collect by $a_0$, $a_1$ and the rest:
> $$y=a_0\left(1-\frac{x^2}{2}+\frac{x^4}{24}-\cdots\right)+a_1\left(x-\frac{x^3}{6}+\frac{x^5}{120}-\cdots\right)+\left(\frac{x^2}{2}+\frac{x^3}{6}+\cdots\right)$$
> The first bracket is $\cos x$, the second is $\sin x$. They solve $y''+y=0$. The last bracket is a particular solution. In closed form it is $\tfrac12e^x-\tfrac12\cos x-\tfrac12\sin x$: its series is $\tfrac12\left(1+x+\tfrac{x^2}{2}+\tfrac{x^3}{6}\right)-\tfrac12\left(1-\tfrac{x^2}{2}\right)-\tfrac12\left(x-\tfrac{x^3}{6}\right)+\cdots=\tfrac{x^2}{2}+\tfrac{x^3}{6}+\cdots$
> **Check** (coefficients of $y''+y$ against $e^x=1+x+\tfrac{x^2}{2}+\tfrac{x^3}{6}+\cdots$):
> - $x^0$: $2a_2+a_0=(1-a_0)+a_0=1$
> - $x^1$: $6a_3+a_1=(1-a_1)+a_1=1$
> - $x^2$: $12a_4+a_2=\tfrac{a_0}{2}+\tfrac12-\tfrac{a_0}{2}=\tfrac12$
> - $x^3$: $20a_5+a_3=\tfrac{a_1}{6}+\tfrac16-\tfrac{a_1}{6}=\tfrac16$
>
> All four agree.

> [!question]- Check (slide 5): Find the first three nonzero terms of each of two linearly independent power series solutions of $y''+x^2y=0$ about 0. By how much does the recurrence jump, and why?
> **Type of point.** $p=0$, $q=x^2$ are analytic at 0: ordinary point. **Method:** power series.
> **Step 1.** $y=\sum_{n\ge0}a_nx^n$, $y''=\sum_{n\ge2}n(n-1)a_nx^{n-2}$.
> **Step 2, substitute.**
> $$\sum_{n\ge2}n(n-1)a_nx^{n-2}+\sum_{n\ge0}a_nx^{n+2}=0$$
> **Step 3, shift.** First sum: $n\to n+2$, start $n=0$. Second sum: $n\to n-2$, start $n=2$.
> $$\sum_{n\ge0}(n+2)(n+1)a_{n+2}x^n+\sum_{n\ge2}a_{n-2}x^n=0$$
> **Step 4, same start.** Pull out $n=0$ and $n=1$ of the first sum: $2\cdot1\,a_2=2a_2$ and $3\cdot2\,a_3x=6a_3x$.
> $$2a_2+6a_3x+\sum_{n\ge2}\left[(n+2)(n+1)a_{n+2}+a_{n-2}\right]x^n=0$$
> **Step 5.** $x^0$: $a_2=0$. $x^1$: $a_3=0$. For $n\ge2$:
> $$a_{n+2}=-\frac{a_{n-2}}{(n+2)(n+1)}$$
> The recurrence jumps by four: $a_{n+2}$ comes from $a_{n-2}$. Reason: $y''$ lowers the power by 2 and $x^2y$ raises it by 2.
> **Step 6.**
> - $n=2$: $a_4=-\dfrac{a_0}{4\cdot3}=-\dfrac{a_0}{12}$
> - $n=3$: $a_5=-\dfrac{a_1}{5\cdot4}=-\dfrac{a_1}{20}$
> - $n=4$: $a_6=-\dfrac{a_2}{6\cdot5}=0$
> - $n=5$: $a_7=-\dfrac{a_3}{7\cdot6}=0$
> - $n=6$: $a_8=-\dfrac{a_4}{8\cdot7}=\dfrac{a_0}{12\cdot56}=\dfrac{a_0}{672}$
> - $n=7$: $a_9=-\dfrac{a_5}{9\cdot8}=\dfrac{a_1}{20\cdot72}=\dfrac{a_1}{1440}$
>
> With $a_0=1$, $a_1=0$ and then $a_0=0$, $a_1=1$:
> $$y_1=1-\frac{x^4}{12}+\frac{x^8}{672}-\cdots,\qquad y_2=x-\frac{x^5}{20}+\frac{x^9}{1440}-\cdots$$
> **Check.** $y_1''=-\dfrac{4\cdot3}{12}x^2+\dfrac{8\cdot7}{672}x^6=-x^2+\dfrac{x^6}{12}$ and $x^2y_1=x^2-\dfrac{x^6}{12}+\cdots$. The sum is 0 up to $x^6$.
> $y_2''=-\dfrac{5\cdot4}{20}x^3+\dfrac{9\cdot8}{1440}x^7=-x^3+\dfrac{x^7}{20}$ and $x^2y_2=x^3-\dfrac{x^7}{20}+\cdots$. The sum is 0 up to $x^7$.

> [!question]- Check (slide 6): Find the first five nonzero terms of the power series solution about 0 of $(1+x^2)y''+2xy'-2y=0$, $y(0)=2$, $y'(0)=3$. Recognise the function. Where is the series guaranteed to converge?
> **Type of point.** $p=\dfrac{2x}{1+x^2}$, $q=\dfrac{-2}{1+x^2}$. At $x=0$ the denominator is $1\neq0$, so 0 is an ordinary point. **Method:** power series, then the initial conditions give $a_0$ and $a_1$.
> **Step 1.** $y=\sum_{n\ge0}a_nx^n$, $y'=\sum_{n\ge1}na_nx^{n-1}$, $y''=\sum_{n\ge2}n(n-1)a_nx^{n-2}$.
> **Step 2, substitute and multiply out.**
> $$\sum_{n\ge2}n(n-1)a_nx^{n-2}+\sum_{n\ge2}n(n-1)a_nx^n+\sum_{n\ge1}2na_nx^n-\sum_{n\ge0}2a_nx^n=0$$
> **Step 3, shift.** Only the first sum needs it: $n\to n+2$ gives $\sum_{n\ge0}(n+2)(n+1)a_{n+2}x^n$.
> **Step 4, same start.** The second sum may start at $n=0$, because $n(n-1)=0$ for $n=0$ and $n=1$. The third sum may start at $n=0$, because $2n=0$ for $n=0$. So all sums start at $n=0$:
> $$\sum_{n\ge0}\left[(n+2)(n+1)a_{n+2}+\left(n(n-1)+2n-2\right)a_n\right]x^n=0$$
> **Step 5.** Simplify: $n(n-1)+2n-2=n^2+n-2=(n+2)(n-1)$. So $(n+2)(n+1)a_{n+2}+(n+2)(n-1)a_n=0$ and
> $$a_{n+2}=-\frac{n-1}{n+1}\,a_n,\qquad n=0,1,2,\dots$$
> **Step 6.**
> - $n=0$: $a_2=-\dfrac{-1}{1}a_0=a_0$
> - $n=1$: $a_3=-\dfrac{0}{2}a_1=0$, so $a_5=a_7=\dots=0$ too
> - $n=2$: $a_4=-\dfrac13a_2=-\dfrac{a_0}{3}$
> - $n=4$: $a_6=-\dfrac35a_4=\dfrac{a_0}{5}$
> - $n=6$: $a_8=-\dfrac57a_6=-\dfrac{a_0}{7}$
>
> General solution: $y=a_0\left(1+x^2-\dfrac{x^4}{3}+\dfrac{x^6}{5}-\dfrac{x^8}{7}+\cdots\right)+a_1x$.
> **Initial conditions.** $y(0)=a_0=2$. $y'=a_1+a_0\left(2x-\tfrac43x^3+\cdots\right)$, so $y'(0)=a_1=3$.
> $$y=2+3x+2x^2-\frac23x^4+\frac25x^6-\cdots$$
> **Recognise.** $x\arctan x=x\left(x-\dfrac{x^3}{3}+\dfrac{x^5}{5}-\cdots\right)=x^2-\dfrac{x^4}{3}+\dfrac{x^6}{5}-\cdots$ (series 5 on slide 2). So $y_1=1+x\arctan x$, $y_2=x$, and the IVP solution is $y=2+3x+2x\arctan x$.
> **Check** with $y=2+3x+2x^2-\tfrac23x^4+\tfrac25x^6$: $y'=3+4x-\tfrac83x^3+\tfrac{12}{5}x^5$, $y''=4-8x^2+12x^4$.
> - $y''=4-8x^2+12x^4$
> - $x^2y''=4x^2-8x^4+\cdots$
> - $2xy'=6x+8x^2-\tfrac{16}{3}x^4+\cdots$
> - $-2y=-4-6x-4x^2+\tfrac43x^4+\cdots$
>
> $x^0$: $4-4=0$. $x^1$: $6-6=0$. $x^2$: $-8+4+8-4=0$. $x^4$: $12-8-\tfrac{16}{3}+\tfrac43=0$. All vanish.
> **Convergence (beyond the slides).** $1+x^2=0$ at $x=\pm i$. The distance from 0 to $\pm i$ is 1, so the series converges at least for $\lvert x\rvert<1$. This fits the $\arctan$ series.

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

> [!info] Where the indicial equation comes from (beyond the slides)
> Slide 8 only says "it is possible to obtain a quadratic equation in $r$". The steps:
> 1. Divide $Py''+Qy'+Ry=0$ by $P$ and use $p(x)=x\dfrac QP$, $q(x)=x^2\dfrac RP$: $\ y''+\dfrac{p(x)}{x}y'+\dfrac{q(x)}{x^2}y=0$.
> 2. Put in $y=a_0x^r+a_1x^{r+1}+\cdots$, $p=c_0+c_1x+\cdots$, $q=d_0+d_1x+\cdots$ and keep only the lowest power, $x^{r-2}$:
>    - $y''=r(r-1)a_0x^{r-2}+\cdots$
>    - $\dfrac{p}{x}y'=\dfrac{c_0+\cdots}{x}\cdot ra_0x^{r-1}+\cdots=c_0ra_0x^{r-2}+\cdots$
>    - $\dfrac{q}{x^2}y=\dfrac{d_0+\cdots}{x^2}\cdot a_0x^r+\cdots=d_0a_0x^{r-2}+\cdots$
> 3. The coefficient of $x^{r-2}$ must be zero: $\left[r(r-1)+c_0r+d_0\right]a_0=0$. Because $a_0\neq0$: $r(r-1)+c_0r+d_0=0$.
>
> $c_0=p(0)$ and $d_0=q(0)$ are the constant terms of the two series. That is why they can be computed as limits for $x\to0$.
> The higher powers $x^{n+r-2}$, $n\ge1$, give the recurrence for $a_n$.

> [!warning] Slide wording (slides 8 and 11)
> Case (2.) on slide 8 says "if $r_1-r_2$ is not a positive integer". Read it as "if $r_1-r_2$ is not an integer" (not zero and not a positive integer). For $r_1-r_2=0$ both series would start with the same power $x^{r_1}$ and would be the same solution. That case is (3.) on slide 9 and needs $\ln x$. Slide 11 repeats the wording "$r_1-r_2$ is not a positive integer" for $r_1-r_2=\tfrac32$. This is not an integer, so case (2.) applies there.

> [!question]- Check (slide 7, classification): Find and classify the singular points of $(x^2-9)^2y''+(x+3)y'+2y=0$.
> $P(x)=(x^2-9)^2=(x-3)^2(x+3)^2$, $Q(x)=x+3$, $R(x)=2$.
> $P(x)=0$ gives $x=3$ or $x=-3$. These are the singular points.
> **At $x_0=3$.**
> $$(x-3)\frac{Q}{P}=(x-3)\cdot\frac{x+3}{(x-3)^2(x+3)^2}=\frac{1}{(x-3)(x+3)}$$
> For $x\to3$ the denominator goes to 0 and the function is unbounded. It is not analytic at 3. So $x=3$ is an **irregular** singular point. (The second function need not be tested.)
> **At $x_0=-3$.**
> $$(x+3)\frac{Q}{P}=(x+3)\cdot\frac{x+3}{(x-3)^2(x+3)^2}=\frac{1}{(x-3)^2},\qquad(x+3)^2\frac{R}{P}=(x+3)^2\cdot\frac{2}{(x-3)^2(x+3)^2}=\frac{2}{(x-3)^2}$$
> At $x=-3$ the denominator is $(-6)^2=36\neq0$. Both functions are analytic at $-3$, with the finite limits $\dfrac{1}{36}$ and $\dfrac{2}{36}=\dfrac{1}{18}$. So $x=-3$ is a **regular** singular point.
> Rule of thumb: after cancelling, $(x-x_0)$ may stay at most to power 1 in the denominator of $Q/P$ and at most to power 2 in the denominator of $R/P$.

> [!question]- Check (slide 7, Frobenius' theorem): For $2x^2y''+3xy'-y=0$ try $y=x^r$. Find both values of $r$. Why does this show that the theorem needs $x^{n+r}$ and not an ordinary power series $\sum a_nx^n$?
> **Type of point.** $P=2x^2$ is 0 at $x=0$: singular point. $x\dfrac QP=x\cdot\dfrac{3x}{2x^2}=\dfrac32$ and $x^2\dfrac RP=x^2\cdot\dfrac{-1}{2x^2}=-\dfrac12$ are constants, so analytic: 0 is a regular singular point.
> **Try $y=x^r$:** $y'=rx^{r-1}$, $y''=r(r-1)x^{r-2}$.
> $$2x^2\cdot r(r-1)x^{r-2}+3x\cdot rx^{r-1}-x^r=\left[2r(r-1)+3r-1\right]x^r=\left(2r^2+r-1\right)x^r$$
> Factor: $2r^2+r-1=(2r-1)(r+1)=0$, so $r=\tfrac12$ or $r=-1$.
> Solutions: $y_1=x^{1/2}=\sqrt x$ and $y_2=x^{-1}=\dfrac1x$.
> **Check for $y_2=x^{-1}$:** $y'=-x^{-2}$, $y''=2x^{-3}$: $\ 2x^2\cdot2x^{-3}+3x\cdot(-x^{-2})-x^{-1}=(4-3-1)x^{-1}=0$.
> **Check for $y_1=x^{1/2}$:** $y'=\tfrac12x^{-1/2}$, $y''=-\tfrac14x^{-3/2}$: $\ 2x^2\cdot\left(-\tfrac14\right)x^{-3/2}+3x\cdot\tfrac12x^{-1/2}-x^{1/2}=\left(-\tfrac12+\tfrac32-1\right)x^{1/2}=0$.
> Neither solution is a power series about 0: $\sqrt x$ has no derivative at 0 and $\dfrac1x$ is not defined at 0. A series $\sum a_nx^n$ can not produce them. The extra factor $x^r$ with a real $r$ (here $\tfrac12$ and $-1$) makes it possible. Here the series part is just $a_0$.

> [!question]- Check (slide 8, indicial equation): Find the indicial equation and its roots at 0 for $x^2y''+(\sin x)\,y'-(\cos x)\,y=0$. Which case of the theorem applies?
> $P=x^2$, $Q=\sin x$, $R=-\cos x$. $P(0)=0$: singular point.
> $$p(x)=x\frac QP=\frac{x\sin x}{x^2}=\frac{\sin x}{x}=1-\frac{x^2}{6}+\frac{x^4}{120}-\cdots$$
> $$q(x)=x^2\frac RP=\frac{x^2\cdot(-\cos x)}{x^2}=-\cos x=-1+\frac{x^2}{2}-\cdots$$
> Both are power series, so both are analytic at 0: regular singular point.
> Constant terms: $c_0=\lim_{x\to0}\dfrac{\sin x}{x}=1$ and $d_0=\lim_{x\to0}(-\cos x)=-1$.
> Indicial equation: $r(r-1)+c_0r+d_0=r^2-r+r-1=r^2-1=0$.
> Roots: $(r-1)(r+1)=0$, so $r_1=1$, $r_2=-1$.
> $r_1-r_2=2$ is a positive integer: case (4.). $y_1=\sum_{n\ge0}a_nx^{n+1}$ and $y_2=k\,y_1\ln x+\sum_{n\ge0}a_n^*x^{n-1}$, where $k$ may be 0.

> [!question]- Check (slide 9): For $xy''+y=0$ the indicial roots are $r_1=1$, $r_2=0$. Show this. Then try a plain series $y=\sum_{n\ge0}b_nx^n$ with $b_0\neq0$ for the smaller root. What goes wrong, and what does it say about $k$ in case (4.)? Also give the first four terms of $y_1$.
> **Type of point.** $P=x$, $Q=0$, $R=1$. $P(0)=0$: singular. $x\dfrac QP=0$ and $x^2\dfrac RP=\dfrac{x^2}{x}=x$ are analytic: regular singular point. $c_0=0$, $d_0=0$.
> **Indicial equation.** $r(r-1)+0\cdot r+0=r(r-1)=0$: $r_1=1$, $r_2=0$. Difference 1, a positive integer: case (4.).
> **Smaller root, $r=0$.** $y=\sum_{n\ge0}b_nx^n$, $y''=\sum_{n\ge2}n(n-1)b_nx^{n-2}$.
> $xy''=\sum_{n\ge2}n(n-1)b_nx^{n-1}$. It may start at $n=1$, because $n(n-1)=0$ for $n=1$.
> $y=\sum_{n\ge0}b_nx^n=\sum_{n\ge1}b_{n-1}x^{n-1}$ (shift $n\to n-1$).
> $$\sum_{n\ge1}\left[n(n-1)b_n+b_{n-1}\right]x^{n-1}=0\quad\Rightarrow\quad n(n-1)b_n+b_{n-1}=0,\ n\ge1$$
> $n=1$: $1\cdot0\cdot b_1+b_0=0$, so $b_0=0$. This contradicts $b_0\neq0$. No Frobenius series with $r=0$ exists.
> So the second solution must contain the logarithm: $k\neq0$ in $y_2=k\,y_1\ln x+\sum a_n^*x^n$.
> Compare with "Check yourself" 6, where the critical step reads $0=0$ and $k=0$.
> **Larger root, $r=1$.** $y=\sum_{n\ge0}a_nx^{n+1}$, $y''=\sum_{n\ge0}(n+1)n\,a_nx^{n-1}$.
> $xy''=\sum_{n\ge0}(n+1)n\,a_nx^n$ and $y=\sum_{n\ge0}a_nx^{n+1}=\sum_{n\ge1}a_{n-1}x^n$.
> $n=0$: $1\cdot0\cdot a_0=0$, true for every $a_0$. $n\ge1$: $n(n+1)a_n+a_{n-1}=0$, so $a_n=-\dfrac{a_{n-1}}{n(n+1)}$.
> With $a_0=1$: $a_1=-\dfrac{1}{1\cdot2}=-\dfrac12$, $a_2=-\dfrac{a_1}{2\cdot3}=\dfrac{1}{12}$, $a_3=-\dfrac{a_2}{3\cdot4}=-\dfrac{1}{144}$.
> $$y_1=x-\frac{x^2}{2}+\frac{x^3}{12}-\frac{x^4}{144}+\cdots$$
> **Check.** $y_1''=-1+\dfrac x2-\dfrac{x^2}{12}+\cdots$, so $xy_1''=-x+\dfrac{x^2}{2}-\dfrac{x^3}{12}+\cdots$. Adding $y_1$ gives 0 up to $x^3$.

## 5. Frobenius example: roots not differing by an integer (slides 10-12)
![[math501_lecture_04_math501_chapter_4_p010.jpg]]
![[math501_lecture_04_math501_chapter_4_p011.jpg]]

**Notes.** $x^2y''+\left(2x^2+\tfrac x2\right)y'+\left(x-\tfrac12\right)y=0$ about 0.

- $x\,Q/P=2x+\tfrac12$ and $x^2R/P=x-\tfrac12$ are analytic: 0 is a regular singular point, $c_0=\tfrac12$, $d_0=-\tfrac12$.
- Indicial equation: $r^2-\tfrac12r-\tfrac12=(r-1)(r+\tfrac12)=0$, so $r_1=1$, $r_2=-\tfrac12$.
- Recurrence: $\left[(n+r)(n+r-\tfrac12)-\tfrac12\right]a_n+(2n+2r-1)a_{n-1}=0$.
- $r=1$: $a_n=-\dfrac{(2n+1)a_{n-1}}{n(n+\frac32)}$, so $y_1=x-\tfrac65x^2+\tfrac67x^3-\tfrac49x^4+\tfrac{2}{11}x^5+\cdots$
- $r=-\tfrac12$: $a_n^*=-\dfrac{(2n-2)a_{n-1}^*}{n(n-\frac32)}$. For $n=1$ the numerator is 0, so all $a_n^*=0$ for $n\ge1$ and $y_2=\dfrac{1}{\sqrt x}$ (top of slide 12).

> [!question]- Check (slides 10-11): For $2xy''+(1+x)y'+y=0$ about 0: classify the point, find the indicial equation and its roots, the recurrence for general $r$, and the solution $y_1$ for the larger root (four terms). Recognise $y_1$.
> **Type of point.** $P=2x$, $Q=1+x$, $R=1$. $P(0)=0$: singular.
> $x\dfrac QP=x\cdot\dfrac{1+x}{2x}=\dfrac12+\dfrac x2$ and $x^2\dfrac RP=x^2\cdot\dfrac{1}{2x}=\dfrac x2$ are polynomials, so analytic: regular singular point, $c_0=\tfrac12$, $d_0=0$. **Method:** Frobenius.
> **Series.** $y=\sum_{n\ge0}a_nx^{n+r}$ ($a_0\neq0$), $y'=\sum_{n\ge0}(n+r)a_nx^{n+r-1}$, $y''=\sum_{n\ge0}(n+r)(n+r-1)a_nx^{n+r-2}$.
> **Substitute, term by term.**
> - $2xy''=\sum_{n\ge0}2(n+r)(n+r-1)a_nx^{n+r-1}$
> - $y'=\sum_{n\ge0}(n+r)a_nx^{n+r-1}$
> - $xy'=\sum_{n\ge0}(n+r)a_nx^{n+r}$
> - $y=\sum_{n\ge0}a_nx^{n+r}$
>
> The first two have the power $x^{n+r-1}$. Add them: $2(n+r)(n+r-1)+(n+r)=(n+r)(2n+2r-1)$.
> The last two have the power $x^{n+r}$. Add them: $(n+r)+1=n+r+1$.
> $$\sum_{n\ge0}(n+r)(2n+2r-1)a_nx^{n+r-1}+\sum_{n\ge0}(n+r+1)a_nx^{n+r}=0$$
> **Shift** the second sum ($n\to n-1$, start $n=1$): $\sum_{n\ge1}(n+r)a_{n-1}x^{n+r-1}$.
> **Pull out $n=0$** of the first sum:
> $$r(2r-1)a_0x^{r-1}+\sum_{n\ge1}\left[(n+r)(2n+2r-1)a_n+(n+r)a_{n-1}\right]x^{n+r-1}=0$$
> **Indicial equation.** $r(2r-1)=0$, so $r_1=\tfrac12$, $r_2=0$. (Same as the formula: $r(r-1)+\tfrac12r+0=r^2-\tfrac12r=\tfrac12r(2r-1)$.) The difference $\tfrac12$ is not an integer: case (2.), two Frobenius series.
> **Recurrence.** $(n+r)(2n+2r-1)a_n+(n+r)a_{n-1}=0$. Divide by $(n+r)\neq0$:
> $$a_n=-\frac{a_{n-1}}{2n+2r-1},\qquad n\ge1$$
> **Larger root $r=\tfrac12$:** $2n+2\cdot\tfrac12-1=2n$, so $a_n=-\dfrac{a_{n-1}}{2n}$. With $a_0=1$:
> - $a_1=-\dfrac12$
> - $a_2=-\dfrac{a_1}{4}=\dfrac18$
> - $a_3=-\dfrac{a_2}{6}=-\dfrac{1}{48}$
> - $a_4=-\dfrac{a_3}{8}=\dfrac{1}{384}$
>
> $$y_1=x^{1/2}\left(1-\frac x2+\frac{x^2}{8}-\frac{x^3}{48}+\frac{x^4}{384}-\cdots\right)$$
> **Recognise.** $a_n=\dfrac{(-1)^n}{2^n\,n!}$, so the bracket is $\sum\dfrac{(-x/2)^n}{n!}=e^{-x/2}$ and $y_1=\sqrt x\,e^{-x/2}$.
> **Check** (coefficient of $x^{n+r-1}$ with $r=\tfrac12$): $n=1$: $\tfrac32\cdot2\cdot a_1+\tfrac32a_0=-\tfrac32+\tfrac32=0$. $n=2$: $\tfrac52\cdot4\cdot a_2+\tfrac52a_1=\tfrac54-\tfrac54=0$.

> [!question]- Check (slide 11, second root): Continue with $2xy''+(1+x)y'+y=0$. Find the second solution $y_2$ for $r_2=0$ (five terms) and check it. Does the series stop, as $y_2$ on the slide does?
> Recurrence from the question before: $a_n^*=-\dfrac{a_{n-1}^*}{2n+2r-1}$. With $r=0$: $a_n^*=-\dfrac{a_{n-1}^*}{2n-1}$.
> With $a_0^*=1$:
> - $n=1$: $a_1^*=-\dfrac{1}{1}=-1$
> - $n=2$: $a_2^*=-\dfrac{a_1^*}{3}=\dfrac13$
> - $n=3$: $a_3^*=-\dfrac{a_2^*}{5}=-\dfrac{1}{15}$
> - $n=4$: $a_4^*=-\dfrac{a_3^*}{7}=\dfrac{1}{105}$
>
> $$y_2=1-x+\frac{x^2}{3}-\frac{x^3}{15}+\frac{x^4}{105}-\cdots$$
> The numerator is never 0, so the series does not stop. On the slide the factor $(2n-2)$ is 0 at $n=1$, and only there the series ends after one term.
> **Check.** $y_2'=-1+\tfrac23x-\tfrac15x^2+\cdots$, $y_2''=\tfrac23-\tfrac25x+\cdots$.
> - $2xy_2''=\tfrac43x-\tfrac45x^2+\cdots$
> - $(1+x)y_2'=-1+\left(\tfrac23-1\right)x+\left(-\tfrac15+\tfrac23\right)x^2+\cdots=-1-\tfrac13x+\tfrac{7}{15}x^2+\cdots$
> - $y_2=1-x+\tfrac13x^2+\cdots$
>
> $x^0$: $-1+1=0$. $x^1$: $\tfrac43-\tfrac13-1=0$. $x^2$: $-\tfrac45+\tfrac{7}{15}+\tfrac13=\tfrac{-12+7+5}{15}=0$. All vanish.
> General solution for $x>0$: $y=C_1\sqrt x\,e^{-x/2}+C_2\,y_2$.

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

> [!question]- Check (slide 12, end of the previous example): The top of slide 12 gives $y_2=\dfrac{1}{\sqrt x}$ for $x^2y''+\left(2x^2+\tfrac x2\right)y'+\left(x-\tfrac12\right)y=0$. Verify it by direct substitution.
> $y=x^{-1/2}$, $y'=-\tfrac12x^{-3/2}$, $y''=\left(-\tfrac12\right)\left(-\tfrac32\right)x^{-5/2}=\tfrac34x^{-5/2}$.
> - $x^2y''=\tfrac34x^{-1/2}$
> - $\left(2x^2+\tfrac x2\right)y'=2x^2\cdot\left(-\tfrac12\right)x^{-3/2}+\tfrac x2\cdot\left(-\tfrac12\right)x^{-3/2}=-x^{1/2}-\tfrac14x^{-1/2}$
> - $\left(x-\tfrac12\right)y=x^{1/2}-\tfrac12x^{-1/2}$
>
> Sum of the $x^{1/2}$ terms: $-1+1=0$. Sum of the $x^{-1/2}$ terms: $\tfrac34-\tfrac14-\tfrac12=0$.
> The left side is 0 for all $x>0$, so $y_2$ is an exact solution. Not only the first terms vanish.

> [!question]- Check (slides 12-13): For $xy''+y'-y=0$ about 0: classify the point, find the indicial equation, the recurrence and the Frobenius solution $y_1$ (five terms and the general coefficient).
> **Type of point.** $P=x$, $Q=1$, $R=-1$. $P(0)=0$: singular. $x\dfrac QP=x\cdot\dfrac1x=1$ and $x^2\dfrac RP=x^2\cdot\dfrac{-1}{x}=-x$ are analytic: regular singular point, $c_0=1$, $d_0=0$. **Method:** Frobenius.
> **Series.** $y=\sum_{n\ge0}a_nx^{n+r}$, $y'=\sum_{n\ge0}(n+r)a_nx^{n+r-1}$, $y''=\sum_{n\ge0}(n+r)(n+r-1)a_nx^{n+r-2}$.
> **Substitute.**
> $$\sum_{n\ge0}(n+r)(n+r-1)a_nx^{n+r-1}+\sum_{n\ge0}(n+r)a_nx^{n+r-1}-\sum_{n\ge0}a_nx^{n+r}=0$$
> Add the first two: $(n+r)(n+r-1)+(n+r)=(n+r)^2$. Shift the third ($n\to n-1$, start $n=1$): $\sum_{n\ge1}a_{n-1}x^{n+r-1}$.
> $$r^2a_0x^{r-1}+\sum_{n\ge1}\left[(n+r)^2a_n-a_{n-1}\right]x^{n+r-1}=0$$
> **Indicial equation.** $r^2=0$: repeated root $r_1=r_2=0$. (Formula: $r(r-1)+1\cdot r+0=r^2$.) This is case (3.).
> **Recurrence.** $(n+r)^2a_n=a_{n-1}$. With $r=0$: $a_n=\dfrac{a_{n-1}}{n^2}$, $n\ge1$.
> With $a_0=1$:
> - $a_1=\dfrac{1}{1^2}=1$
> - $a_2=\dfrac{a_1}{2^2}=\dfrac14$
> - $a_3=\dfrac{a_2}{3^2}=\dfrac{1}{36}$
> - $a_4=\dfrac{a_3}{4^2}=\dfrac{1}{576}$
>
> In general $a_n=\dfrac{1}{1^2\cdot2^2\cdots n^2}=\dfrac{1}{(n!)^2}$.
> $$y_1=\sum_{n\ge0}\frac{x^n}{(n!)^2}=1+x+\frac{x^2}{4}+\frac{x^3}{36}+\frac{x^4}{576}+\cdots$$
> **Check.** $y_1'=1+\tfrac x2+\tfrac{x^2}{12}+\tfrac{x^3}{144}+\cdots$, $y_1''=\tfrac12+\tfrac x6+\tfrac{x^2}{48}+\cdots$, so $xy_1''=\tfrac x2+\tfrac{x^2}{6}+\tfrac{x^3}{48}+\cdots$
> $x^0$: $1-1=0$. $x^1$: $\tfrac12+\tfrac12-1=0$. $x^2$: $\tfrac16+\tfrac{1}{12}-\tfrac14=0$. $x^3$: $\tfrac{1}{48}+\tfrac{1}{144}-\tfrac{1}{36}=\tfrac{3+1-4}{144}=0$.
> Compare with the slide: there $a_n=\dfrac{(-1)^n}{(n!)^2}$ and $r=-2$. Here there is no sign change and $r=0$.

> [!question]- Check (slides 13-14): Continue with $xy''+y'-y=0$, $y_1=\sum_{n\ge0}\dfrac{x^n}{(n!)^2}$. Put $y_2=y_1\ln x+\sum_{n\ge1}b_nx^n$ into the equation. Show that all $\ln x$ terms cancel, and find $b_1$, $b_2$, $b_3$.
> **Derivatives** (product rule on $y_1\ln x$):
> - $y_2'=y_1'\ln x+\dfrac{y_1}{x}+\sum_{n\ge1}nb_nx^{n-1}$
> - $y_2''=y_1''\ln x+\dfrac{y_1'}{x}+\dfrac{y_1'}{x}-\dfrac{y_1}{x^2}+\sum_{n\ge1}n(n-1)b_nx^{n-2}=y_1''\ln x+\dfrac{2y_1'}{x}-\dfrac{y_1}{x^2}+\sum_{n\ge1}n(n-1)b_nx^{n-2}$
>
> **Substitute into $xy''+y'-y$:**
> - $xy_2''=xy_1''\ln x+2y_1'-\dfrac{y_1}{x}+\sum_{n\ge1}n(n-1)b_nx^{n-1}$
> - $y_2'=y_1'\ln x+\dfrac{y_1}{x}+\sum_{n\ge1}nb_nx^{n-1}$
> - $-y_2=-y_1\ln x-\sum_{n\ge1}b_nx^n$
>
> **Collect.** The $\ln x$ terms: $\ln x\left[xy_1''+y_1'-y_1\right]=\ln x\cdot0$, because $y_1$ solves the ODE. Also $-\dfrac{y_1}{x}+\dfrac{y_1}{x}=0$. What is left:
> $$2y_1'+\sum_{n\ge1}\left[n(n-1)+n\right]b_nx^{n-1}-\sum_{n\ge1}b_nx^n=0$$
> $n(n-1)+n=n^2$. Shift the last sum ($n\to n-1$, start $n=2$): $\sum_{n\ge2}b_{n-1}x^{n-1}$.
> **Series of $2y_1'$.** $y_1'=\sum_{n\ge1}\dfrac{n\,x^{n-1}}{(n!)^2}$, so $2y_1'=\sum_{n\ge1}\dfrac{2n}{(n!)^2}x^{n-1}=2+x+\dfrac{x^2}{6}+\cdots$ (values $\tfrac{2}{1}$, $\tfrac{4}{4}$, $\tfrac{6}{36}$).
> **Coefficient of $x^{n-1}$.**
> - $n=1$: $2+1^2\,b_1=0$, so $b_1=-2$.
> - $n\ge2$: $\dfrac{2n}{(n!)^2}+n^2b_n-b_{n-1}=0$, so $b_n=\dfrac{1}{n^2}\left[b_{n-1}-\dfrac{2n}{(n!)^2}\right]$.
>
> **Compute.**
> - $n=2$: $b_2=\dfrac14\left[-2-\dfrac44\right]=\dfrac14\cdot(-3)=-\dfrac34$
> - $n=3$: $b_3=\dfrac19\left[-\dfrac34-\dfrac{6}{36}\right]=\dfrac19\left[-\dfrac{9}{12}-\dfrac{2}{12}\right]=\dfrac19\cdot\left(-\dfrac{11}{12}\right)=-\dfrac{11}{108}$
>
> $$y_2=y_1\ln x-2x-\frac34x^2-\frac{11}{108}x^3-\cdots$$
> **Check** (coefficients of $2y_1'+\sum n^2b_nx^{n-1}-\sum b_{n-1}x^{n-1}$):
> $x^0$: $2+b_1=2-2=0$. $x^1$: $1+4b_2-b_1=1-3+2=0$. $x^2$: $\tfrac16+9b_3-b_2=\tfrac16-\tfrac{11}{12}+\tfrac34=\tfrac{2-11+9}{12}=0$.
> The numbers $2$, $\tfrac34$, $\tfrac{11}{108}$ are the same as on slide 15 up to sign. The two equations are closely related.

> [!question]- Check (slide 15): Slide 15 gives $a_3^*=\tfrac{11}{108}$ and $a_4^*=-\tfrac{25}{3456}$ without the computation. Do both with the slide's recurrence $a_n^*=-\dfrac{1}{n^2}\left[a_{n-1}^*+\dfrac{4(-1)^n}{(n!)^2}+\dfrac{2(-1)^n(n-2)}{(n!)^2}\right]$, starting from $a_2^*=-\tfrac34$.
> **$n=3$.** $(3!)^2=36$, $(-1)^3=-1$, $n-2=1$.
> - $\dfrac{4(-1)^3}{36}=-\dfrac{4}{36}=-\dfrac19$
> - $\dfrac{2(-1)^3\cdot1}{36}=-\dfrac{2}{36}=-\dfrac{1}{18}$
> - Bracket: $-\dfrac34-\dfrac19-\dfrac{1}{18}=-\dfrac{27}{36}-\dfrac{4}{36}-\dfrac{2}{36}=-\dfrac{33}{36}=-\dfrac{11}{12}$
>
> $a_3^*=-\dfrac19\cdot\left(-\dfrac{11}{12}\right)=\dfrac{11}{108}$.
> **$n=4$.** $(4!)^2=576$, $(-1)^4=1$, $n-2=2$.
> - $\dfrac{4\cdot1}{576}=\dfrac{1}{144}$
> - $\dfrac{2\cdot1\cdot2}{576}=\dfrac{4}{576}=\dfrac{1}{144}$
> - Bracket: $\dfrac{11}{108}+\dfrac{1}{144}+\dfrac{1}{144}=\dfrac{44}{432}+\dfrac{3}{432}+\dfrac{3}{432}=\dfrac{50}{432}=\dfrac{25}{216}$
>
> $a_4^*=-\dfrac{1}{16}\cdot\dfrac{25}{216}=-\dfrac{25}{3456}$.
> Both agree with the slide. In $y_2$ they multiply $x^{3-2}=x$ and $x^{4-2}=x^2$.

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
- Quiz: [[MATH501 L04 - Series solutions of ODEs - quiz]]

Slides not embedded: none.
