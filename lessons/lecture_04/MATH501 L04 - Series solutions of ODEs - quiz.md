---
course: MATH 501 Advanced Engineering Mathematics
lesson: MATH501 L04 - Series solutions of ODEs
type: quiz
questions: 19
---

# MATH501 L04 - Series solutions of ODEs - quiz

Lesson note: [[MATH501 L04 - Series solutions of ODEs]]. One question per check question of the lesson. Pick an option, then open the answer.

## 1. Power series, analytic functions, Maclaurin series (slides 1-2)

### Q1 (slide 1, coefficient formula)

Write $f(x)=e^{2x}$ as a power series about $x_0=1$ with $a_n=\dfrac{f^{(n)}(x_0)}{n!}$. What is the coefficient of $(x-1)^3$?

- A) $8e^2$
- B) $2e^2$
- C) $\dfrac{4e^2}{3}$
- D) $\dfrac{8e^2}{3}$

> [!success]- Answer
> **C.** $f^{(n)}(x)=2^ne^{2x}$, so $f'''(1)=8e^2$.
> $a_3=\dfrac{8e^2}{3!}=\dfrac{8e^2}{6}=\dfrac{4e^2}{3}$.
> The series is $e^2+2e^2(x-1)+2e^2(x-1)^2+\dfrac{4e^2}{3}(x-1)^3+\cdots$
> - A: The factorial is dropped: $a_3=f'''(1)=8e^2$.
> - B: This is $a_2=\dfrac{4e^2}{2!}$, the coefficient of $(x-1)^2$. Index off by one.
> - D: Divided by $n=3$ instead of $n!=6$.

### Q2 (slide 1, radius of convergence)

Use the ratio test on $\sum_{n\ge1}\dfrac{n}{3^n}x^n$, and check the end points separately. On which interval does the series converge?

- A) $(-3,3)$
- B) $[-3,3]$
- C) $\left(-\tfrac13,\tfrac13\right)$
- D) $\left[-\tfrac13,\tfrac13\right]$

> [!success]- Answer
> **A.** $\left\lvert\dfrac{a_{n+1}x^{n+1}}{a_nx^n}\right\rvert=\dfrac{n+1}{n}\cdot\dfrac{\lvert x\rvert}{3}\to\dfrac{\lvert x\rvert}{3}$. This is $<1$ for $\lvert x\rvert<3$, so $R=3$.
> At $x=3$ the terms are $n$, at $x=-3$ they are $(-1)^nn$. They do not go to 0, so both end points diverge.
> - B: Right radius, but the end points are taken as convergent. There the ratio test gives $L=1$ and decides nothing.
> - C: The ratio is inverted: $R$ computed as $\lim\lvert a_{n+1}/a_n\rvert=\tfrac13$ instead of $\lim\lvert a_n/a_{n+1}\rvert$.
> - D: Two slips: the inverted ratio of C and the closed end points of B.

## 2. Ordinary points and the power series method (slides 2-3)

### Q3 (slide 2, Maclaurin series)

Differentiate $\ln(1+x)=\sum_{n\ge1}\dfrac{(-1)^{n-1}x^n}{n}$ term by term, then shift the index so that the sum has $x^n$. Which result is correct?

- A) $\sum_{n\ge0}(-1)^{n-1}x^n=-\dfrac{1}{1+x}$
- B) $\sum_{n\ge1}(-1)^nx^n=-\dfrac{x}{1+x}$
- C) $\sum_{n\ge0}\dfrac{(-1)^nx^n}{n+1}=\dfrac{\ln(1+x)}{x}$
- D) $\sum_{n\ge0}(-1)^nx^n=\dfrac{1}{1+x}$

