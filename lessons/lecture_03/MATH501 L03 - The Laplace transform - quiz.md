---
course: MATH 501 Advanced Engineering Mathematics
lesson: MATH501 L03 - The Laplace transform
type: quiz
questions: 35
---

# MATH501 L03 - The Laplace transform - quiz

Lesson note: [[MATH501 L03 - The Laplace transform]]. One question per check question of the lesson. Pick an option, then open the answer.

## 1. Definition and transforms from the definition (slides 1-3)

### Q1 (slide 1)

Let $f(t)=5$ for $0\le t<2$ and $f(t)=0$ for $t\ge2$. Use the definition $F(s)=\int_0^\infty e^{-st}f(t)\,dt$. Which statement is correct?

- A) $F(s)=\dfrac{5(1-e^{-2s})}{s}$, and it exists only for $s>0$.
- B) $F(s)=\dfrac{5(e^{-2s}-1)}{s}$, and it exists for every real $s$.
- C) $F(s)=\dfrac{5(e^{-2s}-1)}{s}$, and it exists only for $s>0$.
- D) $F(s)=\dfrac{5(1-e^{-2s})}{s}$, and it exists for every real $s$.

> [!success]- Answer
> **D.** $f=0$ after $t=2$, so $F(s)=5\int_0^2e^{-st}\,dt=5\left[-\dfrac{e^{-st}}{s}\right]_0^2=\dfrac{5(1-e^{-2s})}{s}$ for $s\neq0$.
> At $s=0$ the integral is $5\cdot2=10$, the limit of the formula.
> The integral runs over $[0,2]$ only. No limit $R\to\infty$ is needed, so it exists for every real $s$.
> - A: Right formula, but the condition $s>0$ belongs to $\mathcal L[1]$, whose integral runs to infinity.
> - B: Sign slip in the antiderivative: $+\dfrac{e^{-st}}{s}$ instead of $-\dfrac{e^{-st}}{s}$. The condition is right.
> - C: Two slips: the sign slip of B and the condition $s>0$ of A.

### Q2 (slide 2)

Compute $\mathcal L[e^{-3t}]=\lim_{R\to\infty}\int_0^Re^{-st}e^{-3t}\,dt$ from the definition. For which $s$ does the integral converge?

- A) For $s>-3$. So $s=-2$ is allowed, and the integral there equals $1$.
- B) For $s>0$, as for every transform. So $s=-2$ is not allowed.
- C) For $s>3$. So $s=-2$ is not allowed.
- D) For $s\ge-3$. So $s=-2$ is allowed, and the integral there equals $1$.

> [!success]- Answer
> **A.** The integrand is $e^{-(s+3)t}$. For $s\neq-3$: $\int_0^Re^{-(s+3)t}dt=\dfrac{1-e^{-(s+3)R}}{s+3}$.
> $e^{-(s+3)R}\to0$ only if $s+3>0$. So $\mathcal L[e^{-3t}]=\dfrac{1}{s+3}$ for $s>-3$.
> At $s=-2$: $\int_0^\infty e^{2t}e^{-3t}dt=\int_0^\infty e^{-t}dt=1=\dfrac{1}{-2+3}$.
> - B: The condition is $s>a$, not $s>0$. Here $a=-3$, so negative $s$ can be allowed.
> - C: Sign slip: the exponent taken as $-(s-3)t$, as for $e^{3t}$.
> - D: The end point $s=-3$ is included. There the integrand is $e^{0}=1$ and $\int_0^\infty1\,dt$ diverges.

### Q3 (slides 2-3)

Use the definition and two integrations by parts (the same integral comes back, then solve for it) to find $\mathcal L[\cos2t]$. Which result is correct?

- A) $\dfrac{2}{s^2+4}$ for $s>0$
- B) $\dfrac{s}{s^2+4}$ for $s>0$
- C) $\dfrac{s}{s^2-4}$ for $s>2$
- D) $\dfrac{s}{s^2+2}$ for $s>0$

> [!success]- Answer
> **B.** With $I=\int_0^\infty e^{-st}\cos2t\,dt$, two integrations by parts give $I=\dfrac1s-\dfrac{4}{s^2}I$ for $s>0$.
> So $\dfrac{s^2+4}{s^2}I=\dfrac1s$ and $I=\dfrac{s}{s^2+4}$.
> - A: This is $\mathcal L[\sin2t]$. For the cosine the numerator is $s$.
> - C: Sign slip when moving $-\dfrac{4}{s^2}I$ to the left: $\dfrac{s^2-4}{s^2}I=\dfrac1s$.
> - D: The factor $2$ from $\dfrac{d}{dt}\sin2t=2\cos2t$ is lost in the second integration by parts. Then $I=\dfrac1s-\dfrac{2}{s^2}I$.

### Q4 (slide 3)

Let $f(t)=0$ for $0\le t<1$ and $f(t)=t$ for $t\ge1$. Find $\mathcal L[f]$ from the definition, for $s>0$.

- A) $e^{-s}\left(\dfrac1s+\dfrac{1}{s^2}\right)$
- B) $\dfrac{e^{-s}}{s^2}$
- C) $e^{-s}\left(\dfrac1s-\dfrac{1}{s^2}\right)$
- D) $\dfrac{1}{s^2}$

> [!success]- Answer
> **A.** $\mathcal L[f]=\int_1^\infty t\,e^{-st}dt$. Parts with $u=t$, $v=-\dfrac{e^{-st}}{s}$:
> $\left[-\dfrac{te^{-st}}{s}\right]_1^\infty+\dfrac1s\int_1^\infty e^{-st}dt=\dfrac{e^{-s}}{s}+\dfrac{e^{-s}}{s^2}$.
> - B: This is $\mathcal L[H(t-1)(t-1)]$. The function $t$ was treated as $t-1$; the lost part is $H(t-1)\cdot1$.
> - C: Sign slip in the parts formula: $-\dfrac1s\int e^{-st}dt$ instead of $+\dfrac1s\int e^{-st}dt$.
> - D: The integral was started at $0$, as if $f(t)=t$ for all $t\ge0$.

