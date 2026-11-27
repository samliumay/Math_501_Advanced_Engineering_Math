---
course: MATH 501 Advanced Engineering Mathematics
lesson: MATH501 L01 - First order differential equations
type: quiz
questions: 22
---

# MATH501 L01 - First order differential equations - quiz

Lesson note: [[MATH501 L01 - First order differential equations]]. One question per check question of the lesson. Pick an option, then open the answer.

## 1. What is a differential equation? (slides 2-3)

### Q1 (slide 2)

Four relations: (a) $\dfrac{d^2\theta}{dt^2}+\dfrac gL\sin\theta=0$, (b) $\dfrac{\partial u}{\partial t}=k\,\dfrac{\partial^2u}{\partial x^2}$, (c) $(y''')^2+x\,(y')^5=e^x$, (d) $\dfrac{d}{dx}\sin x=\cos x$. Which statement is correct?

- A) (c) is an ODE of order 5. The order is the highest power of a derivative.
- B) (b) is an ODE of order 2. It has only one unknown function, $u$.
- C) (d) is an ODE of order 1. It contains the derivative $d/dx$.
- D) (c) is an ODE of order 3. The powers 2 and 5 do not change the order.

> [!success]- Answer
> **D.** The order is the highest derivative that appears. In (c) that is $y'''$, so the order is 3.
> There is one independent variable, $x$, so (c) is an ODE. A power such as $(y''')^2$ does not raise the order.
> - A: The order is the highest derivative ($y'''$), not the highest power. The power 5 sits on $y'$.
> - B: The number of unknown functions does not decide this. $u$ depends on two independent variables, $x$ and $t$, so (b) is a PDE.
> - C: (d) has no unknown function. It is an identity, true for every $x$, so it is not a differential equation.

### Q2 (slide 3, classification)

Linear means the form $a_n(x)y^{(n)}+\dots+a_1(x)y'+a_0(x)y=b(x)$, and a linear ODE is homogeneous if $b\equiv0$. Four ODEs: (a) $x^3y'''-(\cos x)\,y'+y=0$, (b) $y\,y'+x=0$, (c) $y''+e^{y}=x$, (d) $(1+x^2)\,y''+\dfrac yx=\ln x$. Which statement is correct?

- A) (a) is nonlinear of order 3, since $x^3$ and $\cos x$ are not constants.
- B) (d) is linear of order 2 and non-homogeneous, since $b=\ln x$.
- C) (b) is linear and homogeneous of order 1, since its right side is 0.
- D) (c) is linear of order 2, since $y''$ appears only to the first power.

> [!success]- Answer
> **B.** (d): $a_2=1+x^2$, $a_1=0$, $a_0=\tfrac1x$, $b=\ln x$. All of them depend on $x$ only, so (d) is linear of order 2.
> $b=\ln x$ is not the zero function, so (d) is non-homogeneous.
> - A: Linear does not mean constant coefficients. The coefficients may depend on $x$. (a) is linear and homogeneous.
> - C: The term $y\,y'$ is a product of $y$ and $y'$. So (b) is nonlinear, and the word homogeneous is not used.
> - D: The term $e^{y}$ puts $y$ inside another function. So (c) is nonlinear.

### Q3 (slide 3, solution)

Put $\phi(x)=x^2\ln x$ into the left side of $x^2y''-3xy'+4y=0$ for $x>0$. What does $x^2\phi''-3x\phi'+4\phi$ simplify to?

- A) $2x^2$
- B) $-2x^2$
- C) $0$
- D) $-x^2$

> [!success]- Answer
> **C.** Product rule: $\phi'=2x\ln x+x$ and $\phi''=2\ln x+2+1=2\ln x+3$.
> Left side: $x^2(2\ln x+3)-3x(2x\ln x+x)+4x^2\ln x$.
> The $\ln x$ terms give $(2-6+4)x^2\ln x=0$. The rest gives $3x^2-3x^2=0$. So $\phi$ is a solution.
> - A: The second term of the product rule is lost: $\phi'=2x\ln x$, $\phi''=2\ln x+2$. Then $2x^2\ln x+2x^2-6x^2\ln x+4x^2\ln x=2x^2$.
> - B: $\phi'$ is right, but $(2x\ln x)'$ is taken as $2\ln x$: $\phi''=2\ln x+1$. Then $x^2-3x^2=-2x^2$.
> - D: $\phi'$ is right, but the derivative of the term $x$ in $\phi'$ is lost: $\phi''=2\ln x+2$. Then $2x^2-3x^2=-x^2$.

