---
course: MATH 501 Advanced Engineering Mathematics
lesson: MATH501 L02 - Higher order linear ODEs
type: quiz
questions: 25
---

# MATH501 L02 - Higher order linear ODEs - quiz

Lesson note: [[MATH501 L02 - Higher order linear ODEs]]. One question per check question of the lesson. Pick an option, then open the answer.

## 1. Linear dependence, independence, Wronskian (slides 1-2)

### Q1 (slide 1)

Find constants $(c_1,c_2,c_3)$, not all zero, with $c_1(x+1)+c_2(x-1)+c_3x=0$ for all $x$. If no such constants exist, the functions $x+1$, $x-1$, $x$ are independent. Which answer is correct?

- A) $(c_1,c_2,c_3)=(1,1,2)$
- B) $(c_1,c_2,c_3)=(1,1,-1)$
- C) None exist, so the functions are independent
- D) $(c_1,c_2,c_3)=(1,1,-2)$

> [!success]- Answer
> **D.** Collect powers of $x$: $(c_1+c_2+c_3)x+(c_1-c_2)=0$ for all $x$.
> So $c_1-c_2=0$ and $c_1+c_2+c_3=0$. Take $c_1=1$: $c_2=1$, $c_3=-2$.
> Check: $(x+1)+(x-1)-2x=0$. The constants are not all zero, so the functions are dependent.
> - A: Sign slip: $c_3=c_1+c_2$ instead of $c_3=-(c_1+c_2)$. The sum is $(x+1)+(x-1)+2x=4x\neq0$.
> - B: $c_2$ is left out of $c_3=-(c_1+c_2)$, so $c_3=-1$. The sum is $(x+1)+(x-1)-x=x\neq0$.
> - C: This uses the ratio rule: no two of them are proportional. The ratio rule works for two functions only. The constants $(1,1,-2)$ exist.

### Q2 (slide 2, Wronskian)

Let $f=x^2$ and $g=x^2\ln x$ on $x>0$. The Wronskian is the determinant with first row $f,\ g$ and second row $f',\ g'$. What is $W$?

- A) $W=-x^3$
- B) $W=x^3$
- C) $W=0$
- D) $W=x^3+4x^3\ln x$

> [!success]- Answer
> **B.** $f'=2x$. Product rule: $g'=2x\ln x+x^2\cdot\tfrac1x=2x\ln x+x$.
> $W=fg'-gf'=x^2(2x\ln x+x)-x^2\ln x\cdot2x=x^3$.
> $W(1)=1\neq0$, so $f$ and $g$ are independent on $(0,\infty)$.
> - A: Wrong order: $gf'-fg'$. This is the determinant with the two columns swapped.
> - C: The second product-rule term $x^2\cdot\tfrac1x$ is lost: $g'=2x\ln x$. Then $2x^3\ln x-2x^3\ln x=0$.
> - D: Plus sign instead of minus: $fg'+gf'=2x^3\ln x+x^3+2x^3\ln x$.

## 2. Second order linear ODEs: superposition and basis (slides 2-3)

### Q3 (slide 2, section 2.2)

Standard form: $y''+P(x)y'+Q(x)y=R(x)$; linear homogeneous means $R\equiv0$. Four ODEs: (a) $y''+x^2y'-y=0$, (b) $y''+3y'+2y=\sin x$, (c) $y''+y\,y'=0$, (d) $xy''+y'=x^2$ for $x>0$. Which statement is correct?

- A) (a) is nonlinear, because the coefficient $x^2$ is not constant.
- B) (b) is homogeneous, because its coefficients $3$ and $2$ are constant.
- C) (d) is linear and non-homogeneous, with $P=\tfrac1x$ and $R=x$.
- D) (c) is linear and homogeneous, with $P=y$ and $Q=0$.

> [!success]- Answer
> **C.** Divide (d) by $x$ to reach the standard form: $y''+\tfrac1xy'=x$.
> So $P=\tfrac1x$, $Q=0$, $R=x\neq0$: linear and non-homogeneous.
> - A: Linear does not mean constant coefficients. $P=x^2$ depends on $x$ only. (a) is linear and homogeneous.
> - B: Homogeneous means $R\equiv0$. Here $R=\sin x\neq0$, so (b) is non-homogeneous.
> - D: $P$ may depend on $x$ only. $y\,y'$ is a product of $y$ and $y'$, so (c) is nonlinear.

