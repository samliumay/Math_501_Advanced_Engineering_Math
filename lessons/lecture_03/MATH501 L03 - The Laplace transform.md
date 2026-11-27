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

> [!warning] Slide error (slide 2)
> In the line "If $s>a$" the slide writes $-\dfrac1s e^{-(s-a)R}-\dfrac{1}{a-s}$. This is a misprint: the factor in front of the exponential must be $\dfrac{1}{a-s}$ instead of $-\dfrac1s$, as in the line above it, so the bracket should read $\dfrac{1}{a-s}e^{-(s-a)R}-\dfrac{1}{a-s}$. The limit is not changed: the exponential goes to $0$ and the result is $-\dfrac{1}{a-s}=\dfrac{1}{s-a}$.

> [!question]- Check (slide 1): Let $f(t)=5$ for $0\le t<2$ and $f(t)=0$ for $t\ge2$. Find $\mathcal L[f]$ from the definition. For which $s$ does it exist? Compare with $\mathcal L[1]$.
> Method: the definition. Split the integral at $t=2$, where $f$ changes.
> $$\mathcal L[f]=\int_0^2e^{-st}\cdot5\,dt+\int_2^\infty e^{-st}\cdot0\,dt=5\int_0^2e^{-st}\,dt .$$
> Case $s\neq0$: an antiderivative of $e^{-st}$ is $-\dfrac{e^{-st}}{s}$. So
> $$5\left[-\frac{e^{-st}}{s}\right]_0^2=5\left(-\frac{e^{-2s}}{s}+\frac1s\right)=\frac{5\,(1-e^{-2s})}{s}.$$
> Case $s=0$: $5\int_0^21\,dt=10$.
> The integral runs over the finite interval $[0,2]$ only. No limit $R\to\infty$ is needed, so the transform exists for every real $s$.
> Compare: $\mathcal L[1]=\tfrac1s$ exists only for $s>0$, because there the integral runs to infinity.
> Check: as $s\to0$, $1-e^{-2s}\approx2s$, so $\dfrac{5(1-e^{-2s})}{s}\to10$. This agrees with the case $s=0$.

> [!question]- Check (slide 2): Find $\mathcal L[e^{-3t}]$ from the definition and state the condition on $s$. Is $s=-2$ allowed? If yes, compute the integral at $s=-2$ directly and compare.
> Method: the definition, with the same three cases as on the slide ($a=-3$).
> $$\mathcal L[e^{-3t}]=\int_0^\infty e^{-st}e^{-3t}\,dt=\lim_{R\to\infty}\int_0^Re^{-(s+3)t}\,dt .$$
> Case $s=-3$: the integrand is $1$, $\int_0^R1\,dt=R\to\infty$. Divergent.
> Case $s\neq-3$:
> $$\int_0^Re^{-(s+3)t}\,dt=\left[-\frac{e^{-(s+3)t}}{s+3}\right]_0^R=-\frac{e^{-(s+3)R}}{s+3}+\frac{1}{s+3}.$$
> If $s<-3$, the exponent $-(s+3)R$ is positive and grows, so the limit does not exist. If $s>-3$, $e^{-(s+3)R}\to0$.
> Result: $\mathcal L[e^{-3t}]=\dfrac{1}{s+3}$ for $s>-3$.
> $s=-2$ is allowed because $-2>-3$. Directly: $\int_0^\infty e^{2t}e^{-3t}\,dt=\int_0^\infty e^{-t}\,dt=\left[-e^{-t}\right]_0^\infty=0+1=1$. The formula gives $\dfrac{1}{-2+3}=1$. They agree.
> So $s$ may be negative. The condition is $s>a$, not $s>0$.

> [!question]- Check (slides 2-3): Use the definition and the method of the slides (two integrations by parts, then solve for the integral) to find $\mathcal L[\cos2t]$.
> Method: integration by parts twice. The same integral comes back, so we solve an equation for it.
> Let $I=\int_0^Re^{-st}\cos2t\,dt$ and $J=\int_0^Re^{-st}\sin2t\,dt$, with $s\neq0$.
> Step 1. $u=\cos2t$, $dv=e^{-st}dt$. Then $du=-2\sin2t\,dt$, $v=-\dfrac{e^{-st}}{s}$.
> $$I=\left[-\frac{e^{-st}\cos2t}{s}\right]_0^R-\frac2s\int_0^Re^{-st}\sin2t\,dt=-\frac{e^{-sR}\cos2R}{s}+\frac1s-\frac2sJ .$$
> Step 2. $u=\sin2t$, $dv=e^{-st}dt$. Then $du=2\cos2t\,dt$, $v=-\dfrac{e^{-st}}{s}$.
> $$J=\left[-\frac{e^{-st}\sin2t}{s}\right]_0^R+\frac2s\int_0^Re^{-st}\cos2t\,dt=-\frac{e^{-sR}\sin2R}{s}+\frac2sI .$$
> Step 3. Insert $J$ into $I$:
> $$I=\frac1s-\frac{e^{-sR}\cos2R}{s}+\frac{2e^{-sR}\sin2R}{s^2}-\frac{4}{s^2}I .$$
> Step 4. Move $-\dfrac{4}{s^2}I$ to the left: $\dfrac{s^2+4}{s^2}I=\dfrac1s-\dfrac{e^{-sR}\cos2R}{s}+\dfrac{2e^{-sR}\sin2R}{s^2}$. Multiply by $\dfrac{s^2}{s^2+4}$:
> $$I=\frac{s-s\,e^{-sR}\cos2R+2e^{-sR}\sin2R}{s^2+4}.$$
> Step 5. Let $R\to\infty$ with $s>0$. Since $|\cos2R|\le1$ and $|\sin2R|\le1$, both terms with $e^{-sR}$ are squeezed to $0$. For $s<0$ they oscillate with growing size, so there is no limit. For $s=0$: $\int_0^R\cos2t\,dt=\tfrac12\sin2R$ has no limit.
> Result: $\mathcal L[\cos2t]=\dfrac{s}{s^2+4}$ for $s>0$. This is the table entry $\dfrac{s}{s^2+a^2}$ with $a=2$.

> [!question]- Check (slide 3): Exercise c) of the slide: $f(t)=0$ for $0\le t<1$ and $f(t)=t$ for $t\ge1$. Find $\mathcal L[f]$ from the definition.
> Method: the definition and one integration by parts. The integral starts at $t=1$ because $f=0$ before.
> $$\mathcal L[f]=\lim_{R\to\infty}\int_1^Rt\,e^{-st}\,dt .$$
> Parts: $u=t$, $dv=e^{-st}dt$, $du=dt$, $v=-\dfrac{e^{-st}}{s}$ ($s\neq0$).
> $$\int_1^Rt\,e^{-st}\,dt=\left[-\frac{t\,e^{-st}}{s}\right]_1^R+\frac1s\int_1^Re^{-st}\,dt=-\frac{Re^{-sR}}{s}+\frac{e^{-s}}{s}+\frac1s\left[-\frac{e^{-st}}{s}\right]_1^R .$$
> The last bracket is $-\dfrac{e^{-sR}}{s}+\dfrac{e^{-s}}{s}$. So
> $$\int_1^Rt\,e^{-st}\,dt=-\frac{Re^{-sR}}{s}+\frac{e^{-s}}{s}-\frac{e^{-sR}}{s^2}+\frac{e^{-s}}{s^2}.$$
> For $s>0$: $Re^{-sR}\to0$ and $e^{-sR}\to0$. For $s\le0$ the integrand $t\,e^{-st}\ge t$ does not go to $0$, so the integral diverges.
> Result: $\mathcal L[f]=e^{-s}\left(\dfrac1s+\dfrac{1}{s^2}\right)$ for $s>0$.
> Check with a later tool (section 7): $f(t)=H(t-1)\,[(t-1)+1]$, so $\mathcal L[f]=e^{-s}\left(\dfrac{1}{s^2}+\dfrac1s\right)$. The same.

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

