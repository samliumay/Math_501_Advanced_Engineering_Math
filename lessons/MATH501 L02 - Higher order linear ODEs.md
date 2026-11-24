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

Slides not embedded: none.