### Q4 (slide 3)

$y_1=\cosh x$ and $y_2=\sinh x$ form a basis of solutions of $y''-y=0$. Which function solves the IVP $y''-y=0$, $y(0)=2$, $y'(0)=-3$?

- A) $y=-3\cosh x+2\sinh x$
- B) $y=2\cosh x-3\sinh x$
- C) $y=2\cos x-3\sin x$
- D) $y=2e^{x}-3e^{-x}$

> [!success]- Answer
> **B.** $y=c_1\cosh x+c_2\sinh x$ and $y'=c_1\sinh x+c_2\cosh x$.
> $\cosh0=1$, $\sinh0=0$. So $y(0)=c_1=2$ and $y'(0)=c_2=-3$.
> Check: $y''=y$, $y(0)=2$, $y'(0)=-3$.
> - A: The constants are swapped, as if $\cosh0=0$ and $\sinh0=1$. Then $y(0)=-3$.
> - C: This is the basis of $y''+y=0$. It fits the conditions, but $y''-y=-2y\neq0$.
> - D: The rule $c_1=y(0)$, $c_2=y'(0)$ is carried over to the basis $e^x,e^{-x}$. There it fails: $y(0)=-1$.

## 3. Constant coefficients, second order (slides 3-7)

### Q5 (slide 4)

Solve the IVP $y''-y'-6y=0$, $y(0)=1$, $y'(0)=8$.

- A) $y=2e^{3x}-e^{-2x}$
- B) $y=6e^{3x}-5e^{-2x}$
- C) $y=-e^{3x}+2e^{-2x}$
- D) $y=-\tfrac65e^{-3x}+\tfrac{11}5e^{2x}$

> [!success]- Answer
> **A.** $\lambda^2-\lambda-6=(\lambda-3)(\lambda+2)=0$, so $\lambda=3,-2$ and $y=c_1e^{3x}+c_2e^{-2x}$.
> $y(0)=c_1+c_2=1$, $y'(0)=3c_1-2c_2=8$. So $5c_1-2=8$, $c_1=2$, $c_2=-1$.
> - B: The minus sign from $(e^{-2x})'$ is lost: $3c_1+2c_2=8$. Then $c_1=6$, $c_2=-5$, and $y'(0)=28$.
> - C: The two constants are put on the wrong exponentials. Then $y'(0)=-3-4=-7$.
> - D: Root signs flipped: $(\lambda+3)(\lambda-2)$ gives $\lambda=-3,2$. These are not roots of $\lambda^2-\lambda-6$.

### Q6 (slide 5, reduction of order)

$y_1=e^{2x}$ solves $y''-4y'+4y=0$. Put $y_2=u(x)e^{2x}$ into the ODE. Which equation for $u$ and which second solution result?

- A) $u''-2u'+u=0$, so $y_2=xe^{3x}$
- B) $u''=0$, so $y_2=x^2e^{2x}$
- C) $u''-2u'+u=0$, so $y_2=e^{3x}$
- D) $u''=0$, so $y_2=xe^{2x}$

> [!success]- Answer
> **D.** $y_2'=(u'+2u)e^{2x}$, $y_2''=(u''+4u'+4u)e^{2x}$.
> ODE: $\left[u''+(4-4)u'+(4-8+4)u\right]e^{2x}=u''e^{2x}=0$, so $u''=0$.
> $u=cx+d$. Take $u=x$: $y_2=xe^{2x}$, and $W=e^{4x}\neq0$.
> - A: $(e^{2x})'$ is taken as $e^{2x}$, as in C, and the double root $1$ of the $u$-equation gives $u=xe^x$. But $xe^{3x}$ does not solve the ODE.
> - B: $u''=0$ is right, but integrating twice gives $u=cx+d$, not $x^2$. $x^2e^{2x}$ does not solve the ODE.
> - C: $(e^{2x})'$ is taken as $e^{2x}$: $y_2'=(u'+u)e^{2x}$. Then $u=e^x$. But $e^{3x}$ does not solve the ODE.

### Q7 (slides 5-6, repeated root example)

Solve the IVP $4y''+4y'+y=0$, $y(0)=2$, $y'(0)=1$.

- A) $y=(2+x)e^{-x/2}$
- B) $y=2e^{-x/2}$
- C) $y=(2+2x)e^{-x/2}$
- D) $y=2e^{x/2}$

