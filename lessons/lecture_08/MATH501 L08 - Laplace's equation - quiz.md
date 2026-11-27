---
course: MATH 501 Advanced Engineering Mathematics
lesson: MATH501 L08 - Laplace's equation
type: quiz
questions: 23
---

# MATH501 L08 - Laplace's equation - quiz

Lesson note: [[MATH501 L08 - Laplace's equation]]. One question per check question of the lesson. Pick an option, then open the answer.

## 1. Laplacian, Laplace's equation, harmonic functions (slide 1)

### Q1 (slide 1, Laplacian)

Compute $\nabla^2u$ for (a) $u(x,y)=x^2y^3+e^{y}\sin(2x)$ and (b) $u(x,y,z)=xyz^2+ze^{3x}$.

- A) (a) $2y^3+6x^2y-e^{y}\sin(2x)$; (b) $2xy+9ze^{3x}$
- B) (a) $2y^3+6x^2y-3e^{y}\sin(2x)$; (b) $2xy+9ze^{3x}$
- C) (a) $2y^3+6x^2y-e^{y}\sin(2x)$; (b) $2xy+3ze^{3x}$
- D) (a) $2y^3+6x^2y-3e^{y}\sin(2x)$; (b) $2xy+3ze^{3x}$

> [!success]- Answer
> **B.** (a) $u_{xx}=2y^3-4e^{y}\sin(2x)$ (the inner factor 2 of $\sin(2x)$ comes out twice, $2\cdot2=4$). $u_{yy}=6x^2y+e^{y}\sin(2x)$.
> Sum: $2y^3+6x^2y-3e^{y}\sin(2x)$.
> (b) $u_{xx}=9ze^{3x}$ (factor $3\cdot3$), $u_{yy}=0$, $u_{zz}=2xy$. Sum: $2xy+9ze^{3x}$.
> - A: In (a) the inner factor 2 is used only once: $u_{xx}$ gets $-2e^{y}\sin(2x)$, so the sum has $-e^{y}\sin(2x)$.
> - C: The inner factor is used only once in both parts: $-2e^{y}\sin(2x)$ in (a) and $3ze^{3x}$ in (b).
> - D: In (b) the inner factor 3 of $e^{3x}$ is used only once: $3ze^{3x}$ in place of $9ze^{3x}$.

### Q2 (slide 1, harmonic)

Which of these functions is NOT harmonic on the whole plane?

- A) $u=x^3-3xy^2$
- B) $u=e^{-3x}\cos(3y)$
- C) $u=\cos(2x)\cosh(2y)$
- D) $u=x^2y+xy^2$

> [!success]- Answer
> **D.** $u_x=2xy+y^2$, $u_{xx}=2y$. $u_y=x^2+2xy$, $u_{yy}=2x$.
> $u_{xx}+u_{yy}=2x+2y$. This is zero only on the line $y=-x$, not on a region. So $u$ is not harmonic.
> - A: $u_{xx}=6x$, $u_{yy}=-6x$, sum $0$. Harmonic.
> - B: $u_{xx}=9e^{-3x}\cos(3y)$, $u_{yy}=-9e^{-3x}\cos(3y)$, sum $0$. Harmonic.
> - C: $u_{xx}=-4\cos(2x)\cosh(2y)$, $u_{yy}=+4\cos(2x)\cosh(2y)$ (because $(\cosh t)''=\cosh t$), sum $0$. Harmonic.

### Q3 (slide 1, three dimensions)

Let $r=\sqrt{x^2+y^2+z^2}$ and $u=\dfrac1r$. For $r\neq0$, what is $u_{xx}$?

- A) $-r^{-3}+3x^2r^{-5}$
- B) $r^{-3}-3x^2r^{-5}$
- C) $-r^{-3}+3x\,r^{-4}$
- D) $-r^{-3}-3x^2r^{-5}$

> [!success]- Answer
> **A.** $u=(x^2+y^2+z^2)^{-1/2}$, so $u_x=-\tfrac12(x^2+y^2+z^2)^{-3/2}\cdot2x=-x\,r^{-3}$.
> $\dfrac{\partial}{\partial x}r^{-3}=-\tfrac32(x^2+y^2+z^2)^{-5/2}\cdot2x=-3x\,r^{-5}$.
> Product rule: $u_{xx}=-r^{-3}+(-x)(-3x\,r^{-5})=-r^{-3}+3x^2r^{-5}$.
> Then $\nabla^2u=-3r^{-3}+3(x^2+y^2+z^2)r^{-5}=0$ for $r\neq0$.
> - B: Sign slip in $u_x$: $+x\,r^{-3}$ in place of $-x\,r^{-3}$. Every term changes sign.
> - C: The inner derivative of $r^{-3}$ is forgotten: $-3r^{-4}$ in place of $-3x\,r^{-5}$.
> - D: Sign slip in the derivative of $r^{-3}$: $+3x\,r^{-5}$ in place of $-3x\,r^{-5}$.

## 2. Dirichlet problem and the eigenvalue problem (slides 2-3)

### Q4 (slide 2, Dirichlet problem)

