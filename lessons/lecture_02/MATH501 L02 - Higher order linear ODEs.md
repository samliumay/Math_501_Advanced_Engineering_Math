---
course: MATH 501 Advanced Engineering Mathematics
lecture: 2
title: Higher order linear ODEs
tags: [math501, lecture]
slides: lectures/lecture_02/Math501 Chapter 2.pdf
full_notes: lecture_notes/lecture_02/MATH501_Lecture_02_Higher_Order_Linear_ODEs.pdf
---
# MATH 501 · Lecture 2 · Higher order linear ODEs

> [!summary] In short
> - Functions are linearly independent when only zero weights give the zero function. Two functions: check the ratio. More: use the Wronskian.
> - Linear homogeneous ODE: general solution $y=c_1y_1+c_2y_2$ with two independent solutions.
> - Constant coefficients: guess $e^{\lambda x}$, solve the characteristic equation, three cases (distinct, repeated, complex).
> - Non-homogeneous: $y=y_h+y_p$. Find $y_p$ by variation of parameters or by undetermined coefficients.
> - Euler's equation $x^2y''+Axy'+By=0$: guess $x^{\lambda}$, auxiliary equation $\lambda^2+(A-1)\lambda+B=0$.

The slide numbers below are the pages of the Chapter 2 PDF (page 1 is printed page 21).

## 1. Linear dependence, independence, Wronskian (slides 1-2)
![[math501_lecture_02_math501_chapter_2_p001.jpg]]
![[math501_lecture_02_math501_chapter_2_p002.jpg]]

**Notes.** $f_1,\dots,f_n$ are **linearly independent** on an interval $J$ if $c_1f_1+\dots+c_nf_n=0$ everywhere on $J$ forces $c_1=\dots=c_n=0$. Otherwise they are **dependent**.

Two functions are dependent exactly when they are proportional. So for two functions, look at the ratio: $e^x/e^{4x}=e^{-3x}$ is not constant, so independent.

The **Wronskian** of $f_1,\dots,f_n$ is the determinant whose rows are the functions, their first derivatives, up to the $(n-1)$-th derivatives. If $W(x_0)\neq0$ at one point $x_0$ of $J$, the functions are independent on $J$.

> [!example] Slide examples
> - $f=2\sin 2x$, $g=3\sin x\cos x$: $-3f+4g=0$, dependent.
> - $e^x$, $xe^x$: $W=e^x(e^x+xe^x)-xe^x\cdot e^x=e^{2x}\neq0$, independent.

> [!warning] Watch out
> - The ratio rule is for two functions only. $1$, $\sin^2x$, $\cos^2x$ are dependent although no two are proportional.
> - The Wronskian test works in one direction. $W=0$ everywhere does not prove dependence: $x$ and $|x|$ have $W=0$ but are independent on $\mathbb R$.

Section 2.2 starts at the bottom of slide 2.

> [!question]- Check (slide 1): Are $f_1=x+1$, $f_2=x-1$, $f_3=x$ linearly dependent or independent on $\mathbb R$? If they are dependent, give the constants.
> Set $c_1(x+1)+c_2(x-1)+c_3x=0$ for all $x$.
> Collect the powers of $x$: $(c_1+c_2+c_3)x+(c_1-c_2)=0$.
> A polynomial is zero for all $x$ only if every coefficient is zero: $c_1-c_2=0$ and $c_1+c_2+c_3=0$.
> First equation: $c_2=c_1$. Second equation: $c_3=-c_1-c_2=-2c_1$.
> Take $c_1=1$: $c_2=1$, $c_3=-2$. These are not all zero, so the functions are **dependent**.
> Check: $(x+1)+(x-1)-2x=2x-2x=0$.
> Remark: no two of the three functions are proportional. The ratio rule works for two functions only.

> [!question]- Check (slide 2, Wronskian): Compute the Wronskian of $f=x^2$ and $g=x^2\ln x$ on $x>0$. What do you conclude?
> Derivatives: $f'=2x$. Product rule: $g'=2x\ln x+x^2\cdot\tfrac1x=2x\ln x+x$.
> Wronskian (first row the functions, second row the derivatives):
> $$W=f\,g'-g\,f'=x^2(2x\ln x+x)-x^2\ln x\cdot 2x$$
> $$W=2x^3\ln x+x^3-2x^3\ln x=x^3 .$$
> At $x_0=1$: $W(1)=1\neq0$. By the theorem, $x^2$ and $x^2\ln x$ are **linearly independent** on $(0,\infty)$.
> (These two functions come back in "Check yourself" question 6 as the basis of an Euler equation with a repeated root.)

## 2. Second order linear ODEs: superposition and basis (slides 2-3)
![[math501_lecture_02_math501_chapter_2_p003.jpg]]

**Notes.** Standard form: $y''+P(x)y'+Q(x)y=R(x)$. Homogeneous if $R\equiv0$.

**Superposition principle.** For a linear homogeneous ODE, every linear combination of solutions is again a solution.

A **basis** (fundamental set) is a pair of linearly independent solutions $y_1,y_2$. Then every solution is

$$y=c_1y_1+c_2y_2 .$$

An IVP needs two conditions, $y(x_0)=\alpha$ and $y'(x_0)=\beta$. They fix $c_1$ and $c_2$.

> [!example] Slide example
> $y''+y=0$: $\cos x$ and $\sin x$ are solutions, and $\cos x/\sin x=\cot x$ is not constant. General solution: $y=c_1\cos x+c_2\sin x$.

> [!warning] Watch out
> Superposition fails for non-homogeneous and for nonlinear equations. Example: $\tfrac12x^2$ and $\tfrac12x^2+x$ both solve $y''=1$, but their sum has second derivative 2.

> [!question]- Check (slide 2, section 2.2): Classify each equation as linear or nonlinear. If it is linear, say homogeneous or non-homogeneous and read $P$, $Q$, $R$. (a) $y''+x^2y'-y=0$ (b) $y''+3y'+2y=\sin x$ (c) $y''+y\,y'=0$ (d) $xy''+y'=x^2$ for $x>0$.
> Compare each one with the standard form $y''+P(x)y'+Q(x)y=R(x)$. Linear means: $y$, $y'$, $y''$ appear only to the first power and are not multiplied with each other.
> (a) Linear. $P=x^2$, $Q=-1$, $R=0$. Since $R=0$ it is **homogeneous**. The coefficient $x^2$ depends on $x$ only, so it does not break linearity.
> (b) Linear. $P=3$, $Q=2$, $R=\sin x\neq0$. **Non-homogeneous**, with constant coefficients.
> (c) **Nonlinear**: the term $y\,y'$ is a product of $y$ and $y'$. Superposition does not hold.
> (d) Divide by $x$ to reach the standard form: $y''+\tfrac1x y'=x$. Linear, $P=\tfrac1x$, $Q=0$, $R=x\neq0$. **Non-homogeneous**.

> [!question]- Check (slide 3): Show that $y_1=\cosh x$ and $y_2=\sinh x$ form a basis of solutions of $y''-y=0$. Then solve the IVP $y(0)=2$, $y'(0)=-3$.
> Type: second order, linear, homogeneous.
> **Solutions.** $y_1=\cosh x$: $y_1'=\sinh x$, $y_1''=\cosh x$, so $y_1''-y_1=\cosh x-\cosh x=0$.
> $y_2=\sinh x$: $y_2'=\cosh x$, $y_2''=\sinh x$, so $y_2''-y_2=\sinh x-\sinh x=0$.
> **Independent.** $W=y_1y_2'-y_2y_1'=\cosh x\cdot\cosh x-\sinh x\cdot\sinh x=\cosh^2x-\sinh^2x=1\neq0$. So they form a basis.
> **General solution** (superposition): $y=c_1\cosh x+c_2\sinh x$, and $y'=c_1\sinh x+c_2\cosh x$.
> **Initial conditions.** $\cosh0=1$, $\sinh0=0$. $y(0)=c_1=2$. $y'(0)=c_2=-3$.
> **Answer:** $y=2\cosh x-3\sinh x$.
> Check: $y''=2\cosh x-3\sinh x=y$, so $y''-y=0$. $y(0)=2$, $y'(0)=-3$.
> In exponentials: $y=2\cdot\tfrac{e^x+e^{-x}}2-3\cdot\tfrac{e^x-e^{-x}}2=-\tfrac12e^x+\tfrac52e^{-x}$. The basis $e^x$, $e^{-x}$ gives the same solution: a basis is not unique.