> [!success]- Answer
> **D.** $\dfrac{d}{dx}\dfrac{(-1)^{n-1}x^n}{n}=(-1)^{n-1}x^{n-1}$. Put $k=n-1$: the start $n=1$ becomes $k=0$, and $(-1)^{n-1}x^{n-1}$ becomes $(-1)^kx^k$.
> $\sum_{k\ge0}(-x)^k=\dfrac{1}{1+x}$ for $\lvert x\rvert<1$. Check: $\dfrac{d}{dx}\ln(1+x)=\dfrac{1}{1+x}$.
> - A: The power was shifted, but the sign factor $(-1)^{n-1}$ was not.
> - B: The power and the sign were shifted, but the start stayed at 1. The $x^0$ term $1$ is lost.
> - C: The factor $n$ of the power rule is not brought down: $x^n/n$ differentiated to $x^{n-1}/n$.

### Q4 (slide 2, ordinary point)

The point $x_0=1$ is an ordinary point of $(x^2+4)y''+xy'+y=0$. Use this result: a power series solution about $x_0$ converges at least for $\lvert x-x_0\rvert<\rho$, where $\rho$ is the distance from $x_0$ to the nearest point where $p=\dfrac{x}{x^2+4}$ or $q=\dfrac{1}{x^2+4}$ is not analytic. Where is the series in powers of $(x-1)$ guaranteed to converge?

- A) For $\lvert x-1\rvert<2$
- B) For $\lvert x-1\rvert<1$
- C) For $\lvert x-1\rvert<\sqrt5$
- D) For every real $x$

> [!success]- Answer
> **C.** $x^2+4=0$ gives $x=\pm2i$. Distance from $1$ to $\pm2i$: $\sqrt{(1-0)^2+2^2}=\sqrt5\approx2.24$.
> (About $x_0=0$ the same rule gives $\lvert x\rvert<2$.)
> - A: Only the imaginary part $2$ is used. That is the distance from $0$, not from $1$.
> - B: Sign slip: $x^2+4=0$ solved as $x=\pm2$. The nearest point $2$ is at distance $1$.
> - D: Only real singular points are counted. The complex points $\pm2i$ count too.

### Q5 (slides 2-3)

Solve $y'-2xy=0$ with $y=\sum_{n\ge0}a_nx^n$ about 0. Which series and function do you get?

- A) $y=a_0\left(1-x^2+\tfrac{x^4}{2}-\tfrac{x^6}{6}+\cdots\right)=a_0e^{-x^2}$
- B) $y=a_0\left(1+x^2+\tfrac{x^4}{2}+\tfrac{x^6}{6}+\cdots\right)=a_0e^{x^2}$
- C) $y=a_0\left(1+2x^2+4x^4+8x^6+\cdots\right)=\dfrac{a_0}{1-2x^2}$
- D) $y=a_0\left(1+\tfrac{x^2}{2}+\tfrac{x^4}{8}+\tfrac{x^6}{48}+\cdots\right)=a_0e^{x^2/2}$

> [!success]- Answer
> **B.** After the shift: $a_1+\sum_{n\ge1}\left[(n+1)a_{n+1}-2a_{n-1}\right]x^n=0$.
> So $a_1=0$ and $a_{n+1}=\dfrac{2a_{n-1}}{n+1}$: $a_2=a_0$, $a_4=\dfrac{a_0}{2}$, $a_6=\dfrac{a_0}{6}$, odd ones 0.
> $1+x^2+\dfrac{x^4}{2!}+\dfrac{x^6}{3!}$ is $e^u$ with $u=x^2$.
> - A: Sign slip: $a_{n+1}=-\dfrac{2a_{n-1}}{n+1}$. That solves $y'+2xy=0$.
> - C: The factor $(n+1)$ from $y'$ is dropped: $a_{n+1}=2a_{n-1}$.
> - D: The factor 2 of $2x$ is dropped: $a_{n+1}=\dfrac{a_{n-1}}{n+1}$. That solves $y'-xy=0$.

### Q6 (slide 3, index shift)

The term $-x\,y''$ gives $-\sum_{n\ge2}n(n-1)a_nx^{n-1}$. Re-index $\sum_{n\ge2}n(n-1)a_nx^{n-1}$ so that the power is $x^n$. Which sum is equal to it?