$D$ is the unit disk $x^2+y^2<1$. The boundary data on the circle $x^2+y^2=1$ is $f(x,y)=x^2$. Which function solves this Dirichlet problem?

- A) $u=x^2$
- B) $u=x^2-y^2$
- C) $u=1+x^2-y^2$
- D) $u=\tfrac12(1+x^2-y^2)$

> [!success]- Answer
> **D.** Equation: $u_{xx}=1$, $u_{yy}=-1$, sum $0$. Harmonic.
> Boundary: on the circle $y^2=1-x^2$, so $u=\tfrac12\bigl(1+x^2-(1-x^2)\bigr)=\tfrac12\cdot2x^2=x^2=f$.
> Both conditions hold.
> - A: Right boundary values, but $u_{xx}+u_{yy}=2+0=2\neq0$. Not harmonic.
> - B: Harmonic, but on the circle $x^2-(1-x^2)=2x^2-1\neq x^2$.
> - C: The factor $\tfrac12$ is forgotten. Harmonic, but on the circle $u=2x^2\neq x^2$.

### Q5 (slide 2, boundary value problem)

For $y''+y=0$, how many solutions are there with (b) $y(0)=0$, $y(\pi)=1$, and with (c) $y(0)=0$, $y(\pi)=0$?

- A) (b) one solution, $y=\sin x$; (c) only $y=0$
- B) (b) one solution, $y=\sin x$; (c) infinitely many, $y=c_2\sin x$
- C) (b) no solution; (c) infinitely many, $y=c_2\sin x$
- D) (b) no solution; (c) only $y=0$

> [!success]- Answer
> **C.** $y=c_1\cos x+c_2\sin x$. $y(0)=c_1=0$, so $y=c_2\sin x$.
> (b) $y(\pi)=c_2\sin\pi=0$, but the condition asks for $1$. $0=1$ is impossible. No solution.
> (c) $y(\pi)=c_2\cdot0=0$ holds for every $c_2$. Infinitely many solutions.
> - A: Two slips: in (b) $c_2=1$ is taken without checking $\sin\pi=0$, and in (c) $c_2\sin\pi=0$ is read as forcing $c_2=0$.
> - B: In (b) $c_2=1$ is taken without checking: $\sin x$ is $0$ at $x=\pi$, not $1$.
> - D: In (c) $c_2\cdot0=0$ is read as $c_2=0$. It holds for every $c_2$.

### Q6 (slides 2-3, case i)

Find all eigenvalues $\lambda>0$ of $y''+\lambda y=0$, $y(0)=0$, $y(3)=0$ ($n=1,2,3,\dots$).

- A) $\lambda_n=\dfrac{n^2\pi^2}{9}$
- B) $\lambda_n=\dfrac{n\pi}{3}$
- C) $\lambda_n=\dfrac{n^2\pi^2}{3}$
- D) $\lambda_n=\dfrac{n^2\pi}{9}$

> [!success]- Answer
> **A.** $y=c_1\cos(\sqrt\lambda\,x)+c_2\sin(\sqrt\lambda\,x)$. $y(0)=0$ gives $c_1=0$.
> $y(3)=c_2\sin(3\sqrt\lambda)=0$ with $c_2\neq0$ needs $3\sqrt\lambda=n\pi$, so $\sqrt\lambda=\dfrac{n\pi}{3}$ and $\lambda_n=\dfrac{n^2\pi^2}{9}$.
> - B: $\sqrt\lambda=\dfrac{n\pi}{3}$ is not squared at the end.
> - C: Only $n\pi$ is squared, not $L=3$: $\dfrac{(n\pi)^2}{3}$ in place of $\left(\dfrac{n\pi}{3}\right)^2$.
> - D: $\pi$ is not squared: $\dfrac{n^2\pi}{9}$ in place of $\dfrac{n^2\pi^2}{9}$.

### Q7 (slide 3, cases ii and iii)

For $\lambda=-4$ the problem is $y''-4y=0$, $y(0)=0$, $y(3)=0$. Which argument for "only $y=0$" is correct?

- A) $y=c_1\cos(2x)+c_2\sin(2x)$; $y(0)=0$ gives $c_1=0$; $c_2\sin6=0$ with $\sin6\neq0$ gives $c_2=0$
- B) $y=c_1\cosh(4x)+c_2\sinh(4x)$; $y(0)=0$ gives $c_1=0$; $c_2\sinh12=0$ with $\sinh12\neq0$ gives $c_2=0$
- C) $y=c_1\cosh(2x)+c_2\sinh(2x)$; $y(0)=0$ gives $c_2=0$; $c_1\cosh6=0$ with $\cosh6\neq0$ gives $c_1=0$
- D) $y=c_1\cosh(2x)+c_2\sinh(2x)$; $y(0)=0$ gives $c_1=0$; $c_2\sinh6=0$ with $\sinh6\neq0$ gives $c_2=0$