## 2. General solution, IVP, existence and uniqueness (slides 4-5)

### Q4 (slide 4)

Solve $y''=12x^2-4\sin 2x$ with $y(0)=1$ and $y'(0)=3$ by integrating twice.

- A) $y=x^4+\sin 2x+x+1$
- B) $y=x^4-\sin 2x+x+1$
- C) $y=x^4+\sin 2x+5x+1$
- D) $y=x^4-\sin 2x+5x+1$

> [!success]- Answer
> **A.** $\int\sin 2x\,dx=-\tfrac12\cos 2x$, so $y'=4x^3+2\cos 2x+c_1$.
> $y'(0)=2+c_1=3$ gives $c_1=1$.
> $y=x^4+\sin 2x+x+c_2$, and $y(0)=c_2=1$.
> - B: Sign slip in the second integration: $\int 2\cos 2x\,dx$ taken as $-\sin 2x$. Then $y''=12x^2+4\sin 2x$.
> - C: $2+c_1=3$ is solved as $c_1=3+2=5$. Then $y'(0)=2+5=7$, not 3.
> - D: Sign slip in the first integration: $\int\sin 2x\,dx$ taken as $+\tfrac12\cos 2x$. Then $y'=4x^3-2\cos 2x+c_1$, $c_1=5$, and $y''=12x^2+4\sin 2x$.

### Q5 (slide 5, theorem)

Take $y'=x\,y^{1/3}$ (real cube root). The existence and uniqueness theorem asks that $f$ and $\partial f/\partial y$ are continuous in a rectangle around $(x_0,y_0)$. Which pair of statements is right? (a) is about $y(2)=1$, (b) is about $y(0)=0$.

- A) (a) Exactly one solution near $x=2$ is guaranteed. (b) The theorem does not apply. So no solution exists.
- B) (a) Exactly one solution near $x=2$ is guaranteed. (b) The theorem does not apply. There are at least three solutions.
- C) (a) Nothing is guaranteed, as $\partial f/\partial y$ fails on $y=0$. (b) The theorem does not apply. There are at least three solutions.
- D) (a) Nothing is guaranteed, as $\partial f/\partial y$ fails on $y=0$. (b) The theorem does not apply. So no solution exists.

> [!success]- Answer
> **B.** $\dfrac{\partial f}{\partial y}=\dfrac{x}{3y^{2/3}}$ is not continuous on the line $y=0$. $f$ is continuous everywhere.
> (a) The rectangle $(1,3)\times(\tfrac12,2)$ around $(2,1)$ avoids $y=0$. So the theorem applies.
> (b) Every rectangle around $(0,0)$ meets the line $y=0$. Direct check: $y\equiv0$ and $y=\pm\dfrac{\lvert x\rvert^3}{3\sqrt3}$ all solve the IVP.
> - A: (a) is right. In (b) a failed hypothesis is read as 'no solution'. The theorem then says nothing, and $y\equiv0$ is a solution.
> - C: (b) is right. In (a) the hypotheses are asked on the whole plane. They are needed only in some rectangle around $(2,1)$.
> - D: Two slips: the hypotheses are asked on the whole plane in (a), and a failed hypothesis is read as 'no solution' in (b).

## 3. Separable equations (slides 5-6)

### Q6 (slide 5, separable equations)

Solve the IVP $y'=\dfrac{e^x}{2y}$, $y(0)=-3$. Which explicit solution is right?

- A) $y=\sqrt{e^x+8}$
- B) $y=-e^{x/2}-2$
- C) $y=e^{x/2}-4$
- D) $y=-\sqrt{e^x+8}$

> [!success]- Answer
> **D.** Separate: $2y\,dy=e^x\,dx$. Integrate: $y^2=e^x+c$.
> $y(0)=-3$: $9=1+c$, so $c=8$.
> Both roots $\pm\sqrt{e^x+8}$ solve the ODE. Only the minus root gives $y(0)=-3$.
> - A: The sign of the root is not taken from the condition. This gives $y(0)=+3$.
> - B: The constant is added after taking the root: $y=-\sqrt{e^x}+c$, $c=-2$. It meets $y(0)=-3$ but not the ODE: $y'=-\tfrac12e^{x/2}\ne\dfrac{e^x}{2y}$.
> - C: The same slip with the plus root: $y=\sqrt{e^x}+c$, $c=-4$. It meets $y(0)=-3$ but not the ODE.