> [!info] What the existence conditions mean (beyond the slides)
> - **Piecewise continuous** on $[\alpha,\beta]$: only finitely many jumps, and at every jump (and at both ends) the one-sided limits are finite. A step is allowed. A blow-up like $1/t$ at $t=0$ is not.
> - **Exponential order**: $|f(t)|\le Me^{kt}$ for $t\ge T$ says that $f$ does not grow faster than some exponential. Then $|e^{-st}f(t)|\le Me^{-(s-k)t}$, and for $s>k$ this bound has the finite integral $\dfrac{M}{s-k}$. This is why the transform exists for $s>k$.
> - Why $e^{t^2}$ fails: $\dfrac{e^{t^2}}{Me^{kt}}=\dfrac{e^{t(t-k)}}{M}\to\infty$ for every $k$ and $M$, so no bound $Me^{kt}$ works. In the integral, $e^{-st}e^{t^2}=e^{t(t-s)}\ge1$ for all $t\ge s$, so the area is infinite for every $s$.

> [!info] Where the two rules for $t$ come from (beyond the slides)
> - Multiplication by $t$: differentiate $F(s)=\int_0^\infty e^{-st}f(t)\,dt$ with respect to $s$ under the integral. Since $\dfrac{\partial}{\partial s}e^{-st}=-t\,e^{-st}$, we get $F'(s)=-\int_0^\infty e^{-st}\,t\,f(t)\,dt=-\mathcal L[t\,f(t)]$. Each further derivative gives one more factor $-t$. This is the factor $(-1)^n$.
> - Division by $t$: integrate $F$ from $s$ to $\infty$ and change the order of integration. Since $\int_s^\infty e^{-ut}\,du=\dfrac{e^{-st}}{t}$ for $t>0$, we get $\int_s^\infty F(u)\,du=\int_0^\infty f(t)\,\dfrac{e^{-st}}{t}\,dt=\mathcal L\!\left[\dfrac{f(t)}{t}\right]$.
> - Differentiating $F$ multiplies $f$ by $-t$. Integrating $F$ divides $f$ by $t$.

> [!question]- Check (slide 4, existence): (a) Show that $f(t)=t^2e^{5t}$ satisfies the conditions of the existence theorem and say for which $s$ the theorem guarantees a transform. (b) Show that $g(t)=\dfrac1t$ has no Laplace transform. Which condition fails?
> (a) $f$ is continuous, so it is piecewise continuous on every finite interval. Bound: $e^t=1+t+\dfrac{t^2}{2}+\dots\ge\dfrac{t^2}{2}$ for $t\ge0$, so $t^2\le2e^t$. Then $|f(t)|=t^2e^{5t}\le2e^{t}e^{5t}=2e^{6t}$. So $M=2$, $k=6$, and the theorem guarantees $F(s)$ for $s>6$.
> The true transform is $\dfrac{2}{(s-5)^3}$ for $s>5$ (table, $t^ne^{at}$ with $n=2$, $a=5$). The theorem gives a safe range, not always the largest one.
> (b) Look at the part of the integral near $t=0$. Take $s>0$ and $0<t\le1$. Then $e^{-st}\ge e^{-s}$, so for $0<\epsilon<1$:
> $$\int_\epsilon^1\frac{e^{-st}}{t}\,dt\ge e^{-s}\int_\epsilon^1\frac{dt}{t}=e^{-s}\,(\ln1-\ln\epsilon)=-e^{-s}\ln\epsilon\to\infty\quad(\epsilon\to0^+).$$
> For $s\le0$ we have $e^{-st}\ge1$ on $(0,1]$ and the same bound works without the factor $e^{-s}$. The integral diverges for every $s$.
> Failed condition: $\tfrac1t$ is not piecewise continuous on $[0,1]$, because the limit as $t\to0^+$ is not finite. The growth for large $t$ is not the problem here: $\tfrac1t\le1$ for $t\ge1$.

> [!question]- Check (slide 4, linearity): Use linearity and $\mathcal L[e^{at}]=\dfrac{1}{s-a}$ to derive $\mathcal L[\cosh3t]$. Explain where the condition $s>3$ comes from.
> Rule: linearity, $\mathcal L[af+bg]=aF+bG$.
> Step 1. $\cosh3t=\tfrac12e^{3t}+\tfrac12e^{-3t}$.
> Step 2. $\mathcal L[e^{3t}]=\dfrac{1}{s-3}$ for $s>3$. $\mathcal L[e^{-3t}]=\dfrac{1}{s+3}$ for $s>-3$.
> Step 3. $\mathcal L[\cosh3t]=\dfrac12\cdot\dfrac{1}{s-3}+\dfrac12\cdot\dfrac{1}{s+3}=\dfrac12\cdot\dfrac{(s+3)+(s-3)}{(s-3)(s+3)}=\dfrac12\cdot\dfrac{2s}{s^2-9}=\dfrac{s}{s^2-9}.$
> Condition: both transforms must exist at the same $s$. We need $s>3$ and $s>-3$, so $s>3$. In general $s>|a|$, as in the table.

> [!question]- Check (slide 5): Use Table 3.1 to write down (a) $\mathcal L[t^3e^{-2t}]$, (b) $\mathcal L[e^{4t}-e^{-t}]$, (c) $\mathcal L[t\cos2t]$, each with its condition on $s$. Confirm (b) with linearity.
> (a) Row $t^ne^{at}$ with $n=3$, $a=-2$: $\dfrac{3!}{(s-(-2))^{4}}=\dfrac{6}{(s+2)^4}$, $s>-2$.
> (b) Row $e^{at}-e^{bt}$ with $a=4$, $b=-1$: $\dfrac{a-b}{(s-a)(s-b)}=\dfrac{4-(-1)}{(s-4)(s+1)}=\dfrac{5}{(s-4)(s+1)}$, $s>\max\{4,-1\}=4$.
> Linearity: $\dfrac{1}{s-4}-\dfrac{1}{s+1}=\dfrac{(s+1)-(s-4)}{(s-4)(s+1)}=\dfrac{5}{(s-4)(s+1)}$. The same.
> (c) Row $t\cos(at)$ with $a=2$: $\dfrac{s^2-a^2}{(s^2+a^2)^2}=\dfrac{s^2-4}{(s^2+4)^2}$, $s>0$.

> [!question]- Check (slide 6): Find $\mathcal L[t^2\sin t]$ with the rule for multiplication by $t^n$. Show both derivatives.
> Rule: $\mathcal L[t^nf(t)]=(-1)^nF^{(n)}(s)$ with $n=2$ and $f=\sin t$, $F(s)=\dfrac{1}{s^2+1}=(s^2+1)^{-1}$.
> First derivative (chain rule): $F'(s)=-(s^2+1)^{-2}\cdot2s=\dfrac{-2s}{(s^2+1)^2}$.
> Second derivative (quotient rule with $u=-2s$, $v=(s^2+1)^2$, $u'=-2$, $v'=4s(s^2+1)$):
> $$F''(s)=\frac{-2(s^2+1)^2-(-2s)\cdot4s(s^2+1)}{(s^2+1)^4}=\frac{-2(s^2+1)+8s^2}{(s^2+1)^3}=\frac{6s^2-2}{(s^2+1)^3}.$$
> Since $(-1)^2=1$: $\mathcal L[t^2\sin t]=\dfrac{6s^2-2}{(s^2+1)^3}$ for $s>0$.
> Check with the slide example: the same two steps for $\cos t$ gave $\dfrac{2s^3-6s}{(s^2+1)^3}$. Both results have the denominator $(s^2+1)^3$, and both come from $\dfrac{2}{(s-i)^3}=\dfrac{2(s+i)^3}{(s^2+1)^3}$, the transform of $t^2e^{it}=t^2\cos t+i\,t^2\sin t$ (beyond the slides). Expand: $2(s+i)^3=2\,(s^3+3is^2-3s-i)=(2s^3-6s)+i\,(6s^2-2)$. The real part is the slide's numerator and the imaginary part is ours.