> [!success]- Answer
> **D.** $r^2-4=0$, so $r=\pm2$ (real roots) and $y=c_1\cosh(2x)+c_2\sinh(2x)$.
> $y(0)=c_1\cosh0+c_2\sinh0=c_1$, so $c_1=0$. $y(3)=c_2\sinh6=0$ and $\sinh6\approx201.7\neq0$, so $c_2=0$.
> (For $\lambda=0$: $y=c_1x+c_2$, and the two conditions give $c_2=0$, $c_1=0$.)
> - A: Wrong sign in the characteristic equation: $r^2+4=0$ gives trigonometric functions, but $y''-4y=0$ has real roots.
> - B: The root is not taken: $r=\pm4$ in place of $r=\pm\sqrt4=\pm2$.
> - C: The values are swapped: $\cosh0=1$ and $\sinh0=0$, so $y(0)=0$ removes $c_1$, not $c_2$.

### Q8 (slide 3, summary)

The problem is $y''+\lambda y=0$, $y(0)=0$, $y(L)=0$ with $L>0$. For which lengths $L$ is $\lambda=9$ an eigenvalue ($n=1,2,3,\dots$)?

- A) $L=\dfrac{n\pi}{9}$
- B) $L=\dfrac{n\pi}{3}$
- C) $L=3n\pi$
- D) $L=\dfrac{n^2\pi^2}{9}$

> [!success]- Answer
> **B.** The eigenvalues are $\lambda_n=\dfrac{n^2\pi^2}{L^2}$. We need $\dfrac{n^2\pi^2}{L^2}=9$, so $L^2=\dfrac{n^2\pi^2}{9}$ and $L=\dfrac{n\pi}{3}$.
> Check: $\sin(3x)$ solves $y''+9y=0$ and is zero at $x=\dfrac{n\pi}{3}$.
> - A: The square is forgotten: $\dfrac{n\pi}{L}=9$.
> - C: Divided the wrong way: $L=\sqrt\lambda\cdot n\pi$ in place of $L=\dfrac{n\pi}{\sqrt\lambda}$.
> - D: The root is not taken at the end: $L^2=\dfrac{n^2\pi^2}{9}$ is written as $L$.

### Q9 (slide 3, other boundary conditions, beyond the slides)

Find the eigenvalues and eigenfunctions of $y''+\lambda y=0$, $y'(0)=0$, $y'(\pi)=0$ ($n=1,2,3,\dots$).

- A) $\lambda_n=n^2$ with $\cos(nx)$; $\lambda=0$ is not an eigenvalue
- B) $\lambda_n=n^2$ with $\sin(nx)$; $\lambda=0$ is not an eigenvalue
- C) $\lambda_0=0$ with $y_0=1$, and $\lambda_n=n^2$ with $\cos(nx)$
- D) $\lambda_0=0$ with $y_0=1$, and $\lambda_n=n^2$ with $\sin(nx)$

> [!success]- Answer
> **C.** $\lambda>0$, $s=\sqrt\lambda$: $y'=-c_1s\sin(sx)+c_2s\cos(sx)$. $y'(0)=c_2s=0$ gives $c_2=0$. $y'(\pi)=-c_1s\sin(s\pi)=0$ gives $s=n$. So $\lambda_n=n^2$, $y_n=\cos(nx)$.
> $\lambda=0$: $y=c_1x+c_2$, $y'=c_1$. Both conditions give only $c_1=0$, so $y=c_2$ is non-trivial: $\lambda_0=0$, $y_0=1$.
> $\lambda<0$: $y'=c_1s\sinh(sx)+c_2s\cosh(sx)$ gives $c_2=0$, then $c_1s\sinh(s\pi)=0$ gives $c_1=0$. Nothing.
> - A: The case $\lambda=0$ is skipped or done with the old conditions $y(0)=y(\pi)=0$. With $y'$ conditions the constant $c_2$ stays free.
> - B: The summary for $y(0)=0$, $y(\pi)=0$ is copied. It does not hold for conditions on $y'$.
> - D: $y'(0)=0$ is read as removing the cosine. It removes the sine: $y'(0)=c_2s$.

## 3. Orthogonality of the sines (slide 4)

### Q10 (slide 4, part i)

Compute $\displaystyle\int_0^3\sin^2\left(\frac{2\pi x}{3}\right)dx$.

- A) $3$
- B) $\dfrac32$
- C) $0$
- D) $\dfrac34$

> [!success]- Answer
> **B.** $\sin^2\theta=\tfrac12(1-\cos2\theta)$ with $2\theta=\dfrac{4\pi x}{3}$:
> $\displaystyle\int_0^3\tfrac12\left(1-\cos\frac{4\pi x}{3}\right)dx=\tfrac12\left[x-\frac{3}{4\pi}\sin\frac{4\pi x}{3}\right]_0^3=\tfrac12(3-0)=\dfrac32$.
> This is the rule $\dfrac L2$ with $L=3$, $m=n=2$.
> - A: The factor $\tfrac12$ of the identity is dropped: $\int_0^3(1-\cos\cdots)\,dx=3$.
> - C: The rule for $m\neq n$ is used. Here the two sines are the same, $m=n=2$.
> - D: The factor $\tfrac12$ is used twice: $\tfrac12\cdot\tfrac12\cdot3$.

### Q11 (slide 4, part ii)

To compute $\displaystyle\int_0^2\sin\left(\frac{\pi x}{2}\right)\sin\left(\frac{3\pi x}{2}\right)dx$, rewrite the integrand with a product-to-sum identity. Which rewriting is correct?