- A) $\sum_{n\ge1}(n+2)(n+1)a_{n+2}x^n$
- B) $\sum_{n\ge3}(n-1)(n-2)a_{n-1}x^n$
- C) $\sum_{n\ge1}n(n-1)a_{n+1}x^n$
- D) $\sum_{n\ge1}n(n+1)a_{n+1}x^n$

> [!success]- Answer
> **D.** Put $k=n-1$, so $n=k+1$: $n(n-1)\to(k+1)k$, $a_n\to a_{k+1}$, $x^{n-1}\to x^k$, start $n=2\to k=1$.
> It starts at 1 because the lowest power of the old sum is $x^{2-1}=x^1$. Check: old $n=2$ term $2a_2x$, new $n=1$ term $1\cdot2\,a_2x$.
> - A: Shifted by 2, as for $y''=\sum n(n-1)a_nx^{n-2}$. The factor $x$ already raised the power by one.
> - B: Shifted the wrong way ($n\to n-1$ instead of $n\to n+1$). This sum is $\sum n(n-1)a_nx^{n+1}$.
> - C: $a_n$ and the power were shifted, but the factor $n(n-1)$ was not. Its $n=1$ term is 0 instead of $2a_2x$.

## 3. Second order examples and an IVP (slides 3-6)

### Q7 (slide 4)

Solve $y''+y=e^x$ with $y=\sum_{n\ge0}a_nx^n$ about 0, so $a_0=y(0)$ and $a_1=y'(0)$. Collect the result as $y=a_0\,u(x)+a_1\,v(x)+w(x)$, where $w$ contains no $a_0$, $a_1$. Which are $u$ and $v$?

- A) $u=\cosh x$, $v=\sinh x$
- B) $u=\sin x$, $v=\cos x$
- C) $u=\cos x$, $v=\sin x$
- D) $u=\dfrac{1}{1+x^2}$, $v=\dfrac{x}{1+x^2}$

> [!success]- Answer
> **C.** Recurrence: $a_{n+2}=\dfrac{\frac{1}{n!}-a_n}{(n+2)(n+1)}$. So $a_2=\dfrac{1-a_0}{2}$, $a_3=\dfrac{1-a_1}{6}$, $a_4=\dfrac{a_0}{24}$, $a_5=\dfrac{a_1}{120}$.
> $a_0$ multiplies $1-\dfrac{x^2}{2}+\dfrac{x^4}{24}-\cdots=\cos x$, and $a_1$ multiplies $x-\dfrac{x^3}{6}+\dfrac{x^5}{120}-\cdots=\sin x$.
> The rest $w=\dfrac{x^2}{2}+\dfrac{x^3}{6}+\cdots=\tfrac12e^x-\tfrac12\cos x-\tfrac12\sin x$ is a particular solution.
> - A: Sign slip: $+a_n$ in the recurrence. Those are the solutions of $y''-y=0$.
> - B: The roles are swapped. $u(0)=1$ is needed because $a_0=y(0)$, but $\sin0=0$.
> - D: The factorials of the pattern are dropped: $1-x^2+x^4-\cdots$ instead of $1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$

### Q8 (slide 5)

Solve $y''+x^2y=0$ with a power series about 0. Take the solution $y_1$ with $y_1(0)=1$, $y_1'(0)=0$. What are its first three nonzero terms?

- A) $1-\dfrac{x^4}{12}+\dfrac{x^8}{672}$
- B) $1-\dfrac{x^2}{2}+\dfrac{x^4}{24}$
- C) $1-\dfrac{x^4}{2}+\dfrac{x^8}{60}$
- D) $1-\dfrac{x^4}{4}+\dfrac{x^8}{32}$