### Q7 (slide 6)

Take $y'=2x(y-1)^2$. Which pair gives the solution with $y(0)=2$ and the solution with $y(0)=1$?

- A) $y(0)=2$: $y=1+\dfrac{1}{1-x^2}$. $y(0)=1$: $y\equiv1$.
- B) $y(0)=2$: $y=1+\dfrac{1}{1-x^2}$. $y(0)=1$: no solution exists.
- C) $y(0)=2$: $y=1+\dfrac{1}{1+x^2}$. $y(0)=1$: $y\equiv1$.
- D) $y(0)=2$: $y=1+\dfrac{1}{1+x^2}$. $y(0)=1$: no solution exists.

> [!success]- Answer
> **A.** For $y\ne1$: $\dfrac{dy}{(y-1)^2}=2x\,dx$ gives $-\dfrac{1}{y-1}=x^2+c$, so $y=1-\dfrac{1}{x^2+c}$.
> $y(0)=2$: $c=-1$, so $y=1+\dfrac{1}{1-x^2}$ on $-1<x<1$.
> $y(0)=1$ would need $\tfrac1c=0$, impossible. But $g(y)=(y-1)^2$ is $0$ at $y=1$, and $y\equiv1$ solves the ODE ($0=2x\cdot0$).
> - B: The first part is right. The constant solution $y\equiv1$, lost when dividing by $(y-1)^2$, is forgotten.
> - C: Sign slip: $\int(y-1)^{-2}dy$ taken as $+\dfrac{1}{y-1}$. Then $y=1+\dfrac1{x^2+c}$ and $c=1$. This does not solve the ODE.
> - D: Two slips: the sign of $\int(y-1)^{-2}dy$, and the forgotten constant solution $y\equiv1$.

## 4. First order linear equations (slides 7-8)

### Q8 (slide 7)

Solve $xy'+3y=x^2$ for $x>0$ with an integrating factor $\mu$. What is the general solution, and what happens if you use $5\mu$ in place of $\mu$?

- A) $y=\dfrac{x^2}{5}+\dfrac{c}{x^3}$. With $5\mu$ you get the same family, only $c$ is renamed.
- B) $y=-x^2+cx^3$. With $5\mu$ you get the same family, only $c$ is renamed.
- C) $y=\dfrac{x^2}{5}+\dfrac{c}{x^3}$. With $5\mu$ you get a different family of solutions.
- D) $y=-x^2+cx^3$. With $5\mu$ you get a different family of solutions.

> [!success]- Answer
> **A.** Standard form: $y'+\tfrac3x\,y=x$. So $\mu=e^{\int 3/x\,dx}=x^3$.
> $(x^3y)'=x^4$, so $x^3y=\tfrac{x^5}{5}+c$ and $y=\tfrac{x^2}{5}+\tfrac{c}{x^3}$.
> With $5x^3$: $5x^3y=x^5+c_1$, so $y=\tfrac{x^2}{5}+\tfrac{c_1/5}{x^3}$. The same family with $c=c_1/5$.
> - B: Integrating factor $e^{-\int p\,dx}=x^{-3}$. Then $(x^{-3}y)'=x^{-2}$ gives $y=-x^2+cx^3$, which does not solve the ODE. The second part is right.
> - C: The first part is right. The 5 is put on the left side only: $(5x^3y)'=x^4$ gives $y=\tfrac{x^2}{25}+\tfrac{c}{5x^3}$, which does not solve the ODE.
> - D: Two slips: the factor $e^{-\int p\,dx}$, and the 5 put on the left side only.

### Q9 (slide 8)

Solve the IVP $y'-\dfrac{y}{x}=x\,e^{x}$, $y(1)=0$, for $x>0$.

- A) $y=x\,e^x-e$
- B) $y=\dfrac{e^x-e}{x}$
- C) $y=x\,(e^x-e)$
- D) $y=x\,(e^x+e)$