- A) $\tfrac12\bigl[\cos(\pi x)-\cos(2\pi x)\bigr]$
- B) $\tfrac12\bigl[\cos(2\pi x)-\cos(\pi x)\bigr]$
- C) $\tfrac12\bigl[\cos(\pi x)+\cos(2\pi x)\bigr]$
- D) $\tfrac12\bigl[1-\cos(2\pi x)\bigr]$

> [!success]- Answer
> **A.** $\sin a\sin b=\tfrac12[\cos(a-b)-\cos(a+b)]$ with $a=\dfrac{\pi x}{2}$, $b=\dfrac{3\pi x}{2}$: $a-b=-\pi x$, $\cos(-\pi x)=\cos(\pi x)$, $a+b=2\pi x$.
> Then $\tfrac12\left[\dfrac1\pi\sin(\pi x)-\dfrac{1}{2\pi}\sin(2\pi x)\right]_0^2=0$. This is the rule for $m=1\neq n=3$.
> - B: $a-b$ and $a+b$ are swapped in the identity.
> - C: The identity for $\cos a\cos b$ (with $+$) is used.
> - D: The identity for $\sin^2\theta$ is used, as if the two sines were the same.

### Q12 (slide 4, use)

It is known that $5\sin(2x)-3\sin(7x)=\sum_{n=1}^{\infty}b_n\sin(nx)$ on $[0,\pi]$. Multiply by $\sin(2x)$ and integrate from $0$ to $\pi$. What is $b_2$?

- A) $5$
- B) $\dfrac{5\pi}{2}$
- C) $\dfrac{5\pi^2}{4}$
- D) $2$

> [!success]- Answer
> **A.** Left side: $5\int_0^\pi\sin^2(2x)\,dx-3\int_0^\pi\sin(7x)\sin(2x)\,dx=5\cdot\dfrac\pi2-3\cdot0=\dfrac{5\pi}{2}$.
> Right side: only $n=2$ stays, $b_2\cdot\dfrac\pi2$.
> So $b_2=\dfrac{5\pi/2}{\pi/2}=5$.
> - B: The left side is not divided by $\dfrac\pi2$.
> - C: Multiplied by $\dfrac\pi2$ in place of dividing.
> - D: The integral of $\sin(7x)\sin(2x)$ is also taken as $\dfrac\pi2$: $\left(\dfrac{5\pi}{2}-\dfrac{3\pi}{2}\right)\Big/\dfrac\pi2=2$.

## 4. Dirichlet problem for a rectangle: separation of variables (slides 5-7)

### Q13 (slide 5)

Consider $u_{xx}+u_{yy}=0$ in $0<x<3$, $0<y<5$ with $u(0,y)=0$, $u(3,y)=0$, $u(x,0)=0$ and $u(x,5)=f(x)$. Put $u=X(x)Y(y)$ and name the constant so that $\dfrac{X''}{X}=-\dfrac{Y''}{Y}=-\lambda$. Then $X''+\lambda X=0$ with $X(0)=0$, $X(3)=0$. Which ODE and which conditions does $Y$ get?

- A) $Y''+\lambda Y=0$; only $Y(0)=0$
- B) $Y''-\lambda Y=0$; only $Y(0)=0$
- C) $Y''-\lambda Y=0$; $Y(0)=0$ and $Y(5)=0$
- D) $Y''+\lambda Y=0$; $Y(0)=0$ and $Y(5)=0$

> [!success]- Answer
> **B.** $-\dfrac{Y''}{Y}=-\lambda$ gives $Y''=\lambda Y$, so $Y''-\lambda Y=0$.
> $u(x,0)=X(x)Y(0)=0$ for all $x$ gives $Y(0)=0$. The top condition $u(x,5)=f(x)$ is not zero, so it gives no condition on $Y$ alone. It is used at the end for the coefficients.
> - A: Sign slip: the minus sign in $-\dfrac{Y''}{Y}$ is lost.
> - C: The top edge is treated as a zero edge. $f$ is not zero.
> - D: $Y$ is treated like $X$: same ODE and two zero conditions. Both the sign and the top edge are wrong.

### Q14 (slide 6)

Same rectangle $0<x<3$, $0<y<5$ with $u=0$ on the left, right and bottom edges. Which product satisfies Laplace's equation and the three zero conditions for every $n=1,2,3,\dots$?

- A) $\sin\left(\dfrac{n\pi x}{3}\right)\sinh\left(\dfrac{n\pi y}{5}\right)$
- B) $\sin\left(\dfrac{n\pi x}{3}\right)\sinh\left(\dfrac{n\pi y}{3}\right)$
- C) $\sin\left(\dfrac{n\pi x}{3}\right)\cosh\left(\dfrac{n\pi y}{3}\right)$
- D) $\sin\left(\dfrac{n\pi x}{3}\right)\sin\left(\dfrac{n\pi y}{3}\right)$