> [!success]- Answer
> **A.** $\sum_{n\ge0}(n+2)(n+1)a_{n+2}x^n+\sum_{n\ge2}a_{n-2}x^n=0$ gives $a_2=a_3=0$ and $a_{n+2}=-\dfrac{a_{n-2}}{(n+2)(n+1)}$.
> The jump is 4: $y''$ lowers the power by 2 and $x^2y$ raises it by 2.
> $a_4=-\dfrac{1}{4\cdot3}=-\dfrac{1}{12}$, $a_8=-\dfrac{a_4}{8\cdot7}=\dfrac{1}{672}$. (The other solution is $y_2=x-\frac{x^5}{20}+\frac{x^9}{1440}-\cdots$)
> - B: $x^2y=\sum a_nx^{n+2}$ is not re-indexed, so it acts like $y$: $a_{n+2}=-\dfrac{a_n}{(n+2)(n+1)}$. This is $\cos x$.
> - C: After $a_n\to a_{n+2}$ the factor $n(n-1)$ was kept instead of $(n+2)(n+1)$: $a_4=-\dfrac{1}{2\cdot1}$, $a_8=-\dfrac{a_4}{6\cdot5}$.
> - D: The factor $(n+1)$ is dropped: $a_{n+2}=-\dfrac{a_{n-2}}{n+2}$.

### Q9 (slide 6)

Solve $(1+x^2)y''+2xy'-2y=0$, $y(0)=2$, $y'(0)=3$, with a power series about 0, and recognise the function. Which closed form is correct?

- A) $y=3+2x+3x\arctan x$
- B) $y=2+3x+2x\arctan x$
- C) $y=2+3x-2x\operatorname{artanh}x$
- D) $y=2+3x+2\arctan x$

> [!success]- Answer
> **B.** All sums start at $n=0$ after the shift: $(n+2)(n+1)a_{n+2}+(n+2)(n-1)a_n=0$, so $a_{n+2}=-\dfrac{n-1}{n+1}a_n$.
> $a_2=a_0$, $a_4=-\dfrac{a_0}{3}$, $a_6=\dfrac{a_0}{5}$, and $a_3=0$, so all odd ones after $a_1$ are 0.
> $a_0=2$, $a_1=3$: $y=2+3x+2\left(x^2-\dfrac{x^4}{3}+\dfrac{x^6}{5}-\cdots\right)=2+3x+2x\arctan x$. It converges for $\lvert x\rvert<1$ (nearest singular points $\pm i$).
> - A: $a_0$ and $a_1$ swapped: $a_0=y(0)=2$ and $a_1=y'(0)=3$.
> - C: Sign slip: $a_{n+2}=+\dfrac{n-1}{n+1}a_n$ gives $x^2+\dfrac{x^4}{3}+\dfrac{x^6}{5}+\cdots=x\operatorname{artanh}x$ with a minus in front.
> - D: The factor $x$ is lost: $x^2-\frac{x^4}{3}+\cdots$ is $x\arctan x$, not $\arctan x$.

## 4. Singular points, Frobenius' theorem, indicial equation (slides 7-9)

### Q10 (slide 7, classification)

$x_0$ is a regular singular point of $Py''+Qy'+Ry=0$ if $P(x_0)=0$ and both $(x-x_0)\dfrac QP$ and $(x-x_0)^2\dfrac RP$ are analytic at $x_0$. Classify the singular points $x=3$ and $x=-3$ of $(x^2-9)^2y''+(x+3)y'+2y=0$.

- A) $x=3$ is irregular, $x=-3$ is regular.
- B) $x=3$ is regular, $x=-3$ is irregular.
- C) Both $x=3$ and $x=-3$ are regular.
- D) Both $x=3$ and $x=-3$ are irregular.

> [!success]- Answer
> **A.** $P=(x-3)^2(x+3)^2$, $Q=x+3$, $R=2$.
> At 3: $(x-3)\dfrac QP=\dfrac{1}{(x-3)(x+3)}$ is unbounded at 3. Irregular.
> At $-3$: $(x+3)\dfrac QP=\dfrac{1}{(x-3)^2}$ and $(x+3)^2\dfrac RP=\dfrac{2}{(x-3)^2}$ are analytic at $-3$ (denominator 36). Regular.
> - B: The two points are swapped: the factor $x+3$ of $Q$ cancels against $(x+3)^2$, not against $(x-3)^2$.
> - C: Only $(x-x_0)^2R/P$ is tested. It is analytic at both points, but $(x-3)Q/P$ fails at 3.
> - D: A double zero of $P$ is taken as "irregular" at once. The test is on the quotients after cancelling.