> [!question]- Check (slides 6-7): Find $\mathcal L\!\left[\dfrac{e^{-2t}-e^{-5t}}{t}\right]$ with the rule for division by $t$. First check that the rule may be used.
> Rule: $\mathcal L\!\left[\dfrac{f(t)}{t}\right]=\int_s^\infty F(u)\,du$, if $\lim_{t\to0}\dfrac{f(t)}{t}$ exists.
> Step 1, the limit. $f(t)=e^{-2t}-e^{-5t}$ and $f(0)=0$, so by L'Hopital $\lim_{t\to0}\dfrac{f(t)}{t}=\lim_{t\to0}\left(-2e^{-2t}+5e^{-5t}\right)=3$. It exists.
> Step 2. $F(s)=\dfrac{1}{s+2}-\dfrac{1}{s+5}$, for $s>-2$.
> Step 3.
> $$\int_s^R\left(\frac{1}{u+2}-\frac{1}{u+5}\right)du=\Big[\ln(u+2)-\ln(u+5)\Big]_s^R=\ln\frac{R+2}{R+5}-\ln\frac{s+2}{s+5}.$$
> Step 4. As $R\to\infty$, $\dfrac{R+2}{R+5}\to1$ and $\ln1=0$. Keep the two logarithms together. Separately each one goes to infinity.
> Result: $\mathcal L\!\left[\dfrac{e^{-2t}-e^{-5t}}{t}\right]=-\ln\dfrac{s+2}{s+5}=\ln\dfrac{s+5}{s+2}$ for $s>-2$.
> Check with the rule for multiplication by $t$: call the result $G(s)=\ln(s+5)-\ln(s+2)$. Multiplying $\dfrac{f(t)}{t}$ by $t$ gives $f(t)$ back, so $-G'(s)$ must be $F(s)$. Indeed $-G'(s)=-\dfrac{1}{s+5}+\dfrac{1}{s+2}=F(s)$. Also $G(s)\to\ln1=0$ as $s\to\infty$, as every transform must.

## 3. The inverse Laplace transform (slide 7)
![[math501_lecture_03_math501_chapter_3_p007.jpg]]

**Notes.** If $\mathcal L[f]=F$, then $f=\mathcal L^{-1}[F]$. The inverse is also linear. It is essentially unique: two continuous functions with the same transform are identical.

Method: split $F$ into simple pieces (partial fractions, or complete the square), adjust constants so that each piece matches a table entry exactly, then read the table backwards.

> [!example] Slide examples
> - $\mathcal L^{-1}\!\left[\dfrac{-2s+6}{s^2+4}\right]=-2\cos2t+3\sin2t$ (write $6=3\cdot2$).
> - $\dfrac{3}{(s-1)(s-2)}=\dfrac{-3}{s-1}+\dfrac{3}{s-2}$, so the inverse is $-3e^{t}+3e^{2t}$.

> [!question]- Check (slide 7, table matching): Evaluate $\mathcal L^{-1}\!\left[\dfrac{7}{s^4}+\dfrac{3s-8}{s^2+16}\right]$. Show how each constant is adjusted.
> Rule: linearity of the inverse. Each piece must look exactly like a table entry.
> Piece 1. Table: $\mathcal L[t^3]=\dfrac{3!}{s^4}=\dfrac{6}{s^4}$. Write $\dfrac{7}{s^4}=\dfrac76\cdot\dfrac{6}{s^4}$. Inverse: $\dfrac76t^3$.
> Piece 2. $\dfrac{3s}{s^2+16}=3\cdot\dfrac{s}{s^2+4^2}$. Inverse: $3\cos4t$.
> Piece 3. $\sin4t$ needs a $4$ on top: $\dfrac{-8}{s^2+16}=-2\cdot\dfrac{4}{s^2+4^2}$. Inverse: $-2\sin4t$.
> Answer: $\dfrac76t^3+3\cos4t-2\sin4t$.
> Check: transform back. $\dfrac76\cdot\dfrac{6}{s^4}+\dfrac{3s}{s^2+16}-\dfrac{2\cdot4}{s^2+16}=\dfrac{7}{s^4}+\dfrac{3s-8}{s^2+16}$.

> [!question]- Check (slide 7, partial fractions): Evaluate $\mathcal L^{-1}\!\left[\dfrac{s+6}{s(s+2)(s+3)}\right]$ with the slide's method (compare coefficients).
> Method: partial fractions with three different linear factors, then the table.
> Step 1. $\dfrac{s+6}{s(s+2)(s+3)}=\dfrac As+\dfrac{B}{s+2}+\dfrac{C}{s+3}$.
> Step 2. Multiply by $s(s+2)(s+3)$: $s+6=A(s+2)(s+3)+Bs(s+3)+Cs(s+2)$.
> Step 3. Expand: $A(s^2+5s+6)+B(s^2+3s)+C(s^2+2s)=(A+B+C)s^2+(5A+3B+2C)s+6A$.
> Step 4. Compare coefficients: $A+B+C=0$, $5A+3B+2C=1$, $6A=6$.
> Step 5. Solve. $A=1$. Then $B+C=-1$ and $3B+2C=1-5=-4$. From the first, $C=-1-B$. Insert: $3B-2-2B=-4$, so $B=-2$ and $C=1$.
> Step 6. $\dfrac{s+6}{s(s+2)(s+3)}=\dfrac1s-\dfrac{2}{s+2}+\dfrac{1}{s+3}$.
> Answer: $1-2e^{-2t}+e^{-3t}$.
> Check with the cover-up values: $s=0$: $\dfrac{6}{2\cdot3}=1$. $s=-2$: $\dfrac{4}{(-2)(1)}=-2$. $s=-3$: $\dfrac{3}{(-3)(-1)}=1$. The same.

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