> [!success]- Answer
> **C.** $4\lambda^2+4\lambda+1=(2\lambda+1)^2=0$: $\lambda=-\tfrac12$ (double). $y=(c_1+c_2x)e^{-x/2}$.
> $y'=-\tfrac12c_1e^{-x/2}+c_2\left(1-\tfrac x2\right)e^{-x/2}$.
> $y(0)=c_1=2$. $y'(0)=-\tfrac12c_1+c_2=1$, so $c_2=2$.
> - A: The term $-\tfrac12c_1$ from the product rule is lost: $y'(0)=c_2=1$. Then $y'(0)$ is really $0$.
> - B: Repeated root written as $c_1e^{-x/2}+c_2e^{-x/2}$, without the $x$. This is one constant, fixed by $y(0)$. Then $y'(0)=-1$.
> - D: Wrong root sign: $\lambda=+\tfrac12$. Then $c_2=0$. But $\lambda=\tfrac12$ gives $4+2+1\neq0$.

### Q8 (slide 6, complex roots)

Solve the IVP $y''-4y'+13y=0$, $y(0)=1$, $y'(0)=8$.

- A) $y=e^{3x}\left(\cos2x+\tfrac52\sin2x\right)$
- B) $y=e^{2x}\left(\cos3x+2\sin3x\right)$
- C) $y=e^{2x}\left(\cos3x+\tfrac83\sin3x\right)$
- D) $y=e^{-2x}\left(\cos3x+\tfrac{10}3\sin3x\right)$

> [!success]- Answer
> **B.** $\lambda^2-4\lambda+13=0$: $\lambda=\tfrac{4\pm6i}2=2\pm3i$. $y=e^{2x}(c_1\cos3x+c_2\sin3x)$.
> $y(0)=c_1=1$. $y'(0)=2c_1+3c_2=8$, so $c_2=2$.
> - A: $\alpha$ and $\beta$ swapped: $e^{3x}$ and $\cos2x$. Then $3c_1+2c_2=8$. This does not solve the ODE.
> - C: The product rule term $2c_1$ is lost: $3c_2=8$. Then $y'(0)=2+8=10$.
> - D: Wrong sign of $\alpha$: $\alpha=-2$ instead of $-\tfrac{(-4)}2=2$. This does not solve the ODE.

### Q9 (slide 7)

Solve the IVP $y''+9y=0$, $y(0)=3$, $y'(0)=-6$. Which option gives the solution and its behaviour for large $x$?

- A) $y=3\cos3x-6\sin3x$; it neither grows nor decays
- B) $y=\tfrac12e^{3x}+\tfrac52e^{-3x}$; it grows
- C) $y=3\cos3x-2\sin3x$; it neither grows nor decays
- D) $y=(3-15x)e^{3x}$; it grows

> [!success]- Answer
> **C.** $\lambda^2=-9$, $\lambda=\pm3i$, $\alpha=0$. $y=c_1\cos3x+c_2\sin3x$.
> $y(0)=c_1=3$. $y'(0)=3c_2=-6$, so $c_2=-2$.
> No factor $e^{\alpha x}$: constant amplitude $\sqrt{13}$, no growth, no decay.
> - A: $c_2=y'(0)$ without the factor 3 from $(\sin3x)'=3\cos3x$. Then $y'(0)=-18$.
> - B: $\lambda^2=9$ instead of $-9$: real roots $\pm3$. These do not solve $\lambda^2+9=0$.
> - D: Wrong factoring: $\lambda^2+9=(\lambda-3)^2$, double root $3$. But $(\lambda-3)^2=\lambda^2-6\lambda+9$.

## 4. Constant coefficients, order n (slides 7-9)

### Q10 (slide 8)