> [!success]- Answer
> **C.** $p=-\tfrac1x$, so $\mu=e^{-\ln x}=\tfrac1x$ and $\left(\tfrac yx\right)'=e^x$.
> Integrate: $\tfrac yx=e^x+c$, so $y=xe^x+cx$.
> $y(1)=e+c=0$ gives $c=-e$.
> - A: The constant is added after multiplying by $x$: $y=xe^x+c$, $c=-e$. It meets $y(1)=0$ but not the ODE.
> - B: At the end $\tfrac yx=e^x+c$ is divided by $x$ instead of multiplied: $y=\tfrac{e^x+c}{x}$, $c=-e$. It does not solve the ODE.
> - D: $e+c=0$ is solved as $c=e$. It solves the ODE, but $y(1)=2e\ne0$.

## 5. Homogeneous equations (slides 9-12)

### Q10 (slide 9)

$f$ is homogeneous of degree $n$ if $f(\alpha x,\alpha y)=\alpha^nf(x,y)$ for every $\alpha\ne0$. Take (a) $f=\dfrac{\sqrt{x^4+y^4}}{x+y}$, (b) $f=\dfrac{x^3+xy^2}{x-y}$, (c) $f=xy+1$. Which line is right?

- A) (a) degree 2, (b) degree 3, (c) not homogeneous
- B) (a) degree 1, (b) degree 2, (c) degree 2
- C) (a) degree 1, (b) degree 2, (c) not homogeneous
- D) (a) degree 2, (b) degree 3, (c) degree 2

> [!success]- Answer
> **C.** (a) $\dfrac{\alpha^2\sqrt{x^4+y^4}}{\alpha(x+y)}=\alpha f$. (b) $\dfrac{\alpha^3(x^3+xy^2)}{\alpha(x-y)}=\alpha^2f$.
> (c) $\alpha^2xy+1=\alpha^n(xy+1)$ would need $\alpha^2=\alpha^n$ and $1=\alpha^n$, so $\alpha^2=1$. This is false for $\alpha=2$.
> - A: Only the numerator is counted: $\sqrt{x^4+y^4}$ has degree 2 and $x^3+xy^2$ degree 3. The denominator (degree 1) is forgotten.
> - B: The constant 1 in (c) is ignored. $f(\alpha x,\alpha y)=\alpha^2xy+1$ is not $\alpha^2(xy+1)$.
> - D: The ordinary degree of the numerator polynomial is taken as the degree: 2 for $\sqrt{x^4+y^4}$, 3 for $x^3+xy^2$, 2 for $xy+1$. The test $f(\alpha x,\alpha y)=\alpha^nf$ is never done.

### Q11 (slide 10)

A first order ODE is homogeneous if it can be written as $y'=g(y/x)$. Take (a) $y'=\dfrac{x^2+y^2}{xy}$, (b) $y'=\dfrac{x^2+y}{x}$, (c) $y'=\dfrac{y-\sqrt{x^2+y^2}}{x}$ for $x>0$. Which ODEs are homogeneous, and what is $g(t)$ for (c)?

- A) (a) and (c). For (c), $g(t)=t-\sqrt{1+t^2}$.
- B) (a) and (c). For (c), $g(t)=t-\sqrt{1+t}$.
- C) (a), (b) and (c). For (c), $g(t)=t-\sqrt{1+t^2}$.
- D) (a), (b) and (c). For (c), $g(t)=t-\sqrt{1+t}$.

> [!success]- Answer
> **A.** (a) $\dfrac{x^2+y^2}{xy}=\dfrac xy+\dfrac yx=\dfrac1t+t$ with $t=y/x$.
> (b) $\dfrac{x^2+y}{x}=x+\dfrac yx$. The lone $x$ stays: $f(\alpha x,\alpha y)=\alpha x+\dfrac yx\ne f$. Not homogeneous.
> (c) For $x>0$, $\sqrt{x^2+y^2}=x\sqrt{1+(y/x)^2}$. So $y'=t-\sqrt{1+t^2}$.
> - B: The set is right. Taking $x$ out of the root, $(y/x)^2$ is written as $y/x$.
> - C: $g$ is right. But (b) is $y'=x+\tfrac yx$, and the lone $x$ cannot be written with $y/x$ only.
> - D: Two slips: (b) is counted as homogeneous, and $(y/x)^2$ inside the root is written as $y/x$.

### Q12 (slide 11)

Solve the IVP $y'=\dfrac{x^2+y^2}{xy}$, $y(1)=2$, with $y=vx$ ($x>0$). Which is the solution near $x=1$?