### Q11 (slide 7, Frobenius' theorem)

Try $y=x^r$ in $2x^2y''+3xy'-y=0$. For which values of $r$ is $x^r$ a solution?

- A) $r=\tfrac12$ and $r=-1$
- B) $r=-\tfrac12$ and $r=1$
- C) $r=-1+\sqrt2$ and $r=-1-\sqrt2$
- D) $r=\dfrac{-3+\sqrt{17}}{4}$ and $r=\dfrac{-3-\sqrt{17}}{4}$

> [!success]- Answer
> **A.** $y'=rx^{r-1}$, $y''=r(r-1)x^{r-2}$: $\left[2r(r-1)+3r-1\right]x^r=(2r^2+r-1)x^r=(2r-1)(r+1)x^r$.
> So $y_1=\sqrt x$ and $y_2=\dfrac1x$. Neither is a power series $\sum a_nx^n$, which is why Frobenius uses $x^{n+r}$.
> - B: Sign slip in the factors: $(2r+1)(r-1)=2r^2-r-1$, not $2r^2+r-1$.
> - C: The factor 2 of $2x^2y''$ is dropped: $r(r-1)+3r-1=r^2+2r-1=0$.
> - D: $r^2$ used for $y''$ instead of $r(r-1)$: $2r^2+3r-1=0$.

### Q12 (slide 8, indicial equation)

For $x^2y''+(\sin x)\,y'-(\cos x)\,y=0$ at 0 use $c_0=\lim_{x\to0}x\dfrac QP$, $d_0=\lim_{x\to0}x^2\dfrac RP$ and $r(r-1)+c_0r+d_0=0$. Cases: (2.) $r_1-r_2$ not an integer, (3.) $r_1=r_2$, (4.) $r_1-r_2$ a positive integer. Which is correct?

- A) $r=1$ twice, case (3.)
- B) $r=1$ and $r=-1$, case (4.)
- C) $r=\frac{1\pm\sqrt5}{2}$, case (2.)
- D) $r=\pm i$, no real root

> [!success]- Answer
> **B.** $x\dfrac QP=\dfrac{\sin x}{x}\to1$ and $x^2\dfrac RP=-\cos x\to-1$. So $c_0=1$, $d_0=-1$.
> $r(r-1)+r-1=r^2-1=0$: $r_1=1$, $r_2=-1$. $r_1-r_2=2$ is a positive integer: case (4.), $y_2=k\,y_1\ln x+\sum a_n^*x^{n-1}$, $k$ may be 0.
> - A: $c_0$ and $d_0$ swapped: $r(r-1)-r+1=(r-1)^2$.
> - C: $c_0$ taken as $Q(0)=\sin0=0$ instead of $\lim x\,Q/P$: $r^2-r-1=0$.
> - D: The minus sign of $-\cos x$ is lost, $d_0=+1$: $r^2+1=0$.

### Q13 (slide 9)

$xy''+y=0$ has the indicial roots $r_1=1$, $r_2=0$ at 0, so the second solution has the form $y_2=k\,y_1\ln x+\sum_{n\ge0}b_nx^n$. Try a plain series $y=\sum_{n\ge0}b_nx^n$ with $b_0\neq0$, and find $y_1=\sum a_nx^{n+1}$ with $a_0=1$. Which is correct?