## 2. Existence, linearity, table, multiplying and dividing by t (slides 4-6)

### Q5 (slide 4, existence)

The existence theorem: if $f$ is piecewise continuous on every finite interval of $t\ge0$ and $\lvert f(t)\rvert\le Me^{kt}$ for large $t$, then $F(s)$ exists for $s>k$. Which statement is correct?

- A) $t^2e^{5t}\le2e^{6t}$ for $t\ge0$, so the theorem guarantees $F(s)$ for $s>6$.
- B) $t^2e^{5t}$ has no bound $Me^{kt}$, because the factor $t^2$ grows without limit.
- C) $\tfrac1t$ fails the growth condition: it has no bound $Me^{kt}$ for large $t$.
- D) $\tfrac1t$ has a transform for $s>0$, because $\tfrac1t\to0$ as $t\to\infty$.

> [!success]- Answer
> **A.** $e^t\ge\dfrac{t^2}{2}$ for $t\ge0$, so $t^2\le2e^t$ and $t^2e^{5t}\le2e^{6t}$. So $M=2$, $k=6$.
> (The true range is $s>5$; the theorem gives a safe range only.)
> - B: $t^2$ grows, but slower than any $e^{\epsilon t}$. A bound with $k=6$ exists.
> - C: For $t\ge1$, $\tfrac1t\le1$, so the growth is fine. The failure is at $t=0$: the limit is not finite, so $\tfrac1t$ is not piecewise continuous.
> - D: Near $t=0$, $\int_\epsilon^1\dfrac{e^{-st}}{t}dt\ge-e^{-s}\ln\epsilon\to\infty$. The integral diverges for every $s$.

### Q6 (slide 4, linearity)

Use $\cosh3t=\tfrac12e^{3t}+\tfrac12e^{-3t}$, linearity and $\mathcal L[e^{at}]=\dfrac{1}{s-a}$. Which result, with its condition, is correct?

- A) $\mathcal L[\cosh3t]=\dfrac{3}{s^2-9}$ for $s>3$
- B) $\mathcal L[\cosh3t]=\dfrac{s}{s^2-9}$ for $s>-3$
- C) $\mathcal L[\cosh3t]=\dfrac{3}{s^2-9}$ for $s>-3$
- D) $\mathcal L[\cosh3t]=\dfrac{s}{s^2-9}$ for $s>3$

> [!success]- Answer
> **D.** $\dfrac12\cdot\dfrac{1}{s-3}+\dfrac12\cdot\dfrac{1}{s+3}=\dfrac12\cdot\dfrac{2s}{s^2-9}=\dfrac{s}{s^2-9}$.
> Both transforms must exist at the same $s$: $s>3$ and $s>-3$, so $s>3$.
> - A: Minus instead of plus between the two parts. That gives $\mathcal L[\sinh3t]$.
> - B: Only the condition of $e^{-3t}$ was kept. $\mathcal L[e^{3t}]$ does not exist for $-3<s\le3$.
> - C: Two slips: the minus sign of A and the condition of B.

### Q7 (slide 5)

Table rows: $t^ne^{at}\to\dfrac{n!}{(s-a)^{n+1}}$, $e^{at}-e^{bt}\to\dfrac{a-b}{(s-a)(s-b)}$, $t\cos at\to\dfrac{s^2-a^2}{(s^2+a^2)^2}$, $t\sin at\to\dfrac{2as}{(s^2+a^2)^2}$. Which statement is correct?

- A) $\mathcal L[t^3e^{-2t}]=\dfrac{6}{(s+2)^4}$ for $s>-2$
- B) $\mathcal L[e^{4t}-e^{-t}]=\dfrac{3}{(s-4)(s+1)}$ for $s>4$
- C) $\mathcal L[t\cos2t]=\dfrac{4s}{(s^2+4)^2}$ for $s>0$
- D) $\mathcal L[t^3e^{-2t}]=\dfrac{6}{(s-2)^4}$ for $s>2$

> [!success]- Answer
> **A.** $n=3$, $a=-2$: $\dfrac{3!}{(s-(-2))^4}=\dfrac{6}{(s+2)^4}$, for $s>-2$.
> - B: $a-b$ computed as $4-1$. With $b=-1$ it is $4-(-1)=5$.
> - C: This is the row for $t\sin2t$. The correct value is $\dfrac{s^2-4}{(s^2+4)^2}$.
> - D: Sign slip in $s-a$: with $a=-2$ the denominator is $(s+2)^4$, not $(s-2)^4$.

### Q8 (slide 6)

Use $\mathcal L[t^nf(t)]=(-1)^nF^{(n)}(s)$ with $f=\sin t$, $F(s)=\dfrac{1}{s^2+1}$. What is $\mathcal L[t^2\sin t]$?

- A) $\dfrac{2s^3-6s}{(s^2+1)^3}$
- B) $\dfrac{2-6s^2}{(s^2+1)^3}$
- C) $\dfrac{6s^2-2}{(s^2+1)^3}$
- D) $-\dfrac{10s^2+2}{(s^2+1)^3}$

> [!success]- Answer
> **C.** $F'(s)=\dfrac{-2s}{(s^2+1)^2}$.
> Quotient rule: $F''(s)=\dfrac{-2(s^2+1)^2-(-2s)\cdot4s(s^2+1)}{(s^2+1)^4}=\dfrac{6s^2-2}{(s^2+1)^3}$.
> $(-1)^2=1$, so this is the answer.
> - A: This is $\mathcal L[t^2\cos t]$, the slide example with $F=\dfrac{s}{s^2+1}$.
> - B: The sign $(-1)^n$ was taken as $-1$. For $n=2$ it is $+1$.
> - D: Quotient rule with plus: $\dfrac{u'v+uv'}{v^2}$ instead of $\dfrac{u'v-uv'}{v^2}$.

### Q9 (slides 6-7)

Use $\mathcal L\!\left[\dfrac{f(t)}{t}\right]=\int_s^\infty F(u)\,du$ (valid if $\lim_{t\to0}f(t)/t$ exists) for $f(t)=e^{-2t}-e^{-5t}$. What is $\mathcal L\!\left[\dfrac{e^{-2t}-e^{-5t}}{t}\right]$?

