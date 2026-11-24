---
course: MATH 501 Advanced Engineering Mathematics
lecture: 1
title: First order differential equations
tags: [math501, lecture]
slides: lectures/lecture_01/Math501 Chapter 1.pdf
full_notes: lecture_notes/lecture_01/MATH501_Lecture_01_First_Order_ODEs.pdf
---
# MATH 501 · Lecture 1 · First order differential equations

> [!summary] In short
> - An ODE has one independent variable. Its order is the highest derivative. It is linear when $y, y', \dots$ appear only to the first power with coefficients in $x$.
> - A general solution of an $n$-th order ODE has $n$ constants. $n$ initial conditions at one point fix them.
> - Six solvable first order types: separable, linear, homogeneous ($y'=g(y/x)$), $y'=F(Ax+By+C)$, exact, Bernoulli, plus Riccati when one solution is known.
> - Each substitution turns the equation into a separable or a linear one.
> - Whenever you divide by something, check the excluded constant solutions separately.

## 1. What is a differential equation? (slides 2-3)
![[math501_lecture_01_math501_chapter_1_p002.jpg]]
![[math501_lecture_01_math501_chapter_1_p003.jpg]]

**Notes.** A differential equation relates an unknown function to its derivatives. One independent variable: ODE. Several: PDE. The **order** is the highest derivative that appears. A power does not raise the order: $(y')^4$ is still first order.

An ODE is **linear** when it has the form

$$a_n(x)y^{(n)} + \dots + a_1(x)y' + a_0(x)y = b(x).$$

So $y, y', \dots$ appear only to the first power, are not multiplied by each other, and are not inside another function. If $b(x) \equiv 0$ (zero for every $x$) the linear ODE is **homogeneous**, otherwise non-homogeneous.

A **solution** on an interval $I$ is a function $\phi$ that satisfies the ODE for every $x$ in $I$.

> [!example] Check a solution
> $\phi(x)=x^{-3/2}$ in $4x^2y''+12xy'+3y=0$, $x>0$. With $\phi'=-\tfrac32x^{-5/2}$, $\phi''=\tfrac{15}{4}x^{-7/2}$: $15x^{-3/2}-18x^{-3/2}+3x^{-3/2}=0$.

> [!warning] Watch out
> - Row 6 on slide 3: $y^{(5)}+\sin^4(2x)\,y^{(9)}+3\cos x=0$ has order 9, not 5, and $b(x)=-3\cos x$, so it is non-homogeneous.
> - "Homogeneous" is defined only for linear ODEs here. The word gets a second meaning in section 5.

## 2. General solution, IVP, existence and uniqueness (slides 4-5)
![[math501_lecture_01_math501_chapter_1_p004.jpg]]
![[math501_lecture_01_math501_chapter_1_p005.jpg]]

**Notes.** A **general solution** of an $n$-th order ODE contains $n$ arbitrary constants. Giving values to all of them gives a **particular solution**. An **initial value problem (IVP)** is an ODE plus $n$ conditions, all at the same point $x_0$.

To solve an IVP: find the general solution, put the conditions in, solve for the constants.

> [!example] IVP by direct integration
> $y''=e^{2x}+1$, $y(1)=0$, $y'(1)=2$. Integrate twice: $y=\tfrac14e^{2x}+\tfrac{x^2}{2}+c_1x+c_2$. The conditions give $c_1=1-\tfrac12e^2$, $c_2=\tfrac14e^2-\tfrac32$.

**Existence and Uniqueness Theorem.** If $f$ and $\partial f/\partial y$ are continuous in a rectangle $R$ containing $(x_0,y_0)$, then $y'=f(x,y)$, $y(x_0)=y_0$ has exactly one solution on some interval $(x_0-h,\,x_0+h)$.

How to use it: compute $\partial f/\partial y$, find where $f$ or $\partial f/\partial y$ is not continuous, choose a rectangle around $(x_0,y_0)$ that avoids those points. On the slide: $f=x^2+x/y$, $\partial f/\partial y=-x/y^2$, both fail only on $y=0$, so $R=(0,2)\times(2,4)$ works for the point $(1,3)$.

> [!warning] Watch out
> The theorem is local and works in one direction only. If the hypotheses fail, it says nothing: there may be one solution, many, or none. Example: $y'=3y^{2/3}$, $y(0)=0$ has both $y\equiv0$ and $y=x^3$.

Section 1.2 (separable equations) starts at the bottom of slide 5.

## 3. Separable equations (slides 5-6)
![[math501_lecture_01_math501_chapter_1_p006.jpg]]

**Notes.** Form: $\dfrac{dy}{dx}=f(x)\,g(y)$. Move the $y$ terms to one side and the $x$ terms to the other, then integrate:

$$\int\frac{dy}{g(y)}=\int f(x)\,dx .$$

Add one constant, on one side only. An answer solved for $y$ is **explicit**. A relation between $x$ and $y$ is **implicit**.

> [!example] Slide examples
> - $y'=x^2/y$: $y\,dy=x^2\,dx$, so $\tfrac{y^2}{2}=\tfrac{x^3}{3}+c$.
> - $y'=y^2e^{-x}$: $-\tfrac1y=-e^{-x}+c$, so $y=\dfrac{1}{e^{-x}+c}$. Also $y\equiv0$, which no value of $c$ gives.
> - $y'=\dfrac{3x^2-e^x}{2y-5}$, $y(0)=1$: $y^2-5y=x^3-e^x+c$, $c=-3$.

> [!warning] Watch out
> Dividing by $g(y)$ needs $g(y)\neq0$. Each number $y_0$ with $g(y_0)=0$ gives a constant solution $y\equiv y_0$ that may be missing from the general solution.

## 4. First order linear equations (slides 7-8)
![[math501_lecture_01_math501_chapter_1_p007.jpg]]
![[math501_lecture_01_math501_chapter_1_p008.jpg]]

**Notes.** Standard form: $y'+p(x)y=q(x)$ (coefficient of $y'$ equal to 1). The **integrating factor** $\mu$ is chosen so that the left side becomes one derivative, $(\mu y)'$. This needs $\mu'=\mu p$, which is separable and gives

$$\mu(x)=e^{\int p(x)\,dx},\qquad y=\frac{1}{\mu(x)}\int\mu(x)\,q(x)\,dx .$$

Steps: standard form, compute $\mu$ (no constant), write $(\mu y)'=\mu q$, integrate (constant $c$ here), divide by $\mu$.

> [!example] Slide examples
> - $y'+y=xe^{-x}+1$: $\mu=e^x$, $(e^xy)'=x+e^x$, so $y=\tfrac{x^2}{2}e^{-x}+1+ce^{-x}$.
> - $y'+y\cos x=\cos x$, $y(0)=3$: $\mu=e^{\sin x}$, $y=1+ce^{-\sin x}$, $c=2$.

> [!warning] Watch out
> Put the ODE in standard form before computing $\mu$. The constant $c$ is added after integrating $\mu q$, not inside $\mu$.

The top of slide 7 holds the exercises of section 1.2.

## 5. Homogeneous equations (slides 9-12)
![[math501_lecture_01_math501_chapter_1_p009.jpg]]
![[math501_lecture_01_math501_chapter_1_p010.jpg]]
![[math501_lecture_01_math501_chapter_1_p011.jpg]]
![[math501_lecture_01_math501_chapter_1_p012.jpg]]

**Notes.** A function is **homogeneous of degree $n$** if $f(\alpha x,\alpha y)=\alpha^nf(x,y)$ for every nonzero $\alpha$. A first order ODE is **homogeneous** if it can be written as $y'=g(y/x)$. This holds exactly when $f(x,y)$ is homogeneous of degree 0.

Test: check $f(\alpha x,\alpha y)=f(x,y)$, or divide top and bottom by a power of $x$ and try to write everything with $y/x$.

Method: put $v=y/x$, so $y=vx$ and $y'=v+xv'$. The equation becomes separable:

$$\int\frac{dv}{g(v)-v}=\ln|x|+c\qquad(g(v)\neq v).$$

Then replace $v$ by $y/x$.

> [!example] Slide examples
> - $xy^2\,dy-(x^3+y^3)\,dx=0$: $v+xv'=v+\tfrac{1}{v^2}$, so $\tfrac{v^3}{3}=\ln|x|+c$ and $y=x(3\ln|x|+c)^{1/3}$.
> - $xy'=y+xe^{y/x}$, $y(1)=2$: $-e^{-v}=\ln|x|+c$, $c=-e^{-2}$, $y=-x\ln\!\left(e^{-2}-\ln|x|\right)$.
> - $y'=\tfrac{y^2}{x^2}-\tfrac yx+1$: $xv'=(v-1)^2$, $y=x-\dfrac{x}{\ln|x|+c}$.

> [!warning] Watch out
> - This "homogeneous" is not the "homogeneous linear" ($b\equiv0$) of section 1.
> - Check the lines $y=v_0x$ with $g(v_0)=v_0$. In the third example $y=x$ is a solution that no value of $c$ gives.
> - The IVP solution of the second example lives on one interval containing $x_0=1$: $0<x<e^{e^{-2}}\approx1.145$.

## 6. Equations of the form y' = F(Ax + By + C) (slides 13-14)
![[math501_lecture_01_math501_chapter_1_p013.jpg]]

**Notes.** Put $u=Ax+By+C$. Then $u'=A+By'=A+BF(u)$, which is separable:

$$\int\frac{du}{BF(u)+A}=x+c .$$

Put $u$ back at the end.

> [!example] Slide examples
> - $y'=(-4x+y)^2+7$, $y(0)=0$: $u=-4x+y$, $u'=u^2+3$, $\tfrac{1}{\sqrt3}\arctan\tfrac{u}{\sqrt3}=x+c$, $c=0$. Answer: $\arctan\!\left(\dfrac{-4x+y}{\sqrt3}\right)-\sqrt3\,x=0$.
> - $y'=\sin(2x+2y+1)$: $u'=2(\sin u+1)$, answer $\tan(2x+2y+1)-\sec(2x+2y+1)=2x+c$ (the end is at the top of slide 14).

> [!warning] Watch out
> The first solution is $y=4x+\sqrt3\tan(\sqrt3x)$. It blows up at $x=\pm\tfrac{\pi}{2\sqrt3}\approx\pm0.907$ although $f$ is smooth everywhere. Existence and uniqueness is only local.

## 7. Exact equations (slides 14-16)
![[math501_lecture_01_math501_chapter_1_p014.jpg]]
![[math501_lecture_01_math501_chapter_1_p015.jpg]]
![[math501_lecture_01_math501_chapter_1_p016.jpg]]

**Notes.** $M(x,y)\,dx+N(x,y)\,dy=0$ is **exact** if there is a **potential function** $u(x,y)$ with $u_x=M$ and $u_y=N$. Then the equation says $du=0$ and the general solution is the implicit relation $u(x,y)=c$.

Test (on a region without holes): exact if and only if

$$\frac{\partial M}{\partial y}=\frac{\partial N}{\partial x}.$$

To find $u$: integrate $M$ in $x$ with $y$ held constant, $u=\int M\,dx+\phi(y)$. Differentiate in $y$, set $u_y=N$, and solve for $\phi'(y)$. Integrate to get $\phi$.

> [!example] Slide examples
> - $(3x^2+2y\sin 2x)\,dx+(2\sin^2x+3y^2)\,dy=0$: $M_y=N_x=2\sin2x$. Answer: $2y\sin^2x+x^3+y^3=c$.
> - $(x^2+\ln y)\,dx+\tfrac xy\,dy=0$, $y(1)=e$: $M_y=N_x=\tfrac1y$, $u=\tfrac{x^3}{3}+x\ln y$, $c=\tfrac43$.

> [!warning] Watch out
> - The signs belong to $M$ and $N$: in $(\dots)\,dx-(4y-x)\,dy=0$, $N=-(4y-x)$.
> - $\phi'$ must depend on $y$ only. If an $x$ is left, there is an error or the ODE is not exact.
> - The answer is $u(x,y)=c$, not $u(x,y)$ alone.

## 8. Bernoulli equation (slides 17-18)
![[math501_lecture_01_math501_chapter_1_p017.jpg]]
![[math501_lecture_01_math501_chapter_1_p018.jpg]]

**Notes.** Form: $y'+p(x)y=q(x)y^{\alpha}$ with $\alpha\neq0,1$. Divide by $y^{\alpha}$ and put $v=y^{1-\alpha}$. The result is linear:

$$\frac{dv}{dx}+(1-\alpha)p(x)\,v=(1-\alpha)q(x),\qquad y=v^{1/(1-\alpha)} .$$

> [!example] Slide examples
> - $x^2y'+2xy-y^3=0$, $x>0$: $\alpha=3$, $v=y^{-2}$, $v'-\tfrac4xv=-\tfrac{2}{x^2}$, $\mu=x^{-4}$, $v=\tfrac{2}{5x}+cx^4$. Answer: $y=\pm\left(\tfrac{2}{5x}+cx^4\right)^{-1/2}$.
> - $dx+\tfrac{2x}{y}\,dy=2x^2y^2\,dx$, $y(1)=1$: $y'+\tfrac{y}{2x}=xy^3$, $v=y^{-2}$, $v=-2x^2+cx$, $c=3$. Answer: $y=(3x-2x^2)^{-1/2}$ on $0<x<\tfrac32$.

> [!warning] Watch out
> If $\alpha>0$, $y\equiv0$ is also a solution. It is lost when dividing by $y^{\alpha}$. The slide gives only the $+$ root in the first example. Our notes keep $\pm$.

## 9. Riccati equation (slides 19-20)
![[math501_lecture_01_math501_chapter_1_p019.jpg]]
![[math501_lecture_01_math501_chapter_1_p020.jpg]]

**Notes.** Form: $y'+p(x)y=q(x)y^2+r(x)$. It needs one known solution $\phi(x)$. Check first that $\phi$ really solves the ODE.

- $y=\phi+z$ gives a Bernoulli equation with $\alpha=2$.
- $y=\phi+\dfrac1u$ gives a linear equation for $u$. Use this one.

With $y'=\phi'-\dfrac{u'}{u^2}$ the terms without $u$ cancel. Multiply by $-u^2$ and solve with an integrating factor.

> [!example] Slide example
> $y'=\tfrac{y^2}{x}+\tfrac yx-\tfrac2x$, $\phi=1$. With $y=1+\tfrac1u$: $u'+\tfrac3xu=-\tfrac1x$, $\mu=x^3$, $u=-\tfrac13+\tfrac{c}{x^3}$. Answer: $y=1+\dfrac{3x^3}{3c-x^3}$, together with $y=1$.

## Key formulas and terms
| Term | Meaning / formula |
|---|---|
| Order | Highest derivative in the equation |
| Linear ODE | $a_n(x)y^{(n)}+\dots+a_0(x)y=b(x)$; homogeneous if $b\equiv0$ |
| IVP | ODE of order $n$ plus $n$ conditions at one point $x_0$ |
| Existence and uniqueness | $f$, $\partial f/\partial y$ continuous near $(x_0,y_0)$: exactly one local solution |
| Separable | $y'=f(x)g(y)$: $\int\frac{dy}{g(y)}=\int f(x)\,dx$ |
| Linear, first order | $y'+py=q$: $\mu=e^{\int p\,dx}$, $(\mu y)'=\mu q$ |
| Homogeneous ODE | $y'=g(y/x)$: $y=vx$, $xv'=g(v)-v$ |
| $y'=F(Ax+By+C)$ | $u=Ax+By+C$, $u'=A+BF(u)$ |
| Exact | $M\,dx+N\,dy=0$ with $M_y=N_x$: solution $u(x,y)=c$, $u_x=M$, $u_y=N$ |
| Bernoulli | $y'+py=qy^{\alpha}$: $v=y^{1-\alpha}$, $v'+(1-\alpha)pv=(1-\alpha)q$ |
| Riccati | $y'+py=qy^2+r$, known $\phi$: $y=\phi+1/u$ gives a linear ODE |

## Check yourself
> [!question]- 1. Find the general solution of $y'''=e^{-x}$.
> Integrate three times: $y''=-e^{-x}+c_1$, $y'=e^{-x}+c_1x+c_2$, $y=-e^{-x}+\tfrac{c_1}{2}x^2+c_2x+c_3$.
> Rename the constants: $y=-e^{-x}+k_1x^2+k_2x+k_3$.

> [!question]- 2. Solve the IVP $y'=\dfrac{3x^2}{3y^2-4}$, $y(1)=0$.
> Separable: $(3y^2-4)\,dy=3x^2\,dx$, so $y^3-4y=x^3+c$.
> $y(1)=0$ gives $c=-1$. Answer (implicit): $y^3-4y=x^3-1$.

> [!question]- 3. Solve $y'+\dfrac{2y}{x}=\dfrac{\cos x}{x^2}$, $y(\pi)=0$.
> Linear: $\mu=e^{2\ln|x|}=x^2$, so $(x^2y)'=\cos x$ and $x^2y=\sin x+C$.
> $y(\pi)=0$ gives $C=0$. Answer: $y=\dfrac{\sin x}{x^2}$ on $(0,\infty)$.

> [!question]- 4. Find the general solution of $\dfrac{dy}{dx}=\dfrac{x^2-3y^2}{2xy}$.
> Homogeneous: $g(v)=\tfrac{1}{2v}-\tfrac{3v}{2}$, so $xv'=\dfrac{1-5v^2}{2v}$.
> $-\tfrac15\ln|1-5v^2|=\ln|x|+c$, so $1-5v^2=Cx^{-5}$. Answer: $x^5-5x^3y^2=C$.

> [!question]- 5. Is $(9x^2+y-1)\,dx-(4y-x)\,dy=0$ exact? If yes, solve it.
> $M=9x^2+y-1$, $N=x-4y$: $M_y=1=N_x$, exact.
> $u=3x^3+xy-x+\phi(y)$, $u_y=x+\phi'=x-4y$, so $\phi=-2y^2$. Answer: $3x^3+xy-x-2y^2=c$.

> [!question]- 6. Solve $y'+4xy=2e^{-x^2}\sqrt y$.
> Bernoulli, $\alpha=\tfrac12$, $v=\sqrt y$: $v'+2xv=e^{-x^2}$.
> $\mu=e^{x^2}$, $(e^{x^2}v)'=1$, $v=(x+c)e^{-x^2}$. Answer: $y=(x+c)^2e^{-2x^2}$ for $x\ge-c$, and also $y\equiv0$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Next lecture: [[MATH501 L02 - Higher order linear ODEs]]
- Full step-by-step notes (PDF): [MATH501_Lecture_01_First_Order_ODEs.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_01/MATH501_Lecture_01_First_Order_ODEs.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_01/MATH501_Lecture_01_First_Order_ODEs.pdf`
- Original chapter notes (PDF): [Math501 Chapter 1.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_01/Math501%20Chapter%201.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_01/Math501 Chapter 1.pdf`

Slides not embedded: 1 (title page).
