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

> [!question]- Check (slide 2): For each relation say if it is an ODE, a PDE or no differential equation, and give the order: (a) $\dfrac{d^2\theta}{dt^2}+\dfrac gL\sin\theta=0$, (b) $\dfrac{\partial u}{\partial t}=k\,\dfrac{\partial^2u}{\partial x^2}$, (c) $(y''')^2+x\,(y')^5=e^x$, (d) $\dfrac{d}{dx}\sin x=\cos x$.
> (a) One independent variable ($t$), dependent variable $\theta$. It is an ODE. The highest derivative is $\dfrac{d^2\theta}{dt^2}$, so the order is 2.
> (b) Two independent variables ($x$ and $t$), dependent variable $u$. It is a PDE. The highest derivative is the second one, so the order is 2.
> (c) One independent variable ($x$). It is an ODE. The highest derivative is $y'''$, so the order is 3. The powers 2 and 5 do not change the order.
> (d) There is no unknown function. The relation is true for every $x$. It is an identity, not a differential equation (like example 3 on the slide).

> [!question]- Check (slide 3, classification): Give the order of each ODE and say if it is linear. If it is linear, say if it is homogeneous: (a) $x^3y'''-(\cos x)\,y'+y=0$, (b) $y\,y'+x=0$, (c) $y''+e^{y}=x$, (d) $(1+x^2)\,y''+\dfrac yx=\ln x$.
> Compare each one with $a_n(x)y^{(n)}+\dots+a_1(x)y'+a_0(x)y=b(x)$.
> (a) Order 3. Here $a_3=x^3$, $a_2=0$, $a_1=-\cos x$, $a_0=1$, $b=0$. All coefficients depend on $x$ only. Linear, and homogeneous because $b\equiv0$.
> (b) Order 1. The term $y\,y'$ is a product of $y$ and $y'$. Nonlinear. (The word homogeneous is not used.)
> (c) Order 2. The term $e^{y}$ puts $y$ inside another function. Nonlinear.
> (d) Order 2. Here $a_2=1+x^2$, $a_1=0$, $a_0=\tfrac1x$, $b=\ln x$. Linear. Since $b=\ln x$ is not the zero function, it is non-homogeneous.

> [!question]- Check (slide 3, solution): Show that $\phi(x)=x^2\ln x$ is a solution of $x^2y''-3xy'+4y=0$ for $x>0$.
> Step 1, first derivative (product rule): $\phi'=2x\ln x+x^2\cdot\tfrac1x=2x\ln x+x$.
> Step 2, second derivative: $\phi''=2\ln x+2x\cdot\tfrac1x+1=2\ln x+3$.
> Step 3, put them into the left side:
> $$x^2(2\ln x+3)-3x(2x\ln x+x)+4x^2\ln x$$
> $$=2x^2\ln x+3x^2-6x^2\ln x-3x^2+4x^2\ln x .$$
> Step 4, collect: the $\ln x$ terms give $(2-6+4)x^2\ln x=0$ and the other terms give $3x^2-3x^2=0$.
> The left side is $0$ for every $x>0$, so $\phi$ is a solution on $(0,\infty)$.

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

> [!question]- Check (slide 4): Find the general solution of $y''=12x^2-4\sin 2x$. Then solve the IVP with $y(0)=1$, $y'(0)=3$.
> Type: second order, the right side depends on $x$ only. Method: integrate twice.
> Step 1: $y'=\int(12x^2-4\sin 2x)\,dx=4x^3+2\cos 2x+c_1$. (Because $\int\sin 2x\,dx=-\tfrac12\cos 2x$, so $-4\cdot\left(-\tfrac12\cos 2x\right)=2\cos 2x$.)
> Step 2: $y=\int(4x^3+2\cos 2x+c_1)\,dx=x^4+\sin 2x+c_1x+c_2$.
> This is the general solution. It has 2 constants because the order is 2.
> Step 3, use $y'(0)=3$: $4\cdot0+2\cos0+c_1=3$, so $2+c_1=3$ and $c_1=1$.
> Step 4, use $y(0)=1$: $0+\sin0+c_1\cdot0+c_2=1$, so $c_2=1$.
> Answer: $y=x^4+\sin 2x+x+1$ (a particular solution).
> Check: $y'=4x^3+2\cos 2x+1$, $y''=12x^2-4\sin 2x$. Also $y(0)=1$ and $y'(0)=2+1=3$.

> [!question]- Check (slide 5, theorem): Take $y'=x\,y^{1/3}$. (a) Does the theorem give a unique solution for $y(2)=1$? (b) Does it apply for $y(0)=0$? How many solutions can you find there?
> Step 1: $f(x,y)=x\,y^{1/3}$ and $\dfrac{\partial f}{\partial y}=x\cdot\tfrac13y^{-2/3}=\dfrac{x}{3y^{2/3}}$.
> Step 2: $f$ is continuous everywhere. $\dfrac{\partial f}{\partial y}$ is not defined on the line $y=0$ (for $x\neq0$), so it is not continuous there.
> (a) The point $(2,1)$ has $y=1\neq0$. Take $R=(1,3)\times\left(\tfrac12,2\right)$. In $R$ we have $y>0$, so $f$ and $\partial f/\partial y$ are continuous. The theorem applies: exactly one solution on some interval $(2-h,2+h)$.
> (b) The point $(0,0)$ lies on the line $y=0$. Every rectangle around it contains points $(x,0)$ with $x\neq0$, where $\partial f/\partial y$ is not continuous. The theorem does not apply, so it promises nothing.
> Now look for solutions directly.
> Solution 1: $y\equiv0$. Then $y'=0$ and $x\cdot0^{1/3}=0$. It also satisfies $y(0)=0$.
> Solution 2 (separable, $y\neq0$): $y^{-1/3}\,dy=x\,dx$. Integrate: $\tfrac32y^{2/3}=\tfrac{x^2}{2}+c$.
> $y(0)=0$ gives $0=0+c$, so $c=0$. Then $y^{2/3}=\tfrac{x^2}{3}$, so $y=\pm\left(\tfrac{x^2}{3}\right)^{3/2}=\pm\dfrac{|x|^3}{3\sqrt3}$.
> Check for $x\ge0$ and the $+$ sign: $y=\dfrac{x^3}{3\sqrt3}$, $y'=\dfrac{3x^2}{3\sqrt3}=\dfrac{x^2}{\sqrt3}$. Right side: $y^{1/3}=\dfrac{x}{\sqrt3}$ because $(3\sqrt3)^{1/3}=\sqrt3$, so $x\,y^{1/3}=\dfrac{x^2}{\sqrt3}$. Equal.
> Check for every $x$ and both signs: $\left(|x|^3\right)'=3x|x|$, so $y'=\pm\dfrac{3x|x|}{3\sqrt3}=\pm\dfrac{x|x|}{\sqrt3}$. Right side: $y^{1/3}=\pm\dfrac{|x|}{\sqrt3}$ (real cube root), so $x\,y^{1/3}=\pm\dfrac{x|x|}{\sqrt3}$. Equal. And $y(0)=0$.
> So this IVP has at least three solutions: $y\equiv0$, $y=\dfrac{|x|^3}{3\sqrt3}$ and $y=-\dfrac{|x|^3}{3\sqrt3}$. The hypothesis that fails is the continuity of $\partial f/\partial y$ at $y=0$ ($f$ itself is continuous), and uniqueness fails exactly there.

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

> [!question]- Check (slide 5, separable equations): Solve the IVP $y'=\dfrac{e^{x}}{2y}$, $y(0)=-3$. Give $y$ explicitly. Which sign of the square root is correct, and why?
> Type: first order, separable, with $f(x)=e^x$ and $g(y)=\dfrac{1}{2y}$. Method: separate and integrate.
> Step 1, separate: $2y\,dy=e^x\,dx$.
> Step 2, integrate both sides: $\int2y\,dy=y^2$ and $\int e^x\,dx=e^x$. So $y^2=e^x+c$ (one constant).
> Step 3, initial condition $x=0$, $y=-3$: $(-3)^2=e^0+c$, so $9=1+c$ and $c=8$.
> Step 4, solve for $y$: $y^2=e^x+8$ gives $y=\sqrt{e^x+8}$ or $y=-\sqrt{e^x+8}$.
> At $x=0$ the first gives $+3$ and the second gives $-3$. The condition is $y(0)=-3$, so we must take the minus sign.
> Answer: $y=-\sqrt{e^x+8}$, valid for all $x$ (because $e^x+8>0$).
> Check: $y'=-\dfrac{e^x}{2\sqrt{e^x+8}}$. Right side: $\dfrac{e^x}{2y}=\dfrac{e^x}{-2\sqrt{e^x+8}}$. Equal. And $y(0)=-\sqrt9=-3$.

> [!question]- Check (slide 6): Find ALL solutions of $y'=2x(y-1)^2$. Then give the solution with $y(0)=2$ and the solution with $y(0)=1$.
> Type: first order, separable, with $f(x)=2x$ and $g(y)=(y-1)^2$.
> Step 1, separate (this needs $y\neq1$): $\dfrac{dy}{(y-1)^2}=2x\,dx$.
> Step 2, integrate: $\int(y-1)^{-2}\,dy=-\dfrac{1}{y-1}$ and $\int2x\,dx=x^2$. So $-\dfrac{1}{y-1}=x^2+c$.
> Step 3, solve for $y$: $y-1=-\dfrac{1}{x^2+c}$, so $y=1-\dfrac{1}{x^2+c}$ (general solution).
> Step 4, the excluded case $g(y)=0$, that is $y\equiv1$: then $y'=0$ and $2x\cdot0^2=0$. So $y\equiv1$ is also a solution. No value of $c$ gives it, because $\dfrac{1}{x^2+c}$ is never $0$.
> IVP $y(0)=2$: $2=1-\dfrac1c$, so $\dfrac1c=-1$ and $c=-1$. Then $y=1-\dfrac{1}{x^2-1}=1+\dfrac{1}{1-x^2}$ on $-1<x<1$.
> Check: $y'=\dfrac{2x}{(1-x^2)^2}$ and $2x(y-1)^2=2x\cdot\dfrac{1}{(1-x^2)^2}$. Equal. And $y(0)=1+1=2$.
> IVP $y(0)=1$: the formula would need $\dfrac1c=0$, which is impossible. The solution is the constant one, $y\equiv1$.

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

> [!question]- Check (slide 7): Solve $xy'+3y=x^2$ for $x>0$ with an integrating factor. Then explain what changes if you use $5\mu$ instead of $\mu$.
> Type: first order, linear, non-homogeneous. Method: integrating factor.
> Step 1, standard form (divide by $x$): $y'+\dfrac3x\,y=x$. So $p(x)=\dfrac3x$ and $q(x)=x$.
> Step 2, integrating factor: $\int p\,dx=3\ln x$, so $\mu=e^{3\ln x}=x^3$.
> Step 3, multiply the standard form by $x^3$: $x^3y'+3x^2y=x^4$.
> Step 4, the left side is one derivative: $(x^3y)'=x^3y'+3x^2y$. So $(x^3y)'=x^4$.
> Step 5, integrate: $x^3y=\dfrac{x^5}{5}+c$.
> Step 6, divide by $x^3$: $y=\dfrac{x^2}{5}+\dfrac{c}{x^3}$.
> Check: $y'=\dfrac{2x}{5}-\dfrac{3c}{x^4}$. Then $xy'=\dfrac{2x^2}{5}-\dfrac{3c}{x^3}$ and $3y=\dfrac{3x^2}{5}+\dfrac{3c}{x^3}$. The sum is $x^2$.
> With $5\mu=5x^3$: every line is multiplied by 5. $(5x^3y)'=5x^4$, $5x^3y=x^5+c_1$, $y=\dfrac{x^2}{5}+\dfrac{c_1/5}{x^3}$. This is the same family with $c=c_1/5$. A nonzero constant factor in $\mu$ does not matter (the remark on the slide).

> [!question]- Check (slide 8): Solve the IVP $y'-\dfrac{y}{x}=x\,e^{x}$, $y(1)=0$, for $x>0$.
> Type: first order, linear, already in standard form with $p(x)=-\dfrac1x$, $q(x)=xe^x$. Method: integrating factor.
> Step 1: $\int p\,dx=-\ln x$, so $\mu=e^{-\ln x}=\dfrac1x$.
> Step 2, multiply by $\dfrac1x$: $\dfrac1x\,y'-\dfrac{1}{x^2}\,y=e^x$.
> Step 3, the left side is $\left(\dfrac yx\right)'$, because $\left(\dfrac yx\right)'=\dfrac{y'}{x}-\dfrac{y}{x^2}$. So $\left(\dfrac yx\right)'=e^x$.
> Step 4, integrate: $\dfrac yx=e^x+c$.
> Step 5, multiply by $x$: $y=xe^x+cx$ (general solution).
> Step 6, initial condition $y(1)=0$: $1\cdot e^1+c\cdot1=0$, so $c=-e$.
> Answer: $y=xe^x-ex=x\,(e^x-e)$.
> Check: $y'=e^x+xe^x-e$ and $\dfrac yx=e^x-e$. Then $y'-\dfrac yx=e^x+xe^x-e-e^x+e=xe^x$. And $y(1)=1\cdot(e-e)=0$.

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

> [!question]- Check (slide 9): Is each function homogeneous? If yes, give the degree: (a) $f=\dfrac{\sqrt{x^4+y^4}}{x+y}$, (b) $f=\dfrac{x^3+xy^2}{x-y}$, (c) $f=xy+1$.
> Method: replace $x$ by $\alpha x$ and $y$ by $\alpha y$ and try to take a power of $\alpha$ out.
> (a) $f(\alpha x,\alpha y)=\dfrac{\sqrt{\alpha^4x^4+\alpha^4y^4}}{\alpha x+\alpha y}=\dfrac{\alpha^2\sqrt{x^4+y^4}}{\alpha(x+y)}=\alpha\,f(x,y)$. Homogeneous of degree 1. (Here $\sqrt{\alpha^4}=\alpha^2$.)
> (b) $f(\alpha x,\alpha y)=\dfrac{\alpha^3x^3+\alpha x\cdot\alpha^2y^2}{\alpha x-\alpha y}=\dfrac{\alpha^3(x^3+xy^2)}{\alpha(x-y)}=\alpha^2f(x,y)$. Homogeneous of degree 2.
> (c) $f(\alpha x,\alpha y)=\alpha^2xy+1$. If $f$ were homogeneous of degree $n$, then $\alpha^2xy+1=\alpha^n(xy+1)=\alpha^nxy+\alpha^n$ for all $x,y$. Comparing the $xy$ terms gives $\alpha^2=\alpha^n$. Comparing the constants gives $1=\alpha^n$. Then $\alpha^2=1$, which is false for $\alpha=2$. Not homogeneous (the same argument as the third example on the slide).

> [!question]- Check (slide 10): Which of these ODEs are homogeneous? For each homogeneous one, write the function $g$ with $y'=g(y/x)$: (a) $y'=\dfrac{x^2+y^2}{xy}$, (b) $y'=\dfrac{x^2+y}{x}$, (c) $y'=\dfrac{y-\sqrt{x^2+y^2}}{x}$ for $x>0$.
> (a) $f(\alpha x,\alpha y)=\dfrac{\alpha^2x^2+\alpha^2y^2}{\alpha x\cdot\alpha y}=\dfrac{\alpha^2(x^2+y^2)}{\alpha^2xy}=f(x,y)$. Degree 0, so the ODE is homogeneous. Divide term by term: $\dfrac{x^2}{xy}+\dfrac{y^2}{xy}=\dfrac xy+\dfrac yx$. So $g(t)=\dfrac1t+t$.
> (b) $f(\alpha x,\alpha y)=\dfrac{\alpha^2x^2+\alpha y}{\alpha x}=\dfrac{\alpha x^2+y}{x}$. This is not $f(x,y)$ unless $\alpha=1$. Not of degree 0, so the ODE is not homogeneous. (It is linear: $y'-\dfrac yx=x$.)
> (c) For $x>0$ we have $\sqrt{x^2+y^2}=x\sqrt{1+(y/x)^2}$. So $y'=\dfrac yx-\sqrt{1+\left(\dfrac yx\right)^2}$. Homogeneous, with $g(t)=t-\sqrt{1+t^2}$.

> [!question]- Check (slide 11): Solve the IVP $y'=\dfrac{x^2+y^2}{xy}$, $y(1)=2$.
> Type: first order, homogeneous, with $g(v)=\dfrac1v+v$ (see the check for slide 10). Method: $y=vx$.
> Step 1: $v=\dfrac yx$, $y=vx$, $y'=v+xv'$.
> Step 2, substitute: $v+xv'=\dfrac1v+v$.
> Step 3, subtract $v$: $xv'=\dfrac1v$. This is separable.
> Step 4, separate: $v\,dv=\dfrac{dx}{x}$.
> Step 5, integrate: $\dfrac{v^2}{2}=\ln|x|+c$.
> Step 6, multiply by 2 and write $C=2c$: $v^2=2\ln|x|+C$.
> Step 7, go back to $y$ with $v=\dfrac yx$: $y^2=x^2\,(2\ln|x|+C)$ (general solution, implicit).
> Step 8, initial condition $x=1$, $y=2$: $4=1\cdot(2\ln1+C)=C$. So $C=4$.
> Step 9, solve for $y$: near $x=1$ we have $x>0$ and $y>0$, so we take the positive root: $y=x\sqrt{2\ln x+4}$.
> It is valid while $2\ln x+4>0$, that is $x>e^{-2}\approx0.135$.
> Check: from $y^2=x^2(2\ln x+4)$, differentiate both sides: $2yy'=2x(2\ln x+4)+x^2\cdot\dfrac2x=\dfrac{2y^2}{x}+2x$. Divide by $2y$: $y'=\dfrac yx+\dfrac xy=\dfrac{y^2+x^2}{xy}$. And $y(1)=1\cdot\sqrt{0+4}=2$.

> [!question]- Check (slide 12): Solve $xy'=y+x\cos^2\!\left(\dfrac yx\right)$ for $x>0$ with $y(1)=\dfrac{\pi}{4}$. Which straight lines are solutions that the general formula does not give?
> Type: first order, homogeneous. Method: $y=vx$.
> Step 1, divide by $x$: $y'=\dfrac yx+\cos^2\!\left(\dfrac yx\right)$. So $g(v)=v+\cos^2v$.
> Step 2, put $y=vx$, $y'=v+xv'$: $v+xv'=v+\cos^2v$.
> Step 3, subtract $v$: $xv'=\cos^2v$.
> Step 4, separate (this needs $\cos v\neq0$): $\dfrac{dv}{\cos^2v}=\dfrac{dx}{x}$.
> Step 5, integrate: $\int\sec^2v\,dv=\tan v$. So $\tan v=\ln x+c$.
> Step 6, go back to $y$: $\tan\!\left(\dfrac yx\right)=\ln x+c$ (general solution, implicit).
> Step 7, initial condition $x=1$, $y=\dfrac\pi4$: $\tan\dfrac\pi4=\ln1+c$, so $1=0+c$ and $c=1$.
> Step 8, solve for $y$: $v(1)=\dfrac\pi4$ lies between $-\dfrac\pi2$ and $\dfrac\pi2$, so $v=\arctan(\ln x+1)$ and $y=x\arctan(\ln x+1)$.
> Check: $y'=\arctan(\ln x+1)+x\cdot\dfrac{1/x}{1+(\ln x+1)^2}=\dfrac yx+\dfrac{1}{1+\tan^2v}=\dfrac yx+\cos^2v$. And $y(1)=\arctan1=\dfrac\pi4$.
> Lost lines: the excluded case is $\cos v_0=0$, that is $v_0=\dfrac\pi2+k\pi$ ($k$ an integer). Then $g(v_0)=v_0$. For $y=v_0x$: left side $xy'=v_0x$, right side $v_0x+x\cdot0=v_0x$. So the lines $y=\left(\dfrac\pi2+k\pi\right)x$ are solutions. No $c$ gives them, because $\tan v$ is not defined there.

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

> [!info] The integral and the lost lines of the second example (beyond the slides)
> Slide 14 (top) computes $\int\dfrac{du}{\sin u+1}$ with one trick: multiply top and bottom by $\sin u-1$. The bottom becomes $\sin^2u-1=-\cos^2u$. So
> $$\frac{1}{\sin u+1}=\frac{\sin u-1}{-\cos^2u}=\frac{1}{\cos^2u}-\frac{\sin u}{\cos^2u}=\sec^2u-\sec u\tan u .$$
> Now both terms are known derivatives: $(\tan u)'=\sec^2u$ and $(\sec u)'=\sec u\tan u$. This gives $\tan u-\sec u$.
> Dividing by $\sin u+1$ needs $\sin u\neq-1$. The excluded constants are $u=-\dfrac\pi2+2k\pi$ ($k$ an integer). With $u=2x+2y+1$ these are the lines $y=-x-\dfrac12-\dfrac\pi4+k\pi$. On them $y'=-1$ and $\sin u=-1$, so they are also solutions. The slide does not list them.

> [!question]- Check (slide 13): Solve the IVP $y'=(2x+y)^2+7$, $y(0)=3$. Give $y$ explicitly.
> Type: first order, of the form $y'=F(Ax+By+C)$ with $A=2$, $B=1$, $C=0$, $F(u)=u^2+7$. Method: $u=2x+y$.
> Step 1: $u=2x+y$, so $u'=2+y'$.
> Step 2, substitute $y'=u^2+7$: $u'=2+u^2+7=u^2+9$. This is separable.
> Step 3, separate: $\dfrac{du}{u^2+9}=dx$.
> Step 4, the left integral: $\dfrac{1}{u^2+9}=\dfrac19\cdot\dfrac{1}{(u/3)^2+1}$. Put $t=\dfrac u3$, $du=3\,dt$: $\int\dfrac{du}{u^2+9}=\dfrac39\int\dfrac{dt}{t^2+1}=\dfrac13\arctan t=\dfrac13\arctan\dfrac u3$.
> Step 5: $\dfrac13\arctan\dfrac u3=x+c$.
> Step 6, initial condition: $x=0$, $y=3$ gives $u=2\cdot0+3=3$. Then $\dfrac13\arctan1=0+c$, so $c=\dfrac13\cdot\dfrac\pi4=\dfrac{\pi}{12}$.
> Step 7, solve for $u$: $\arctan\dfrac u3=3x+\dfrac\pi4$, so $u=3\tan\!\left(3x+\dfrac\pi4\right)$.
> Step 8, go back to $y=u-2x$: $y=3\tan\!\left(3x+\dfrac\pi4\right)-2x$.
> Check: $y(0)=3\tan\dfrac\pi4-0=3$. And $y'=9\sec^2\!\left(3x+\dfrac\pi4\right)-2=9\left(1+\tan^2\right)-2=9\tan^2\!\left(3x+\dfrac\pi4\right)+7=u^2+7$.
> The solution lives where $-\dfrac\pi2<3x+\dfrac\pi4<\dfrac\pi2$, that is $-\dfrac\pi4<x<\dfrac{\pi}{12}$.

> [!question]- Check (slide 14, top): Find the general solution of $y'=\cos(x+y)$. Which lines are lost when you divide?
> Type: first order, $y'=F(Ax+By+C)$ with $A=B=1$, $C=0$, $F(u)=\cos u$. Method: $u=x+y$.
> Step 1: $u=x+y$, so $u'=1+y'=1+\cos u$. This is separable.
> Step 2, separate (this needs $1+\cos u\neq0$): $\dfrac{du}{1+\cos u}=dx$.
> Step 3, the left integral: use $1+\cos u=2\cos^2\dfrac u2$. Then $\int\dfrac{du}{1+\cos u}=\int\dfrac12\sec^2\dfrac u2\,du=\tan\dfrac u2$.
> Step 4: $\tan\dfrac u2=x+c$.
> Step 5, put $u$ back: $\tan\dfrac{x+y}{2}=x+c$ (general solution, implicit).
> Step 6, explicit form: $\tan$ has period $\pi$, so $\dfrac{x+y}{2}=\arctan(x+c)+k\pi$ and $y=2\arctan(x+c)-x+2k\pi$. Do not drop $2k\pi$: for example $y(0)=2\pi$ needs $k=1$, $c=0$.
> Check: $y'=\dfrac{2}{1+(x+c)^2}-1$. With $w=\dfrac{x+y}{2}$ and $\tan w=x+c$: $\cos(x+y)=\cos 2w=\dfrac{1-\tan^2w}{1+\tan^2w}=\dfrac{1-(x+c)^2}{1+(x+c)^2}=\dfrac{2}{1+(x+c)^2}-1$. Equal.
> Lost lines: $1+\cos u=0$ means $u=\pi+2k\pi$ ($k$ an integer), that is $y=-x+\pi+2k\pi$. There $y'=-1$ and $\cos(x+y)=\cos(\pi+2k\pi)=-1$. So these lines are also solutions.

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

> [!info] When the test fails: an integrating factor (beyond the slides)
> If $M_y\neq N_x$, we can try to multiply the equation by a function $\mu$ so that the new equation is exact. For $\mu=\mu(x)$ we need $(\mu M)_y=(\mu N)_x$, that is $\mu M_y=\mu'N+\mu N_x$. So
> $$\frac{\mu'}{\mu}=\frac{M_y-N_x}{N}.$$
> This works when the right side depends on $x$ only. Call it $h(x)$. Then $\mu=e^{\int h(x)\,dx}$. (In the same way, if $\dfrac{N_x-M_y}{M}=k(y)$ depends on $y$ only, then $\mu=e^{\int k(y)\,dy}$.)
> Example: $(3xy+y^2)\,dx+(x^2+xy)\,dy=0$. Here $M_y=3x+2y$ and $N_x=2x+y$. They are different, so the ODE is not exact.
> $\dfrac{M_y-N_x}{N}=\dfrac{x+y}{x(x+y)}=\dfrac1x$, a function of $x$ only. So $\mu=e^{\ln x}=x$.
> Multiply by $x$: $(3x^2y+xy^2)\,dx+(x^3+x^2y)\,dy=0$. Now $M_y=3x^2+2xy$ and $N_x=3x^2+2xy$: exact.
> $u=\int(3x^2y+xy^2)\,dx=x^3y+\dfrac{x^2y^2}{2}+\phi(y)$. Then $u_y=x^3+x^2y+\phi'(y)$ must equal $x^3+x^2y$, so $\phi'=0$.
> Solution: $x^3y+\dfrac{x^2y^2}{2}=c$.

> [!question]- Check (slide 14, exact equations): The function $u(x,y)=x^3y^2+e^{x}y$ is a potential function. Write the exact ODE $M\,dx+N\,dy=0$ that it belongs to, confirm $M_y=N_x$, and give the solution through the point $(0,2)$.
> Step 1: $M=u_x=3x^2y^2+e^xy$ and $N=u_y=2x^3y+e^x$.
> Step 2, the ODE: $(3x^2y^2+e^xy)\,dx+(2x^3y+e^x)\,dy=0$. It says $du=0$.
> Step 3, the test: $M_y=6x^2y+e^x$ and $N_x=6x^2y+e^x$. They are equal. Both are the mixed derivative $u_{xy}=u_{yx}$, and this is the reason why the test works.
> Step 4, general solution: $x^3y^2+e^xy=c$.
> Step 5, the point $x=0$, $y=2$: $0\cdot4+e^0\cdot2=c$, so $c=2$.
> Answer: $x^3y^2+e^xy=2$ (an implicit solution).

> [!question]- Check (slide 15): Show that $(y\cos x+2xe^{y})\,dx+(\sin x+x^2e^{y}-1)\,dy=0$ is exact. Solve it by starting from $u_y=N$, as the slide does.
> Type: first order, written as $M\,dx+N\,dy=0$. Method: exactness test, then find the potential.
> Step 1: $M=y\cos x+2xe^y$ and $N=\sin x+x^2e^y-1$.
> Step 2, the test: $M_y=\cos x+2xe^y$ and $N_x=\cos x+2xe^y$. Equal, so the ODE is exact on the whole plane.
> Step 3, integrate $N$ in $y$ with $x$ held constant: $u=\int(\sin x+x^2e^y-1)\,dy=y\sin x+x^2e^y-y+\psi(x)$.
> Step 4, differentiate in $x$: $u_x=y\cos x+2xe^y+\psi'(x)$.
> Step 5, set $u_x=M$: $y\cos x+2xe^y+\psi'(x)=y\cos x+2xe^y$, so $\psi'(x)=0$ and $\psi$ is a constant. Take $\psi=0$.
> Step 6: $u=y\sin x+x^2e^y-y$.
> Answer: $y\sin x+x^2e^y-y=c$.
> Check: $u_x=y\cos x+2xe^y=M$ and $u_y=\sin x+x^2e^y-1=N$.

> [!question]- Check (slide 16): Solve the IVP $\dfrac{2x}{y}\,dx+\left(3y^2-\dfrac{x^2}{y^2}\right)dy=0$, $y(1)=1$.
> Type: first order, $M\,dx+N\,dy=0$. Method: exactness test, potential, then the initial condition.
> Step 1: $M=\dfrac{2x}{y}$ and $N=3y^2-\dfrac{x^2}{y^2}$. Both are continuous with continuous partial derivatives on the region $y>0$, which contains the point $(1,1)$.
> Step 2, the test: $M_y=-\dfrac{2x}{y^2}$ and $N_x=-\dfrac{2x}{y^2}$. Equal, so the ODE is exact for $y>0$.
> Step 3, integrate $M$ in $x$ with $y$ held constant: $u=\int\dfrac{2x}{y}\,dx=\dfrac{x^2}{y}+\phi(y)$.
> Step 4, differentiate in $y$: $u_y=-\dfrac{x^2}{y^2}+\phi'(y)$.
> Step 5, set $u_y=N$: $-\dfrac{x^2}{y^2}+\phi'(y)=3y^2-\dfrac{x^2}{y^2}$, so $\phi'(y)=3y^2$. It depends on $y$ only, as it must.
> Step 6: $\phi(y)=y^3$ (take the constant $0$). So $u=\dfrac{x^2}{y}+y^3$.
> Step 7, general solution: $\dfrac{x^2}{y}+y^3=c$.
> Step 8, initial condition $x=1$, $y=1$: $\dfrac11+1=c$, so $c=2$.
> Answer: $\dfrac{x^2}{y}+y^3=2$.
> Check: differentiate the answer in $x$ with $y=y(x)$: $\dfrac{2x}{y}-\dfrac{x^2}{y^2}\,y'+3y^2y'=0$. This is $M+Ny'=0$. At $(1,1)$: $1+1=2$.

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

> [!question]- Check (slide 17): Find all solutions of $y'+\dfrac{y}{x}=x\,y^2$ for $x>0$.
> Type: first order, Bernoulli with $p=\dfrac1x$, $q=x$, $\alpha=2$. Method: $v=y^{1-\alpha}=y^{-1}$.
> Step 1, divide by $y^2$ (this needs $y\neq0$): $y^{-2}y'+\dfrac1x\,y^{-1}=x$.
> Step 2: $v=y^{-1}$, so $v'=-y^{-2}y'$, that is $y^{-2}y'=-v'$.
> Step 3, substitute: $-v'+\dfrac1x\,v=x$.
> Step 4, multiply by $-1$: $v'-\dfrac1x\,v=-x$. This is linear in $v$.
> Step 5, integrating factor: $\mu=e^{\int-\frac1x\,dx}=e^{-\ln x}=\dfrac1x$.
> Step 6, multiply by $\dfrac1x$: $\dfrac{v'}{x}-\dfrac{v}{x^2}=-1$, that is $\left(\dfrac vx\right)'=-1$.
> Step 7, integrate: $\dfrac vx=-x+c$, so $v=cx-x^2$.
> Step 8, go back with $y=v^{-1}$: $y=\dfrac{1}{cx-x^2}$.
> Step 9, the lost solution: $y\equiv0$ gives $0+0=x\cdot0$. It is a solution, and no $c$ gives it.
> Check: $y'=-\dfrac{c-2x}{(cx-x^2)^2}$ and $\dfrac yx=\dfrac{1}{x(cx-x^2)}=\dfrac{cx-x^2}{x(cx-x^2)^2}$. Sum: $\dfrac{-x(c-2x)+cx-x^2}{x(cx-x^2)^2}=\dfrac{x^2}{x(cx-x^2)^2}=\dfrac{x}{(cx-x^2)^2}=x\,y^2$.

> [!question]- Check (slide 18): Solve the IVP $y'+y=\dfrac{x}{y}$, $y(0)=1$.
> Type: first order, Bernoulli with $p=1$, $q=x$, $\alpha=-1$ (because $\dfrac xy=x\,y^{-1}$). Method: $v=y^{1-\alpha}=y^{2}$.
> Step 1, divide by $y^{-1}$, that is multiply by $y$: $y\,y'+y^2=x$.
> Step 2: $v=y^2$, so $v'=2y\,y'$, that is $y\,y'=\dfrac{v'}{2}$.
> Step 3, substitute: $\dfrac{v'}{2}+v=x$.
> Step 4, multiply by 2: $v'+2v=2x$. This is linear in $v$.
> Step 5, integrating factor: $\mu=e^{\int2\,dx}=e^{2x}$.
> Step 6: $(e^{2x}v)'=2xe^{2x}$.
> Step 7, integrate by parts with $f=x$, $g'=2e^{2x}$, $g=e^{2x}$: $\int2xe^{2x}\,dx=xe^{2x}-\int e^{2x}\,dx=xe^{2x}-\dfrac12e^{2x}+c$.
> Step 8: $e^{2x}v=xe^{2x}-\dfrac12e^{2x}+c$. Divide by $e^{2x}$: $v=x-\dfrac12+ce^{-2x}$.
> Step 9, initial condition: $y(0)=1$ gives $v(0)=1^2=1$. Then $1=0-\dfrac12+c$, so $c=\dfrac32$.
> Step 10, go back: $y^2=x-\dfrac12+\dfrac32e^{-2x}$. Since $y(0)=1>0$, take the positive root.
> Answer: $y=\sqrt{x-\dfrac12+\dfrac32e^{-2x}}$.
> Check: $v'=1-3e^{-2x}$ and $2v=2x-1+3e^{-2x}$, so $v'+2v=2x$. And $y(0)=\sqrt{-\dfrac12+\dfrac32}=1$.
> Interval: $v'=0$ gives $e^{-2x}=\dfrac13$, $x=\dfrac{\ln3}{2}$. There $v=\dfrac{\ln3}{2}-\dfrac12+\dfrac32\cdot\dfrac13=\dfrac{\ln3}{2}\approx0.549>0$. This is the minimum of $v$, so $v>0$ and the solution is valid for all $x$.
> Note: here $\alpha<0$, so $y\equiv0$ is not a solution ($\dfrac xy$ is not defined at $y=0$).

## 9. Riccati equation (slides 19-20)
![[math501_lecture_01_math501_chapter_1_p019.jpg]]
![[math501_lecture_01_math501_chapter_1_p020.jpg]]

**Notes.** Form: $y'+p(x)y=q(x)y^2+r(x)$. It needs one known solution $\phi(x)$. Check first that $\phi$ really solves the ODE.

- $y=\phi+z$ gives a Bernoulli equation with $\alpha=2$.
- $y=\phi+\dfrac1u$ gives a linear equation for $u$. Use this one.

With $y'=\phi'-\dfrac{u'}{u^2}$ the terms without $u$ cancel. Multiply by $-u^2$ and solve with an integrating factor.

> [!example] Slide example
> $y'=\tfrac{y^2}{x}+\tfrac yx-\tfrac2x$, $\phi=1$. With $y=1+\tfrac1u$: $u'+\tfrac3xu=-\tfrac1x$, $\mu=x^3$, $u=-\tfrac13+\tfrac{c}{x^3}$. Answer: $y=1+\dfrac{3x^3}{3c-x^3}$, together with $y=1$.

> [!info] The linear equation for u in general (beyond the slides)
> Put $y=\phi+\dfrac1u$ into $y'+py=qy^2+r$. The left side is $\phi'-\dfrac{u'}{u^2}+p\phi+\dfrac pu$. The right side is $q\phi^2+\dfrac{2q\phi}{u}+\dfrac{q}{u^2}+r$.
> Because $\phi$ is a solution, $\phi'+p\phi=q\phi^2+r$. These terms cancel. What is left is $-\dfrac{u'}{u^2}+\dfrac pu=\dfrac{2q\phi}{u}+\dfrac{q}{u^2}$.
> Multiply by $-u^2$: $u'-pu=-2q\phi\,u-q$. So
> $$u'+\bigl(2q\phi-p\bigr)u=-q .$$
> Slide example: $p=-\dfrac1x$, $q=\dfrac1x$, $\phi=1$ give $u'+\dfrac3x\,u=-\dfrac1x$, the same equation as on the slide. Use this formula to check your own substitution.
> The solution $y=\phi$ itself is never of the form $\phi+\dfrac1u$, so always list it next to the general solution.

> [!question]- Check (slide 19): The function $\phi(x)=\dfrac1x$ solves $y'=y^2-\dfrac{y}{x}-\dfrac{1}{x^2}$ for $x>0$. Verify this, then find the general solution with $y=\phi+\dfrac1u$.
> Type: first order, Riccati ($y'+\dfrac1x\,y=y^2-\dfrac{1}{x^2}$, so $p=\dfrac1x$, $q=1$, $r=-\dfrac{1}{x^2}$). Method: $y=\phi+\dfrac1u$, then a linear ODE for $u$.
> Step 1, verify $\phi$: $\phi'=-\dfrac{1}{x^2}$. Right side: $\dfrac{1}{x^2}-\dfrac{1}{x}\cdot\dfrac1x-\dfrac{1}{x^2}=-\dfrac{1}{x^2}$. Equal, so $\phi$ is a solution.
> Step 2: $y=\dfrac1x+\dfrac1u$, so $y'=-\dfrac{1}{x^2}-\dfrac{u'}{u^2}$.
> Step 3, the right side, term by term: $y^2=\dfrac{1}{x^2}+\dfrac{2}{xu}+\dfrac{1}{u^2}$ and $-\dfrac yx=-\dfrac{1}{x^2}-\dfrac{1}{xu}$. Together with $-\dfrac{1}{x^2}$:
> $$y^2-\frac yx-\frac{1}{x^2}=-\frac{1}{x^2}+\frac{1}{xu}+\frac{1}{u^2}.$$
> Step 4, set left = right: $-\dfrac{1}{x^2}-\dfrac{u'}{u^2}=-\dfrac{1}{x^2}+\dfrac{1}{xu}+\dfrac{1}{u^2}$. The terms $-\dfrac{1}{x^2}$ cancel: $-\dfrac{u'}{u^2}=\dfrac{1}{xu}+\dfrac{1}{u^2}$.
> Step 5, multiply by $-u^2$: $u'=-\dfrac ux-1$, that is $u'+\dfrac1x\,u=-1$. Linear.
> Step 6, integrating factor: $\mu=e^{\int\frac1x\,dx}=e^{\ln x}=x$. Then $(xu)'=-x$.
> Step 7, integrate: $xu=-\dfrac{x^2}{2}+c$, so $u=\dfrac{2c-x^2}{2x}$.
> Step 8, go back: $\dfrac1u=\dfrac{2x}{2c-x^2}$. With $C=2c$: $y=\dfrac1x+\dfrac{2x}{C-x^2}$.
> All solutions: this family and $y=\dfrac1x$ itself.
> Check with $C=0$: $y=\dfrac1x-\dfrac2x=-\dfrac1x$. Then $y'=\dfrac{1}{x^2}$ and $y^2-\dfrac yx-\dfrac{1}{x^2}=\dfrac{1}{x^2}+\dfrac{1}{x^2}-\dfrac{1}{x^2}=\dfrac{1}{x^2}$. Equal.

> [!question]- Check (slide 20): Use the general solution $y=1+\dfrac{3x^3}{3c-x^3}$ of the slide example $y'=\dfrac{y^2}{x}+\dfrac yx-\dfrac2x$. (a) Show how the first form on the slide becomes the second. (b) Find the solution with $y(1)=2$. (c) Which solution has $y(1)=1$?
> (a) Multiply top and bottom of $\dfrac{1}{-\frac13+\frac{c}{x^3}}$ by $3x^3$: the top is $3x^3$, the bottom is $-x^3+3c$. So it equals $\dfrac{3x^3}{3c-x^3}$.
> (b) Put $x=1$, $y=2$: $2=1+\dfrac{3}{3c-1}$, so $\dfrac{3}{3c-1}=1$, $3c-1=3$, $c=\dfrac43$. Then $3c=4$ and
> $$y=1+\frac{3x^3}{4-x^3},\qquad 0<x<4^{1/3}\approx1.587 .$$
> Check of the condition: $y(1)=1+\dfrac33=2$.
> Check of the ODE: quotient rule, $y'=\dfrac{9x^2(4-x^3)+3x^3\cdot3x^2}{(4-x^3)^2}=\dfrac{36x^2}{(4-x^3)^2}$.
> Right side: $\dfrac{y^2+y-2}{x}=\dfrac{(y-1)(y+2)}{x}$. Here $y-1=\dfrac{3x^3}{4-x^3}$ and $y+2=\dfrac{3(4-x^3)+3x^3}{4-x^3}=\dfrac{12}{4-x^3}$. The product divided by $x$ is $\dfrac{36x^3}{x\,(4-x^3)^2}=\dfrac{36x^2}{(4-x^3)^2}$. Equal.
> (c) $1=1+\dfrac{3}{3c-1}$ would need $\dfrac{3}{3c-1}=0$, which is impossible. The solution is the known one, $y\equiv1$. It is not in the family for any $c$.

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