- A) $\ln\dfrac{s+2}{s+5}$
- B) No transform: $f(t)/t$ blows up at $t=0$.
- C) $\ln\dfrac{s+5}{s+2}$
- D) $\dfrac{1}{(s+2)^2}-\dfrac{1}{(s+5)^2}$

> [!success]- Answer
> **C.** $\lim_{t\to0}\dfrac{f(t)}{t}=\lim(-2e^{-2t}+5e^{-5t})=3$ exists, so the rule applies.
> $\int_s^R\left(\dfrac{1}{u+2}-\dfrac{1}{u+5}\right)du=\ln\dfrac{R+2}{R+5}-\ln\dfrac{s+2}{s+5}\to0-\ln\dfrac{s+2}{s+5}=\ln\dfrac{s+5}{s+2}$.
> - A: The minus sign of the lower limit was lost: the value at $u=s$ is subtracted.
> - B: $f(0)=0$, so the quotient has the finite limit $3$. It does not blow up.
> - D: This is $-F'(s)$, the rule for multiplication by $t$, not for division by $t$.

## 3. The inverse Laplace transform (slide 7)

### Q10 (slide 7, table matching)

Use $\mathcal L[t^n]=\dfrac{n!}{s^{n+1}}$, $\mathcal L[\sin at]=\dfrac{a}{s^2+a^2}$ and the table row for $\cos at$. What is $\mathcal L^{-1}\!\left[\dfrac{7}{s^4}+\dfrac{3s-8}{s^2+16}\right]$?

- A) $\tfrac76t^3+3\cos4t-2\sin4t$
- B) $\tfrac76t^3+3\cos4t-8\sin4t$
- C) $\tfrac{7}{24}t^3+3\cos4t-2\sin4t$
- D) $\tfrac{7}{24}t^3+3\cos4t-8\sin4t$

> [!success]- Answer
> **A.** $\dfrac{7}{s^4}=\dfrac76\cdot\dfrac{3!}{s^4}$ gives $\tfrac76t^3$.
> $\dfrac{3s}{s^2+16}$ gives $3\cos4t$. $\dfrac{-8}{s^2+16}=-2\cdot\dfrac{4}{s^2+4^2}$ gives $-2\sin4t$.
> - B: The $4$ needed on top for $\sin4t$ was not made: $-8\sin4t$ has the transform $\dfrac{-32}{s^2+16}$.
> - C: $4!$ used for $\dfrac{1}{s^4}$. The power $s^{n+1}=s^4$ means $n=3$ and $3!=6$.
> - D: Two slips: the $4!$ of C and the missing $4$ of B.

### Q11 (slide 7, partial fractions)

Write $\dfrac{s+6}{s(s+2)(s+3)}=\dfrac As+\dfrac{B}{s+2}+\dfrac{C}{s+3}$ and compare coefficients in $s+6=A(s+2)(s+3)+Bs(s+3)+Cs(s+2)$. What is $\mathcal L^{-1}\!\left[\dfrac{s+6}{s(s+2)(s+3)}\right]$?

- A) $1+8e^{-2t}-9e^{-3t}$
- B) $1-4e^{-2t}+4e^{-3t}$
- C) $1+e^{-2t}-2e^{-3t}$
- D) $1-2e^{-2t}+e^{-3t}$

> [!success]- Answer
> **D.** Coefficients: $A+B+C=0$, $5A+3B+2C=1$, $6A=6$. So $A=1$, $B+C=-1$, $3B+2C=-4$.
> Then $B=-2$, $C=1$. Inverse: $1-2e^{-2t}+e^{-3t}$.
> Cover-up check: $s=-2$ gives $\dfrac{4}{(-2)(1)}=-2$; $s=-3$ gives $\dfrac{3}{(-3)(-1)}=1$.
> - A: Sign slip: $3B+2C=1-5$ written as $1+5=6$. Then $B=8$, $C=-9$.
> - B: The $s^2$ coefficient set to $1$ instead of $0$: $A+B+C=1$. Then $B=-4$, $C=4$.
> - C: The $s$ coefficients of $B$ and $C$ swapped: $2B+3C=-4$ instead of $3B+2C=-4$. Then $B=1$, $C=-2$.

## 4. Solving initial value problems (slides 8-11)

### Q12 (slide 8, derivative rule)

Integration by parts gives $\int_0^Re^{-st}f'(t)\,dt=e^{-sR}f(R)-f(0)+s\int_0^Re^{-st}f(t)\,dt$. Then $R\to\infty$ gives $\mathcal L[f']=sF(s)-f(0)$. Where is the bound $\lvert f(t)\rvert\le Me^{kt}$ used?

- A) To remove the term $-f(0)$, which is small when $f$ is bounded.
- B) To show $e^{-sR}f(R)\to0$ as $R\to\infty$, for $s>k$.
- C) To show $e^{-sR}f(R)\to0$ as $R\to\infty$, for every real $s$.
- D) To show that $f'$ also satisfies a bound $\lvert f'(t)\rvert\le Me^{kt}$.

> [!success]- Answer
> **B.** $\lvert e^{-sR}f(R)\rvert\le Me^{-(s-k)R}$, and this goes to $0$ when $s>k$.
> The term $-f(0)$ stays in the result.
> - A: $-f(0)$ is not removed. It is part of $sF(s)-f(0)$.
> - C: For $s<k$ the bound $Me^{-(s-k)R}$ grows, so it proves nothing.
> - D: No bound on $f'$ is needed. The proof only uses the bound on $f$.

### Q13 (slide 8, first-order IVP)

Solve $y'+4y=8$, $y(0)=5$ with the Laplace transform, using $\mathcal L[y']=sY-y(0)$.

- A) $y=2-2e^{-4t}$
- B) $y=2-7e^{-4t}$
- C) $y=13e^{-4t}$
- D) $y=2+3e^{-4t}$