> [!success]- Answer
> **B.** $X_n=\sin\dfrac{n\pi x}{3}$, $\lambda=\dfrac{n^2\pi^2}{9}$. $Y''-\dfrac{n^2\pi^2}{9}Y=0$ gives $Y=k_1\cosh\dfrac{n\pi y}{3}+k_2\sinh\dfrac{n\pi y}{3}$, and $Y(0)=k_1=0$.
> With $a=\dfrac{n\pi}{3}$: $u_{xx}=-a^2u$, $u_{yy}=a^2u$, sum $0$. $\sin0=0$, $\sin(n\pi)=0$, $\sinh0=0$.
> - A: The height $K=5$ is put inside the $\sinh$. Then $u_{xx}+u_{yy}=\left(\dfrac{n^2\pi^2}{25}-\dfrac{n^2\pi^2}{9}\right)u\neq0$.
> - C: $\sinh$ and $\cosh$ swapped: $\cosh0=1$, so $u(x,0)=\sin\dfrac{n\pi x}{3}\neq0$.
> - D: Wrong sign of the constant in $Y$: trig in place of hyperbolic. $u_{xx}+u_{yy}=-\dfrac{2n^2\pi^2}{9}u\neq0$.

### Q15 (slides 6-7, constant data)

Solve $u_{xx}+u_{yy}=0$ in $0<x<2$, $0<y<1$ with $u=0$ on the left, right and bottom edges and $u(x,1)=3$. Separation of variables gives a series with one term for each $n$, and the terms with even $n$ are zero. Which is the term for odd $n$?

- A) $\dfrac{6}{n\pi}\,\dfrac{\sinh(n\pi y/2)}{\sinh(n\pi/2)}\,\sin\dfrac{n\pi x}{2}$
- B) $\dfrac{12}{n\pi}\,\dfrac{\sinh(n\pi y)}{\sinh(n\pi)}\,\sin\dfrac{n\pi x}{2}$
- C) $\dfrac{12}{n\pi}\,\dfrac{\sinh(n\pi y/2)}{\sinh(n\pi/2)}\,\sin\dfrac{n\pi x}{2}$
- D) $\dfrac{6}{n\pi}\,\dfrac{\sinh(n\pi y)}{\sinh(n\pi)}\,\sin\dfrac{n\pi x}{2}$

> [!success]- Answer
> **C.** $X_n=\sin\dfrac{n\pi x}{2}$, $\lambda=\dfrac{n^2\pi^2}{4}$. $Y''-\dfrac{n^2\pi^2}{4}Y=0$ with $Y(0)=0$ gives $Y_n=\sinh\dfrac{n\pi y}{2}$. So $u=\sum c_n\sin\dfrac{n\pi x}{2}\sinh\dfrac{n\pi y}{2}$.
> At $y=1$: $3=\sum c_n\sinh\dfrac{n\pi}{2}\sin\dfrac{n\pi x}{2}$. Orthogonality on $[0,2]$: $c_n\sinh\dfrac{n\pi}{2}=\dfrac22\displaystyle\int_0^23\sin\frac{n\pi x}{2}\,dx=\frac{6}{n\pi}\bigl(1-(-1)^n\bigr)=\frac{12}{n\pi}$ for odd $n$.
> So the term is $\dfrac{12}{n\pi}\,\dfrac{\sinh(n\pi y/2)}{\sinh(n\pi/2)}\,\sin\dfrac{n\pi x}{2}$.
> - A: $\dfrac1L$ in place of $\dfrac2L$ in the coefficient formula. Then the series gives $\dfrac32$ on the top edge, not $3$.
> - B: The height $K=1$ is put inside the $\sinh$: $\sinh(n\pi y)$. It has the right top values, but $u_{xx}+u_{yy}=\left(n^2\pi^2-\dfrac{n^2\pi^2}{4}\right)\cdot(\text{term})\neq0$.
> - D: Both slips of A and B: $\dfrac1L$ in the coefficient and $K$ inside the $\sinh$.

### Q16 (slide 7, formula with $f(x)=x$)

For $0<x<1$, $0<y<2$ with $u=0$ on the left, right and bottom edges and $u(x,2)=x$, separation of variables gives a series with one term for each $n=1,2,3,\dots$ Which is the term with $\sin(n\pi x)$?

- A) $\dfrac{2(-1)^{n+1}}{n\pi}\,\dfrac{\sinh(n\pi y/2)}{\sinh(n\pi)}\,\sin(n\pi x)$
- B) $\dfrac{2(-1)^{n}}{n\pi}\,\dfrac{\sinh(n\pi y)}{\sinh(2n\pi)}\,\sin(n\pi x)$
- C) $\dfrac{2(-1)^{n}}{n\pi}\,\dfrac{\sinh(n\pi y/2)}{\sinh(n\pi)}\,\sin(n\pi x)$
- D) $\dfrac{2(-1)^{n+1}}{n\pi}\,\dfrac{\sinh(n\pi y)}{\sinh(2n\pi)}\,\sin(n\pi x)$