- A) $y=x\sqrt{\ln x+4}$
- B) $y=\sqrt{2\ln x+4}$
- C) $y=\sqrt{\ln x+4}$
- D) $y=x\sqrt{2\ln x+4}$

> [!success]- Answer
> **D.** $y'=v+xv'$, so $v+xv'=\tfrac1v+v$ and $xv'=\tfrac1v$. Separate: $v\,dv=\tfrac{dx}{x}$.
> $\tfrac{v^2}{2}=\ln x+c$, so $v^2=2\ln x+C$ and $y^2=x^2(2\ln x+C)$.
> $y(1)=2$: $4=C$. Take the positive root, since $y(1)>0$.
> - A: The factor $\tfrac12$ is dropped: $\tfrac{v^2}{2}=\ln x+c$ is written as $v^2=\ln x+C$.
> - B: The factor $x^2$ is lost when going back from $v$ to $y$: $y^2=2\ln x+C$ in place of $y^2=x^2(2\ln x+C)$.
> - C: Two slips: the factor $\tfrac12$ is dropped, and $x^2$ is lost when going back to $y$.

### Q13 (slide 12)

Solve $xy'=y+x\cos^2\!\left(\dfrac yx\right)$ for $x>0$ with $y(1)=\dfrac\pi4$, using $y=vx$. Which option gives this solution and the straight lines $y=mx$ that are also solutions but not given by the general formula ($k$ an integer)?

- A) $y=x\arctan\!\left(\ln x+\tfrac\pi4\right)$. Lines $y=\left(\tfrac\pi2+k\pi\right)x$.
- B) $y=x\arctan(\ln x+1)$. Lines $y=\left(\tfrac\pi2+k\pi\right)x$.
- C) $y=x\arctan(\ln x+1)$. Lines $y=k\pi x$.
- D) $y=x\arctan\!\left(\ln x+\tfrac\pi4\right)$. Lines $y=k\pi x$.

> [!success]- Answer
> **B.** $v+xv'=v+\cos^2v$, so $xv'=\cos^2v$. For $\cos v\ne0$: $\sec^2v\,dv=\tfrac{dx}{x}$, so $\tan v=\ln x+c$.
> $v(1)=\tfrac\pi4$: $1=0+c$, so $c=1$ and $y=x\arctan(\ln x+1)$.
> Lost: $\cos v_0=0$, $v_0=\tfrac\pi2+k\pi$. For $y=v_0x$: $xy'=v_0x$ and $v_0x+x\cdot0=v_0x$. Equal.
> - A: The condition is put in as $v(1)=c$ in place of $\tan v(1)=c$: $c=\tfrac\pi4$. Then $y(1)=\arctan\tfrac\pi4\ne\tfrac\pi4$.
> - C: $\cos v=0$ is solved as $v=k\pi$ (the zeros of $\sin$). On $y=k\pi x$ the right side is $k\pi x+x\ne xy'$.
> - D: Two slips: the condition is put in as $v(1)=c$, and $\cos v=0$ is solved as $v=k\pi$.

## 6. Equations of the form y' = F(Ax + By + C) (slides 13-14)

### Q14 (slide 13)

Solve the IVP $y'=(2x+y)^2+7$, $y(0)=3$, with $u=2x+y$. Give $y$ explicitly.

- A) $y=3\tan\!\left(3x+\tfrac\pi4\right)-2x$
- B) $y=3\tan\!\left(3x+\tfrac\pi4\right)+2x$
- C) $y=3\tan\!\left(x+\tfrac\pi4\right)-2x$
- D) $y=3\tan\!\left(x+\tfrac\pi4\right)+2x$

> [!success]- Answer
> **A.** $u'=2+y'=u^2+9$. Separate: $\int\dfrac{du}{u^2+9}=\tfrac13\arctan\tfrac u3=x+c$.
> $u(0)=3$: $\tfrac13\cdot\tfrac\pi4=c$, so $\arctan\tfrac u3=3x+\tfrac\pi4$.
> $u=3\tan\!\left(3x+\tfrac\pi4\right)$ and $y=u-2x$.
> - B: Going back, $y=u+2x$ is used in place of $y=u-2x$.
> - C: The factor $\tfrac13$ of the integral is lost: $\arctan\tfrac u3=x+c$, $c=\tfrac\pi4$.
> - D: Two slips: the factor $\tfrac13$ of the integral is lost, and $y=u+2x$ is used going back.

### Q15 (slide 14, top)