> [!success]- Answer
> **D.** $sY-5+4Y=\dfrac8s$, so $Y=\dfrac{5s+8}{s(s+4)}=\dfrac2s+\dfrac{3}{s+4}$.
> So $y=2+3e^{-4t}$. Check: $y(0)=5$ and $y'+4y=-12e^{-4t}+8+12e^{-4t}=8$.
> - A: The initial value was forgotten: $Y=\dfrac{8}{s(s+4)}$. Then $y(0)=0$.
> - B: Sign slip: $sY+5$ instead of $sY-5$. Then $y(0)=-5$.
> - C: $\mathcal L[8]$ taken as $8$ instead of $\dfrac8s$. Then $Y=\dfrac{13}{s+4}$, and $y'+4y=0$.

### Q14 (slides 8-9)

Solve $y''+3y'+2y=4t$, $y(0)=1$, $y'(0)=-1$ with the Laplace transform. Use $\mathcal L[y'']=s^2Y-sy(0)-y'(0)$.

- A) $y=-3+2t+4e^{-t}-e^{-2t}$
- B) $y=-3+2t+2e^{-t}+2e^{-2t}$
- C) $y=-3+2t+5e^{-t}-e^{-2t}$
- D) $y=-3+2t+7e^{-t}-3e^{-2t}$

> [!success]- Answer
> **C.** $(s^2Y-s+1)+3(sY-1)+2Y=\dfrac{4}{s^2}$, so $(s+1)(s+2)Y=s+2+\dfrac{4}{s^2}$.
> $Y=\dfrac{1}{s+1}+\dfrac{4}{s^2(s+1)(s+2)}=-\dfrac3s+\dfrac{2}{s^2}+\dfrac{5}{s+1}-\dfrac{1}{s+2}$.
> Check: $y(0)=-3+5-1=1$, $y'(0)=2-5+2=-1$.
> - A: Both initial values forgotten: $Y=\dfrac{4}{s^2(s+1)(s+2)}$. Then $y(0)=0$.
> - B: The term $-3y(0)$ from $3(sY-y(0))$ was dropped. Then $y(0)=1$ but $y'(0)=-4$.
> - D: Sign slip: $-y'(0)$ taken as $-1$ instead of $+1$. Then $y'(0)=1$.

### Q15 (slides 9-10)

Solve $y''+2y'+y=4e^{t}$, $y(0)=1$, $y'(0)=0$ with the Laplace transform. Use $\mathcal L[te^{at}]=\dfrac{1}{(s-a)^2}$.

- A) $y=e^{t}-e^{-t}-2te^{-t}$
- B) $y=e^{t}-3te^{-t}$
- C) $y=e^{t}-te^{t}$
- D) $y=e^{t}-te^{-t}$

> [!success]- Answer
> **D.** $(s^2Y-s)+2(sY-1)+Y=\dfrac{4}{s-1}$, so $(s+1)^2Y=s+2+\dfrac{4}{s-1}=\dfrac{s^2+s+2}{s-1}$.
> Partial fractions: $Y=\dfrac{1}{s-1}+\dfrac{0}{s+1}-\dfrac{1}{(s+1)^2}$, so $y=e^t-te^{-t}$.
> Check: $y(0)=1$, $y'(0)=1-1=0$.
> - A: Both initial values forgotten: $Y=\dfrac{4}{(s-1)(s+1)^2}$. Then $y(0)=0$.
> - B: The term $-2y(0)$ from $2(sY-y(0))$ was dropped. Then $y'(0)=-2$.
> - C: $\dfrac{1}{(s+1)^2}$ inverted as $te^{t}$: the $s$-shift with the wrong sign. It is $te^{-t}$.

### Q16 (slides 10-11)

Solve $y''+4y=8t$, $y(0)=3$, $y'(0)=0$ with the Laplace transform. Use $\mathcal L[y'']=s^2Y-sy(0)-y'(0)$.

- A) $y=2t-\sin2t$
- B) $y=3\cos2t+2t-\sin2t$
- C) $y=3\cos2t+2t-2\sin2t$
- D) $y=2t+\tfrac12\sin2t$

> [!success]- Answer
> **B.** $(s^2+4)Y=3s+\dfrac{8}{s^2}$, so $Y=\dfrac{3s}{s^2+4}+\dfrac{2}{s^2}-\dfrac{2}{s^2+4}$.
> $\dfrac{2}{s^2+4}=\dfrac{2}{s^2+2^2}$ is exactly $\mathcal L[\sin2t]$. So $y=3\cos2t+2t-\sin2t$.
> Check: $y(0)=3$, $y'(0)=0+2-2=0$.
> - A: The initial values were forgotten. Then $y(0)=0$.
> - C: $\dfrac{2}{s^2+4}$ inverted as $2\sin2t$. The $2$ on top is already the $a$ of $\sin2t$.
> - D: $-sy(0)$ written as $-y(0)$: $\dfrac{3}{s^2+4}$ gives $\tfrac32\sin2t$. Then $y(0)=0$.

## 5. First shifting theorem (slides 11-12)

### Q17 (slide 11, transform)

Use the first shifting theorem $\mathcal L[e^{at}f(t)]=F(s-a)$. What is $\mathcal L\!\left[e^{-2t}(t^3+\cos5t)\right]$, with its condition on $s$?

- A) $\dfrac{6}{(s-2)^4}+\dfrac{s-2}{(s-2)^2+25}$ for $s>2$
- B) $\dfrac{6}{(s+2)^4}+\dfrac{s}{(s+2)^2+25}$ for $s>-2$
- C) $\dfrac{6}{(s+2)^4}+\dfrac{s+2}{(s+2)^2+25}$ for $s>-2$
- D) $\dfrac{6}{(s-2)^4}+\dfrac{s}{(s-2)^2+25}$ for $s>2$

> [!success]- Answer
> **C.** $F(s)=\dfrac{6}{s^4}+\dfrac{s}{s^2+25}$ for $s>0$. With $a=-2$, replace every $s$ by $s+2$.
> The condition $s>0$ becomes $s+2>0$, so $s>-2$.
> - A: The shift applied as $F(s+a)$: $s$ replaced by $s-2$. That is the transform of $e^{2t}(t^3+\cos5t)$.
> - B: The $s$ in the numerator of the cosine term was not shifted.
> - D: Two slips: the wrong shift direction of A and the unshifted numerator of B.

