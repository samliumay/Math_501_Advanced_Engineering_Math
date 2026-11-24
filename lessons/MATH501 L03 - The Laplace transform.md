---
course: MATH 501 Advanced Engineering Mathematics
lecture: 3
title: The Laplace transform
tags: [math501, lecture]
slides: lectures/lecture_03/Math501 Chapter 3.pdf
full_notes: lecture_notes/lecture_03/MATH501_Lecture_03_Laplace_Transform.pdf
---
# MATH 501 · Lecture 3 · The Laplace transform

> [!summary] In short
> - $F(s)=\mathcal L[f(t)]=\int_0^\infty e^{-st}f(t)\,dt$, defined for $s$ larger than some number.
> - Derivatives become algebra: $\mathcal L[y']=sY-y(0)$, $\mathcal L[y'']=s^2Y-sy(0)-y'(0)$. An IVP becomes one linear equation for $Y$.
> - Inverting means reading the table backwards after partial fractions or completing the square.
> - First shifting: $e^{at}$ in $t$ shifts $s$. Second shifting: $e^{-as}$ in $s$ delays $t$.
> - A product $F(s)G(s)$ belongs to the convolution $f*g$. The delta function has $\mathcal L[\delta(t-a)]=e^{-as}$.

The slide numbers below are the pages of the Chapter 3 PDF (page 1 is printed page 43).

## 1. Definition and transforms from the definition (slides 1-3)
![[math501_lecture_03_math501_chapter_3_p001.jpg]]
![[math501_lecture_03_math501_chapter_3_p002.jpg]]
![[math501_lecture_03_math501_chapter_3_p003.jpg]]

**Notes.** For $f(t)$ defined on $t\ge0$:

$$F(s)=\mathcal L[f(t)]=\int_0^\infty e^{-st}f(t)\,dt=\lim_{R\to\infty}\int_0^Re^{-st}f(t)\,dt .$$

The integral is in $t$. The result is a function of the new variable $s$, for those $s$ where the limit exists.

To compute from the definition: integrate up to $R$ (often by parts), let $R\to\infty$, and state for which $s$ the limit exists.

> [!example] Slide results
> - $\mathcal L[1]=\dfrac1s$ for $s>0$.
> - $\mathcal L[e^{at}]=\dfrac{1}{s-a}$ for $s>a$.
> - $\mathcal L[\sin at]=\dfrac{a}{s^2+a^2}$ for $s>0$ (two integrations by parts, then solve for the integral).

## 2. Existence, linearity, table, multiplying and dividing by t (slides 4-6)
![[math501_lecture_03_math501_chapter_3_p004.jpg]]
![[math501_lecture_03_math501_chapter_3_p005.jpg]]
![[math501_lecture_03_math501_chapter_3_p006.jpg]]

**Notes.** **Existence.** If $f$ is piecewise continuous on every finite interval of $t\ge0$ and $|f(t)|\le Me^{kt}$ for $t\ge T$, then $F(s)$ exists for all $s>k$. These conditions are sufficient, not necessary. $e^{t^2}$ has no transform.

**Linearity.** $\mathcal L[af+bg]=aF(s)+bG(s)$.

**Multiplication by $t^n$.**

$$\mathcal L[t^nf(t)]=(-1)^n\frac{d^n}{ds^n}F(s).$$

**Division by $t$.** If $\lim_{t\to0}f(t)/t$ exists, then $\mathcal L\!\left[\dfrac{f(t)}{t}\right]=\displaystyle\int_s^\infty F(u)\,du$.

> [!example] Slide examples
> - $\mathcal L[t+t^2\cos t]=\dfrac{1}{s^2}+\dfrac{d^2}{ds^2}\dfrac{s}{s^2+1}=\dfrac{1}{s^2}+\dfrac{2s^3-6s}{(s^2+1)^3}$.
> - $\mathcal L[te^{2t}\cos3t]=-\dfrac{d}{ds}\dfrac{s-2}{(s-2)^2+9}=\dfrac{s^2-4s-5}{(s^2-4s+13)^2}$.
> - $\mathcal L\!\left[\dfrac{\sin t}{t}\right]=\displaystyle\int_s^\infty\frac{du}{u^2+1}=\frac\pi2-\arctan s$ (the end is at the top of slide 7).

## 3. The inverse Laplace transform (slide 7)
![[math501_lecture_03_math501_chapter_3_p007.jpg]]

**Notes.** If $\mathcal L[f]=F$, then $f=\mathcal L^{-1}[F]$. The inverse is also linear. It is essentially unique: two continuous functions with the same transform are identical.

Method: split $F$ into simple pieces (partial fractions, or complete the square), adjust constants so that each piece matches a table entry exactly, then read the table backwards.

> [!example] Slide examples
> - $\mathcal L^{-1}\!\left[\dfrac{-2s+6}{s^2+4}\right]=-2\cos2t+3\sin2t$ (write $6=3\cdot2$).
> - $\dfrac{3}{(s-1)(s-2)}=\dfrac{-3}{s-1}+\dfrac{3}{s-2}$, so the inverse is $-3e^{t}+3e^{2t}$.

## 4. Solving initial value problems (slides 8-11)
![[math501_lecture_03_math501_chapter_3_p008.jpg]]
![[math501_lecture_03_math501_chapter_3_p009.jpg]]
![[math501_lecture_03_math501_chapter_3_p010.jpg]]

**Notes.** Write $Y=\mathcal L[y]$.

$$\mathcal L[y']=sY-y(0),\qquad\mathcal L[y'']=s^2Y-sy(0)-y'(0).$$

In general $\mathcal L[f^{(n)}]=s^nF-s^{n-1}f(0)-\dots-f^{(n-1)}(0)$.

Steps: transform both sides, insert the initial values, solve for $Y$, partial fractions, invert. The initial conditions are used automatically, so there are no constants to find at the end.

> [!example] Slide examples
> - $y'+2y=0$, $y(0)=\tfrac32$: $(s+2)Y=\tfrac32$, $y=\tfrac32e^{-2t}$.
> - $y''-4y'+3y=6t-8$, $y(0)=y'(0)=0$: $Y=\dfrac{6-8s}{s^2(s-1)(s-3)}=\dfrac{2}{s^2}+\dfrac{1}{s-1}-\dfrac{1}{s-3}$, $y=2t+e^t-e^{3t}$.
> - $y''-4y'+4y=\cos t$, $y(0)=1$, $y'(0)=-1$: $y=\tfrac{3}{25}\cos t-\tfrac{4}{25}\sin t+\tfrac{22}{25}e^{2t}-\tfrac{13}{5}te^{2t}$.
> - $y''+16y=1+t$, $y(0)=-2$, $y'(0)=1$: $y=\tfrac{1}{16}+\tfrac{t}{16}-\tfrac{33}{16}\cos4t+\tfrac{15}{64}\sin4t$ (ends on slide 11).

> [!warning] Watch out
> Do not drop the initial value terms. $\mathcal L[y'']$ contains $-sy(0)$ and $-y'(0)$. They vanish only when the initial values are zero.

## 5. First shifting theorem (slides 11-12)
![[math501_lecture_03_math501_chapter_3_p011.jpg]]
![[math501_lecture_03_math501_chapter_3_p012.jpg]]

**Notes.** A factor $e^{at}$ in time replaces $s$ by $s-a$:

$$\mathcal L[e^{at}f(t)]=F(s-a),\qquad\mathcal L^{-1}[F(s-a)]=e^{at}f(t).$$

For an inverse with an irreducible quadratic: complete the square, write the numerator with the same shifted variable, then shift.

> [!example] Slide examples
> - $\mathcal L[t^4]=\dfrac{24}{s^5}$, so $\mathcal L[t^4e^{9t}]=\dfrac{24}{(s-9)^5}$.
> - $s^2+6s+1=(s+3)^2-(2\sqrt2)^2$ and $s+2=(s+3)-1$, so $\mathcal L^{-1}\!\left[\dfrac{s+2}{s^2+6s+1}\right]=e^{-3t}\cosh(2\sqrt2\,t)-\dfrac{1}{2\sqrt2}e^{-3t}\sinh(2\sqrt2\,t)$.

After completing the square, a minus sign gives $\cosh$ and $\sinh$. A plus sign gives $\cos$ and $\sin$.

## 6. Heaviside function and pulses (slides 12-13)
![[math501_lecture_03_math501_chapter_3_p013.jpg]]

**Notes.** The **Heaviside (unit step) function** is $H(t)=0$ for $t<0$ and $1$ for $t\ge0$. The shifted step $u_c(t)=H(t-c)$ switches on at $t=c$. A **pulse** on $[a,b)$ is $H(t-a)-H(t-b)$. The definitions start at the bottom of slide 12.

$$\mathcal L[H(t-c)]=\frac{e^{-cs}}{s},\qquad s>0,\ c>0.$$

To write a piecewise function with steps: for each piece $[a,b)$ with value $g$, write $g\,[H(t-a)-H(t-b)]$. Add the pieces and collect.

> [!example] Slide example
> $f=3$ on $[0,1)$, $8$ on $[1,2)$, $-2$ for $t\ge2$: $f=3H(t)+5H(t-1)-10H(t-2)$, so $\mathcal L[f]=\dfrac3s+\dfrac{5e^{-s}}{s}-\dfrac{10e^{-2s}}{s}$.

## 7. Second shifting theorem (slides 14-15)
![[math501_lecture_03_math501_chapter_3_p014.jpg]]
![[math501_lecture_03_math501_chapter_3_p015.jpg]]

**Notes.** Delaying a signal by $a$ multiplies its transform by $e^{-as}$:

$$\mathcal L[H(t-a)f(t-a)]=e^{-as}F(s),\qquad\mathcal L^{-1}[e^{-as}F(s)]=H(t-a)f(t-a).$$

> [!example] Slide examples
> - $\dfrac{1}{s(s^2+16)}=\dfrac{1}{16}\cdot\dfrac1s-\dfrac{1}{16}\cdot\dfrac{s}{s^2+16}$, so $\mathcal L^{-1}\!\left[\dfrac{e^{-9s}}{s(s^2+16)}\right]=H(t-9)\left(\tfrac{1}{16}-\tfrac{1}{16}\cos(4t-36)\right)$.
> - $y''+4y=3H(t-4)$, $y(0)=1$, $y'(0)=0$: $Y=\dfrac{3e^{-4s}}{s(s^2+4)}+\dfrac{s}{s^2+4}$, $y=\cos2t+H(t-4)\left(\tfrac34-\tfrac34\cos(2t-8)\right)$.

> [!warning] Watch out
> - Shift the argument too: the inverse is $H(t-a)f(t-a)$, not $H(t-a)f(t)$.
> - The slide says "a real constant $a$". The proof needs $a\ge0$.

## 8. Convolution (slides 16-18)
![[math501_lecture_03_math501_chapter_3_p016.jpg]]
![[math501_lecture_03_math501_chapter_3_p017.jpg]]

**Notes.** The **convolution** of $f$ and $g$ is

$$(f*g)(t)=\int_0^tf(t-\tau)\,g(\tau)\,d\tau .$$

It is commutative, distributive and associative. **Convolution theorem:**

$$\mathcal L[f*g]=F(s)G(s),\qquad\mathcal L^{-1}[F(s)G(s)]=(f*g)(t).$$

> [!example] Slide examples
> - $u_2(t)*\sin t=\mathcal L^{-1}\!\left[\dfrac{e^{-2s}}{s(s^2+1)}\right]=H(t-2)\,(1-\cos(t-2))$.
> - $\mathcal L^{-1}\!\left[\dfrac{1}{(s+1)(s^2+4)}\right]=e^{-t}*\tfrac12\sin2t=\tfrac{1}{10}\left(\sin2t-2\cos2t+2e^{-t}\right)$.
> - $y''-5y'+6y=f(t)$, $y(0)=y'(0)=0$ (top of slide 18): $Y=\dfrac{F(s)}{(s-3)(s-2)}$, so $y=\displaystyle\int_0^tf(\tau)\left(e^{3(t-\tau)}-e^{2(t-\tau)}\right)d\tau$.

> [!warning] Watch out
> $\mathcal L[fg]\neq F\,G$. Example: $\mathcal L[1\cdot1]=\tfrac1s$, but $\tfrac1s\cdot\tfrac1s=\tfrac{1}{s^2}$.

## 9. Dirac delta function (slides 18-20)
![[math501_lecture_03_math501_chapter_3_p018.jpg]]
![[math501_lecture_03_math501_chapter_3_p019.jpg]]
![[math501_lecture_03_math501_chapter_3_p020.jpg]]

**Notes.** Take the pulse $\delta_\epsilon(t)=\tfrac1\epsilon\,(H(t)-H(t-\epsilon))$: width $\epsilon$, height $1/\epsilon$, area 1. The **Dirac delta** is the limit $\epsilon\to0^+$: a kick of total size one at a single instant.

$$\mathcal L[\delta(t-a)]=e^{-as},\qquad\mathcal L[\delta(t)]=1.$$

**Filtering property.** If $f$ is continuous at $a>0$: $\displaystyle\int_0^\infty f(t)\,\delta(t-a)\,dt=f(a)$.

> [!example] Slide examples
> - $y'+3y=\delta(t-1)$, $y(0)=1$: $Y=\dfrac{e^{-s}}{s+3}+\dfrac{1}{s+3}$, $y=H(t-1)e^{-3(t-1)}+e^{-3t}$.
> - $y''+2y'+2y=\delta(t-3)$, $y(0)=y'(0)=0$: $Y=\dfrac{e^{-3s}}{(s+1)^2+1}$, $y=H(t-3)\,e^{-(t-3)}\sin(t-3)$ (both shifting theorems).

> [!warning] Watch out
> $\mathcal L[\delta(t)]=1$ but $\mathcal L[1]=\tfrac1s$.

## 10. Systems of ODEs (slides 21-22)
![[math501_lecture_03_math501_chapter_3_p021.jpg]]
![[math501_lecture_03_math501_chapter_3_p022.jpg]]

**Notes.** Transform each equation with $X=\mathcal L[x]$, $Y=\mathcal L[y]$. The result is two linear algebraic equations in $X$ and $Y$. Solve them, then invert each with partial fractions.

> [!example] Slide example
> $x''-2x'+3y'+2y=4$, $2y'-x'+3y=0$, $x(0)=x'(0)=y(0)=0$.
> Transformed: $(s^2-2s)X+(3s+2)Y=\tfrac4s$ and $-sX+(2s+3)Y=0$. So $X=\tfrac{2s+3}{s}Y$ and
> $$Y=\frac{2}{s(s+2)(s-1)},\qquad X=\frac{4s+6}{s^2(s+2)(s-1)} .$$
> Answer: $x=-\tfrac72-3t+\tfrac16e^{-2t}+\tfrac{10}{3}e^{t}$, $y=-1+\tfrac13e^{-2t}+\tfrac23e^{t}$.

## Key formulas and terms
| $f(t)$ | $F(s)$ |
|---|---|
| $1$ | $\dfrac1s$, $s>0$ |
| $t^n$ | $\dfrac{n!}{s^{n+1}}$, $s>0$ |
| $e^{at}$ | $\dfrac{1}{s-a}$, $s>a$ |
| $\sin at$, $\cos at$ | $\dfrac{a}{s^2+a^2}$, $\dfrac{s}{s^2+a^2}$ |
| $\sinh at$, $\cosh at$ | $\dfrac{a}{s^2-a^2}$, $\dfrac{s}{s^2-a^2}$ |
| $e^{at}\sin bt$, $e^{at}\cos bt$ | $\dfrac{b}{(s-a)^2+b^2}$, $\dfrac{s-a}{(s-a)^2+b^2}$ |
| $t^nf(t)$ | $(-1)^nF^{(n)}(s)$ |
| $f'(t)$, $f''(t)$ | $sF-f(0)$, $s^2F-sf(0)-f'(0)$ |
| $e^{at}f(t)$ | $F(s-a)$ |
| $H(t-a)f(t-a)$ | $e^{-as}F(s)$ |
| $H(t-c)$ | $\dfrac{e^{-cs}}{s}$ |
| $(f*g)(t)$ | $F(s)G(s)$ |
| $\delta(t-a)$ | $e^{-as}$ |

## Check yourself
> [!question]- 1. Find $\mathcal L[\sin2t+t\sinh2t]$.
> $\mathcal L[\sin2t]=\dfrac{2}{s^2+4}$. $\mathcal L[t\sinh2t]=-\dfrac{d}{ds}\dfrac{2}{s^2-4}=\dfrac{4s}{(s^2-4)^2}$.
> Answer: $\dfrac{2}{s^2+4}+\dfrac{4s}{(s^2-4)^2}$ for $s>2$.

> [!question]- 2. Evaluate $\mathcal L^{-1}\!\left[\dfrac{s+7}{(s+1)(s-3)}\right]$.
> $s+7=A(s-3)+B(s+1)$. $s=-1$: $A=-\tfrac32$. $s=3$: $B=\tfrac52$.
> Answer: $-\tfrac32e^{-t}+\tfrac52e^{3t}$.

> [!question]- 3. Solve $y''+4y'+3y=e^t$, $y(0)=0$, $y'(0)=2$ with the Laplace transform.
> $(s^2+4s+3)Y=2+\dfrac{1}{s-1}$, so $Y=\dfrac{2s-1}{(s-1)(s+1)(s+3)}$.
> Cover-up: $A=\tfrac18$, $B=\tfrac34$, $C=-\tfrac78$. Answer: $y=\tfrac18e^t+\tfrac34e^{-t}-\tfrac78e^{-3t}$.

> [!question]- 4. Find $\mathcal L^{-1}\!\left[\dfrac{2s+3}{s^2+4s+13}\right]$.
> $s^2+4s+13=(s+2)^2+3^2$ and $2s+3=2(s+2)-1$.
> Answer: $2e^{-2t}\cos3t-\tfrac13e^{-2t}\sin3t$.

> [!question]- 5. Use the convolution theorem to find $\mathcal L^{-1}\!\left[\dfrac{1}{(s^2+1)^2}\right]$.
> $f=g=\sin t$: $\displaystyle\int_0^t\sin(t-\tau)\sin\tau\,d\tau=\tfrac12\int_0^t\cos(t-2\tau)\,d\tau-\tfrac12t\cos t$.
> The first integral is $\sin t$. Answer: $\tfrac12(\sin t-t\cos t)$.

> [!question]- 6. Solve $y''+y=\delta(t-\pi)$, $y(0)=y'(0)=0$.
> $Y=\dfrac{e^{-\pi s}}{s^2+1}$, so $y=H(t-\pi)\sin(t-\pi)$.
> Since $\sin(t-\pi)=-\sin t$: $y=0$ for $t<\pi$ and $y=-\sin t$ for $t\ge\pi$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L02 - Higher order linear ODEs]]. Next: [[MATH501 L04 - Series solutions of ODEs]]
- Full step-by-step notes (PDF): [MATH501_Lecture_03_Laplace_Transform.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_03/MATH501_Lecture_03_Laplace_Transform.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_03/MATH501_Lecture_03_Laplace_Transform.pdf`
- Original chapter notes (PDF): [Math501 Chapter 3.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_03/Math501%20Chapter%203.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_03/Math501 Chapter 3.pdf`

Slides not embedded: none.