- A) The $x^0$ equation reads $0=0$, so $k=0$. $y_1=x-\frac{x^2}{2}+\frac{x^3}{12}-\frac{x^4}{144}$
- B) The $x^0$ equation forces $b_0=0$, so $k\neq0$. $y_1=x-\frac{x^2}{2}+\frac{x^3}{6}-\frac{x^4}{24}$
- C) The $x^0$ equation forces $b_0=0$, so $k\neq0$. $y_1=x-\frac{x^2}{2}+\frac{x^3}{12}-\frac{x^4}{144}$
- D) The $x^0$ equation reads $0=0$, so $k=0$. $y_1=x-\frac{x^2}{2}+\frac{x^3}{6}-\frac{x^4}{24}$

> [!success]- Answer
> **C.** Plain series: $\sum_{n\ge1}\left[n(n-1)b_n+b_{n-1}\right]x^{n-1}=0$. At $n=1$: $0\cdot b_1+b_0=0$, so $b_0=0$. Contradiction, so the logarithm is needed: $k\neq0$.
> For $r=1$: $n(n+1)a_n+a_{n-1}=0$, $a_n=-\dfrac{a_{n-1}}{n(n+1)}$: $a_1=-\tfrac12$, $a_2=\tfrac{1}{12}$, $a_3=-\tfrac{1}{144}$.
> - A: The term $b_0$ of $y$ is left out of the $x^0$ equation. Then it reads $0\cdot b_1=0$, which is the $k=0$ situation.
> - B: Right about $k$, but the factor $n$ is dropped: $a_n=-\dfrac{a_{n-1}}{n+1}$.
> - D: Two slips: the lost $b_0$ of A and the dropped factor of B.

## 5. Frobenius example: roots not differing by an integer (slides 10-12)

### Q14 (slides 10-11)

For $2xy''+(1+x)y'+y=0$ about 0: find the indicial roots, then the Frobenius solution $y_1$ for the larger root with $a_0=1$. Which closed form is $y_1$?

- A) $y_1=\sqrt x\,e^{x/2}$
- B) $y_1=\sqrt x\,e^{-x/2}$
- C) $y_1=\dfrac{2\sqrt x}{2+x}$
- D) $y_1=\sqrt x\cos\sqrt x$

> [!success]- Answer
> **B.** Lowest power: $r(2r-1)a_0=0$, so $r_1=\tfrac12$, $r_2=0$. Recurrence: $a_n=-\dfrac{a_{n-1}}{2n+2r-1}$.
> With $r=\tfrac12$: $a_n=-\dfrac{a_{n-1}}{2n}$, so $a_n=\dfrac{(-1)^n}{2^nn!}$: $1-\frac x2+\frac{x^2}{8}-\frac{x^3}{48}+\cdots=e^{-x/2}$.
> - A: The minus sign of the recurrence is lost: $a_n=+\dfrac{a_{n-1}}{2n}$.
> - C: The factorial of the pattern is dropped: $a_n=\dfrac{(-1)^n}{2^n}$ gives $\dfrac{1}{1+x/2}$.
> - D: The product $2\cdot4\cdots(2n)=2^nn!$ taken as $(2n)!$: $a_n=\dfrac{(-1)^n}{(2n)!}$ gives $\sum\dfrac{(-1)^nx^n}{(2n)!}=\cos\sqrt x$.

### Q15 (slide 11, second root)

$2xy''+(1+x)y'+y=0$ has the smaller indicial root $r_2=0$ at 0. Find the Frobenius solution $y_2=\sum_{n\ge0}a_n^*x^n$ with $a_0^*=1$. Which is correct?

- A) $1-x+\frac{x^2}{3}-\frac{x^3}{15}+\frac{x^4}{105}-\cdots$, it never stops
- B) $1-x+\frac{x^2}{2}-\frac{x^3}{6}+\frac{x^4}{24}-\cdots$, it never stops
- C) $y_2=1$: all $a_n^*$ with $n\ge1$ are 0, it stops
- D) $1-\frac{x}{3}+\frac{x^2}{15}-\frac{x^3}{105}+\frac{x^4}{945}-\cdots$, it never stops