### Q18 (slide 11, inverse)

Use $\mathcal L^{-1}[F(s-a)]=e^{at}f(t)$, after writing the numerator in powers of $s-3$. What is $\mathcal L^{-1}\!\left[\dfrac{2s+1}{(s-3)^3}\right]$?

- A) $e^{3t}\left(2t+\tfrac72t^2\right)$
- B) $e^{3t}\left(2t+\tfrac12t^2\right)$
- C) $e^{3t}\left(2t+7t^2\right)$
- D) $e^{-3t}\left(2t+\tfrac72t^2\right)$

> [!success]- Answer
> **A.** $2s+1=2(s-3)+7$, so the fraction is $\dfrac{2}{(s-3)^2}+\dfrac{7}{(s-3)^3}=F(s-3)$ with $F=\dfrac{2}{s^2}+\dfrac{7}{s^3}$.
> $\dfrac{7}{s^3}=\dfrac72\cdot\dfrac{2}{s^3}$, so $f=2t+\tfrac72t^2$. Shift with $a=3$.
> - B: $2s+1$ written as $2(s-3)+1$. The $+6$ from $2\cdot3$ is lost.
> - C: $\dfrac{1}{s^3}$ inverted as $t^2$. It is $\tfrac12t^2$, because $\mathcal L[t^2]=\dfrac{2}{s^3}$.
> - D: Wrong sign of the shift: $F(s-3)$ belongs to $e^{3t}$, not $e^{-3t}$.

### Q19 (slide 12)

Find $\mathcal L^{-1}\!\left[\dfrac{s-1}{s^2-4s-5}\right]$. Note $s^2-4s-5=(s-2)^2-3^2=(s-5)(s+1)$.

- A) $e^{2t}\left(\cos3t+\tfrac13\sin3t\right)$
- B) $\tfrac23e^{5t}-\tfrac13e^{-t}$
- C) $\tfrac23e^{5t}+\tfrac13e^{-t}$
- D) $e^{2t}\left(\cosh3t+\sinh3t\right)$

> [!success]- Answer
> **C.** $s-1=A(s+1)+B(s-5)$. $s=5$: $4=6A$, $A=\tfrac23$. $s=-1$: $-2=-6B$, $B=\tfrac13$.
> The same function from completing the square: $e^{2t}\cosh3t+\tfrac13e^{2t}\sinh3t=\tfrac23e^{5t}+\tfrac13e^{-t}$.
> - A: After completing the square the sign is minus, so the result has $\cosh$ and $\sinh$, not $\cos$ and $\sin$.
> - B: Sign slip in $-2=-6B$: $B=-\tfrac13$ instead of $\tfrac13$.
> - D: $\dfrac{1}{(s-2)^2-9}$ inverted as $e^{2t}\sinh3t$. A $3$ on top is needed, so the factor is $\tfrac13$.

## 6. Heaviside function and pulses (slides 12-13)

### Q20 (slides 12-13)

$H(t-c)=0$ for $t<c$ and $1$ for $t\ge c$. Let $f(t)=2H(t-1)-5H(t-3)+3H(t-6)$. What are $\big(f(0.5),\,f(2),\,f(4),\,f(7)\big)$?

- A) $(0,\ 2,\ -5,\ 3)$
- B) $(0,\ 2,\ -3,\ 0)$
- C) $(0,\ -2,\ 3,\ 0)$
- D) $(0,\ 2,\ 7,\ 10)$

> [!success]- Answer
> **B.** Add the steps that are already on. $t=0.5$: none, $0$. $t=2$: $2$. $t=4$: $2-5=-3$. $t=7$: $2-5+3=0$.
> Each coefficient is a jump, not a value.
> - A: Each coefficient read as the value of $f$ after its step. The earlier steps were not added.
> - C: $H(t-c)$ read as $1$ for $t<c$: then $f(2)=-5+3$ and $f(4)=3$.
> - D: The sign of $-5$ was dropped: $f(4)=2+5$ and $f(7)=2+5+3$.

### Q21 (slide 13, pulse)

Use $\mathcal L[H(t-c)]=\dfrac{e^{-cs}}{s}$ ($c>0$) and linearity. What is the transform of the pulse $p(t)=H(t-2)-H(t-5)$?

- A) $\dfrac{e^{-2s}-e^{-5s}}{s}$
- B) $e^{-2s}-e^{-5s}$
- C) $\dfrac{e^{2s}-e^{5s}}{s}$
- D) $e^{2s}-e^{5s}$

> [!success]- Answer
> **A.** $\dfrac{e^{-2s}}{s}-\dfrac{e^{-5s}}{s}$. Check: $\int_2^5e^{-st}dt=\left[-\dfrac{e^{-st}}{s}\right]_2^5=\dfrac{e^{-2s}-e^{-5s}}{s}$.
> - B: The factor $\dfrac1s$ is lost. $e^{-cs}$ is the transform of $\delta(t-c)$, not of $H(t-c)$.
> - C: The delay written as $e^{cs}$ instead of $e^{-cs}$.
> - D: Two slips: the lost factor $\dfrac1s$ of B and the delay $e^{cs}$ of C.

### Q22 (slide 13, piecewise function)

Let $f(t)=2$ on $[0,3)$, $-1$ on $[3,5)$, $4$ for $t\ge5$. Write $f$ with Heaviside functions and find $\mathcal L[f]$ for $s>0$.

- A) $\dfrac{2-e^{-3s}+4e^{-5s}}{s}$
- B) $\dfrac{2-3e^{-3s}+5e^{-5s}}{s}$
- C) $\dfrac{2+3e^{-3s}-5e^{-5s}}{s}$
- D) $\dfrac{2-3e^{-3s}+3e^{-5s}}{s}$