## 3. Constant coefficients, second order (slides 3-7)
![[math501_lecture_02_math501_chapter_2_p004.jpg]]
![[math501_lecture_02_math501_chapter_2_p005.jpg]]
![[math501_lecture_02_math501_chapter_2_p006.jpg]]
![[math501_lecture_02_math501_chapter_2_p007.jpg]]

**Notes.** For $y''+ay'+by=0$ try $y=e^{\lambda x}$. Since $e^{\lambda x}\neq0$, $\lambda$ must solve the **characteristic equation**

$$\lambda^2+a\lambda+b=0 .$$

| Case | Roots | General solution |
|---|---|---|
| $a^2-4b>0$ | $\lambda_1\neq\lambda_2$ real | $y=c_1e^{\lambda_1x}+c_2e^{\lambda_2x}$ |
| $a^2-4b=0$ | $\lambda=-a/2$ repeated | $y=c_1e^{\lambda x}+c_2xe^{\lambda x}$ |
| $a^2-4b<0$ | $\alpha\pm i\beta$ | $y=c_1e^{\alpha x}\cos\beta x+c_2e^{\alpha x}\sin\beta x$ |

Repeated root: the second solution comes from **reduction of order**. Put $y_2=u(x)y_1$. Substituting gives $u''=0$, so $u=x$ works and $y_2=xy_1$.

Complex roots: $\alpha=-a/2$, $\beta=\tfrac12\sqrt{4b-a^2}$. Euler's formula $e^{i\theta}=\cos\theta+i\sin\theta$ turns $e^{(\alpha\pm i\beta)x}$ into the two real solutions.

> [!example] Slide examples
> - $y''+y'-2y=0$: $(\lambda+2)(\lambda-1)=0$, $y=c_1e^{-2x}+c_2e^{x}$.
> - Basis $e^{4x},e^{-4x}$: $(\lambda-4)(\lambda+4)=0$, so the ODE is $y''-16y=0$.
> - $y''+2\pi y'+\pi^2y=0$, $y(0)=1$, $y'(0)=2\pi$: $\lambda=-\pi$ repeated, $c_1=1$, $c_2=3\pi$, $y=e^{-\pi x}+3\pi xe^{-\pi x}$.
> - $y''+2y'+2y=0$: $\lambda=-1\pm i$, $y=c_1e^{-x}\cos x+c_2e^{-x}\sin x$.
> - $y''+4y=0$, $y(0)=0$, $y'(0)=1$: $\lambda=\pm2i$, $y=\tfrac12\sin 2x$.

> [!question]- Check (slide 4): Solve the IVP $y''-y'-6y=0$, $y(0)=1$, $y'(0)=8$.
> Type: second order, linear, homogeneous, constant coefficients. Method: characteristic equation.
> **Characteristic equation.** $\lambda^2-\lambda-6=0$. Discriminant: $(-1)^2-4(1)(-6)=25>0$, so two distinct real roots.
> $\lambda=\dfrac{1\pm\sqrt{25}}{2}=\dfrac{1\pm5}{2}$, so $\lambda_1=3$, $\lambda_2=-2$. (Factored: $(\lambda-3)(\lambda+2)=0$.)
> **General solution.** $y=c_1e^{3x}+c_2e^{-2x}$, and $y'=3c_1e^{3x}-2c_2e^{-2x}$.
> **Initial conditions.** $y(0)=c_1+c_2=1$. $y'(0)=3c_1-2c_2=8$.
> From the first: $c_2=1-c_1$. Into the second: $3c_1-2(1-c_1)=8$, so $5c_1-2=8$, $c_1=2$. Then $c_2=1-2=-1$.
> **Answer:** $y=2e^{3x}-e^{-2x}$.
> Check: $y'=6e^{3x}+2e^{-2x}$, $y''=18e^{3x}-4e^{-2x}$.
> $y''-y'-6y=(18-6-12)e^{3x}+(-4-2+6)e^{-2x}=0$. $y(0)=2-1=1$. $y'(0)=6+2=8$.