> [!question]- Check (slide 8, derivative rule): Derive $\mathcal L[f'(t)]=sF(s)-f(0)$ from the definition. Where is the bound $\lvert f(t)\rvert\le Me^{kt}$ used?
> Method: integration by parts in the definition.
> $$\mathcal L[f']=\lim_{R\to\infty}\int_0^Re^{-st}f'(t)\,dt .$$
> Parts: $u=e^{-st}$, $dv=f'(t)\,dt$, so $du=-s\,e^{-st}dt$, $v=f(t)$.
> $$\int_0^Re^{-st}f'(t)\,dt=\Big[e^{-st}f(t)\Big]_0^R+s\int_0^Re^{-st}f(t)\,dt=e^{-sR}f(R)-f(0)+s\int_0^Re^{-st}f(t)\,dt .$$
> Limit: $|e^{-sR}f(R)|\le Me^{-(s-k)R}\to0$ for $s>k$. Here the bound is used. The last integral goes to $F(s)$.
> Result: $\mathcal L[f']=sF(s)-f(0)$ for $s>k$.
> Apply it twice for the second derivative: $\mathcal L[f'']=s\,\mathcal L[f']-f'(0)=s\,(sF-f(0))-f'(0)=s^2F-sf(0)-f'(0)$.

> [!question]- Check (slide 8, first-order IVP): Solve $y'+4y=8$, $y(0)=5$ with the Laplace transform.
> Method: transform, solve for $Y$, partial fractions, invert.
> Step 1. Transform: $sY-y(0)+4Y=\dfrac8s$, so $sY-5+4Y=\dfrac8s$.
> Step 2. Solve: $(s+4)Y=5+\dfrac8s=\dfrac{5s+8}{s}$, so $Y=\dfrac{5s+8}{s(s+4)}$.
> Step 3. Partial fractions: $\dfrac{5s+8}{s(s+4)}=\dfrac As+\dfrac{B}{s+4}$, so $5s+8=A(s+4)+Bs$. $s=0$: $8=4A$, $A=2$. $s=-4$: $-12=-4B$, $B=3$.
> Step 4. $Y=\dfrac2s+\dfrac{3}{s+4}$, so $y=2+3e^{-4t}$, valid for $t\ge0$.
> Check: $y(0)=2+3=5$. $y'=-12e^{-4t}$, and $y'+4y=-12e^{-4t}+8+12e^{-4t}=8$.

> [!question]- Check (slides 8-9): Solve $y''+3y'+2y=4t$, $y(0)=1$, $y'(0)=-1$ with the Laplace transform.
> Method: transform with both initial values, solve for $Y$, partial fractions with a repeated factor $s^2$, invert.
> Step 1. Transform: $\left(s^2Y-s\cdot1-(-1)\right)+3\,(sY-1)+2Y=\dfrac{4}{s^2}$.
> Step 2. Collect: $(s^2+3s+2)Y-s+1-3=\dfrac{4}{s^2}$, so $(s+1)(s+2)Y=s+2+\dfrac{4}{s^2}$.
> Step 3. Divide: $Y=\dfrac{s+2}{(s+1)(s+2)}+\dfrac{4}{s^2(s+1)(s+2)}=\dfrac{1}{s+1}+\dfrac{4}{s^2(s+1)(s+2)}$.
> Step 4. Partial fractions for the second term: $\dfrac{4}{s^2(s+1)(s+2)}=\dfrac As+\dfrac{B}{s^2}+\dfrac{C}{s+1}+\dfrac{D}{s+2}$, so
> $$4=As(s+1)(s+2)+B(s+1)(s+2)+Cs^2(s+2)+Ds^2(s+1).$$
> $s=0$: $4=2B$, $B=2$. $s=-1$: $4=C\cdot1\cdot1$, $C=4$. $s=-2$: $4=D\cdot4\cdot(-1)$, $D=-1$. Coefficient of $s^3$: $A+C+D=0$, so $A=-3$.
> Step 5. $Y=\dfrac{1}{s+1}-\dfrac3s+\dfrac{2}{s^2}+\dfrac{4}{s+1}-\dfrac{1}{s+2}=-\dfrac3s+\dfrac{2}{s^2}+\dfrac{5}{s+1}-\dfrac{1}{s+2}$.
> Step 6. Invert: $y=-3+2t+5e^{-t}-e^{-2t}$, for $t\ge0$.
> Check: $y(0)=-3+5-1=1$. $y'=2-5e^{-t}+2e^{-2t}$, $y'(0)=2-5+2=-1$. $y''=5e^{-t}-4e^{-2t}$.
> $y''+3y'+2y=(5-15+10)e^{-t}+(-4+6-2)e^{-2t}+6-6+4t=4t$.

> [!question]- Check (slides 9-10): Solve $y''+2y'+y=4e^{t}$, $y(0)=1$, $y'(0)=0$ with the Laplace transform. Set up the system for the partial fraction constants as on the slide.
> Method: transform, one fraction for $Y$, partial fractions with the repeated factor $(s+1)^2$, invert with $\mathcal L[te^{at}]=\dfrac{1}{(s-a)^2}$.
> Step 1. Transform: $(s^2Y-s-0)+2\,(sY-1)+Y=\dfrac{4}{s-1}$.
> Step 2. Collect: $(s+1)^2Y=s+2+\dfrac{4}{s-1}=\dfrac{(s+2)(s-1)+4}{s-1}=\dfrac{s^2+s+2}{s-1}$.
> Step 3. $Y=\dfrac{s^2+s+2}{(s-1)(s+1)^2}=\dfrac{A}{s-1}+\dfrac{B}{s+1}+\dfrac{C}{(s+1)^2}$.
> Step 4. Multiply out: $s^2+s+2=A(s+1)^2+B(s-1)(s+1)+C(s-1)=(A+B)s^2+(2A+C)s+(A-B-C)$.
> Step 5. System: $A+B=1$, $2A+C=1$, $A-B-C=2$.
> Step 6. Solve. Add all three equations: $4A=4$, so $A=1$. Then $B=0$ and $C=1-2=-1$. Test in the third: $1-0+1=2$. Correct.
> Step 7. $Y=\dfrac{1}{s-1}-\dfrac{1}{(s+1)^2}$, so $y=e^{t}-te^{-t}$, for $t\ge0$.
> Check: $y(0)=1$. $y'=e^t-e^{-t}+te^{-t}$, $y'(0)=1-1+0=0$. $y''=e^t+2e^{-t}-te^{-t}$.
> $y''+2y'+y=(1+2+1)e^t+(2-2)e^{-t}+(-1+2-1)te^{-t}=4e^t$.

> [!question]- Check (slides 10-11): Solve $y''+4y=8t$, $y(0)=3$, $y'(0)=0$ with the Laplace transform.
> Method: transform, partial fractions with the irreducible factor $s^2+4$, invert with $\cos2t$ and $\sin2t$.
> Step 1. Transform: $s^2Y-3s-0+4Y=\dfrac{8}{s^2}$.
> Step 2. Solve: $(s^2+4)Y=3s+\dfrac{8}{s^2}$, so $Y=\dfrac{3s}{s^2+4}+\dfrac{8}{s^2(s^2+4)}$.
> Step 3. Partial fractions: $\dfrac{8}{s^2(s^2+4)}=\dfrac As+\dfrac{B}{s^2}+\dfrac{Cs+D}{s^2+4}$, so
> $$8=As(s^2+4)+B(s^2+4)+(Cs+D)s^2=(A+C)s^3+(B+D)s^2+4As+4B .$$
> Compare: $4B=8$ gives $B=2$. $4A=0$ gives $A=0$. $A+C=0$ gives $C=0$. $B+D=0$ gives $D=-2$.
> Step 4. $Y=\dfrac{3s}{s^2+4}+\dfrac{2}{s^2}-\dfrac{2}{s^2+4}$. The last term is already $1\cdot\dfrac{2}{s^2+2^2}$.
> Step 5. Invert: $y=3\cos2t+2t-\sin2t$, for $t\ge0$.
> Check: $y(0)=3$. $y'=-6\sin2t+2-2\cos2t$, $y'(0)=2-2=0$. $y''=-12\cos2t+4\sin2t$.
> $y''+4y=-12\cos2t+4\sin2t+12\cos2t+8t-4\sin2t=8t$.

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

> [!question]- Check (slide 11, transform): Find $\mathcal L\!\left[e^{-2t}\,(t^3+\cos5t)\right]$ with the first shifting theorem. State the condition on $s$.
> Rule: $\mathcal L[e^{at}f(t)]=F(s-a)$. Here $a=-2$, so replace $s$ by $s-(-2)=s+2$.
> Step 1. Without the exponential: $F(s)=\mathcal L[t^3+\cos5t]=\dfrac{3!}{s^4}+\dfrac{s}{s^2+25}=\dfrac{6}{s^4}+\dfrac{s}{s^2+25}$, for $s>0$.
> Step 2. Shift every $s$, also the one in the numerator: $F(s+2)=\dfrac{6}{(s+2)^4}+\dfrac{s+2}{(s+2)^2+25}$.
> Condition: $s+2>0$, so $s>-2$.
> Check with the table: rows $t^ne^{at}$ and $e^{at}\cos bt$ with $a=-2$, $n=3$, $b=5$ give the same two terms.

> [!question]- Check (slide 11, inverse): Use the corollary $\mathcal L^{-1}[F(s-a)]=e^{at}f(t)$ to find $\mathcal L^{-1}\!\left[\dfrac{2s+1}{(s-3)^3}\right]$.
> Method: write the numerator in powers of $s-3$, then shift.
> Step 1. $2s+1=2(s-3)+6+1=2(s-3)+7$.
> Step 2. $\dfrac{2s+1}{(s-3)^3}=\dfrac{2(s-3)}{(s-3)^3}+\dfrac{7}{(s-3)^3}=\dfrac{2}{(s-3)^2}+\dfrac{7}{(s-3)^3}$.
> Step 3. This is $F(s-3)$ with $F(s)=\dfrac{2}{s^2}+\dfrac{7}{s^3}$.
> Step 4. Invert $F$: $\mathcal L^{-1}\!\left[\dfrac{2}{s^2}\right]=2t$. For the second, $\mathcal L[t^2]=\dfrac{2}{s^3}$, so $\dfrac{7}{s^3}=\dfrac72\cdot\dfrac{2}{s^3}$ gives $\dfrac72t^2$. So $f(t)=2t+\dfrac72t^2$.
> Step 5. Shift with $a=3$: answer $e^{3t}\left(2t+\dfrac72t^2\right)$.
> Check: $\mathcal L[te^{3t}]=\dfrac{1}{(s-3)^2}$ and $\mathcal L[t^2e^{3t}]=\dfrac{2}{(s-3)^3}$, so the transform is $\dfrac{2}{(s-3)^2}+\dfrac{7}{(s-3)^3}=\dfrac{2(s-3)+7}{(s-3)^3}=\dfrac{2s+1}{(s-3)^3}$.

> [!question]- Check (slide 12): Find $\mathcal L^{-1}\!\left[\dfrac{s-1}{s^2-4s-5}\right]$ in two ways: (a) complete the square as on the slide, (b) partial fractions. Show that the two answers are the same function.
> (a) Method: complete the square, then first shifting.
> $s^2-4s-5=(s-2)^2-4-5=(s-2)^2-3^2$. A minus sign, so $\cosh$ and $\sinh$.
> Numerator: $s-1=(s-2)+1$.
> $$\frac{s-1}{s^2-4s-5}=\frac{s-2}{(s-2)^2-3^2}+\frac13\cdot\frac{3}{(s-2)^2-3^2}.$$
> Unshifted: $\mathcal L^{-1}\!\left[\dfrac{s}{s^2-9}\right]=\cosh3t$, $\mathcal L^{-1}\!\left[\dfrac{3}{s^2-9}\right]=\sinh3t$. Shift with $a=2$:
> $$f(t)=e^{2t}\cosh3t+\tfrac13e^{2t}\sinh3t .$$
> (b) Method: the denominator has real roots. $s^2-4s-5=(s-5)(s+1)$.
> $\dfrac{s-1}{(s-5)(s+1)}=\dfrac{A}{s-5}+\dfrac{B}{s+1}$, so $s-1=A(s+1)+B(s-5)$. $s=5$: $4=6A$, $A=\tfrac23$. $s=-1$: $-2=-6B$, $B=\tfrac13$.
> $$f(t)=\tfrac23e^{5t}+\tfrac13e^{-t}.$$
> Same function: use $\cosh3t=\tfrac12(e^{3t}+e^{-3t})$ and $\sinh3t=\tfrac12(e^{3t}-e^{-3t})$ in (a):
> $e^{2t}\left[\left(\tfrac12+\tfrac16\right)e^{3t}+\left(\tfrac12-\tfrac16\right)e^{-3t}\right]=\tfrac23e^{5t}+\tfrac13e^{-t}$.
> A minus sign after completing the square means real roots. Then partial fractions also work. With a plus sign only the $\cos$ and $\sin$ form is real.

## 6. Heaviside function and pulses (slides 12-13)
![[math501_lecture_03_math501_chapter_3_p013.jpg]]

**Notes.** The **Heaviside (unit step) function** is $H(t)=0$ for $t<0$ and $1$ for $t\ge0$. The shifted step $u_c(t)=H(t-c)$ switches on at $t=c$. A **pulse** on $[a,b)$ is $H(t-a)-H(t-b)$. The definitions start at the bottom of slide 12.

$$\mathcal L[H(t-c)]=\frac{e^{-cs}}{s},\qquad s>0,\ c>0.$$

To write a piecewise function with steps: for each piece $[a,b)$ with value $g$, write $g\,[H(t-a)-H(t-b)]$. Add the pieces and collect.

> [!example] Slide example
> $f=3$ on $[0,1)$, $8$ on $[1,2)$, $-2$ for $t\ge2$: $f=3H(t)+5H(t-1)-10H(t-2)$, so $\mathcal L[f]=\dfrac3s+\dfrac{5e^{-s}}{s}-\dfrac{10e^{-2s}}{s}$.

> [!question]- Check (slides 12-13): Let $f(t)=2H(t-1)-5H(t-3)+3H(t-6)$. Find $f(0.5)$, $f(2)$, $f(4)$, $f(7)$ and write $f$ piece by piece.
> Rule: $H(t-c)=0$ for $t<c$ and $1$ for $t\ge c$. At each $t$, count only the steps that are already switched on.
> $t=0.5$: no step is on. $f=0$.
> $t=2$: only $H(t-1)=1$. $f=2$.
> $t=4$: $H(t-1)=H(t-3)=1$. $f=2-5=-3$.
> $t=7$: all three are on. $f=2-5+3=0$.
> Piecewise: $f=0$ on $[0,1)$, $2$ on $[1,3)$, $-3$ on $[3,6)$, $0$ for $t\ge6$.
> As pulses: $f=2\,[H(t-1)-H(t-3)]-3\,[H(t-3)-H(t-6)]$. Expanding gives $2H(t-1)-5H(t-3)+3H(t-6)$ again.
> Each coefficient is the size of the jump at that time: $+2$ at $t=1$, $-5$ at $t=3$, $+3$ at $t=6$.

> [!question]- Check (slide 13, pulse): Find the transform of the pulse $p(t)=H(t-2)-H(t-5)$ in two ways: with the theorem of the slide and directly from the definition.
> Way 1, the theorem $\mathcal L[H(t-c)]=\dfrac{e^{-cs}}{s}$ and linearity:
> $$\mathcal L[p]=\frac{e^{-2s}}{s}-\frac{e^{-5s}}{s}=\frac{e^{-2s}-e^{-5s}}{s},\qquad s>0 .$$
> Way 2, the definition. $p=1$ on $[2,5)$ and $0$ elsewhere:
> $$\mathcal L[p]=\int_2^5e^{-st}\,dt=\left[-\frac{e^{-st}}{s}\right]_2^5=-\frac{e^{-5s}}{s}+\frac{e^{-2s}}{s}=\frac{e^{-2s}-e^{-5s}}{s}\qquad(s\neq0).$$
> The same. The condition $s>0$ is needed for each single step, because a step never switches off. The pulse alone lives on a finite interval. Its integral exists for every $s$ (value $3$ at $s=0$).

> [!question]- Check (slide 13, piecewise function): Write $f(t)=2$ on $[0,3)$, $-1$ on $[3,5)$, $4$ for $t\ge5$ with Heaviside functions and find $\mathcal L[f]$.
> Method: one pulse per piece, then collect, then $\mathcal L[H(t-c)]=\dfrac{e^{-cs}}{s}$.
> Step 1. $f=2\,[H(t)-H(t-3)]+(-1)\,[H(t-3)-H(t-5)]+4H(t-5)$.
> Step 2. Collect: $H(t-3)$ has $-2-1=-3$. $H(t-5)$ has $+1+4=5$. So $f=2H(t)-3H(t-3)+5H(t-5)$.
> Step 3. Jump test: at $t=3$ the value goes from $2$ to $-1$, jump $-3$. At $t=5$ from $-1$ to $4$, jump $+5$. Correct.
> Step 4. $\mathcal L[f]=\dfrac2s-\dfrac{3e^{-3s}}{s}+\dfrac{5e^{-5s}}{s}$ for $s>0$.
> Check from the definition: $2\int_0^3e^{-st}dt-\int_3^5e^{-st}dt+4\int_5^\infty e^{-st}dt=\dfrac{2(1-e^{-3s})}{s}-\dfrac{e^{-3s}-e^{-5s}}{s}+\dfrac{4e^{-5s}}{s}=\dfrac{2-3e^{-3s}+5e^{-5s}}{s}$.

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

> [!info] Why a delay gives the factor $e^{-as}$ (beyond the slides)
> The slide states the theorem without proof. For $a\ge0$:
> $$\mathcal L[H(t-a)f(t-a)]=\int_a^\infty e^{-st}f(t-a)\,dt .$$
> Substitute $\tau=t-a$, so $t=\tau+a$, $dt=d\tau$, and the limits become $0$ and $\infty$:
> $$\int_0^\infty e^{-s(\tau+a)}f(\tau)\,d\tau=e^{-as}\int_0^\infty e^{-s\tau}f(\tau)\,d\tau=e^{-as}F(s).$$
> To use the theorem forwards, the function next to $H(t-a)$ must be written in the variable $t-a$. If it is given as $g(t)$, write $g(t)=g((t-a)+a)$ and expand.

> [!question]- Check (slide 14, transform): Find $\mathcal L[H(t-1)\,t^2]$ with the second shifting theorem.
> Rule: $\mathcal L[H(t-a)f(t-a)]=e^{-as}F(s)$ with $a=1$. First write $t^2$ in powers of $t-1$.
> Step 1. $t=(t-1)+1$, so $t^2=(t-1)^2+2(t-1)+1$.
> Step 2. So $f(t-1)=(t-1)^2+2(t-1)+1$, which means $f(t)=t^2+2t+1$.
> Step 3. $F(s)=\dfrac{2}{s^3}+\dfrac{2}{s^2}+\dfrac1s$.
> Step 4. $\mathcal L[H(t-1)\,t^2]=e^{-s}\left(\dfrac{2}{s^3}+\dfrac{2}{s^2}+\dfrac1s\right)$ for $s>0$.
> Common mistake: $e^{-s}\cdot\dfrac{2}{s^3}$. That is the transform of $H(t-1)(t-1)^2$, a different function.
> Check from the definition: $\int_1^\infty t^2e^{-st}\,dt$ with $\tau=t-1$ is $e^{-s}\int_0^\infty(\tau+1)^2e^{-s\tau}\,d\tau$, the same expression.

> [!question]- Check (slide 14, inverse): Find $\mathcal L^{-1}\!\left[\dfrac{6e^{-2s}}{s^2+3s+2}\right]$ and write the answer piecewise.
> Method: invert without the exponential (partial fractions), then delay by $a=2$.
> Step 1. $s^2+3s+2=(s+1)(s+2)$. $\dfrac{6}{(s+1)(s+2)}=\dfrac{A}{s+1}+\dfrac{B}{s+2}$, so $6=A(s+2)+B(s+1)$. $s=-1$: $A=6$. $s=-2$: $6=-B$, $B=-6$.
> Step 2. $f(t)=\mathcal L^{-1}\!\left[\dfrac{6}{s+1}-\dfrac{6}{s+2}\right]=6e^{-t}-6e^{-2t}$.
> Step 3. Second shifting: replace $t$ by $t-2$ everywhere and multiply by $H(t-2)$:
> $$\mathcal L^{-1}\!\left[\frac{6e^{-2s}}{s^2+3s+2}\right]=H(t-2)\left(6e^{-(t-2)}-6e^{-2(t-2)}\right).$$
> Piecewise: $0$ for $t<2$, and $6e^{-(t-2)}-6e^{-2(t-2)}$ for $t\ge2$.
> Check: at $t=2$ the value is $6-6=0$, so the function is continuous there.

> [!question]- Check (slides 14-15): Solve $y''+9y=f(t)$, $y(0)=0$, $y'(0)=3$, where $f(t)=18$ for $2\le t<5$ and $f(t)=0$ otherwise.
> Method: write $f$ with steps, transform, partial fractions for the part without exponentials, second shifting for each exponential.
> Step 1. $f(t)=18\,[H(t-2)-H(t-5)]$, so $\mathcal L[f]=\dfrac{18e^{-2s}}{s}-\dfrac{18e^{-5s}}{s}$.
> Step 2. Transform the equation: $s^2Y-s\cdot0-3+9Y=\dfrac{18\,(e^{-2s}-e^{-5s})}{s}$.
> Step 3. Solve: $Y=\dfrac{3}{s^2+9}+\left(e^{-2s}-e^{-5s}\right)\dfrac{18}{s(s^2+9)}$.
> Step 4. Partial fractions: $\dfrac{18}{s(s^2+9)}=\dfrac As+\dfrac{Bs+C}{s^2+9}$, so $18=A(s^2+9)+(Bs+C)s=(A+B)s^2+Cs+9A$. Then $9A=18$, $A=2$. $C=0$. $A+B=0$, $B=-2$.
> Step 5. $g(t)=\mathcal L^{-1}\!\left[\dfrac2s-\dfrac{2s}{s^2+9}\right]=2-2\cos3t$. Also $\mathcal L^{-1}\!\left[\dfrac{3}{s^2+9}\right]=\sin3t$.
> Step 6. Second shifting with $a=2$ and $a=5$:
> $$y=\sin3t+H(t-2)\,\big(2-2\cos(3t-6)\big)-H(t-5)\,\big(2-2\cos(3t-15)\big).$$
> Piecewise: $y=\sin3t$ on $[0,2)$. $y=\sin3t+2-2\cos(3t-6)$ on $[2,5)$. $y=\sin3t-2\cos(3t-6)+2\cos(3t-15)$ for $t\ge5$.
> Check. Initial values: $y(0)=0$, $y'(0)=3\cos0=3$.
> On $[0,2)$: $y''+9y=-9\sin3t+9\sin3t=0$.
> On $[2,5)$: the new part $w=2-2\cos(3t-6)$ has $w''=18\cos(3t-6)$, so $w''+9w=18$. Correct.
> For $t\ge5$: the second new part gives $-18$, total $18-18=0$. Correct.
> At $t=2$: $w=2-2=0$ and $w'=6\sin0=0$. So $y$ and $y'$ are continuous. Only $y''$ jumps. The same holds at $t=5$.

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

> [!info] Transform of an integral (beyond the slides)
> Take $g=1$ in the convolution: $(f*1)(t)=\int_0^tf(\tau)\,d\tau$. Since $\mathcal L[1]=\tfrac1s$, the convolution theorem gives
> $$\mathcal L\!\left[\int_0^tf(\tau)\,d\tau\right]=\frac{F(s)}{s},\qquad\mathcal L^{-1}\!\left[\frac{F(s)}{s}\right]=\int_0^tf(\tau)\,d\tau .$$
> Differentiation in $t$ multiplies by $s$. Integration in $t$ divides by $s$.
> Example: $\mathcal L^{-1}\!\left[\dfrac{1}{s(s^2+4)}\right]=\displaystyle\int_0^t\tfrac12\sin2\tau\,d\tau=\left[-\tfrac14\cos2\tau\right]_0^t=\tfrac14-\tfrac14\cos2t$. No partial fractions are needed.

> [!question]- Check (slide 16, definition): Compute $t*e^{-t}$ directly from the definition. Then confirm it with the convolution theorem.
> Direct. Take $f(t)=t$, $g(t)=e^{-t}$: $(f*g)(t)=\int_0^t(t-\tau)\,e^{-\tau}\,d\tau$.
> Parts in $\tau$: $u=t-\tau$, $dv=e^{-\tau}d\tau$, so $du=-d\tau$, $v=-e^{-\tau}$.
> $$\int_0^t(t-\tau)e^{-\tau}d\tau=\Big[-(t-\tau)e^{-\tau}\Big]_0^t-\int_0^te^{-\tau}\,d\tau=(0+t)-\Big[-e^{-\tau}\Big]_0^t=t-(1-e^{-t}).$$
> Result: $t*e^{-t}=t-1+e^{-t}$.
> With the theorem: $\mathcal L[t]\cdot\mathcal L[e^{-t}]=\dfrac{1}{s^2}\cdot\dfrac{1}{s+1}=\dfrac{1}{s^2(s+1)}$.
> Partial fractions: $\dfrac{1}{s^2(s+1)}=\dfrac As+\dfrac{B}{s^2}+\dfrac{C}{s+1}$, so $1=As(s+1)+B(s+1)+Cs^2$. $s=0$: $B=1$. $s=-1$: $C=1$. Coefficient of $s^2$: $A+C=0$, $A=-1$.
> Inverse: $-1+t+e^{-t}$. The same.
> Note: $t*e^{-t}$ is not the product $te^{-t}$.

> [!question]- Check (slide 16, example): The slide finds $u_2(t)*\sin t$ through the transform. Compute it directly from the convolution integral and compare.
> By commutativity, $(u_2*\sin)(t)=\int_0^t\sin(t-\tau)\,H(\tau-2)\,d\tau$.
> Case $t<2$: on $0\le\tau\le t$ we have $\tau<2$, so $H(\tau-2)=0$ and the integral is $0$.
> Case $t\ge2$: $H(\tau-2)=1$ only for $\tau\ge2$, so the integral starts at $2$:
> $$\int_2^t\sin(t-\tau)\,d\tau=\Big[\cos(t-\tau)\Big]_2^t=\cos0-\cos(t-2)=1-\cos(t-2).$$
> The antiderivative is correct because $\dfrac{d}{d\tau}\cos(t-\tau)=\sin(t-\tau)$.
> Result: $H(t-2)\,(1-\cos(t-2))$, the same as on the slide.

> [!question]- Check (slide 17): Use the convolution theorem to find $\mathcal L^{-1}\!\left[\dfrac{s}{(s+1)(s^2+1)}\right]$. Check the result with partial fractions.
> Method: split into a product $F\,G$, invert each factor, compute the convolution integral (two integrations by parts, then solve).
> Step 1. $F(s)=\dfrac{1}{s+1}$, $f(t)=e^{-t}$. $G(s)=\dfrac{s}{s^2+1}$, $g(t)=\cos t$.
> Step 2. $(f*g)(t)=\int_0^te^{-(t-\tau)}\cos\tau\,d\tau=e^{-t}\int_0^te^{\tau}\cos\tau\,d\tau$. Call the last integral $K$.
> Step 3. Parts: $u=\cos\tau$, $dv=e^\tau d\tau$, $du=-\sin\tau\,d\tau$, $v=e^\tau$.
> $$K=\Big[e^\tau\cos\tau\Big]_0^t+\int_0^te^\tau\sin\tau\,d\tau=e^t\cos t-1+\int_0^te^\tau\sin\tau\,d\tau .$$
> Step 4. Parts again: $u=\sin\tau$, $dv=e^\tau d\tau$, $du=\cos\tau\,d\tau$, $v=e^\tau$.
> $$\int_0^te^\tau\sin\tau\,d\tau=\Big[e^\tau\sin\tau\Big]_0^t-\int_0^te^\tau\cos\tau\,d\tau=e^t\sin t-K .$$
> Step 5. $K=e^t\cos t-1+e^t\sin t-K$, so $2K=e^t(\cos t+\sin t)-1$ and $K=\tfrac12\left(e^t(\cos t+\sin t)-1\right)$.
> Step 6. Multiply by $e^{-t}$: answer $\tfrac12\left(\cos t+\sin t-e^{-t}\right)$.
> Check with partial fractions: $\dfrac{s}{(s+1)(s^2+1)}=\dfrac{A}{s+1}+\dfrac{Bs+C}{s^2+1}$, so $s=A(s^2+1)+(Bs+C)(s+1)=(A+B)s^2+(B+C)s+(A+C)$.
> $A+B=0$, $B+C=1$, $A+C=0$. So $B=C=-A$ and $-2A=1$: $A=-\tfrac12$, $B=C=\tfrac12$.
> Inverse: $-\tfrac12e^{-t}+\tfrac12\cos t+\tfrac12\sin t$. The same.

> [!question]- Check (slide 18, convolution IVP): Solve $y''+4y=f(t)$, $y(0)=y'(0)=0$ in terms of $f$, as on the slide. Then test the formula with $f(t)=4$.
> Method: transform, write $Y$ as a product, convolution theorem.
> Step 1. Transform with zero initial values: $s^2Y+4Y=F(s)$, so $Y=F(s)\cdot\dfrac{1}{s^2+4}$.
> Step 2. $\mathcal L^{-1}\!\left[\dfrac{1}{s^2+4}\right]=\dfrac12\sin2t$, because $\dfrac{1}{s^2+4}=\dfrac12\cdot\dfrac{2}{s^2+2^2}$.
> Step 3. Convolution theorem: $y(t)=\left(f*\tfrac12\sin2t\right)(t)=\dfrac12\displaystyle\int_0^tf(\tau)\,\sin\big(2(t-\tau)\big)\,d\tau$.
> Test with $f=4$:
> $$y=2\int_0^t\sin\big(2(t-\tau)\big)\,d\tau=2\left[\tfrac12\cos\big(2(t-\tau)\big)\right]_0^t=\cos0-\cos2t=1-\cos2t .$$
> Check: $y(0)=0$. $y'=2\sin2t$, $y'(0)=0$. $y''=4\cos2t$, and $y''+4y=4\cos2t+4-4\cos2t=4$.
> The formula works for every input $f$. Only the integral changes.

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

> [!info] Where $\mathcal L[\delta(t-a)]=e^{-as}$ comes from (beyond the slides)
> The slide gives the formula without a derivation. Shift the pulse to $t=a\ge0$: $\delta_\epsilon(t-a)=\tfrac1\epsilon\,\big(H(t-a)-H(t-a-\epsilon)\big)$. With $\mathcal L[H(t-c)]=\dfrac{e^{-cs}}{s}$:
> $$\mathcal L[\delta_\epsilon(t-a)]=\frac1\epsilon\cdot\frac{e^{-as}-e^{-(a+\epsilon)s}}{s}=e^{-as}\cdot\frac{1-e^{-\epsilon s}}{\epsilon s}.$$
> As $\epsilon\to0^+$, the last fraction has the form $\tfrac00$. L'Hopital in $\epsilon$: $\dfrac{s\,e^{-\epsilon s}}{s}\to1$. So the limit is $e^{-as}$.
> In an ODE, $\delta(t-a)$ on the right side is a sudden kick at $t=a$. In a first order equation $y'+\dots=c\,\delta(t-a)$ the solution $y$ jumps by $c$ at $t=a$. In a second order equation $y''+\dots=c\,\delta(t-a)$ the solution stays continuous and $y'$ jumps by $c$.

> [!question]- Check (slide 18, delta): For the pulse $\delta_\epsilon(t)=\tfrac1\epsilon(H(t)-H(t-\epsilon))$, find the area and the transform. Evaluate the transform at $s=2$ for $\epsilon=0.1$ and $\epsilon=0.01$. What do the numbers show?
> Area: height $\tfrac1\epsilon$ times width $\epsilon$ is $1$, for every $\epsilon$.
> Transform, from the definition: $\mathcal L[\delta_\epsilon]=\dfrac1\epsilon\displaystyle\int_0^\epsilon e^{-st}\,dt=\dfrac1\epsilon\left[-\dfrac{e^{-st}}{s}\right]_0^\epsilon=\dfrac{1-e^{-\epsilon s}}{\epsilon s}$.
> $s=2$, $\epsilon=0.1$: $\dfrac{1-e^{-0.2}}{0.2}=\dfrac{1-0.81873}{0.2}=0.9063$.
> $s=2$, $\epsilon=0.01$: $\dfrac{1-e^{-0.02}}{0.02}=\dfrac{1-0.980199}{0.02}=0.9901$.
> The values go to $1$ as the pulse gets narrower. This is $\mathcal L[\delta(t)]=1$.
> Reason: $e^{-\epsilon s}\approx1-\epsilon s$ for small $\epsilon s$, so the fraction is about $\dfrac{\epsilon s}{\epsilon s}=1$.

> [!question]- Check (slide 19, filtering): Evaluate (a) $\int_0^\infty t^2e^{-t}\,\delta(t-3)\,dt$, (b) $\int_0^\infty e^{-2t}\cos t\;\delta(t-\pi)\,dt$. (c) Use the filtering property to get $\mathcal L[\delta(t-a)]$ for $a>0$.
> Rule: $\int_0^\infty f(t)\,\delta(t-a)\,dt=f(a)$ for $a>0$ and $f$ continuous at $a$. The delta picks the value of $f$ at the kick time.
> (a) $f(t)=t^2e^{-t}$, $a=3$: $f(3)=9e^{-3}\approx0.448$.
> (b) $f(t)=e^{-2t}\cos t$, $a=\pi$: $f(\pi)=e^{-2\pi}\cos\pi=-e^{-2\pi}\approx-0.00187$.
> (c) $\mathcal L[\delta(t-a)]=\int_0^\infty e^{-st}\,\delta(t-a)\,dt$. Here $f(t)=e^{-st}$, so the value is $f(a)=e^{-as}$. This agrees with the boxed formula on slide 18.

> [!question]- Check (slide 19, impulse IVP): Solve $y'+2y=5\,\delta(t-2)$, $y(0)=3$. What happens to $y$ at $t=2$?
> Method: transform with $\mathcal L[\delta(t-a)]=e^{-as}$, solve for $Y$, second shifting.
> Step 1. Transform: $sY-3+2Y=5e^{-2s}$.
> Step 2. Solve: $Y=\dfrac{3}{s+2}+\dfrac{5e^{-2s}}{s+2}$.
> Step 3. $\mathcal L^{-1}\!\left[\dfrac{1}{s+2}\right]=e^{-2t}$. Second shifting with $a=2$: $\mathcal L^{-1}\!\left[\dfrac{e^{-2s}}{s+2}\right]=H(t-2)\,e^{-2(t-2)}$.
> Step 4. $y=3e^{-2t}+5H(t-2)\,e^{-2(t-2)}$.
> Piecewise: $y=3e^{-2t}$ for $t<2$, and $y=3e^{-2t}+5e^{-2(t-2)}$ for $t\ge2$.
> At $t=2$: just before, $y=3e^{-4}$. Just after, $y=3e^{-4}+5$. The solution jumps by $5$, the size of the impulse.
> Check: $y(0)=3$. For $t<2$ and for $t>2$ every term has the form $ce^{-2t}$, and $(ce^{-2t})'+2ce^{-2t}=0$. So the equation holds away from $t=2$, where the right side is $0$.

> [!question]- Check (slides 19-20): Solve $y''+6y'+9y=2\,\delta(t-1)$, $y(0)=0$, $y'(0)=1$. Use both shifting theorems.
> Method: transform, solve for $Y$, first shifting for $(s+3)^2$, second shifting for $e^{-s}$.
> Step 1. Transform: $(s^2Y-s\cdot0-1)+6\,(sY-0)+9Y=2e^{-s}$.
> Step 2. Collect: $(s^2+6s+9)Y=1+2e^{-s}$, and $s^2+6s+9=(s+3)^2$. So $Y=\dfrac{1}{(s+3)^2}+\dfrac{2e^{-s}}{(s+3)^2}$.
> Step 3. First shifting: $\mathcal L^{-1}\!\left[\dfrac{1}{s^2}\right]=t$, so $\mathcal L^{-1}\!\left[\dfrac{1}{(s+3)^2}\right]=te^{-3t}$.
> Step 4. Second shifting with $a=1$: $\mathcal L^{-1}\!\left[\dfrac{e^{-s}}{(s+3)^2}\right]=H(t-1)\,(t-1)\,e^{-3(t-1)}$.
> Step 5. $y=te^{-3t}+2H(t-1)\,(t-1)\,e^{-3(t-1)}$.
> Piecewise: $y=te^{-3t}$ for $t<1$, and $y=te^{-3t}+2(t-1)e^{-3(t-1)}$ for $t\ge1$.
> Check. $y(0)=0$. $y'=e^{-3t}-3te^{-3t}$ for $t<1$, so $y'(0)=1$.
> Both $te^{-3t}$ and $(t-1)e^{-3(t-1)}$ solve $y''+6y'+9y=0$ (double root $-3$). So the equation holds for $t\ne1$.
> At $t=1$: the new part $w=2(t-1)e^{-3(t-1)}$ has $w(1)=0$, so $y$ is continuous. $w'=2e^{-3(t-1)}-6(t-1)e^{-3(t-1)}$, so $w'(1)=2$. The slope $y'$ jumps by $2$, the size of the impulse.

## 10. Systems of ODEs (slides 21-22)
![[math501_lecture_03_math501_chapter_3_p021.jpg]]
![[math501_lecture_03_math501_chapter_3_p022.jpg]]

**Notes.** Transform each equation with $X=\mathcal L[x]$, $Y=\mathcal L[y]$. The result is two linear algebraic equations in $X$ and $Y$. Solve them, then invert each with partial fractions.

> [!example] Slide example
> $x''-2x'+3y'+2y=4$, $2y'-x'+3y=0$, $x(0)=x'(0)=y(0)=0$.
> Transformed: $(s^2-2s)X+(3s+2)Y=\tfrac4s$ and $-sX+(2s+3)Y=0$. So $X=\tfrac{2s+3}{s}Y$ and
> $$Y=\frac{2}{s(s+2)(s-1)},\qquad X=\frac{4s+6}{s^2(s+2)(s-1)} .$$
> Answer: $x=-\tfrac72-3t+\tfrac16e^{-2t}+\tfrac{10}{3}e^{t}$, $y=-1+\tfrac13e^{-2t}+\tfrac23e^{t}$.

> [!question]- Check (slides 21-22): Solve the system $x'=x+2y$, $y'=2x+y$, $x(0)=2$, $y(0)=0$ with the Laplace transform.
> Method: transform both equations, solve the two algebraic equations for $X$ and $Y$ by substitution, partial fractions, invert.
> Step 1. Transform: $sX-2=X+2Y$ and $sY-0=2X+Y$.
> Step 2. Order: $(s-1)X-2Y=2$ and $-2X+(s-1)Y=0$.
> Step 3. From the second equation: $X=\dfrac{s-1}{2}\,Y$.
> Step 4. Insert into the first: $\dfrac{(s-1)^2}{2}Y-2Y=2$. Multiply by $2$: $\big((s-1)^2-4\big)Y=4$.
> Step 5. $(s-1)^2-4=s^2-2s-3=(s-3)(s+1)$. So $Y=\dfrac{4}{(s-3)(s+1)}$ and $X=\dfrac{s-1}{2}\cdot\dfrac{4}{(s-3)(s+1)}=\dfrac{2(s-1)}{(s-3)(s+1)}$.
> Step 6. Partial fractions for $Y$: $4=A(s+1)+B(s-3)$. $s=3$: $4=4A$, $A=1$. $s=-1$: $4=-4B$, $B=-1$. So $Y=\dfrac{1}{s-3}-\dfrac{1}{s+1}$.
> Step 7. Partial fractions for $X$: $2(s-1)=C(s+1)+D(s-3)$. $s=3$: $4=4C$, $C=1$. $s=-1$: $-4=-4D$, $D=1$. So $X=\dfrac{1}{s-3}+\dfrac{1}{s+1}$.
> Step 8. Invert: $x=e^{3t}+e^{-t}$, $y=e^{3t}-e^{-t}$, for $t\ge0$.
> Check. $x(0)=2$, $y(0)=0$.
> $x'=3e^{3t}-e^{-t}$ and $x+2y=(1+2)e^{3t}+(1-2)e^{-t}=3e^{3t}-e^{-t}$. Equal.
> $y'=3e^{3t}+e^{-t}$ and $2x+y=(2+1)e^{3t}+(2-1)e^{-t}=3e^{3t}+e^{-t}$. Equal.

> [!question]- Check (slide 22): Verify the slide's answer $x=-\tfrac72-3t+\tfrac16e^{-2t}+\tfrac{10}{3}e^{t}$, $y=-1+\tfrac13e^{-2t}+\tfrac23e^{t}$ in the three initial conditions and in the second equation $2y'-x'+3y=0$.
> Initial conditions: $x(0)=-\tfrac72+\tfrac16+\tfrac{10}{3}=\tfrac{-21+1+20}{6}=0$. $y(0)=-1+\tfrac13+\tfrac23=0$.
> Derivatives: $x'=-3-\tfrac13e^{-2t}+\tfrac{10}{3}e^{t}$, so $x'(0)=-3-\tfrac13+\tfrac{10}{3}=0$. $y'=-\tfrac23e^{-2t}+\tfrac23e^{t}$.
> Second equation, term by term:
> Constants: $2\cdot0-(-3)+3\cdot(-1)=3-3=0$.
> $e^{-2t}$: $2\cdot\left(-\tfrac23\right)-\left(-\tfrac13\right)+3\cdot\tfrac13=-\tfrac43+\tfrac13+1=0$.
> $e^{t}$: $2\cdot\tfrac23-\tfrac{10}{3}+3\cdot\tfrac23=\tfrac43-\tfrac{10}{3}+2=0$.
> All three groups vanish, so $2y'-x'+3y=0$ for all $t$.
> The term $-3t$ in $x$ does not appear in this equation, because only $x'$ enters and $(-3t)'=-3$ is a constant.

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
- Quiz: [[MATH501 L03 - The Laplace transform - quiz]]

Slides not embedded: none.