> [!success]- Answer
> **B.** $f=2[H(t)-H(t-3)]-[H(t-3)-H(t-5)]+4H(t-5)=2-3H(t-3)+5H(t-5)$.
> The coefficients are the jumps: $-1-2=-3$ at $t=3$ and $4-(-1)=5$ at $t=5$.
> - A: The values $-1$ and $4$ used as coefficients instead of the jumps.
> - C: Each jump taken as value before minus value after: $2-(-1)=3$ at $t=3$ and $-1-4=-5$ at $t=5$.
> - D: The term $-(-1)H(t-5)$ of the second pulse taken as $-H(t-5)$. Then $H(t-5)$ gets $-1+4=3$.

## 7. Second shifting theorem (slides 14-15)

### Q23 (slide 14, transform)

Use $\mathcal L[H(t-a)f(t-a)]=e^{-as}F(s)$. What is $\mathcal L[H(t-1)\,t^2]$ for $s>0$?

- A) $\dfrac{2e^{-s}}{s^3}$
- B) $e^{-s}\left(\dfrac{2}{s^3}-\dfrac{2}{s^2}+\dfrac1s\right)$
- C) $e^{-s}\left(\dfrac{2}{s^3}+\dfrac{2}{s^2}\right)$
- D) $e^{-s}\left(\dfrac{2}{s^3}+\dfrac{2}{s^2}+\dfrac1s\right)$

> [!success]- Answer
> **D.** $t^2=\big((t-1)+1\big)^2=(t-1)^2+2(t-1)+1$. So $f(\tau)=\tau^2+2\tau+1$.
> $F(s)=\dfrac{2}{s^3}+\dfrac{2}{s^2}+\dfrac1s$, times $e^{-s}$.
> - A: $t^2$ treated as $(t-1)^2$. That is $\mathcal L[H(t-1)(t-1)^2]$, a different function.
> - B: $t$ written as $(t-1)-1$ instead of $(t-1)+1$.
> - C: The constant $1$ of $(t-1)^2+2(t-1)+1$ was dropped, so the term $\dfrac1s$ is missing.

### Q24 (slide 14, inverse)

Find $\mathcal L^{-1}\!\left[\dfrac{6e^{-2s}}{s^2+3s+2}\right]$, with $s^2+3s+2=(s+1)(s+2)$.

- A) $H(t-2)\left(6e^{-t}-6e^{-2t}\right)$
- B) $H(t-2)\left(6e^{-(t-2)}-6e^{-2(t-2)}\right)$
- C) $H(t-2)\left(6e^{-(t-2)}+6e^{-2(t-2)}\right)$
- D) $6e^{-(t+2)}-6e^{-2(t+2)}$ for $t\ge0$

> [!success]- Answer
> **B.** $\dfrac{6}{(s+1)(s+2)}=\dfrac{6}{s+1}-\dfrac{6}{s+2}$, so $f(t)=6e^{-t}-6e^{-2t}$.
> The factor $e^{-2s}$ means: replace $t$ by $t-2$ and multiply by $H(t-2)$.
> - A: Written as $H(t-2)f(t)$ instead of $H(t-2)f(t-2)$.
> - C: Sign slip in the partial fractions: $6=-B$ solved as $B=6$.
> - D: The delay read as $e^{as}$: $t$ replaced by $t+2$ and no step. That has no factor $e^{-2s}$.

### Q25 (slides 14-15)

Solve $y''+9y=f(t)$, $y(0)=0$, $y'(0)=3$, with $f(t)=18$ for $2\le t<5$ and $0$ otherwise. Use $\dfrac{18}{s(s^2+9)}=\dfrac2s-\dfrac{2s}{s^2+9}$. What is $y(t)$ on $2\le t<5$?

- A) $\sin3t+2-2\cos(3t-6)$
- B) $2-2\cos(3t-6)$
- C) $\sin3t+2-2\cos3t$
- D) $2-2\cos3t$

> [!success]- Answer
> **A.** $f=18[H(t-2)-H(t-5)]$. Transform: $(s^2+9)Y-3=\dfrac{18(e^{-2s}-e^{-5s})}{s}$.
> $Y=\dfrac{3}{s^2+9}+(e^{-2s}-e^{-5s})\left(\dfrac2s-\dfrac{2s}{s^2+9}\right)$.
> So $y=\sin3t+H(t-2)\big(2-2\cos(3t-6)\big)-H(t-5)\big(2-2\cos(3t-15)\big)$. On $[2,5)$ only the first step is on.
> - B: The initial value $y'(0)=3$ was forgotten, so the term $\sin3t$ is missing.
> - C: The shifted part written as $H(t-2)g(t)$ instead of $H(t-2)g(t-2)$. Then $y$ jumps at $t=2$.
> - D: Two slips: the missing $\sin3t$ of B and the unshifted cosine of C.

## 8. Convolution (slides 16-18)

### Q26 (slide 16, definition)

The convolution is $(f*g)(t)=\int_0^tf(t-\tau)\,g(\tau)\,d\tau$. Compute $t*e^{-t}$.

- A) $te^{-t}$
- B) $t+1-e^{-t}$
- C) $t-1-e^{-t}$
- D) $t-1+e^{-t}$

> [!success]- Answer
> **D.** $\int_0^t(t-\tau)e^{-\tau}d\tau=\Big[-(t-\tau)e^{-\tau}\Big]_0^t-\int_0^te^{-\tau}d\tau=t-(1-e^{-t})$.
> Check: $\dfrac{1}{s^2}\cdot\dfrac{1}{s+1}=-\dfrac1s+\dfrac{1}{s^2}+\dfrac{1}{s+1}$, inverse $-1+t+e^{-t}$.
> - A: Convolution taken as the product of the functions. $\mathcal L[te^{-t}]=\dfrac{1}{(s+1)^2}$, not $\dfrac{1}{s^2(s+1)}$.
> - B: Sign slip in the parts formula: $+\int_0^te^{-\tau}d\tau$ instead of $-\int_0^te^{-\tau}d\tau$.
> - C: Partial-fraction sign slip: $C=-1$ for $\dfrac{C}{s+1}$. Then the value at $t=0$ is $-2$, but a convolution is $0$ at $t=0$.

### Q27 (slide 16, example)

$u_2(t)=H(t-2)$. Compute $(u_2*\sin)(t)=\int_0^t\sin(t-\tau)\,H(\tau-2)\,d\tau$ directly, for $t\ge2$.