Find the general solution of $y'=\cos(x+y)$ with $u=x+y$, and the lines lost when you divide ($k$ an integer).

- A) $\tfrac12\tan(x+y)=x+c$. Lines $y=-x+\pi+2k\pi$.
- B) $\tan\dfrac{x+y}{2}=x+c$. Lines $y=-x+\tfrac\pi2+k\pi$.
- C) $\tfrac12\tan(x+y)=x+c$. Lines $y=-x+\tfrac\pi2+k\pi$.
- D) $\tan\dfrac{x+y}{2}=x+c$. Lines $y=-x+\pi+2k\pi$.

> [!success]- Answer
> **D.** $u'=1+y'=1+\cos u$. Use $1+\cos u=2\cos^2\tfrac u2$: $\int\dfrac{du}{1+\cos u}=\int\tfrac12\sec^2\tfrac u2\,du=\tan\tfrac u2$.
> So $\tan\tfrac{x+y}{2}=x+c$.
> Dividing needs $1+\cos u\ne0$. Lost: $u=\pi+2k\pi$, that is $y=-x+\pi+2k\pi$. There $y'=-1=\cos(\pi+2k\pi)$.
> - A: The lines come from $1+\cos u=0$ and are right. But in the integral $1+\cos u$ is taken as $2\cos^2u$ (no half angle): $\int\tfrac12\sec^2u\,du=\tfrac12\tan u$.
> - B: The lost lines come from $\cos u=0$ in place of $1+\cos u=0$. There $y'=-1$ but $\cos(x+y)=0$.
> - C: $1+\cos u$ is rewritten as $2\cos^2u$ (no half angle) before both steps. The integral gives $\tfrac12\tan u$, and $2\cos^2u=0$ gives $u=\tfrac\pi2+k\pi$.

## 7. Exact equations (slides 14-16)

### Q16 (slide 14, exact equations)

The function $u(x,y)=x^3y^2+e^{x}y$ is a potential function. Which exact ODE $M\,dx+N\,dy=0$ belongs to it, and which solution passes through the point $(x,y)=(0,2)$?

- A) $(3x^2y^2+e^xy)\,dx+(2x^3y+e^x)\,dy=0$, solution $x^3y^2+e^xy=2$
- B) $(2x^3y+e^x)\,dx+(3x^2y^2+e^xy)\,dy=0$, solution $x^3y^2+e^xy=2$
- C) $(3x^2y^2+e^xy)\,dx+(2x^3y+e^x)\,dy=0$, solution $x^3y^2+e^xy=0$
- D) $(2x^3y+e^x)\,dx+(3x^2y^2+e^xy)\,dy=0$, solution $x^3y^2+e^xy=0$

> [!success]- Answer
> **A.** $M=u_x=3x^2y^2+e^xy$ and $N=u_y=2x^3y+e^x$. Test: $M_y=6x^2y+e^x=N_x$.
> The solution is $u=c$. At $x=0$, $y=2$: $0+1\cdot2=c$, so $c=2$.
> - B: $M$ and $N$ are swapped ($M=u_y$, $N=u_x$). This ODE is not exact: $M_y=2x^3$ but $N_x=6xy^2+e^xy$.
> - C: The ODE is right. The point is read as $x=2$, $y=0$, which gives $c=0$.
> - D: Two slips: $M$ and $N$ swapped, and the point read as $x=2$, $y=0$.

### Q17 (slide 15)

The ODE $(y\cos x+2xe^{y})\,dx+(\sin x+x^2e^{y}-1)\,dy=0$ is exact. Solve it by integrating $N$ in $y$ first, as the slide does. Which is the general solution?

- A) $y\sin x+x^2e^y+y=c$
- B) $y\sin x+x^2e^y-y=c$
- C) $2y\sin x+2x^2e^y-y=c$
- D) $2y\sin x+2x^2e^y+y=c$

> [!success]- Answer
> **B.** $u=\int N\,dy=y\sin x+x^2e^y-y+\psi(x)$.
> $u_x=y\cos x+2xe^y+\psi'(x)$ must equal $M$, so $\psi'=0$.
> Check: $u_x=M$ and $u_y=N$.
> - A: Sign slip: $\int(-1)\,dy$ taken as $+y$. Then $u_y=\sin x+x^2e^y+1\ne N$.
> - C: $\psi'(x)$ is set equal to all of $M$, not to $M-(y\cos x+2xe^y)$. The shared terms are counted twice.
> - D: Two slips: $\int(-1)\,dy=+y$, and the shared terms counted twice through $\psi'=M$.