> [!question]- Check (slide 5, reduction of order): $y_1=e^{2x}$ solves $y''-4y'+4y=0$. Use reduction of order to find a second independent solution.
> Set $y_2=u(x)e^{2x}$.
> Product rule: $y_2'=u'e^{2x}+2ue^{2x}$.
> Again: $y_2''=u''e^{2x}+2u'e^{2x}+2u'e^{2x}+4ue^{2x}=u''e^{2x}+4u'e^{2x}+4ue^{2x}$.
> Substitute into $y''-4y'+4y=0$:
> $$\left(u''+4u'+4u\right)e^{2x}-4\left(u'+2u\right)e^{2x}+4ue^{2x}=0$$
> $$\left(u''+(4-4)u'+(4-8+4)u\right)e^{2x}=0\quad\Rightarrow\quad u''e^{2x}=0 .$$
> Since $e^{2x}\neq0$: $u''=0$. Integrate twice: $u'=c$, $u=cx+d$. Choose $c=1$, $d=0$: $u=x$.
> **Second solution:** $y_2=xe^{2x}$.
> Independence: $W=e^{2x}\left(e^{2x}+2xe^{2x}\right)-xe^{2x}\cdot2e^{2x}=e^{4x}\neq0$.
> Why $u'$ and $u$ disappear: $\lambda=2$ is a double root, so both $\lambda^2-4\lambda+4$ and its derivative $2\lambda-4$ are zero at $\lambda=2$.

> [!question]- Check (slides 5-6, repeated root example): Solve the IVP $4y''+4y'+y=0$, $y(0)=2$, $y'(0)=1$.
> Type: second order, linear, homogeneous, constant coefficients. Method: characteristic equation.
> **Characteristic equation.** $4\lambda^2+4\lambda+1=0$. Discriminant: $4^2-4\cdot4\cdot1=0$, so one repeated root.
> $(2\lambda+1)^2=0$, $\lambda=-\tfrac12$ (double).
> **General solution.** $y=c_1e^{-x/2}+c_2xe^{-x/2}$.
> Derivative (product rule on the second term): $y'=-\tfrac12c_1e^{-x/2}+c_2\left(e^{-x/2}-\tfrac12xe^{-x/2}\right)$.
> **Initial conditions.** $y(0)=c_1=2$. $y'(0)=-\tfrac12c_1+c_2=1$, so $-1+c_2=1$, $c_2=2$.
> **Answer:** $y=2e^{-x/2}+2xe^{-x/2}=(2+2x)e^{-x/2}$.
> Check: $y'=2e^{-x/2}-\tfrac12(2+2x)e^{-x/2}=(1-x)e^{-x/2}$.
> $y''=-e^{-x/2}-\tfrac12(1-x)e^{-x/2}=\left(-\tfrac32+\tfrac x2\right)e^{-x/2}$.
> $4y''+4y'+y=\left(-6+2x+4-4x+2+2x\right)e^{-x/2}=0$. $y(0)=2$. $y'(0)=1$.

> [!question]- Check (slide 6, complex roots): Solve the IVP $y''-4y'+13y=0$, $y(0)=1$, $y'(0)=8$.
> Type: second order, linear, homogeneous, constant coefficients. Method: characteristic equation.
> **Characteristic equation.** $\lambda^2-4\lambda+13=0$. Discriminant: $(-4)^2-4\cdot13=16-52=-36<0$, so complex roots.
> $\lambda=\dfrac{4\pm\sqrt{-36}}{2}=\dfrac{4\pm6i}{2}=2\pm3i$. So $\alpha=2$, $\beta=3$.
> **General solution.** $y=e^{2x}\left(c_1\cos3x+c_2\sin3x\right)$.
> Derivative (product rule): $y'=2e^{2x}\left(c_1\cos3x+c_2\sin3x\right)+e^{2x}\left(-3c_1\sin3x+3c_2\cos3x\right)$.
> **Initial conditions.** $y(0)=c_1=1$. $y'(0)=2c_1+3c_2=8$, so $3c_2=6$, $c_2=2$.
> **Answer:** $y=e^{2x}\left(\cos3x+2\sin3x\right)$.
> Check: $y'=e^{2x}\left[(2+6)\cos3x+(4-3)\sin3x\right]=e^{2x}(8\cos3x+\sin3x)$.
> $y''=2e^{2x}(8\cos3x+\sin3x)+e^{2x}(-24\sin3x+3\cos3x)=e^{2x}(19\cos3x-22\sin3x)$.
> $y''-4y'+13y$: $\cos3x$ terms $19-32+13=0$, $\sin3x$ terms $-22-4+26=0$. $y(0)=1$, $y'(0)=8$.

> [!question]- Check (slide 7): Solve the IVP $y''+9y=0$, $y(0)=3$, $y'(0)=-6$. Does the solution grow, decay, or neither?
> Type: second order, linear, homogeneous, constant coefficients. Method: characteristic equation.
> **Characteristic equation.** $\lambda^2+9=0$, $\lambda^2=-9$, $\lambda=\pm3i$. So $\alpha=0$, $\beta=3$.
> **General solution.** $y=c_1\cos3x+c_2\sin3x$ (because $e^{0x}=1$). Derivative: $y'=-3c_1\sin3x+3c_2\cos3x$.
> **Initial conditions.** $y(0)=c_1=3$. $y'(0)=3c_2=-6$, so $c_2=-2$.
> **Answer:** $y=3\cos3x-2\sin3x$.
> Check: $y''=-27\cos3x+18\sin3x=-9(3\cos3x-2\sin3x)=-9y$, so $y''+9y=0$. $y(0)=3$. $y'(0)=3(-2)=-6$.
> The real part of the roots is $\alpha=0$, so there is no factor $e^{\alpha x}$. The solution oscillates forever with constant amplitude $\sqrt{3^2+2^2}=\sqrt{13}$. It neither grows nor decays.

## 4. Constant coefficients, order n (slides 7-9)
![[math501_lecture_02_math501_chapter_2_p008.jpg]]
![[math501_lecture_02_math501_chapter_2_p009.jpg]]

**Notes.** For $a_ny^{(n)}+\dots+a_1y'+a_0y=0$ the characteristic equation is the degree $n$ polynomial $a_n\lambda^n+\dots+a_1\lambda+a_0=0$. Section 2.4 starts at the bottom of slide 7.

- Real distinct roots: one $e^{\lambda_jx}$ for each root.
- Real root $\gamma$ of multiplicity $k$: $e^{\gamma x},\,xe^{\gamma x},\dots,x^{k-1}e^{\gamma x}$.
- Complex pair $\alpha\pm i\beta$ of multiplicity $k$: $x^je^{\alpha x}\cos\beta x$ and $x^je^{\alpha x}\sin\beta x$ for $j=0,\dots,k-1$.

The number of solutions written down must equal the order $n$.

> [!example] Slide examples
> - $y'''+3y''-4y'=0$, $y(0)=1$, $y'(0)=2$, $y''(0)=-1$: $\lambda(\lambda+4)(\lambda-1)=0$, $y=c_1+c_2e^{-4x}+c_3e^{x}$. Answer: $y=-\tfrac14-\tfrac{3}{20}e^{-4x}+\tfrac75e^{x}$.
> - $y^{(4)}+2y''+y=0$: $(\lambda^2+1)^2=0$, $\pm i$ with multiplicity 2. $y=c_1\cos x+c_2\sin x+c_3x\cos x+c_4x\sin x$.

Section 2.5 starts at the bottom of slide 9: for $y''+Py'+Qy=R$ the general solution is

$$y=y_h+y_p,\qquad y_h=c_1y_1+c_2y_2,$$

where $y_p$ is any one particular solution.

> [!info] How to factor a cubic characteristic polynomial (beyond the slides)
> The slide example factors easily because $\lambda$ is a common factor. In general:
> 1. Guess one root. If the coefficients are integers and the leading coefficient is 1, every integer root divides the constant term. Try $\pm1,\pm2,\dots$
> 2. If $\lambda=r$ is a root, divide the polynomial by $(\lambda-r)$. The quotient is a quadratic.
> 3. Solve the quadratic with the usual formula.
>
> A real cubic always has at least one real root, because complex roots come in conjugate pairs.

> [!question]- Check (slide 8): Solve the IVP $y'''-3y'+2y=0$, $y(0)=2$, $y'(0)=0$, $y''(0)=7$.
> Type: third order, linear, homogeneous, constant coefficients. Method: characteristic equation of degree 3.
> **Characteristic equation.** $\lambda^3-3\lambda+2=0$ (there is no $y''$ term, so no $\lambda^2$ term).
> Guess a root among the divisors of 2. $\lambda=1$: $1-3+2=0$. So $(\lambda-1)$ is a factor.
> Divide: $\lambda^3-3\lambda+2=(\lambda-1)(\lambda^2+\lambda-2)$. Check by expanding: $\lambda^3+\lambda^2-2\lambda-\lambda^2-\lambda+2=\lambda^3-3\lambda+2$.
> Quadratic: $\lambda^2+\lambda-2=(\lambda-1)(\lambda+2)$.
> So $(\lambda-1)^2(\lambda+2)=0$: $\lambda=1$ with multiplicity 2, and $\lambda=-2$.
> **General solution.** The double root gives $e^x$ and $xe^x$: $y=c_1e^x+c_2xe^x+c_3e^{-2x}$.
> **Derivatives.** $y'=c_1e^x+c_2(e^x+xe^x)-2c_3e^{-2x}$.
> $y''=c_1e^x+c_2(2e^x+xe^x)+4c_3e^{-2x}$.
> **Initial conditions** (put $x=0$):
> $$c_1+c_3=2,\qquad c_1+c_2-2c_3=0,\qquad c_1+2c_2+4c_3=7 .$$
> From the first: $c_1=2-c_3$.
> Into the second: $2-c_3+c_2-2c_3=0$, so $c_2=3c_3-2$.
> Into the third: $(2-c_3)+2(3c_3-2)+4c_3=7$, so $9c_3-2=7$, $c_3=1$.
> Then $c_2=3-2=1$ and $c_1=2-1=1$.
> **Answer:** $y=e^x+xe^x+e^{-2x}$.
> Check: $y'=2e^x+xe^x-2e^{-2x}$, $y''=3e^x+xe^x+4e^{-2x}$, $y'''=4e^x+xe^x-8e^{-2x}$.
> $y'''-3y'+2y$: $e^x$ terms $4-6+2=0$, $xe^x$ terms $1-3+2=0$, $e^{-2x}$ terms $-8+6+2=0$.
> $y(0)=1+0+1=2$. $y'(0)=2-2=0$. $y''(0)=3+4=7$.

> [!question]- Check (slide 9, fourth order): Find the general solution of $y^{(4)}+8y''+16y=0$.
> Type: fourth order, linear, homogeneous, constant coefficients.
> **Characteristic equation.** $\lambda^4+8\lambda^2+16=0$. Put $s=\lambda^2$: $s^2+8s+16=(s+4)^2=0$.
> So $(\lambda^2+4)^2=0$, $\lambda^2=-4$, $\lambda=\pm2i$, each with multiplicity 2.
> Complex pair $\alpha\pm i\beta$ with $\alpha=0$, $\beta=2$, $k=2$. The solutions are $x^j\cos2x$ and $x^j\sin2x$ for $j=0,1$.
> **Answer:** $y=c_1\cos2x+c_2\sin2x+c_3x\cos2x+c_4x\sin2x$.
> Count: four constants for a fourth order equation.
> Check for one new term, $y=x\cos2x$: $y''=-4\sin2x-4x\cos2x$, $y^{(4)}=32\sin2x+16x\cos2x$.
> $y^{(4)}+8y''+16y=(32-32)\sin2x+(16-32+16)x\cos2x=0$.

> [!question]- Check (slide 9, section 2.5): Show that $y_p=2x$ is a particular solution of $y''+4y=8x$. Then solve the IVP $y(0)=1$, $y'(0)=0$.
> Type: second order, linear, non-homogeneous ($R=8x$), constant coefficients. Method: $y=y_h+y_p$.
> **Particular solution.** $y_p=2x$, $y_p'=2$, $y_p''=0$. Then $y_p''+4y_p=0+8x=8x$. It works.
> **Homogeneous part.** $\lambda^2+4=0$, $\lambda=\pm2i$, $y_h=c_1\cos2x+c_2\sin2x$.
> **General solution.** $y=c_1\cos2x+c_2\sin2x+2x$, and $y'=-2c_1\sin2x+2c_2\cos2x+2$.
> **Initial conditions.** Apply them to the full $y=y_h+y_p$, not to $y_h$ alone.
> $y(0)=c_1=1$. $y'(0)=2c_2+2=0$, so $c_2=-1$.
> **Answer:** $y=\cos2x-\sin2x+2x$.
> Check: $y''=-4\cos2x+4\sin2x$. $y''+4y=(-4+4)\cos2x+(4-4)\sin2x+8x=8x$. $y(0)=1$. $y'(0)=-2+2=0$.

## 5. Variation of parameters (slides 10-12)
![[math501_lecture_02_math501_chapter_2_p010.jpg]]
![[math501_lecture_02_math501_chapter_2_p011.jpg]]
![[math501_lecture_02_math501_chapter_2_p012.jpg]]

**Notes.** Look for $y_p=u_1(x)y_1+u_2(x)y_2$, where $y_1,y_2$ is a basis of the homogeneous equation. Impose $u_1'y_1+u_2'y_2=0$. Substituting into the ODE gives $u_1'y_1'+u_2'y_2'=R$. Solving the two equations:

$$u_1=-\int\frac{y_2R}{W(y_1,y_2)}\,dx,\qquad u_2=\int\frac{y_1R}{W(y_1,y_2)}\,dx .$$

Take the integration constants equal to zero. The method works for any continuous $R$.

> [!example] Slide examples
> - $y''+9y=\sec 3x$: $y_1=\cos3x$, $y_2=\sin3x$, $W=3$. $u_1=\tfrac19\ln|\cos3x|$, $u_2=\tfrac x3$. Answer: $y=c_1\cos3x+c_2\sin3x+\tfrac19\cos3x\,\ln|\cos3x|+\tfrac13x\sin3x$.
> - $4y''-12y'+9y=2e^{3x/2}$: divide by 4 first, $R=\tfrac12e^{3x/2}$. $y_1=e^{3x/2}$, $y_2=xe^{3x/2}$, $W=e^{3x}$, $u_1=-\tfrac{x^2}{4}$, $u_2=\tfrac x2$, $y_p=\tfrac14x^2e^{3x/2}$.

> [!warning] Watch out
> Put the equation in standard form first (coefficient of $y''$ equal to 1), then read $R$. $u_1$ has the minus sign.

> [!info] The steps that slide 10 skips
> **Why the terms with $u_1$, $u_2$ vanish.** After substituting, the equation groups as $u_1(y_1''+Py_1'+Qy_1)+u_2(y_2''+Py_2'+Qy_2)+u_1'y_1'+u_2'y_2'=R$. The two brackets are zero because $y_1$ and $y_2$ solve the homogeneous equation.
>
> **Why we may impose $u_1'y_1+u_2'y_2=0$.** There are two unknown functions but only one equation (the ODE). So one extra condition is free to choose. This choice removes $u_1''$ and $u_2''$ from $y_p''$.
>
> **Solving the system.** The slide says only "we obtain". The system is
> $$u_1'y_1+u_2'y_2=0,\qquad u_1'y_1'+u_2'y_2'=R .$$
> Multiply the first equation by $y_2'$ and the second by $y_2$, then subtract:
> $$u_1'\left(y_1y_2'-y_1'y_2\right)=-y_2R\quad\Rightarrow\quad u_1'=\frac{-y_2R}{W} .$$
> Multiply the first equation by $y_1'$ and the second by $y_1$, then subtract the first from the second:
> $$u_2'\left(y_1y_2'-y_1'y_2\right)=y_1R\quad\Rightarrow\quad u_2'=\frac{y_1R}{W} .$$
> Here $W=y_1y_2'-y_1'y_2$ is the Wronskian. It is not zero because $y_1,y_2$ is a basis, so the division is allowed.

> [!warning] Slide error
> Slide 10 says "Solving the system of equations (2.5a) and (2.5b)". The system is (2.7a) and (2.7b), the two equations directly above that line.

> [!question]- Check (slide 10): For $y''-3y'+2y=e^{3x}$ with $y_1=e^x$, $y_2=e^{2x}$, write the system (2.7a), (2.7b) and solve it by elimination. Then find $y_p$.
> Type: second order, linear, non-homogeneous, constant coefficients, already in standard form. $R=e^{3x}$.
> Basis check: $\lambda^2-3\lambda+2=(\lambda-1)(\lambda-2)=0$, so $e^x$ and $e^{2x}$ are correct.
> Derivatives: $y_1'=e^x$, $y_2'=2e^{2x}$.
> **System.**
> $$u_1'e^x+u_2'e^{2x}=0,\qquad u_1'e^x+2u_2'e^{2x}=e^{3x} .$$
> Subtract the first from the second: $u_2'e^{2x}=e^{3x}$, so $u_2'=e^x$.
> Into the first: $u_1'e^x=-e^x\cdot e^{2x}$, so $u_1'=-e^{2x}$.
> **Integrate** (constants zero): $u_1=-\tfrac12e^{2x}$, $u_2=e^x$.
> **Particular solution.** $y_p=u_1y_1+u_2y_2=-\tfrac12e^{2x}e^x+e^xe^{2x}=-\tfrac12e^{3x}+e^{3x}=\tfrac12e^{3x}$.
> Same result from the formulas: $W=e^x\cdot2e^{2x}-e^{2x}\cdot e^x=e^{3x}$, $u_1'=-\dfrac{e^{2x}e^{3x}}{e^{3x}}=-e^{2x}$, $u_2'=\dfrac{e^xe^{3x}}{e^{3x}}=e^x$.
> Check: $y_p'=\tfrac32e^{3x}$, $y_p''=\tfrac92e^{3x}$. $y_p''-3y_p'+2y_p=\left(\tfrac92-\tfrac92+1\right)e^{3x}=e^{3x}$.
> General solution: $y=c_1e^x+c_2e^{2x}+\tfrac12e^{3x}$.

> [!question]- Check (slide 11): Find the general solution of $y''+y=\tan x$ on $-\tfrac\pi2<x<\tfrac\pi2$.
> Type: second order, linear, non-homogeneous, constant coefficients. $R=\tan x$ is not a polynomial, exponential, sine or cosine, so undetermined coefficients does not apply. Method: variation of parameters.
> **Homogeneous part.** $\lambda^2+1=0$, $\lambda=\pm i$. $y_1=\cos x$, $y_2=\sin x$, $y_h=c_1\cos x+c_2\sin x$.
> **Wronskian.** $W=\cos x\cdot\cos x-\sin x\cdot(-\sin x)=\cos^2x+\sin^2x=1$.
> **$u_1$.**
> $$u_1=-\int\frac{y_2R}{W}\,dx=-\int\sin x\tan x\,dx=-\int\frac{\sin^2x}{\cos x}\,dx=-\int\frac{1-\cos^2x}{\cos x}\,dx$$
> $$u_1=-\int\left(\sec x-\cos x\right)dx=-\ln\lvert\sec x+\tan x\rvert+\sin x .$$
> **$u_2$.**
> $$u_2=\int\frac{y_1R}{W}\,dx=\int\cos x\tan x\,dx=\int\sin x\,dx=-\cos x .$$
> **Particular solution.**
> $$y_p=u_1y_1+u_2y_2=-\cos x\ln\lvert\sec x+\tan x\rvert+\sin x\cos x-\cos x\sin x=-\cos x\ln\lvert\sec x+\tan x\rvert .$$
> **Answer:** $y=c_1\cos x+c_2\sin x-\cos x\,\ln\lvert\sec x+\tan x\rvert$.
> Check: put $L=\ln(\sec x+\tan x)$. Then $L'=\dfrac{\sec x\tan x+\sec^2x}{\sec x+\tan x}=\sec x$.
> $y_p=-L\cos x$. $y_p'=L\sin x-\sec x\cos x=L\sin x-1$. $y_p''=L\cos x+\sec x\sin x=L\cos x+\tan x$.
> $y_p''+y_p=L\cos x+\tan x-L\cos x=\tan x$.

> [!question]- Check (slide 12): Find the general solution of $2y''-4y'+2y=\dfrac{2e^x}{x}$ for $x>0$.
> Type: second order, linear, non-homogeneous, constant coefficients. $R$ contains $\tfrac1x$, so the table of undetermined coefficients does not apply. Method: variation of parameters.
> **Standard form first.** Divide by 2: $y''-2y'+y=\dfrac{e^x}{x}$. So $R=\dfrac{e^x}{x}$ (not $\dfrac{2e^x}{x}$).
> **Homogeneous part.** $\lambda^2-2\lambda+1=(\lambda-1)^2=0$, repeated root $\lambda=1$. $y_1=e^x$, $y_2=xe^x$.
> **Wronskian.** $y_1'=e^x$, $y_2'=e^x+xe^x$. $W=e^x(e^x+xe^x)-xe^x\cdot e^x=e^{2x}$.
> **$u_1$.** $u_1=-\displaystyle\int\frac{xe^x\cdot\frac{e^x}{x}}{e^{2x}}\,dx=-\int1\,dx=-x$.
> **$u_2$.** $u_2=\displaystyle\int\frac{e^x\cdot\frac{e^x}{x}}{e^{2x}}\,dx=\int\frac1x\,dx=\ln x$.
> **Particular solution.** $y_p=u_1y_1+u_2y_2=-xe^x+xe^x\ln x$.
> The term $-xe^x$ is a multiple of $y_2$. It can be absorbed into $c_2xe^x$.
> **Answer:** $y=c_1e^x+c_2xe^x+xe^x\ln x$.
> Check with $y=xe^x\ln x$: $y'=e^x\ln x+xe^x\ln x+e^x$.
> $y''=e^x\ln x+\tfrac{e^x}{x}+e^x\ln x+xe^x\ln x+e^x+e^x=2e^x\ln x+xe^x\ln x+2e^x+\tfrac{e^x}{x}$.
> $y''-2y'+y=(2-2)e^x\ln x+(1-2+1)xe^x\ln x+(2-2)e^x+\tfrac{e^x}{x}=\tfrac{e^x}{x}$.

## 6. Undetermined coefficients (slides 13-18)
![[math501_lecture_02_math501_chapter_2_p013.jpg]]
![[math501_lecture_02_math501_chapter_2_p014.jpg]]
![[math501_lecture_02_math501_chapter_2_p015.jpg]]
![[math501_lecture_02_math501_chapter_2_p016.jpg]]
![[math501_lecture_02_math501_chapter_2_p017.jpg]]

**Notes.** For $y''+ay'+by=R(x)$ with constant $a,b$ and $R$ made of polynomials, exponentials, sines and cosines. Guess $y_p$ with the same shape as $R$ and unknown coefficients.

| Term in $R(x)$ | First choice for $y_p$ |
|---|---|
| polynomial of degree $n$ | $A_nx^n+\dots+A_1x+A_0$ |
| $Ae^{\alpha x}$ | $Ke^{\alpha x}$ |
| $A\cos\beta x$ or $A\sin\beta x$ | $C\cos\beta x+D\sin\beta x$ |
| polynomial times $e^{\alpha x}$ | (full polynomial) $e^{\alpha x}$ |
| polynomial times $\cos\beta x$ or $\sin\beta x$ | (polynomial)$\cos\beta x$ + (polynomial)$\sin\beta x$ |

Steps: (1) solve the homogeneous equation, (2) take the first choice, one term of $R$ at a time, (3) **modification rule**: if a term of the choice already solves the homogeneous equation, multiply the choice by $x$ (single root) or by $x^2$ (double root), (4) substitute and compare coefficients, (5) $y=y_h+y_p$.

For a sum $R=f_1+\dots+f_N$, find a $y_{p_j}$ for each $f_j$ and add them.

> [!example] Slide examples
> - $y''+y'+y=2x+1$: $y_p=Ax+B$, $A=2$, $A+B=1$, $y_p=2x-1$.
> - $y''-2y'-3y=\dots$ with $y_h=c_1e^{3x}+c_2e^{-x}$:
>   - $2e^{3x}$: $e^{3x}$ is in $y_h$ (single root), so $y_p=Axe^{3x}$, $A=\tfrac12$.
>   - $x^2$: $y_p=Ax^2+Bx+C=-\tfrac13x^2+\tfrac49x-\tfrac{14}{27}$.
>   - $3\sin x$: $y_p=A\cos x+B\sin x=\tfrac{3}{10}\cos x-\tfrac35\sin x$.
>   - Sum of the three right sides: add the three $y_p$.

> [!warning] Watch out
> - For a sine or a cosine, always guess both $\cos$ and $\sin$.
> - For a polynomial of degree $n$, guess all powers down to the constant.
> - Check the modification rule before substituting.
> - For $\sec 3x$, $\tan x$, $\ln x$ and similar right sides use variation of parameters.

> [!info] Why the modification rule is needed (beyond the slides)
> Take slide 15, part b: $y''-2y'-3y=2e^{3x}$. Try the first choice $y_p=Ae^{3x}$ without the rule.
> $y_p'=3Ae^{3x}$, $y_p''=9Ae^{3x}$. Then $y_p''-2y_p'-3y_p=(9-6-3)Ae^{3x}=0$.
> The left side is zero for every $A$, because $e^{3x}$ solves the homogeneous equation. So $0=2e^{3x}$, which is impossible. No value of $A$ works.
> With the extra factor $x$, the product rule produces terms without $x$ that do not cancel ($4Ae^{3x}$ on the slide). These can match the right side.
> For a double root, $xe^{\lambda x}$ also solves the homogeneous equation, so one factor $x$ is not enough. Use $x^2$.

> [!question]- Check (slide 13): Write the correct form of $y_p$ (do not find the coefficients). For $y''-3y'+2y=R(x)$: (a) $R=xe^{3x}$ (b) $R=5e^{2x}$ (c) $R=x^2+\cos x$. For $y''-4y'+4y=R(x)$: (d) $R=e^{2x}$.
> Step 1 for (a), (b), (c): $\lambda^2-3\lambda+2=(\lambda-1)(\lambda-2)=0$, so $y_h=c_1e^x+c_2e^{2x}$.
> (a) Table row $p(x)e^{\alpha x}$ with degree 1: $y_p=(A_1x+A_0)e^{3x}$. $e^{3x}$ and $xe^{3x}$ are not in $y_h$, so no change.
> (b) First choice $Ke^{2x}$. But $e^{2x}$ is in $y_h$, and $\lambda=2$ is a single root. Multiply by $x$: $y_p=Kxe^{2x}$.
> (c) Two terms, treat them one at a time (superposition). For $x^2$: $A_2x^2+A_1x+A_0$. For $\cos x$: $C\cos x+D\sin x$. Nothing is in $y_h$. $y_p=A_2x^2+A_1x+A_0+C\cos x+D\sin x$.
> (d) $\lambda^2-4\lambda+4=(\lambda-2)^2=0$, so $y_h=c_1e^{2x}+c_2xe^{2x}$. First choice $Ke^{2x}$ is in $y_h$, and $\lambda=2$ is a double root. Multiply by $x^2$: $y_p=Kx^2e^{2x}$. (With only $x$, $Kxe^{2x}$ is still in $y_h$.)

> [!question]- Check (slide 14): Solve the IVP $y''+2y'+5y=5x^2-x+10$, $y(0)=3$, $y'(0)=2$.
> Type: second order, linear, non-homogeneous, constant coefficients, polynomial right side. Method: undetermined coefficients.
> **Step 1, homogeneous part.** $\lambda^2+2\lambda+5=0$. Discriminant $4-20=-16$. $\lambda=\dfrac{-2\pm4i}{2}=-1\pm2i$.
> $y_h=e^{-x}\left(c_1\cos2x+c_2\sin2x\right)$.
> **Step 2, choice.** $R$ is a polynomial of degree 2: $y_p=Ax^2+Bx+C$. No term of it is in $y_h$, so no factor $x$.
> **Step 3, substitute.** $y_p'=2Ax+B$, $y_p''=2A$.
> $$2A+2(2Ax+B)+5(Ax^2+Bx+C)=5x^2-x+10$$
> $$5Ax^2+(4A+5B)x+(2A+2B+5C)=5x^2-x+10 .$$
> Compare coefficients. $x^2$: $5A=5$, $A=1$. $x$: $4+5B=-1$, $B=-1$. Constant: $2-2+5C=10$, $C=2$.
> $y_p=x^2-x+2$.
> **Step 4, general solution.** $y=e^{-x}\left(c_1\cos2x+c_2\sin2x\right)+x^2-x+2$.
> $y'=-e^{-x}\left(c_1\cos2x+c_2\sin2x\right)+e^{-x}\left(-2c_1\sin2x+2c_2\cos2x\right)+2x-1$.
> **Step 5, initial conditions.** $y(0)=c_1+2=3$, so $c_1=1$. $y'(0)=-c_1+2c_2-1=2$, so $2c_2=4$, $c_2=2$.
> **Answer:** $y=e^{-x}\left(\cos2x+2\sin2x\right)+x^2-x+2$.
> Check of $y_p$: $2+2(2x-1)+5(x^2-x+2)=5x^2+(4-5)x+(2-2+10)=5x^2-x+10$.
> Check of the conditions: $y(0)=1+2=3$. $y'(0)=-1+4-1=2$.

> [!question]- Check (slide 15): Solve the IVP $y''+4y=8\cos2x$, $y(0)=1$, $y'(0)=0$.
> Type: second order, linear, non-homogeneous, constant coefficients, cosine right side. Method: undetermined coefficients with the modification rule.
> **Step 1.** $\lambda^2+4=0$, $\lambda=\pm2i$. $y_h=c_1\cos2x+c_2\sin2x$.
> **Step 2.** First choice: $C\cos2x+D\sin2x$. Both terms are in $y_h$, and $\pm2i$ are single roots. Multiply by $x$:
> $$y_p=x\left(A\cos2x+B\sin2x\right).$$
> **Step 3, derivatives.**
> $y_p'=A\cos2x+B\sin2x+x\left(-2A\sin2x+2B\cos2x\right)$.
> $y_p''=\left(-2A\sin2x+2B\cos2x\right)+\left(-2A\sin2x+2B\cos2x\right)+x\left(-4A\cos2x-4B\sin2x\right)$.
> $y_p''=-4A\sin2x+4B\cos2x-4y_p$.
> **Substitute.** $y_p''+4y_p=-4A\sin2x+4B\cos2x=8\cos2x$.
> Compare: $\sin2x$: $-4A=0$, $A=0$. $\cos2x$: $4B=8$, $B=2$. So $y_p=2x\sin2x$.
> **Step 4.** $y=c_1\cos2x+c_2\sin2x+2x\sin2x$.
> $y'=-2c_1\sin2x+2c_2\cos2x+2\sin2x+4x\cos2x$.
> **Step 5.** $y(0)=c_1=1$. $y'(0)=2c_2=0$, $c_2=0$.
> **Answer:** $y=\cos2x+2x\sin2x$.
> Check: $y'=-2\sin2x+2\sin2x+4x\cos2x=4x\cos2x$. $y''=4\cos2x-8x\sin2x$.
> $y''+4y=4\cos2x-8x\sin2x+4\cos2x+8x\sin2x=8\cos2x$. $y(0)=1$, $y'(0)=0$.
> Remark (beyond the slides): the factor $x$ makes the amplitude grow without bound. This is **resonance**: the forcing has the same frequency as the free oscillation.

> [!question]- Check (slide 16): Find the general solution of $y''-3y'=18x$. Be careful with the form of $y_p$.
> Type: second order, linear, non-homogeneous, constant coefficients, polynomial right side. Method: undetermined coefficients with the modification rule.
> **Step 1.** $\lambda^2-3\lambda=\lambda(\lambda-3)=0$, $\lambda=0$ and $\lambda=3$. $y_h=c_1+c_2e^{3x}$ (because $e^{0x}=1$).
> **Step 2.** First choice for degree 1: $Ax+B$. The constant $B$ is a solution of the homogeneous equation ($\lambda=0$, single root). Multiply the whole choice by $x$:
> $$y_p=x(Ax+B)=Ax^2+Bx .$$
> **Step 3.** $y_p'=2Ax+B$, $y_p''=2A$.
> $2A-3(2Ax+B)=18x$, so $-6Ax+(2A-3B)=18x$.
> Compare: $x$: $-6A=18$, $A=-3$. Constant: $2A-3B=0$, $-6-3B=0$, $B=-2$.
> $y_p=-3x^2-2x$.
> **Answer:** $y=c_1+c_2e^{3x}-3x^2-2x$.
> Check: $y_p'=-6x-2$, $y_p''=-6$. $y_p''-3y_p'=-6+18x+6=18x$.
> Without the factor $x$: $y_p=Ax+B$ gives $0-3A=18x$, which cannot hold for all $x$.

> [!question]- Check (slide 17): Find the general solution of $y''+3y'+2y=10\sin x+12e^{x}$.
> Type: second order, linear, non-homogeneous, constant coefficients. The right side is a sum, so use undetermined coefficients with superposition: one $y_p$ for each term.
> **Step 1.** $\lambda^2+3\lambda+2=(\lambda+1)(\lambda+2)=0$. $y_h=c_1e^{-x}+c_2e^{-2x}$.
> **Term $10\sin x$.** Choice $y_{p_1}=A\cos x+B\sin x$ (always both). Not in $y_h$.
> $y_{p_1}'=-A\sin x+B\cos x$, $y_{p_1}''=-A\cos x-B\sin x$.
> $$\left(-A\cos x-B\sin x\right)+3\left(-A\sin x+B\cos x\right)+2\left(A\cos x+B\sin x\right)=10\sin x$$
> $$(A+3B)\cos x+(B-3A)\sin x=10\sin x .$$
> $\cos x$: $A+3B=0$, so $A=-3B$. $\sin x$: $B-3A=10$, so $B+9B=10$, $B=1$. Then $A=-3$.
> $y_{p_1}=-3\cos x+\sin x$.
> **Term $12e^x$.** Choice $y_{p_2}=Ke^x$. Not in $y_h$ (the roots are $-1$ and $-2$, not $1$).
> $y_{p_2}'=Ke^x$, $y_{p_2}''=Ke^x$. $(1+3+2)Ke^x=12e^x$, $6K=12$, $K=2$. $y_{p_2}=2e^x$.
> **Answer:** $y=c_1e^{-x}+c_2e^{-2x}-3\cos x+\sin x+2e^x$.
> Check of $y_{p_1}$: $y'=3\sin x+\cos x$, $y''=3\cos x-\sin x$.
> $y''+3y'+2y=(3+3-6)\cos x+(-1+9+2)\sin x=10\sin x$.
> Check of $y_{p_2}$: $2e^x+6e^x+4e^x=12e^x$.

## 7. Euler's differential equation (slides 18-22)
![[math501_lecture_02_math501_chapter_2_p018.jpg]]
![[math501_lecture_02_math501_chapter_2_p019.jpg]]
![[math501_lecture_02_math501_chapter_2_p020.jpg]]
![[math501_lecture_02_math501_chapter_2_p021.jpg]]
![[math501_lecture_02_math501_chapter_2_p022.jpg]]

**Notes.** Form: $x^2y''+Axy'+By=0$, solved for $x>0$. The top of slide 18 holds exercises i to iv of section 2.5.

**Method 1.** Put $x=e^t$ ($t=\ln x$) and $z(t)=y(e^t)$. The equation becomes $z''+(A-1)z'+Bz=0$ with constant coefficients. Solve it, then put $t=\ln x$ back.

**Method 2.** Try $y=x^{\lambda}$. Then $\lambda$ must solve the **auxiliary equation**

$$\lambda^2+(A-1)\lambda+B=0 .$$

| Roots | General solution ($x>0$) |
|---|---|
| $\lambda_1\neq\lambda_2$ real | $y=c_1x^{\lambda_1}+c_2x^{\lambda_2}$ |
| $\gamma$ repeated | $y=c_1x^{\gamma}+c_2x^{\gamma}\ln x$ |
| $\alpha\pm i\beta$ | $y=c_1x^{\alpha}\cos(\beta\ln x)+c_2x^{\alpha}\sin(\beta\ln x)$ |

> [!example] Slide examples
> - $x^2y''-9xy'+24y=0$, $y(1)=1$, $y'(1)=10$: $\lambda^2-10\lambda+24=0$, $\lambda=6,4$, $y=c_1x^6+c_2x^4$. Answer: $y=3x^6-2x^4$.
> - $x^2y''-2xy'-4y=0$: $\lambda^2-3\lambda-4=0$, $y=c_1x^4+c_2/x$.
> - $4x^2y''+8xy'+y=0$: divide by 4, $(\lambda+\tfrac12)^2=0$, $y=\dfrac{c_1}{\sqrt x}+\dfrac{c_2\ln x}{\sqrt x}$.
> - $4x^2y''+17y=0$: $\lambda^2-\lambda+\tfrac{17}{4}=0$, $\lambda=\tfrac12\pm2i$, $y=c_1x^{1/2}\cos(2\ln x)+c_2x^{1/2}\sin(2\ln x)$.

> [!warning] Watch out
> - The auxiliary equation has $(A-1)$, not $A$.
> - Divide first so that the coefficient of $x^2y''$ is 1.
> - Repeated root: the second solution has $\ln x$, not an extra factor $x$.

> [!info] Where $\ln x$ comes from in cases ii and iii
> Slide 21 states the solutions for a repeated root and for complex roots without a derivation. Method 1 gives them directly. With $t=\ln x$ the equation is $z''+(A-1)z'+Bz=0$, and its characteristic equation is the auxiliary equation.
> - Repeated root $\gamma$: $z=c_1e^{\gamma t}+c_2te^{\gamma t}$. Put $t=\ln x$: $e^{\gamma t}=e^{\gamma\ln x}=x^{\gamma}$, so $y=c_1x^{\gamma}+c_2x^{\gamma}\ln x$. The factor $t$ becomes $\ln x$.
> - Complex roots $\alpha\pm i\beta$: $z=e^{\alpha t}\left(c_1\cos\beta t+c_2\sin\beta t\right)$. Put $t=\ln x$: $y=x^{\alpha}\left(c_1\cos(\beta\ln x)+c_2\sin(\beta\ln x)\right)$.
>
> The chain rule step on slide 18: $t=\ln x$ gives $\dfrac{dt}{dx}=\dfrac1x$, so $\dfrac{dy}{dx}=\dfrac{dz}{dt}\cdot\dfrac{dt}{dx}=\dfrac1x\dfrac{dz}{dt}$. Then $xy'=z'$ and $x^2y''=z''-z'$ (derivatives of $z$ with respect to $t$).

> [!question]- Check (slide 18, exercise i): Find the general solution of $y''+2y'=2x^3+\cos4x+1$.
> Type: second order, linear, non-homogeneous, constant coefficients. Method: undetermined coefficients, with superposition for the polynomial part $2x^3+1$ and the cosine part.
> **Step 1.** $\lambda^2+2\lambda=\lambda(\lambda+2)=0$, $\lambda=0,-2$. $y_h=c_1+c_2e^{-2x}$.
> **Polynomial part $2x^3+1$.** First choice: $Ax^3+Bx^2+Cx+D$. The constant $D$ is in $y_h$ ($\lambda=0$, single root). Multiply by $x$:
> $y_{p_1}=Ax^4+Bx^3+Cx^2+Dx$.
> $y_{p_1}'=4Ax^3+3Bx^2+2Cx+D$, $y_{p_1}''=12Ax^2+6Bx+2C$.
> $$y_{p_1}''+2y_{p_1}'=8Ax^3+(12A+6B)x^2+(6B+4C)x+(2C+2D)=2x^3+1 .$$
> $x^3$: $8A=2$, $A=\tfrac14$. $x^2$: $3+6B=0$, $B=-\tfrac12$. $x$: $-3+4C=0$, $C=\tfrac34$. Constant: $\tfrac32+2D=1$, $D=-\tfrac14$.
> $y_{p_1}=\tfrac14x^4-\tfrac12x^3+\tfrac34x^2-\tfrac14x$.
> **Cosine part $\cos4x$.** Choice $y_{p_2}=E\cos4x+F\sin4x$. Not in $y_h$.
> $y_{p_2}'=-4E\sin4x+4F\cos4x$, $y_{p_2}''=-16E\cos4x-16F\sin4x$.
> $$y_{p_2}''+2y_{p_2}'=(-16E+8F)\cos4x+(-16F-8E)\sin4x=\cos4x .$$
> $\sin4x$: $-16F-8E=0$, $E=-2F$. $\cos4x$: $-16E+8F=1$, $32F+8F=1$, $F=\tfrac1{40}$. Then $E=-\tfrac1{20}$.
> $y_{p_2}=-\tfrac1{20}\cos4x+\tfrac1{40}\sin4x$.
> **Answer:** $y=c_1+c_2e^{-2x}+\tfrac14x^4-\tfrac12x^3+\tfrac34x^2-\tfrac14x-\tfrac1{20}\cos4x+\tfrac1{40}\sin4x$.
> Check of $y_{p_1}$: $y'=x^3-\tfrac32x^2+\tfrac32x-\tfrac14$, $y''=3x^2-3x+\tfrac32$. $y''+2y'=2x^3+(3-3)x^2+(-3+3)x+\tfrac32-\tfrac12=2x^3+1$.
> Check of $y_{p_2}$: $-16E+8F=\tfrac{16}{20}+\tfrac{8}{40}=\tfrac45+\tfrac15=1$ and $-16F-8E=-\tfrac25+\tfrac25=0$.

> [!question]- Check (slides 18-19): Solve the IVP $x^2y''-xy'-3y=0$, $y(1)=3$, $y'(1)=1$, $x>0$, with the substitution $x=e^t$.
> Type: second order, linear, homogeneous, variable coefficients of Euler form with $A=-1$, $B=-3$. Method 1.
> **Substitute.** Put $z(t)=y(e^t)$, $t=\ln x$. Then $xy'=z'$ and $x^2y''=z''-z'$.
> $$(z''-z')-z'-3z=0\quad\Rightarrow\quad z''-2z'-3z=0 .$$
> This agrees with $z''+(A-1)z'+Bz=0$: $A-1=-2$, $B=-3$.
> **Solve in $t$.** $\lambda^2-2\lambda-3=(\lambda-3)(\lambda+1)=0$, $\lambda=3,-1$. $z=c_1e^{3t}+c_2e^{-t}$.
> **Back to $x$.** $e^{3t}=e^{3\ln x}=x^3$, $e^{-t}=x^{-1}$. $y=c_1x^3+c_2x^{-1}$.
> **Initial conditions.** $y'=3c_1x^2-c_2x^{-2}$. $y(1)=c_1+c_2=3$. $y'(1)=3c_1-c_2=1$.
> Add the two equations: $4c_1=4$, $c_1=1$. Then $c_2=3-1=2$.
> **Answer:** $y=x^3+\dfrac2x$.
> Check: $y'=3x^2-2x^{-2}$, $y''=6x+4x^{-3}$.
> $x^2y''-xy'-3y=\left(6x^3+4x^{-1}\right)-\left(3x^3-2x^{-1}\right)-\left(3x^3+6x^{-1}\right)=0$. $y(1)=1+2=3$. $y'(1)=3-2=1$.

> [!question]- Check (slide 20): Solve the IVP $2x^2y''+3xy'-y=0$, $y(1)=3$, $y'(1)=0$, $x>0$, with the trial solution $y=x^{\lambda}$.
> Type: second order, linear, homogeneous, Euler equation. Method 2.
> **Substitute $y=x^{\lambda}$.** $y'=\lambda x^{\lambda-1}$, $y''=\lambda(\lambda-1)x^{\lambda-2}$.
> $$2x^2\lambda(\lambda-1)x^{\lambda-2}+3x\lambda x^{\lambda-1}-x^{\lambda}=x^{\lambda}\left[2\lambda(\lambda-1)+3\lambda-1\right]=0 .$$
> Since $x^{\lambda}\neq0$: $2\lambda^2-2\lambda+3\lambda-1=2\lambda^2+\lambda-1=0$.
> (Same as dividing by 2 first: $A=\tfrac32$, $B=-\tfrac12$, $\lambda^2+\tfrac12\lambda-\tfrac12=0$.)
> **Roots.** $\lambda=\dfrac{-1\pm\sqrt{1+8}}{4}=\dfrac{-1\pm3}{4}$, so $\lambda_1=\tfrac12$, $\lambda_2=-1$. Distinct real roots (case i).
> **General solution.** $y=c_1x^{1/2}+c_2x^{-1}$, and $y'=\tfrac12c_1x^{-1/2}-c_2x^{-2}$.
> **Initial conditions.** $y(1)=c_1+c_2=3$. $y'(1)=\tfrac12c_1-c_2=0$, so $c_1=2c_2$.
> Then $2c_2+c_2=3$, $c_2=1$, $c_1=2$.
> **Answer:** $y=2\sqrt x+\dfrac1x$.
> Check: $y'=x^{-1/2}-x^{-2}$, $y''=-\tfrac12x^{-3/2}+2x^{-3}$.
> $2x^2y''=-x^{1/2}+4x^{-1}$. $3xy'=3x^{1/2}-3x^{-1}$. $-y=-2x^{1/2}-x^{-1}$.
> Sum: $(-1+3-2)x^{1/2}+(4-3-1)x^{-1}=0$. $y(1)=2+1=3$. $y'(1)=1-1=0$.

> [!question]- Check (slide 21, case ii): Solve the IVP $x^2y''+5xy'+4y=0$, $y(1)=1$, $y'(1)=1$, $x>0$.
> Type: second order, linear, homogeneous, Euler equation with $A=5$, $B=4$. Method 2.
> **Auxiliary equation.** $\lambda^2+(A-1)\lambda+B=\lambda^2+4\lambda+4=(\lambda+2)^2=0$. Repeated root $\gamma=-2$.
> **General solution.** $y=c_1x^{-2}+c_2x^{-2}\ln x$.
> Derivative (product rule on the second term): $y'=-2c_1x^{-3}+c_2\left(-2x^{-3}\ln x+x^{-2}\cdot\tfrac1x\right)=-2c_1x^{-3}+c_2\left(-2x^{-3}\ln x+x^{-3}\right)$.
> **Initial conditions** (use $\ln1=0$). $y(1)=c_1=1$. $y'(1)=-2c_1+c_2=1$, so $c_2=3$.
> **Answer:** $y=\dfrac{1+3\ln x}{x^2}$.
> Check: $y'=-2x^{-3}+3\left(-2x^{-3}\ln x+x^{-3}\right)=x^{-3}\left(1-6\ln x\right)$.
> $y''=-3x^{-4}\left(1-6\ln x\right)+x^{-3}\cdot\left(-\tfrac6x\right)=x^{-4}\left(-9+18\ln x\right)$.
> $x^2y''+5xy'+4y=x^{-2}\left[(-9+18\ln x)+(5-30\ln x)+(4+12\ln x)\right]=0$. $y(1)=1$. $y'(1)=1$.

> [!question]- Check (slides 21-22, case iii): Solve the IVP $x^2y''+3xy'+5y=0$, $y(1)=2$, $y'(1)=4$, $x>0$.
> Type: second order, linear, homogeneous, Euler equation with $A=3$, $B=5$. Method 2.
> **Auxiliary equation.** $\lambda^2+(A-1)\lambda+B=\lambda^2+2\lambda+5=0$. Discriminant $4-20=-16<0$.
> $\lambda=\dfrac{-2\pm4i}{2}=-1\pm2i$. So $\alpha=-1$, $\beta=2$.
> **General solution.** $y=x^{-1}\left(c_1\cos(2\ln x)+c_2\sin(2\ln x)\right)$.
> Derivative (product rule, and chain rule with $\tfrac{d}{dx}(2\ln x)=\tfrac2x$):
> $$y'=-x^{-2}\left(c_1\cos(2\ln x)+c_2\sin(2\ln x)\right)+x^{-1}\cdot\frac2x\left(-c_1\sin(2\ln x)+c_2\cos(2\ln x)\right).$$
> **Initial conditions** ($\ln1=0$, $\cos0=1$, $\sin0=0$). $y(1)=c_1=2$. $y'(1)=-c_1+2c_2=4$, so $2c_2=6$, $c_2=3$.
> **Answer:** $y=\dfrac{2\cos(2\ln x)+3\sin(2\ln x)}{x}$.
> Check with $y=x^{\lambda}$, $\lambda=-1+2i$: $\lambda(\lambda-1)+3\lambda+5=\lambda^2+2\lambda+5=(1-4i-4)+(-2+4i)+5=0$. The real and imaginary parts of $x^{\lambda}$ are $x^{-1}\cos(2\ln x)$ and $x^{-1}\sin(2\ln x)$, so both solve the equation.
> Conditions: $y(1)=2$. $y'(1)=-2+2\cdot3=4$.

## Key formulas and terms
| Term | Meaning / formula |
|---|---|
| Linear independence | $\sum c_jf_j=0$ on $J$ only for all $c_j=0$ |
| Wronskian | Determinant of the functions and their derivatives; nonzero at one point gives independence |
| Basis | Two independent solutions of the homogeneous ODE |
| Characteristic equation | $\lambda^2+a\lambda+b=0$ for $y''+ay'+by=0$ |
| Repeated root | $y=c_1e^{\lambda x}+c_2xe^{\lambda x}$ |
| Complex roots $\alpha\pm i\beta$ | $y=e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$ |
| Non-homogeneous | $y=y_h+y_p$ |
| Variation of parameters | $u_1=-\int\frac{y_2R}{W}dx$, $u_2=\int\frac{y_1R}{W}dx$, $y_p=u_1y_1+u_2y_2$ |
| Modification rule | Multiply the guess by $x$ (single root) or $x^2$ (double root) |
| Euler's equation | $x^2y''+Axy'+By=0$, auxiliary equation $\lambda^2+(A-1)\lambda+B=0$ |

## Check yourself
> [!question]- 1. Are $\sin x$, $\cos x$, $x$ linearly independent on $\mathbb R$?
> Wronskian (rows $f$, $f'$, $f''$), expanded along column 3: $W=x\cdot(-1)-1\cdot0=-x$.
> $W(1)=-1\neq0$, so they are independent.

> [!question]- 2. Solve $y''+6y'+9y=0$.
> $\lambda^2+6\lambda+9=(\lambda+3)^2=0$, repeated root $-3$.
> $y=c_1e^{-3x}+c_2xe^{-3x}$.

> [!question]- 3. Find the general solution of $y'''-y''+y'-y=0$.
> $\lambda^3-\lambda^2+\lambda-1=(\lambda-1)(\lambda^2+1)=0$: $\lambda=1,\ \pm i$.
> $y=c_1e^x+c_2\cos x+c_3\sin x$.

> [!question]- 4. Find the general solution of $y''+4y'+3y=e^{-x}$.
> Roots $-1,-3$: $y_h=c_1e^{-x}+c_2e^{-3x}$. $e^{-x}$ is in $y_h$ (single root), so $y_p=Axe^{-x}$.
> Substituting gives $2Ae^{-x}=e^{-x}$, $A=\tfrac12$. Answer: $y=c_1e^{-x}+c_2e^{-3x}+\tfrac12xe^{-x}$.

> [!question]- 5. Find the general solution of $y''+2y'+y=2e^x+3e^{-x}$.
> Double root $-1$: $y_h=c_1e^{-x}+c_2xe^{-x}$. For $2e^x$: $y_{p_1}=Ae^x$, $4A=2$, $A=\tfrac12$.
> For $3e^{-x}$ (double root): $y_{p_2}=Bx^2e^{-x}$, $2B=3$, $B=\tfrac32$.
> Answer: $y=c_1e^{-x}+c_2xe^{-x}+\tfrac12e^x+\tfrac32x^2e^{-x}$.

> [!question]- 6. Solve $x^2y''-3xy'+4y=0$, $y(1)=1$, $y'(1)=0$, $x>0$.
> $\lambda^2-4\lambda+4=(\lambda-2)^2=0$: $y=c_1x^2+c_2x^2\ln x$, $y'=2c_1x+c_2(2x\ln x+x)$.
> $c_1=1$, $2+c_2=0$. Answer: $y=x^2-2x^2\ln x$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L01 - First order differential equations]]. Next: [[MATH501 L03 - The Laplace transform]]
- Full step-by-step notes (PDF): [MATH501_Lecture_02_Higher_Order_Linear_ODEs.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_02/MATH501_Lecture_02_Higher_Order_Linear_ODEs.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_02/MATH501_Lecture_02_Higher_Order_Linear_ODEs.pdf`
- Original chapter notes (PDF): [Math501 Chapter 2.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_02/Math501%20Chapter%202.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_02/Math501 Chapter 2.pdf`
- Quiz: [[MATH501 L02 - Higher order linear ODEs - quiz]]

Slides not embedded: none.