- A) $1-\cos t$
- B) $\cos(t-2)-1$
- C) $1-\cos(t-2)$
- D) $\cos2-\cos t$

> [!success]- Answer
> **C.** $H(\tau-2)=1$ only for $\tau\ge2$, so the integral is $\int_2^t\sin(t-\tau)\,d\tau$.
> $\dfrac{d}{d\tau}\cos(t-\tau)=\sin(t-\tau)$, so it equals $\Big[\cos(t-\tau)\Big]_2^t=1-\cos(t-2)$.
> - A: The step was ignored and the integral started at $0$: $\int_0^t\sin(t-\tau)d\tau$.
> - B: Antiderivative with the wrong sign: $-\cos(t-\tau)$.
> - D: $\sin(t-\tau)$ replaced by $\sin\tau$: $\int_2^t\sin\tau\,d\tau$.

### Q28 (slide 17)

Use the convolution theorem $\mathcal L^{-1}[F(s)G(s)]=(f*g)(t)$ with $F=\dfrac{1}{s+1}$ and $G=\dfrac{s}{s^2+1}$. What is $\mathcal L^{-1}\!\left[\dfrac{s}{(s+1)(s^2+1)}\right]$?

- A) $e^{-t}\cos t$
- B) $\tfrac12\left(\cos t+\sin t-e^{-t}\right)$
- C) $\tfrac12\left(e^{-t}-\cos t-\sin t\right)$
- D) $\tfrac12\left(\sin t-\cos t+e^{-t}\right)$

> [!success]- Answer
> **B.** $(f*g)(t)=e^{-t}\int_0^te^{\tau}\cos\tau\,d\tau=e^{-t}\cdot\tfrac12\left(e^t(\cos t+\sin t)-1\right)$.
> Partial-fraction check: $A=-\tfrac12$, $B=C=\tfrac12$ in $\dfrac{A}{s+1}+\dfrac{Bs+C}{s^2+1}$.
> - A: Convolution taken as the product $f(t)g(t)$. Its transform is $\dfrac{s+1}{(s+1)^2+1}$.
> - C: Sign slip at $s=-1$: $2A=-1$ solved as $A=\tfrac12$, so $B=C=-\tfrac12$. This is the negative of the answer.
> - D: $G=\dfrac{s}{s^2+1}$ inverted as $\sin t$ instead of $\cos t$. This is $e^{-t}*\sin t$.

### Q29 (slide 18, convolution IVP)

Solve $y''+4y=f(t)$, $y(0)=y'(0)=0$ in terms of $f$. Then test the formula with $f(t)=4$. Which pair is correct?

- A) $y=\int_0^tf(\tau)\sin\big(2(t-\tau)\big)d\tau$; for $f=4$: $y=2-2\cos2t$
- B) $y=\int_0^tf(\tau)\cos\big(2(t-\tau)\big)d\tau$; for $f=4$: $y=2\sin2t$
- C) $y=\tfrac12\int_0^tf(\tau)\sin\big(2(t-\tau)\big)d\tau$; for $f=4$: $y=1-\cos2t$
- D) $y=\tfrac12\int_0^tf(\tau)\cos\big(2(t-\tau)\big)d\tau$; for $f=4$: $y=\sin2t$

> [!success]- Answer
> **C.** $(s^2+4)Y=F(s)$, so $Y=F(s)\cdot\dfrac{1}{s^2+4}$ and $\mathcal L^{-1}\!\left[\dfrac{1}{s^2+4}\right]=\tfrac12\sin2t$.
> For $f=4$: $2\int_0^t\sin\big(2(t-\tau)\big)d\tau=1-\cos2t$. Check: $y''+4y=4\cos2t+4-4\cos2t=4$.
> - A: $\dfrac{1}{s^2+4}$ inverted as $\sin2t$. The $2$ on top is missing, so the factor $\tfrac12$ is lost. Then $y''+4y=8$.
> - B: $\dfrac{1}{s^2+4}$ inverted as $\cos2t$, the row of $\dfrac{s}{s^2+4}$. Then $y''+4y=0$, not $4$.
> - D: $\dfrac{1}{s^2+4}$ inverted as $\tfrac12\cos2t$. Then $y'(0)=2\neq0$.

## 9. Dirac delta function (slides 18-20)

### Q30 (slide 18, delta)

Let $\delta_\epsilon(t)=\tfrac1\epsilon\big(H(t)-H(t-\epsilon)\big)$, a pulse of width $\epsilon$ and height $\tfrac1\epsilon$. Find its transform at $s=2$ for $\epsilon=0.1$ and $\epsilon=0.01$. What do the values show?

- A) $0.8187$ and $0.9802$; they tend to $1$
- B) $0.0906$ and $0.0099$; they tend to $0$
- C) $1.8127$ and $1.9801$; they tend to $2$
- D) $0.9063$ and $0.9901$; they tend to $1$

> [!success]- Answer
> **D.** $\mathcal L[\delta_\epsilon]=\tfrac1\epsilon\int_0^\epsilon e^{-st}dt=\dfrac{1-e^{-\epsilon s}}{\epsilon s}$.
> $\dfrac{1-e^{-0.2}}{0.2}=0.9063$ and $\dfrac{1-e^{-0.02}}{0.02}=0.9901$. The limit is $\mathcal L[\delta(t)]=1$.
> - A: The transform taken as $e^{-\epsilon s}$, as for a delta at $t=\epsilon$.
> - B: The height $\tfrac1\epsilon$ was forgotten: $\dfrac{1-e^{-\epsilon s}}{s}$.
> - C: The $s$ in the denominator was forgotten: $\dfrac{1-e^{-\epsilon s}}{\epsilon}$.

### Q31 (slide 19, filtering)

Filtering property: $\int_0^\infty f(t)\,\delta(t-a)\,dt=f(a)$ for $a>0$ and $f$ continuous at $a$. Which statement is correct?

- A) $\int_0^\infty t^2e^{-t}\,\delta(t-3)\,dt=17e^{-3}$
- B) $\int_0^\infty e^{-st}\,\delta(t-a)\,dt=\dfrac{e^{-as}}{s}$
- C) $\int_0^\infty e^{-2t}\cos t\;\delta(t-\pi)\,dt=-e^{-2\pi}$
- D) $\int_0^\infty t^2e^{-t}\,\delta(t-3)\,dt=0$