### Q18 (slide 16)

Take $\dfrac{2x}{y}\,dx+\left(3y^2-\dfrac{x^2}{y^2}\right)dy=0$ for $y>0$ with $y(1)=1$. Which statement is right?

- A) Exact, since $M_y=N_x=-\dfrac{2x}{y^2}$. Solution: $\dfrac{2x^2}{y}+y^3=3$.
- B) Not exact, since $M_x=\dfrac2y$ and $N_y=6y+\dfrac{2x^2}{y^3}$ differ.
- C) Exact, since $M_y=N_x=-\dfrac{2x}{y^2}$. Solution: $\dfrac{x^2}{y}+y^3=2$.
- D) Not exact, since $M_y=-\dfrac{2x}{y^2}$ and $N_x=\dfrac{2x}{y^2}$ differ.

> [!success]- Answer
> **C.** $M_y=-\dfrac{2x}{y^2}$ and $N_x=-\dfrac{2x}{y^2}$. Equal, so exact.
> $u=\int\dfrac{2x}{y}\,dx=\dfrac{x^2}{y}+\phi(y)$. $u_y=-\dfrac{x^2}{y^2}+\phi'=N$ gives $\phi'=3y^2$, $\phi=y^3$.
> At $(1,1)$: $1+1=c$, so $c=2$.
> - A: The test is right. $\phi'$ is set equal to all of $N$, without subtracting $-\tfrac{x^2}{y^2}$. So $\tfrac{x^2}{y}$ is counted twice.
> - B: The test is done with the partial derivatives swapped. It compares $M_y$ with $N_x$, not $M_x$ with $N_y$.
> - D: Sign slip in $N_x$: the $x$-derivative of $-\tfrac{x^2}{y^2}$ is $-\tfrac{2x}{y^2}$.

## 8. Bernoulli equation (slides 17-18)

### Q19 (slide 17)

Find all solutions of $y'+\dfrac{y}{x}=x\,y^2$ for $x>0$ ($c$, $C$ are arbitrary constants).

- A) $y=\dfrac{3x}{C-x^3}$, and also $y\equiv0$
- B) $y=\dfrac{1}{cx-x^2}$, and also $y\equiv0$
- C) $y=\dfrac{1}{cx-x^2}$, and no other solution
- D) $y=\dfrac{3x}{C-x^3}$, and no other solution

> [!success]- Answer
> **B.** Bernoulli with $\alpha=2$: $v=y^{1-\alpha}=y^{-1}$, $v'=-y^{-2}y'$. Dividing by $y^2$: $-v'+\tfrac vx=x$, so $v'-\tfrac vx=-x$.
> $\mu=e^{-\ln x}=\tfrac1x$: $\left(\tfrac vx\right)'=-1$, so $v=cx-x^2$ and $y=\dfrac1{cx-x^2}$.
> $y\equiv0$ was lost when dividing by $y^2$. It solves the ODE: $0+0=x\cdot0$.
> - A: Integrating factor $e^{-\int p\,dx}=x$ for $v'-\tfrac vx=-x$: $(xv)'=-x^2$, $v=\tfrac{C-x^3}{3x}$. This does not solve the ODE.
> - C: The family is right. The solution $y\equiv0$, lost when dividing by $y^2$, is forgotten.
> - D: Two slips: the factor $e^{-\int p\,dx}$, and the forgotten solution $y\equiv0$.

### Q20 (slide 18)

Solve the IVP $y'+y=\dfrac{x}{y}$, $y(0)=1$.

- A) $y=\sqrt{-x-\tfrac12+\tfrac32e^{2x}}$
- B) $y=\sqrt{x-1+2e^{-x}}$
- C) $y=\sqrt{x+\tfrac12+\tfrac12e^{-2x}}$
- D) $y=\sqrt{x-\tfrac12+\tfrac32e^{-2x}}$