> [!success]- Answer
> **D.** $L=1$: $X_n=\sin(n\pi x)$, $Y_n=\sinh(n\pi y)$, and at $y=2$: $c_n\sinh(2n\pi)=\dfrac21\displaystyle\int_0^1x\sin(n\pi x)\,dx$.
> By parts: $\displaystyle\int_0^1x\sin(n\pi x)\,dx=\left[-\frac{x}{n\pi}\cos(n\pi x)\right]_0^1+\frac{1}{n\pi}\int_0^1\cos(n\pi x)\,dx=-\frac{(-1)^n}{n\pi}+0=\frac{(-1)^{n+1}}{n\pi}$.
> So $c_n=\dfrac{2(-1)^{n+1}}{n\pi\sinh(2n\pi)}$ and the term is $\dfrac{2(-1)^{n+1}}{n\pi}\,\dfrac{\sinh(n\pi y)}{\sinh(2n\pi)}\,\sin(n\pi x)$.
> - A: The height $K=2$ is put inside the $\sinh$: $\sinh\dfrac{n\pi y}{2}$. It has the right top values, but $u_{xx}+u_{yy}=\left(\dfrac{n^2\pi^2}{4}-n^2\pi^2\right)\cdot(\text{term})\neq0$.
> - B: Sign slip in the boundary term: $+\dfrac{(-1)^n}{n\pi}$ in place of $-\dfrac{(-1)^n}{n\pi}$. Then the top edge gets $-x$.
> - C: Both slips of A and B: the sign slip and $K$ inside the $\sinh$.

## 5. Example: data on the top edge (slides 7-9)

### Q17 (slides 7-9)

Solve $u_{xx}+u_{yy}=0$ in $0<x<2$, $0<y<3$ with $u(0,y)=0$, $u(2,y)=0$, $u(x,0)=0$ and $u(x,3)=4\sin(\pi x)-\sin\left(\dfrac{5\pi x}{2}\right)$. The solution has one term with $\sin(\pi x)$. Which is it?

- A) $\dfrac{4\sinh(\pi y)}{\sinh(3\pi)}\sin(\pi x)$
- B) $\dfrac{2\sinh(\pi y)}{\sinh(3\pi)}\sin(\pi x)$
- C) $\dfrac{4\sinh(2\pi y/3)}{\sinh(2\pi)}\sin(\pi x)$
- D) $\dfrac{2\sinh(2\pi y/3)}{\sinh(2\pi)}\sin(\pi x)$

> [!success]- Answer
> **A.** $L=2$: $X_n=\sin\dfrac{n\pi x}{2}$, $Y_n=\sinh\dfrac{n\pi y}{2}$. $\sin(\pi x)=\sin\dfrac{2\pi x}{2}$ is the term $n=2$, with $Y_2=\sinh(\pi y)$. At $y=3$ the factor is $\sinh(3\pi)$.
> Matching: $c_2\sinh(3\pi)=4$, so the term is $\dfrac{4\sinh(\pi y)}{\sinh(3\pi)}\sin(\pi x)$. (The other term: $-\dfrac{\sinh(5\pi y/2)}{\sinh(15\pi/2)}\sin\dfrac{5\pi x}{2}$.)
> - B: $\dfrac1L$ in place of $\dfrac2L$: $\dfrac12\cdot4\int_0^2\sin^2(\pi x)\,dx=2$. Then the top edge gets $2\sin(\pi x)$.
> - C: The height $K=3$ is put inside the $\sinh$: $\sinh\dfrac{2\pi y}{3}$. It has the right top values, but $u_{xx}+u_{yy}=\left(\dfrac{4\pi^2}{9}-\pi^2\right)\cdot(\text{term})\neq0$.
> - D: Both slips of B and C: $\dfrac1L$ in the coefficient and $K$ inside the $\sinh$.

### Q18 (slide 8, find the mistake)

Problem: $u_{xx}+u_{yy}=0$ in $0<x<\pi$, $0<y<2\pi$, $u(0,y)=u(\pi,y)=0$, $u(x,0)=0$, $u(x,2\pi)=\sin x+\sin(3x)$. A student writes $u=\sin x\sinh y+\sin(3x)\sinh(3y)$. What is true about this $u$?

- A) Laplace's equation fails, because $u_{yy}$ has the same sign as $u_{xx}$
- B) Only the top-edge condition fails: $u(x,2\pi)=\sinh(2\pi)\sin x+\sinh(6\pi)\sin(3x)$
- C) Only the bottom-edge condition fails: $u(x,0)=\sin x+\sin(3x)$, not $0$
- D) Everything holds: the equation and all four boundary conditions are satisfied

> [!success]- Answer
> **B.** Each term is $\sin(nx)\sinh(ny)$: $u_{xx}=-n^2(\cdot)$, $u_{yy}=+n^2(\cdot)$, sum $0$. $\sin0=\sin\pi=\sin3\pi=0$ and $\sinh0=0$, so the three zero edges hold.
> At $y=2\pi$: $\sinh(2\pi)\sin x+\sinh(6\pi)\sin(3x)\approx267.7\sin x+7.68\cdot10^{7}\sin(3x)$, not $\sin x+\sin(3x)$.
> The data coefficients are $c_n\sinh(2\pi n)$, so $c_1=\dfrac{1}{\sinh(2\pi)}$, $c_3=\dfrac{1}{\sinh(6\pi)}$.
> - A: $(\sinh t)''=+\sinh t$ while $(\sin t)''=-\sin t$. The signs are opposite and cancel.
> - C: $\sinh0=0$, not $1$. The bottom edge holds.
> - D: The student's reason: the data coefficients are 1 and 1. But at $y=2\pi$ each term is multiplied by $\sinh(2\pi n)$.