> [!success]- Answer
> **C.** The delta picks the value at $t=\pi$: $e^{-2\pi}\cos\pi=-e^{-2\pi}$.
> - A: $\delta(t-3)$ treated as the step $H(t-3)$: $\int_3^\infty t^2e^{-t}dt=17e^{-3}$. The right value is $9e^{-3}$.
> - B: The value of $e^{-st}$ at $t=a$ is $e^{-as}$. The $\dfrac1s$ belongs to $\mathcal L[H(t-a)]$.
> - D: The delta is zero away from $t=3$, but its area is $1$. The integral is $f(3)=9e^{-3}$.

### Q32 (slide 19, impulse IVP)

Solve $y'+2y=5\,\delta(t-2)$, $y(0)=3$ with the Laplace transform. Which pair is correct?

- A) $y=3e^{-2t}+5H(t-2)e^{-2(t-2)}$; $y$ jumps up by $5$ at $t=2$
- B) $y=3e^{-2t}+5H(t-2)e^{-2t}$; $y$ jumps up by $5e^{-4}$ at $t=2$
- C) $y=5H(t-2)e^{-2t}$; $y$ jumps up by $5e^{-4}$ at $t=2$
- D) $y=5H(t-2)e^{-2(t-2)}$; $y$ jumps up by $5$ at $t=2$

> [!success]- Answer
> **A.** $sY-3+2Y=5e^{-2s}$, so $Y=\dfrac{3}{s+2}+\dfrac{5e^{-2s}}{s+2}$.
> Second shifting: $\dfrac{e^{-2s}}{s+2}\to H(t-2)e^{-2(t-2)}$. At $t=2$ this part goes from $0$ to $5$.
> - B: Written as $H(t-2)f(t)$ instead of $H(t-2)f(t-2)$.
> - C: Two slips: the forgotten initial value of D and the unshifted $e^{-2t}$ of B.
> - D: The initial value was forgotten. Then $y(0)=0$.

### Q33 (slides 19-20)

Solve $y''+6y'+9y=2\,\delta(t-1)$, $y(0)=0$, $y'(0)=1$. Use both shifting theorems.

- A) $y=te^{3t}+2H(t-1)(t-1)e^{3(t-1)}$
- B) $y=te^{-3t}+2H(t-1)(t-1)e^{-3(t-1)}$
- C) $y=te^{-3t}+2H(t-1)\,t\,e^{-3t}$
- D) $y=2H(t-1)(t-1)e^{-3(t-1)}$

> [!success]- Answer
> **B.** $(s^2Y-1)+6sY+9Y=2e^{-s}$, so $Y=\dfrac{1}{(s+3)^2}+\dfrac{2e^{-s}}{(s+3)^2}$.
> First shifting: $\dfrac{1}{(s+3)^2}\to te^{-3t}$. Second shifting with $a=1$ for the $e^{-s}$ term.
> - A: The $s$-shift applied with the wrong sign: $\dfrac{1}{(s+3)^2}$ read as $F(s-3)$.
> - C: Written as $H(t-1)f(t)$ instead of $H(t-1)f(t-1)$. Then $y$ jumps at $t=1$.
> - D: The initial value $y'(0)=1$ was forgotten. Then $y'(0)=0$.

## 10. Systems of ODEs (slides 21-22)

### Q34 (slides 21-22)

Solve $x'=x+2y$, $y'=2x+y$, $x(0)=2$, $y(0)=0$ with the Laplace transform.

- A) $x=e^{3t}-e^{-t}$, $y=e^{3t}+e^{-t}$
- B) $x=e^{-3t}+e^{t}$, $y=e^{-3t}-e^{t}$
- C) $x=e^{3t}+e^{-t}$, $y=e^{3t}-e^{-t}$
- D) $x=-e^{3t}-e^{-t}$, $y=-e^{3t}+e^{-t}$

> [!success]- Answer
> **C.** $(s-1)X-2Y=2$ and $-2X+(s-1)Y=0$. So $Y=\dfrac{4}{(s-3)(s+1)}$, $X=\dfrac{2(s-1)}{(s-3)(s+1)}$.
> $Y=\dfrac{1}{s-3}-\dfrac{1}{s+1}$ and $X=\dfrac{1}{s-3}+\dfrac{1}{s+1}$.
> - A: The initial values swapped: $x(0)=0$, $y(0)=2$ used. Then $x(0)=0$ here.
> - B: $\dfrac{1}{s-a}$ inverted as $e^{-at}$. Then $x'=-3e^{-3t}+e^t\neq x+2y$.
> - D: Sign slip: $sX+2$ instead of $sX-2$. Then $x(0)=-2$.

### Q35 (slide 22)

A system from the slides contains the equation $2y'-x'+3y=0$. Its solution has $x=-\tfrac72-3t+\tfrac16e^{-2t}+\tfrac{10}{3}e^{t}$ and $y=-1+c\,e^{-2t}+\tfrac23e^{t}$. Insert both into $2y'-x'+3y=0$. Which $c$ makes the $e^{-2t}$ terms cancel?

- A) $c=\tfrac19$
- B) $c=\tfrac13$
- C) $c=-\tfrac13$
- D) $c=-\tfrac16$

> [!success]- Answer
> **B.** $y'$ has $-2c\,e^{-2t}$ and $x'$ has $-\tfrac13e^{-2t}$.
> $2\cdot(-2c)-\left(-\tfrac13\right)+3c=\tfrac13-c=0$, so $c=\tfrac13$. The constants and the $e^{t}$ terms also give $0$.
> - A: The factor $3$ of $3y$ lost: $-4c+\tfrac13+c=0$.
> - C: The minus sign in front of $x'$ lost: $-4c-\tfrac13+3c=0$.
> - D: The chain-rule factor $-2$ lost in $x'$, so $x'$ has $+\tfrac16e^{-2t}$: $-4c-\tfrac16+3c=0$.