Solve the IVP $y'''-3y'+2y=0$, $y(0)=2$, $y'(0)=0$, $y''(0)=7$.

- A) $y=(1-x)e^{-x}+e^{2x}$
- B) $y=\tfrac56e^x+\tfrac32xe^x+\tfrac76e^{-2x}$
- C) $y=-7e^x-11xe^x+9e^{-2x}$
- D) $y=e^x+xe^x+e^{-2x}$

> [!success]- Answer
> **D.** $\lambda=1$ is a root, and $\lambda^3-3\lambda+2=(\lambda-1)^2(\lambda+2)$. So $y=c_1e^x+c_2xe^x+c_3e^{-2x}$.
> At $x=0$: $c_1+c_3=2$, $c_1+c_2-2c_3=0$, $c_1+2c_2+4c_3=7$.
> Then $c_3=1$, $c_2=1$, $c_1=1$.
> - A: Root signs flipped: $(\lambda+1)^2(\lambda-2)$, the roots of $\lambda^3-3\lambda-2$. This does not solve the ODE.
> - B: $(xe^x)''$ is taken as $e^x+xe^x$ instead of $2e^x+xe^x$. Then the third condition reads $c_1+c_2+4c_3=7$ and $y''(0)$ is really $\tfrac{17}2$.
> - C: The minus sign from $(e^{-2x})'$ is lost: $c_1+c_2+2c_3=0$. Then $y'(0)=-36$.

### Q11 (slide 9, fourth order)

Find the general solution of $y^{(4)}+8y''+16y=0$.

- A) $c_1\cos2x+c_2\sin2x+c_3x\cos2x+c_4x\sin2x$
- B) $c_1\cos2x+c_2\sin2x+c_3\cos2x+c_4\sin2x$
- C) $(c_1+c_2x)e^{2x}+(c_3+c_4x)e^{-2x}$
- D) $c_1\cos4x+c_2\sin4x+c_3x\cos4x+c_4x\sin4x$

> [!success]- Answer
> **A.** $\lambda^4+8\lambda^2+16=(\lambda^2+4)^2=0$: $\lambda=\pm2i$, each double.
> A double pair gives $\cos2x$, $\sin2x$ and $x\cos2x$, $x\sin2x$: four independent solutions.
> - B: The repeated pair is written twice without the factor $x$. These are only two independent functions.
> - C: $\lambda^2=4$ instead of $-4$. These functions do not solve the ODE.
> - D: $\lambda=\pm4i$ from $\lambda^2=-4$: the square root is forgotten. These do not solve the ODE.

### Q12 (slide 9, section 2.5)

$y_p=2x$ is a particular solution of $y''+4y=8x$. Which function solves the IVP $y''+4y=8x$, $y(0)=1$, $y'(0)=0$?

- A) $y=\cos2x+2x$
- B) $y=\cos2x-2\sin2x+2x$
- C) $y=\cos2x-\sin2x+2x$
- D) $y=e^{-2x}+2x$

> [!success]- Answer
> **C.** $y_h=c_1\cos2x+c_2\sin2x$ (roots $\pm2i$). $y=c_1\cos2x+c_2\sin2x+2x$.
> $y(0)=c_1=1$. $y'(0)=2c_2+2=0$, so $c_2=-1$.
> - A: The conditions are applied to $y_h$ alone: $2c_2=0$. The full $y$ then has $y'(0)=2$.
> - B: The factor 2 in $(\sin2x)'=2\cos2x$ is lost: $c_2+2=0$. Then $y'(0)=-2$.
> - D: $\lambda=\pm2$ instead of $\pm2i$. Then $e^{-2x}$ does not solve $y''+4y=0$.

## 5. Variation of parameters (slides 10-12)

### Q13 (slide 10)

Use variation of parameters for $y''-3y'+2y=e^{3x}$ with $y_1=e^x$, $y_2=e^{2x}$ (integration constants zero). Which $y_p=u_1y_1+u_2y_2$ results?

- A) $y_p=\tfrac32e^{3x}$
- B) $y_p=-\tfrac12e^{3x}$
- C) $y_p=\tfrac12e^{4x}-e^{2x}$
- D) $y_p=\tfrac12e^{3x}$

> [!success]- Answer
> **D.** System: $u_1'e^x+u_2'e^{2x}=0$, $u_1'e^x+2u_2'e^{2x}=e^{3x}$.
> Subtract: $u_2'e^{2x}=e^{3x}$, $u_2'=e^x$. Then $u_1'=-e^{2x}$.
> $u_1=-\tfrac12e^{2x}$, $u_2=e^x$. $y_p=-\tfrac12e^{3x}+e^{3x}=\tfrac12e^{3x}$.
> - A: The minus sign of $u_1'=-y_2R/W$ is lost: $u_1=\tfrac12e^{2x}$. Then $y_p''-3y_p'+2y_p=3e^{3x}$.
> - B: Wronskian sign wrong: $W=y_2y_1'-y_1y_2'=-e^{3x}$. Both $u_1$ and $u_2$ flip sign.
> - C: $y_1$ and $y_2$ swapped in the formulas: $u_1=-\int y_1R/W$, $u_2=\int y_2R/W$. The result does not solve the ODE.

### Q14 (slide 11)

For $y''+y=\tan x$ on $-\tfrac\pi2<x<\tfrac\pi2$ take $y_1=\cos x$, $y_2=\sin x$. Which $y_p=u_1y_1+u_2y_2$ does variation of parameters give (integration constants zero)?

- A) $y_p=\cos x\,\ln\lvert\sec x+\tan x\rvert$
- B) $y_p=-\cos x\,\ln\lvert\sec x+\tan x\rvert$
- C) $y_p=\cos x\,\ln\lvert\sec x+\tan x\rvert-\sin2x$
- D) $y_p=\sin x\,\ln\lvert\sec x+\tan x\rvert+\cos2x$

> [!success]- Answer
> **B.** $W=\cos^2x+\sin^2x=1$.
> $u_1=-\int\sin x\tan x\,dx=-\int(\sec x-\cos x)\,dx=-\ln\lvert\sec x+\tan x\rvert+\sin x$.
> $u_2=\int\cos x\tan x\,dx=\int\sin x\,dx=-\cos x$.
> $y_p=-\cos x\,\ln\lvert\sec x+\tan x\rvert+\sin x\cos x-\sin x\cos x=-\cos x\,\ln\lvert\sec x+\tan x\rvert$.
> - A: Wronskian sign wrong ($W=-1$). Then $y_p''+y_p=-\tan x$.
> - C: The minus sign of $u_1$ is lost: $u_1=\ln\lvert\sec x+\tan x\rvert-\sin x$. Then $y_p''+y_p\neq\tan x$.
> - D: $y_1$ and $y_2$ swapped in the formulas: $u_1=\cos x$, $u_2=\int\sin x\tan x\,dx$. This does not solve the ODE.

### Q15 (slide 12)

The general solution of $2y''-4y'+2y=\dfrac{2e^x}{x}$, $x>0$, is written as $y=c_1e^x+c_2xe^x+Y(x)$. Variation of parameters gives which $Y$?

- A) $Y=xe^x\ln x$
- B) $Y=2xe^x\ln x$
- C) $Y=-xe^x\ln x$
- D) $Y=x^2e^x-e^x\ln x$

> [!success]- Answer
> **A.** Standard form: $y''-2y'+y=\tfrac{e^x}x$, so $R=\tfrac{e^x}x$. $y_1=e^x$, $y_2=xe^x$, $W=e^{2x}$.
> $u_1=-\int1\,dx=-x$, $u_2=\int\tfrac1x\,dx=\ln x$.
> $y_p=-xe^x+xe^x\ln x$. The term $-xe^x$ goes into $c_2xe^x$.
> - B: No division by 2 first: $R=\tfrac{2e^x}x$. Then $Y''-2Y'+Y=\tfrac{2e^x}x$.
> - C: Wronskian sign wrong ($W=-e^{2x}$). Then $Y''-2Y'+Y=-\tfrac{e^x}x$.
> - D: $y_1$ and $y_2$ swapped in the formulas: $u_1=-\ln x$, $u_2=x$. This does not solve the ODE.

## 6. Undetermined coefficients (slides 13-18)

### Q16 (slide 13)

Undetermined coefficients. Which trial form $y_p$ is correct (coefficients not yet found)?

- A) $y''-3y'+2y=xe^{3x}$: $y_p=Axe^{3x}$
- B) $y''-4y'+4y=e^{2x}$: $y_p=Kx^2e^{2x}$
- C) $y''-3y'+2y=5e^{2x}$: $y_p=Ke^{2x}$
- D) $y''-3y'+2y=x^2+\cos x$: $y_p=A_2x^2+A_1x+A_0+C\cos x$

> [!success]- Answer
> **B.** $\lambda^2-4\lambda+4=(\lambda-2)^2$: $y_h=c_1e^{2x}+c_2xe^{2x}$.
> $e^{2x}$ and $xe^{2x}$ are both in $y_h$. Double root, so multiply by $x^2$.
> - A: A polynomial of degree 1 times $e^{3x}$ needs the full polynomial: $(A_1x+A_0)e^{3x}$.
> - C: Modification rule forgotten. The roots are $1,2$, so $e^{2x}$ is in $y_h$. Use $Kxe^{2x}$.
> - D: For $\cos x$ guess both $C\cos x+D\sin x$. The $\sin x$ term is missing.

### Q17 (slide 14)

Solve the IVP $y''+2y'+5y=5x^2-x+10$, $y(0)=3$, $y'(0)=2$.

- A) $y=e^{-2x}(\cos x+5\sin x)+x^2-x+2$
- B) $y=e^{-x}(3\cos2x+\tfrac52\sin2x)+x^2-x+2$
- C) $y=e^{-x}(\cos2x+2\sin2x)+x^2-x+2$
- D) $y=e^{-x}(\cos2x+\tfrac32\sin2x)+x^2-x+2$

> [!success]- Answer
> **C.** Roots $-1\pm2i$: $y_h=e^{-x}(c_1\cos2x+c_2\sin2x)$. $y_p=Ax^2+Bx+C$ gives $A=1$, $B=-1$, $C=2$.
> $y(0)=c_1+2=3$, $c_1=1$.
> $y'(0)=-c_1+2c_2-1=2$, $c_2=2$.
> - A: $\alpha$ and $\beta$ swapped: $e^{-2x}$ and $\cos x$. This $y_h$ does not solve the homogeneous ODE.
> - B: The conditions are applied to $y_h$ alone: $c_1=3$, $-c_1+2c_2=2$. Then $y(0)=5$.
> - D: $y_p'(0)=-1$ is left out of $y'(0)$: $-c_1+2c_2=2$. Then $y'(0)=1$.

### Q18 (slide 15)

Solve the IVP $y''+4y=8\cos2x$, $y(0)=1$, $y'(0)=0$.

- A) $y=\cos2x+4x\sin2x$
- B) $y=\cos2x+\sin2x-2x\cos2x$
- C) $y=\cos2x+2x\sin2x$
- D) $y=2x\sin2x$

> [!success]- Answer
> **C.** $y_h=c_1\cos2x+c_2\sin2x$. $\cos2x$ is in $y_h$, so $y_p=x(A\cos2x+B\sin2x)$.
> $y_p''+4y_p=-4A\sin2x+4B\cos2x=8\cos2x$: $A=0$, $B=2$.
> $y(0)=c_1=1$. $y'(0)=2c_2=0$, so $c_2=0$.
> - A: One of the two equal groups $(-2A\sin2x+2B\cos2x)$ in $y_p''$ is lost: $2B=8$. Then $y''+4y=16\cos2x$.
> - B: The $\sin$ and $\cos$ rows are swapped: $-4A=8$, $4B=0$. Then $y''+4y$ has a $\sin2x$ term.
> - D: $y_h$ is forgotten: $y=y_p$ only. It solves the ODE, but $y(0)=0$.

### Q19 (slide 16)

Which function is a particular solution of $y''-3y'=18x$?

- A) $y_p=-3x^2-2x$
- B) $y_p=-3x^2+2x$
- C) $y_p=-3x^2$
- D) $y_p=-6x^2-4x$

> [!success]- Answer
> **A.** $y_h=c_1+c_2e^{3x}$. A constant is in $y_h$, so $y_p=x(Ax+B)$.
> $2A-3(2Ax+B)=18x$: $-6A=18$, $A=-3$; $2A-3B=0$, $B=-2$.
> Check: $-6-3(-6x-2)=18x$.
> - B: Sign slip in $-6-3B=0$: $B=2$. Then $y_p''-3y_p'=18x-12$.
> - C: $2A$ is lost from the constant equation, so $B=0$. Then $y_p''-3y_p'=18x-6$.
> - D: In $-3y_p'$, $(Ax^2)'$ is taken as $Ax$ ($y_p''=2A$ stays right): $-3A=18$, $A=-6$; $2A-3B=0$, $B=-4$. Then $y_p''-3y_p'=36x$.

### Q20 (slide 17)

Which function is a particular solution of $y''+3y'+2y=10\sin x+12e^x$?

- A) $y_p=-3\cos x+\sin x+2e^x$
- B) $y_p=\cos x-3\sin x+2e^x$
- C) $y_p=5\cos x-5\sin x+2e^x$
- D) $y_p=\tfrac{15}4\cos x-\tfrac54\sin x+2e^x$

> [!success]- Answer
> **A.** $A\cos x+B\sin x$: $(A+3B)\cos x+(B-3A)\sin x=10\sin x$, so $A=-3$, $B=1$.
> $Ke^x$: $(1+3+2)K=12$, $K=2$.
> - B: $A$ and $B$ swapped: $A=-3$ is put on $\sin x$. This does not give $10\sin x$.
> - C: $(\cos x)'$ taken as $+\sin x$, and $y''$ found from this wrong $y'=A\sin x+B\cos x$: $y''=A\cos x-B\sin x$. Then $3A+3B=0$, $3A+B=10$. This does not give $10\sin x$.
> - D: Only in $3y'$ the sign of $-3A\sin x$ is lost ($y''$ is right): $A+3B=0$, $B+3A=10$. This does not give $10\sin x$.

### Q21 (slide 18, exercise i)

For $y''+2y'=2x^3+\cos4x+1$, $y_{p_1}$ is the polynomial part of $y_p$, for the terms $2x^3+1$. Choose its constant term 0. Which $y_{p_1}$ is correct?

- A) $\tfrac14x^4-\tfrac12x^3+\tfrac34x^2+\tfrac12x$
- B) $\tfrac14x^4-\tfrac12x^3+\tfrac34x^2-\tfrac34x$
- C) $\tfrac14x^4+\tfrac12x^3-\tfrac34x^2+\tfrac54x$
- D) $\tfrac14x^4-\tfrac12x^3+\tfrac34x^2-\tfrac14x$

> [!success]- Answer
> **D.** $\lambda=0,-2$. A constant is in $y_h$, so $y_{p_1}=Ax^4+Bx^3+Cx^2+Dx$.
> $y''+2y'=8Ax^3+(12A+6B)x^2+(6B+4C)x+(2C+2D)=2x^3+1$.
> $A=\tfrac14$, $B=-\tfrac12$, $C=\tfrac34$, $D=-\tfrac14$.
> - A: $2C$ is lost from the constant equation: $2D=1$. Then the constant term is $\tfrac52$.
> - B: The $+1$ on the right is forgotten: $2C+2D=0$. Then the constant term is $0$.
> - C: Sign slip in the $x^2$ equation: $B=+\tfrac12$. Then $y''+2y'$ has a term $6x^2$.

## 7. Euler's differential equation (slides 18-22)

### Q22 (slides 18-19)

Solve the IVP $x^2y''-xy'-3y=0$, $y(1)=3$, $y'(1)=1$, $x>0$, with $x=e^t$, $z(t)=y(e^t)$.

- A) $y=x^3+\dfrac2x$
- B) $y=\dfrac1{2x^3}+\dfrac{5x}2$
- C) $y=-x^3+\dfrac4x$
- D) $y=-x^3+4x$

> [!success]- Answer
> **A.** $xy'=z'$, $x^2y''=z''-z'$: $z''-2z'-3z=0$, roots $3,-1$.
> $z=c_1e^{3t}+c_2e^{-t}$, so $y=c_1x^3+c_2x^{-1}$.
> $c_1+c_2=3$, $3c_1-c_2=1$: $c_1=1$, $c_2=2$.
> - B: Root signs flipped: $(\lambda+3)(\lambda-1)$ gives $-3,1$. These are not roots of $\lambda^2-2\lambda-3$.
> - C: Sign of $(x^{-1})'=-x^{-2}$ lost: $3c_1+c_2=1$. Then $y'(1)=-7$.
> - D: $e^{-t}$ is written as $x$ instead of $x^{-1}$. Then $y=x$ does not solve the ODE.

### Q23 (slide 20)

Solve the IVP $2x^2y''+3xy'-y=0$, $y(1)=3$, $y'(1)=0$, $x>0$, with $y=x^{\lambda}$.

- A) $y=\dfrac2{\sqrt x}+x$
- B) $y=2\sqrt x+\dfrac1x$
- C) $y=\sqrt x+\dfrac2x$
- D) $y=6\sqrt x-\dfrac3x$

> [!success]- Answer
> **B.** $2\lambda(\lambda-1)+3\lambda-1=2\lambda^2+\lambda-1=(2\lambda-1)(\lambda+1)=0$: $\lambda=\tfrac12,-1$.
> $y=c_1x^{1/2}+c_2x^{-1}$: $c_1+c_2=3$, $\tfrac12c_1-c_2=0$.
> $c_2=1$, $c_1=2$.
> - A: Wrong factoring $(2\lambda+1)(\lambda-1)$: $\lambda=-\tfrac12,1$. These do not solve $2\lambda^2+\lambda-1=0$.
> - C: $\tfrac12c_1-c_2=0$ solved as $c_2=2c_1$. Then $y'(1)=-\tfrac32$.
> - D: Sign of $(x^{-1})'$ lost: $\tfrac12c_1+c_2=0$. Then $y'(1)=6$.

### Q24 (slide 21, case ii)

Solve the IVP $x^2y''+5xy'+4y=0$, $y(1)=1$, $y'(1)=1$, $x>0$.

- A) $y=\dfrac5{3x}-\dfrac2{3x^4}$
- B) $y=-\dfrac2{x^2}+\dfrac3x$
- C) $y=\dfrac{1-\ln x}{x^2}$
- D) $y=\dfrac{1+3\ln x}{x^2}$

> [!success]- Answer
> **D.** $\lambda^2+(5-1)\lambda+4=(\lambda+2)^2=0$: $\gamma=-2$ (double).
> $y=c_1x^{-2}+c_2x^{-2}\ln x$. $y(1)=c_1=1$.
> $y'(1)=-2c_1+c_2=1$, so $c_2=3$.
> - A: Roots from $\lambda^2+5\lambda+4$ (with $A$, not $A-1$): $-1,-4$. This does not solve the ODE.
> - B: Second solution $x\cdot x^{-2}$ instead of $x^{-2}\ln x$. $x^{-1}$ does not solve the ODE.
> - C: Sign slip: $c_2=1-2c_1=-1$ instead of $1+2c_1$. Then $y'(1)=-3$.

### Q25 (slides 21-22, case iii)

Solve the IVP $x^2y''+3xy'+5y=0$, $y(1)=2$, $y'(1)=4$, $x>0$.

- A) $y=\dfrac{2\cos(2\ln x)+3\sin(2\ln x)}{x}$
- B) $y=2x^2\cos(\ln x)$
- C) $y=\dfrac{2\cos(2\ln x)+6\sin(2\ln x)}{x}$
- D) $y=x\left(2\cos(2\ln x)+\sin(2\ln x)\right)$

> [!success]- Answer
> **A.** $\lambda^2+2\lambda+5=0$: $\lambda=-1\pm2i$. $y=x^{-1}\left(c_1\cos(2\ln x)+c_2\sin(2\ln x)\right)$.
> $y(1)=c_1=2$. $y'(1)=-c_1+2c_2=4$, so $c_2=3$.
> - B: $\alpha$ and $\beta$ swapped: $x^{2}$ and $\cos(\ln x)$. Then $c_2=0$. This does not solve the ODE.
> - C: The factor 2 from $(2\ln x)'=\tfrac2x$ is lost: $-c_1+c_2=4$. Then $y'(1)=10$.
> - D: Wrong sign of $\alpha$: $\lambda=1\pm2i$. These are not roots of $\lambda^2+2\lambda+5$.