## 6. Example: data on the right edge (slides 9-11)

### Q19 (slides 9-11)

Solve $u_{xx}+u_{yy}=0$ in $0<x<2$, $0<y<\pi$ with $u(x,0)=0$, $u(x,\pi)=0$, $u(0,y)=0$ and $u(2,y)=3\sin(4y)$.

- A) $u=\dfrac{3}{2\sinh8}\sinh(4x)\sin(4y)$
- B) $u=\dfrac{3}{\sinh(4\pi)}\sinh(4x)\sin(4y)$
- C) $u=\dfrac{3}{\sinh8}\sinh(4x)\sin(4y)$
- D) $u=\dfrac{3}{\cosh8}\cosh(4x)\sin(4y)$

> [!success]- Answer
> **C.** Two zero conditions in $y$: $Y_n=\sin(ny)$, $\lambda=n^2$. $X''-n^2X=0$ with $X(0)=0$: $X_n=\sinh(nx)$.
> Right edge: $3\sin(4y)=\sum c_n\sinh(2n)\sin(ny)$, so only $n=4$: $c_4\sinh8=3$.
> Check: $u_{xx}=16u$, $u_{yy}=-16u$, sum $0$; $\sin0=\sin4\pi=0$, $\sinh0=0$; at $x=2$: $3\sin(4y)$.
> - A: $\dfrac1L$ in place of $\dfrac2L$ with $L=\pi$: $\dfrac1\pi\cdot3\cdot\dfrac\pi2=\dfrac32$. Then $u(2,y)=\dfrac32\sin(4y)$.
> - B: $X_4$ is evaluated at $x=\pi$ (the length in $y$) in place of the edge $x=2$. Then $u(2,y)\neq3\sin(4y)$.
> - D: $\sinh$ and $\cosh$ swapped: $\cosh0=1$, so $u(0,y)=\dfrac{3}{\cosh8}\sin(4y)\neq0$.

### Q20 (slide 10, data that is not a sum of sines)

Same rectangle $0<x<2$, $0<y<\pi$ and the same zero edges $u(x,0)=u(x,\pi)=u(0,y)=0$, but now $u(2,y)=y(\pi-y)$. To meet this condition, expand the data in a sine series on $[0,\pi]$: $y(\pi-y)=\sum_{n\ge1}b_n\sin(ny)$. Then $b_n=0$ for even $n$. What is $b_n$ for odd $n$?

- A) $\dfrac{8}{\pi n^3}$
- B) $\dfrac{4}{\pi n^3}$
- C) $\dfrac{8}{\pi n^2}$
- D) $-\dfrac{8}{\pi n^3}$

> [!success]- Answer
> **A.** $b_n=\dfrac{2}{\pi}\displaystyle\int_0^\pi(\pi y-y^2)\sin(ny)\,dy$.
> Two integrations by parts (both brackets are 0): $\displaystyle\int_0^\pi(\pi y-y^2)\sin(ny)\,dy=\frac1n\cdot\frac2n\int_0^\pi\sin(ny)\,dy=\frac{2}{n^2}\cdot\frac{1-(-1)^n}{n}=\frac{4}{n^3}$ for odd $n$.
> So $b_n=\dfrac2\pi\cdot\dfrac{4}{n^3}=\dfrac{8}{\pi n^3}$. In the solution $u=\sum c_n\sinh(nx)\sin(ny)$ this gives $c_n=\dfrac{b_n}{\sinh(2n)}$.
> - B: $\dfrac1L$ in place of $\dfrac2L$ with $L=\pi$.
> - C: One factor $\dfrac1n$ is lost: $\int_0^\pi\sin(ny)\,dy$ taken as $1-(-1)^n$ without the $\dfrac1n$.
> - D: Sign slip in the second integration by parts: $-\dfrac2n\int\sin(ny)\,dy$ in place of $+\dfrac2n\int\sin(ny)\,dy$.

## 7. Example: data on the left edge (slides 11-13)

### Q21 (slides 11-13)

Solve $u_{xx}+u_{yy}=0$ in $0<x<1$, $0<y<\pi$ with $u(x,0)=0$, $u(x,\pi)=0$, $u(1,y)=0$ and $u(0,y)=2\sin(3y)$.

- A) $u=\dfrac{2\sinh(3x)}{\sinh3}\sin(3y)$
- B) $u=\dfrac{2\cosh\bigl(3(1-x)\bigr)}{\cosh3}\sin(3y)$
- C) $u=\dfrac{2\sinh\bigl(3(1-x)\bigr)}{\sinh3}\sin(3y)$
- D) $u=\dfrac{2\sinh\bigl(3(x-1)\bigr)}{\sinh3}\sin(3y)$