> [!success]- Answer
> **A.** The recurrence is $a_n^*=-\dfrac{a_{n-1}^*}{2n+2r-1}$. With $r=0$: $a_n^*=-\dfrac{a_{n-1}^*}{2n-1}$.
> $a_1^*=-1$, $a_2^*=\tfrac13$, $a_3^*=-\tfrac{1}{15}$, $a_4^*=\tfrac{1}{105}$. The numerator is never 0, so the series does not stop.
> - B: $2n-1$ replaced by $n$. This is $e^{-x}$, and $2xy''+(1+x)y'+y=xe^{-x}\neq0$.
> - C: The factor $(2n-2)$ of the slide example is copied. Here $y=1$ gives $0+0+1\neq0$.
> - D: Sign slip: $2n-1$ written as $2n+1$.

## 6. Frobenius example: repeated root (slides 12-15)

### Q16 (slide 12, end of the previous example)

For which constant $c$ is $y=x^{-1/2}$ ($x>0$) a solution of $x^2y''+\left(2x^2+\tfrac x2\right)y'+(x+c)\,y=0$? Substitute and collect the powers of $x$.

- A) $c=1$
- B) $c=0$
- C) $c=\tfrac12$
- D) $c=-\tfrac12$

> [!success]- Answer
> **D.** $y'=-\tfrac12x^{-3/2}$, $y''=\tfrac34x^{-5/2}$.
> $x^{1/2}$ terms: $2x^2\cdot\left(-\tfrac12x^{-3/2}\right)+x\cdot x^{-1/2}=-x^{1/2}+x^{1/2}=0$, for every $c$.
> $x^{-1/2}$ terms: $\tfrac34-\tfrac14+c=0$, so $c=-\tfrac12$. This is the slide's equation, and $y_2=1/\sqrt x$ solves it exactly.
> - A: Sign slip in $y''$: $-\tfrac34x^{-5/2}$. Then $-\tfrac34-\tfrac14+c=0$ gives $c=1$.
> - B: $y''$ computed with the factor $-\tfrac12$ twice: $\tfrac14x^{-5/2}$. Then $\tfrac14-\tfrac14+c=0$ gives $c=0$.
> - C: The minus of $y'$ is lost: $y'=\tfrac12x^{-3/2}$, so $y''=-\tfrac34x^{-5/2}$. Then $-\tfrac34+\tfrac14+c=0$ gives $c=\tfrac12$.

### Q17 (slides 12-13)

For $xy''+y'-y=0$ about 0: classify the point, find the indicial equation, the recurrence and the Frobenius solution $y_1$ with $a_0=1$. Which is $y_1$?

- A) $1-x+\dfrac{x^2}{4}-\dfrac{x^3}{36}+\cdots$
- B) $1+x+\dfrac{x^2}{4}+\dfrac{x^3}{36}+\cdots$
- C) $1+x+\dfrac{x^2}{2}+\dfrac{x^3}{6}+\cdots$
- D) $1-x+\dfrac{x^2}{2}-\dfrac{x^3}{6}+\cdots$

> [!success]- Answer
> **B.** $xQ/P=1$, $x^2R/P=-x$: regular singular point, $c_0=1$, $d_0=0$. Indicial equation $r^2=0$, $r=0$ twice.
> $\sum(n+r)^2a_nx^{n+r-1}-\sum a_{n-1}x^{n+r-1}=0$, so $a_n=\dfrac{a_{n-1}}{n^2}$ and $a_n=\dfrac{1}{(n!)^2}$: $1,1,\tfrac14,\tfrac{1}{36},\tfrac{1}{576}$.
> - A: Sign slip: $a_n=-\dfrac{a_{n-1}}{n^2}$, as for $xy''+y'+y=0$.
> - C: $(n+r)^2$ taken as $(n+r)$: $a_n=\dfrac{a_{n-1}}{n}$, which gives $e^x$.
> - D: Two slips: the sign slip of A and the lost square of C. $a_n=-\dfrac{a_{n-1}}{n}$ gives $e^{-x}$.