> [!success]- Answer
> **D.** Bernoulli with $\alpha=-1$, so $v=y^{1-\alpha}=y^2$. Multiply by $y$: $yy'+y^2=x$, that is $\tfrac{v'}{2}+v=x$ and $v'+2v=2x$.
> $\mu=e^{2x}$: $e^{2x}v=\int2xe^{2x}\,dx=xe^{2x}-\tfrac12e^{2x}+c$, so $v=x-\tfrac12+ce^{-2x}$.
> $v(0)=1$: $c=\tfrac32$. Positive root, since $y(0)=1>0$.
> - A: Integrating factor $e^{-\int p\,dx}=e^{-2x}$: $(e^{-2x}v)'=2xe^{-2x}$ gives $v=-x-\tfrac12+ce^{2x}$, $c=\tfrac32$.
> - B: $\tfrac{v'}{2}+v=x$ is not multiplied by 2: $v'+v=x$, $\mu=e^x$, $v=x-1+ce^{-x}$, $c=2$.
> - C: Sign slip in the integration by parts: $\int2xe^{2x}\,dx=xe^{2x}+\tfrac12e^{2x}$. Then $v=x+\tfrac12+ce^{-2x}$, $c=\tfrac12$.

## 9. Riccati equation (slides 19-20)

### Q21 (slide 19)

$\phi(x)=\dfrac1x$ solves $y'=y^2-\dfrac{y}{x}-\dfrac{1}{x^2}$ for $x>0$. Put $y=\phi+\dfrac1u$. Which family of solutions do you get ($C$ arbitrary; $y=\phi$ itself is a solution as well)?

- A) $y=\dfrac1x+\dfrac{2x}{C+x^2}$
- B) $y=\dfrac1x+\dfrac{1}{Cx-x\ln x}$
- C) $y=\dfrac1x+\dfrac{2x}{C-x^2}$
- D) $y=\dfrac1x+\dfrac{1}{Cx+x\ln x}$

> [!success]- Answer
> **C.** $y'=-\tfrac1{x^2}-\tfrac{u'}{u^2}$. The right side is $-\tfrac1{x^2}+\tfrac1{xu}+\tfrac1{u^2}$.
> So $-\tfrac{u'}{u^2}=\tfrac1{xu}+\tfrac1{u^2}$. Multiply by $-u^2$: $u'+\tfrac ux=-1$.
> $\mu=x$: $(xu)'=-x$, $xu=-\tfrac{x^2}{2}+c$, so $\tfrac1u=\dfrac{2x}{2c-x^2}$. Put $C=2c$.
> - A: The minus is lost when integrating: $(xu)'=-x$ gives $xu=\tfrac{x^2}{2}+c$.
> - B: Integrating factor $e^{-\int p\,dx}=\tfrac1x$ for $u'+\tfrac ux=-1$: $\left(\tfrac ux\right)'=-\tfrac1x$, $u=Cx-x\ln x$.
> - D: Sign slip in $y'$: $\phi'+\tfrac{u'}{u^2}$. Then $u'-\tfrac ux=1$, $\mu=\tfrac1x$, $u=Cx+x\ln x$.

### Q22 (slide 20)

Every function $y=1+\dfrac{3x^3}{3c-x^3}$ ($c$ a constant) solves $y'=\dfrac{y^2}{x}+\dfrac yx-\dfrac2x$ for $x>0$. Which pair gives the solution with $y(1)=2$ and the solution with $y(1)=1$?

- A) $y(1)=2$: $y=1+\dfrac{6x^3}{5-2x^3}$. $y(1)=1$: $y\equiv1$.
- B) $y(1)=2$: $y=1+\dfrac{3x^3}{4-x^3}$. $y(1)=1$: $y\equiv1$.
- C) $y(1)=2$: $y=1+\dfrac{3x^3}{4-x^3}$. $y(1)=1$: no solution exists.
- D) $y(1)=2$: $y=1+\dfrac{6x^3}{5-2x^3}$. $y(1)=1$: no solution exists.

> [!success]- Answer
> **B.** $2=1+\dfrac{3}{3c-1}$ gives $3c-1=3$, so $3c=4$.
> $y(1)=1$ would need $\dfrac{3}{3c-1}=0$: no $c$ works.
> But $y\equiv1$ solves the ODE: $y'=0$ and $\dfrac{1+1-2}{x}=0$.
> - A: The 1 in front is dropped: $2=\dfrac{3}{3c-1}$ gives $3c=\tfrac52$. Then $y(1)=3$.
> - C: The first part is right. Only the family is searched, and the constant solution $y\equiv1$ is forgotten.
> - D: Two slips: the 1 in front is dropped, and the constant solution $y\equiv1$ is forgotten.