> [!success]- Answer
> **C.** $Y_n=\sin(ny)$; only $n=3$ is in the data. $X''-9X=0$ with $X(1)=0$: $X$ is a multiple of $\sinh\bigl(3(1-x)\bigr)$, because $\sinh(3-3x)=\sinh3\cosh(3x)-\cosh3\sinh(3x)$.
> Check: $u_{xx}=9u$, $u_{yy}=-9u$, sum $0$. $x=1$: $\sinh0=0$. $x=0$: $\dfrac{2\sinh3}{\sinh3}\sin(3y)=2\sin(3y)$. $y=0,\pi$: $\sin0=\sin3\pi=0$.
> - A: The near-end form $\sinh(3x)$ is used. It is $0$ at $x=0$ and $2\sin(3y)$ at $x=1$: the two side edges are exchanged.
> - B: $\cosh$ in place of $\sinh$: at $x=1$, $u=\dfrac{2}{\cosh3}\sin(3y)\neq0$.
> - D: $\sinh\bigl(a(x-L)\bigr)$ in place of $\sinh\bigl(a(L-x)\bigr)$: at $x=0$, $u=-2\sin(3y)$.

### Q22 (slide 13)

Write $\bigl(\cosh(\pi x)-\coth(4\pi)\sinh(\pi x)\bigr)\sin(\pi y)$ with a single hyperbolic function. Use $\coth z=\dfrac{\cosh z}{\sinh z}$.

- A) $\dfrac{\sinh\bigl(\pi(x-4)\bigr)}{\sinh(4\pi)}\sin(\pi y)$
- B) $\sinh\bigl(\pi(4-x)\bigr)\sin(\pi y)$
- C) $\dfrac{\sinh\bigl(\pi(4+x)\bigr)}{\sinh(4\pi)}\sin(\pi y)$
- D) $\dfrac{\sinh\bigl(\pi(4-x)\bigr)}{\sinh(4\pi)}\sin(\pi y)$

> [!success]- Answer
> **D.** $\cosh(\pi x)-\dfrac{\cosh4\pi}{\sinh4\pi}\sinh(\pi x)=\dfrac{\sinh(4\pi)\cosh(\pi x)-\cosh(4\pi)\sinh(\pi x)}{\sinh4\pi}=\dfrac{\sinh(4\pi-\pi x)}{\sinh4\pi}$,
> by $\sinh(a-b)=\sinh a\cosh b-\cosh a\sinh b$.
> Check: $x=0$ gives $\sin(\pi y)$, $x=4$ gives $0$, and $y=0$, $y=2$ give $0$.
> - A: Sign slip in $\sinh(a-b)$: $\sinh(b-a)=-\sinh(a-b)$. At $x=0$ it gives $-\sin(\pi y)$.
> - B: The common denominator $\sinh(4\pi)$ is lost. At $x=0$ it gives $\sinh(4\pi)\sin(\pi y)$.
> - C: The formula for $\sinh(a+b)$ (with $+$) is used, but the numerator has a minus sign.

### Q23 (slide 13, two edges with data, beyond the slides)

Solve $u_{xx}+u_{yy}=0$ in $0<x<\pi$, $0<y<\pi$ with $u(0,y)=0$, $u(x,0)=0$, $u(x,\pi)=\sin x$ and $u(\pi,y)=2\sin(2y)$.

- A) $u=\dfrac{\sin x\sinh y}{\sinh\pi}+\dfrac{2\sinh\bigl(2(\pi-x)\bigr)\sin(2y)}{\sinh(2\pi)}$
- B) $u=\dfrac{\sin x\sinh y}{2\sinh\pi}+\dfrac{\sinh(2x)\sin(2y)}{\sinh(2\pi)}$
- C) $u=\dfrac{\sin x\sinh y}{\sinh\pi}+\dfrac{2\sinh(2x)\sin(2y)}{\sinh(2\pi)}$
- D) $u=\dfrac{\sin x\sinh y}{\sinh\pi}+\dfrac{2\sinh(2x)\sin(2y)}{\sinh\pi}$

> [!success]- Answer
> **C.** Split $u=u_A+u_B$. $u_A$: data $\sin x$ on top, zero elsewhere: $u_A=\dfrac{\sin x\sinh y}{\sinh\pi}$.
> $u_B$: data $2\sin(2y)$ on the right edge, zero elsewhere: $Y_n=\sin(ny)$, $X_n=\sinh(nx)$, $d_2\sinh(2\pi)=2$, so $u_B=\dfrac{2\sinh(2x)\sin(2y)}{\sinh(2\pi)}$.
> Check: at $y=\pi$, $u_A=\sin x$ and $u_B$ has $\sin2\pi=0$. At $x=\pi$, $u_A$ has $\sin\pi=0$ and $u_B=2\sin(2y)$. At $x=0$ and $y=0$ both parts are $0$.
> - A: In $u_B$ the far-end form $\sinh\bigl(2(\pi-x)\bigr)$ is used, as if the zero edge were $x=\pi$. Then $u(0,y)=2\sin(2y)\neq0$ and $u(\pi,y)=0$.
> - B: $\dfrac1L$ in place of $\dfrac2L$ with $L=\pi$ in both parts. Each data value comes out halved.
> - D: The factor $\sinh(n\pi)$ is taken with $n=1$ in $u_B$: $\sinh\pi$ in place of $\sinh(2\pi)$. Then $u(\pi,y)\neq2\sin(2y)$.