### Q18 (slides 13-14)

Let $y_1=\sum_{n\ge0}c_nx^n$, $c_0=1$, be the Frobenius solution of $xy''+y'-y=0$ about 0. Put $y_2=y_1\ln x+\sum_{n\ge1}b_nx^n$ into the equation. The $\ln x$ terms cancel. Find $b_1$ and $b_3$ ($b_2$ is needed on the way).

- A) $b_1=2$, $b_3=\dfrac{11}{108}$
- B) $b_1=-1$, $b_3=-\dfrac{1}{24}$
- C) $b_1=-2$, $b_3=-\dfrac{11}{108}$
- D) $b_1=-1$, $b_3=-\dfrac{11}{216}$

> [!success]- Answer
> **C.** $y_2''=y_1''\ln x+\dfrac{2y_1'}{x}-\dfrac{y_1}{x^2}+\cdots$. The $\ln x$ terms give $\ln x\,(xy_1''+y_1'-y_1)=0$ and $\pm\dfrac{y_1}{x}$ cancel.
> Left: $2y_1'+\sum n^2b_nx^{n-1}-\sum b_{n-1}x^{n-1}=0$, with $2y_1'=2+x+\tfrac{x^2}{6}+\cdots$ ($c_n=\tfrac{1}{(n!)^2}$).
> $x^0$: $2+b_1=0$, $b_1=-2$. $x^1$: $1+4b_2+2=0$, $b_2=-\tfrac34$. $x^2$: $\tfrac16+9b_3+\tfrac34=0$, $b_3=-\tfrac{11}{108}$.
> - A: $2y_1'$ moved to the other side without the sign change: $n^2b_n=b_{n-1}+\dfrac{2n}{(n!)^2}$.
> - B: $n(n-1)+n$ combined as $n(n+1)$ instead of $n^2$.
> - D: Product rule done once only: $\dfrac{y_1'}{x}$ instead of $\dfrac{2y_1'}{x}$ in $y_2''$, so $y_1'$ is left instead of $2y_1'$.

### Q19 (slide 15)

For $x^2y''+5xy'+(x+4)y=0$ the slides use $a_n^*=-\dfrac{1}{n^2}\left[a_{n-1}^*+\dfrac{4(-1)^n}{(n!)^2}+\dfrac{2(-1)^n(n-2)}{(n!)^2}\right]$ with $a_2^*=-\tfrac34$. What are $a_3^*$ and $a_4^*$?

- A) $a_3^*=-\dfrac{11}{108}$, $a_4^*=-\dfrac{19}{3456}$
- B) $a_3^*=\dfrac{7}{108}$, $a_4^*=-\dfrac{17}{3456}$
- C) $a_3^*=\dfrac{11}{36}$, $a_4^*=-\dfrac{23}{288}$
- D) $a_3^*=\dfrac{11}{108}$, $a_4^*=-\dfrac{25}{3456}$

> [!success]- Answer
> **D.** $n=3$: $(3!)^2=36$. Bracket $-\tfrac34-\tfrac{4}{36}-\tfrac{2}{36}=-\tfrac{33}{36}=-\tfrac{11}{12}$, so $a_3^*=-\tfrac19\cdot\left(-\tfrac{11}{12}\right)=\tfrac{11}{108}$.
> $n=4$: $(4!)^2=576$. Bracket $\tfrac{11}{108}+\tfrac{4}{576}+\tfrac{4}{576}=\tfrac{50}{432}=\tfrac{25}{216}$, so $a_4^*=-\tfrac{1}{16}\cdot\tfrac{25}{216}=-\tfrac{25}{3456}$.
> - A: The leading minus is dropped: $a_n^*=+\dfrac{1}{n^2}[\dots]$.
> - B: $(-1)^n$ taken as $+1$, so at $n=3$ the two fractions are added instead of subtracted.
> - C: $\dfrac{1}{n^2}$ taken as $\dfrac1n$.
