---
course: MATH 501 Advanced Engineering Mathematics
lecture: 8
title: Laplace's equation
tags: [math501, lecture]
slides: lectures/lecture_08/Math501 Chapter 8.pdf
full_notes: lecture_notes/lecture_08/MATH501_Lecture_08_Laplace_Equation.pdf
---
# MATH 501 · Lecture 8 · Laplace's equation

> [!summary] In short
> - The Laplacian is $\nabla^2u=u_{xx}+u_{yy}$ (plus $u_{zz}$ in three dimensions). Laplace's equation is $\nabla^2u=0$. Its solutions are called harmonic.
> - A Dirichlet problem asks for a harmonic function in a region $D$ with given values $f$ on the boundary $\partial D$.
> - The problem $y''+\lambda y=0$, $y(0)=y(L)=0$ has non-trivial solutions only for $\lambda_n=\dfrac{n^2\pi^2}{L^2}$, with $y_n=\sin\dfrac{n\pi x}{L}$.
> - The sines are orthogonal on $[0,L]$: the integral of a product is $0$ for $m\neq n$ and $\dfrac L2$ for $m=n$.
> - Rectangle with data on the top edge: $u=\sum c_n\sin\dfrac{n\pi x}{L}\sinh\dfrac{n\pi y}{L}$, $c_n=\dfrac{2}{L\sinh(n\pi K/L)}\displaystyle\int_0^Lf(x)\sin\dfrac{n\pi x}{L}\,dx$.

The slide numbers below are the pages of the Chapter 8 PDF (page 1 is printed page 110).

## 1. Laplacian, Laplace's equation, harmonic functions (slide 1)
![[math501_lecture_08_math501_chapter_8_p001.jpg]]

**Notes.** The **Laplacian** of $u$ adds the second partial derivatives in every coordinate direction:

$$\nabla^2u=\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}\quad\text{(2D)},\qquad\nabla^2u=\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}+\frac{\partial^2u}{\partial z^2}\quad\text{(3D)}.$$

$\dfrac{\partial^2u}{\partial x^2}$ is also written $u_{xx}$. It means: differentiate twice in $x$ and treat $y$ (and $z$) as constants. $\nabla^2$ is read "del squared". It takes a function and gives a new function.

**Laplace's equation** is the partial differential equation $\nabla^2u=0$:

$$u_{xx}+u_{yy}=0\quad\text{(2D)},\qquad u_{xx}+u_{yy}+u_{zz}=0\quad\text{(3D)}.$$

A function that satisfies Laplace's equation in a region is **harmonic** on that region.

Test: compute each second partial derivative, add them, and see if the sum is $0$ at every point of the region.

> [!example] Slide example
> $u(x,y)=x^2-y^2$. Then $u_x=2x$, $u_y=-2y$, $u_{xx}=2$, $u_{yy}=-2$.
> $u_{xx}+u_{yy}=2-2=0$ for all $(x,y)$. So $u$ is harmonic on the entire plane.

> [!warning] Watch out
> - Three different things: the Laplacian $\nabla^2$ is an operation, Laplace's equation is $\nabla^2u=0$, and the Laplace transform of Lecture 3 is a different tool that is not used here.
> - The sum must be $0$ at every point of the region. Zero at some points is not enough.
> - Only the pure second derivatives $u_{xx}$, $u_{yy}$ enter. The mixed derivative $u_{xy}$ does not.

> [!info] What harmonic means for the shape of $u$ (beyond the slides)
> $u_{xx}=-u_{yy}$: the surface curves up in one direction as much as it curves down in the other (a saddle, like $x^2-y^2$).
> So a non-constant harmonic function has no local maximum or minimum inside its region. The largest and smallest values are on the boundary (maximum principle).
> Physical meaning: $u$ is a steady temperature. Nothing changes in time, and no point inside is hotter than all its neighbours.

> [!question]- Check (slide 1, Laplacian): Compute $\nabla^2u$ for (a) $u(x,y)=x^2y^3+e^{y}\sin(2x)$ and (b) $u(x,y,z)=xyz^2+ze^{3x}$.
> **(a)** Two variables, so $\nabla^2u=u_{xx}+u_{yy}$.
> Step 1. $x$-derivatives, $y$ is a constant.
> - $u_x=2xy^3+2e^{y}\cos(2x)$
> - $u_{xx}=2y^3-4e^{y}\sin(2x)$
>
> Step 2. $y$-derivatives, $x$ is a constant.
> - $u_y=3x^2y^2+e^{y}\sin(2x)$
> - $u_{yy}=6x^2y+e^{y}\sin(2x)$
>
> Step 3. Add:
>
> $$\nabla^2u=2y^3-4e^{y}\sin(2x)+6x^2y+e^{y}\sin(2x)=2y^3+6x^2y-3e^{y}\sin(2x).$$
>
> **(b)** Three variables, so $\nabla^2u=u_{xx}+u_{yy}+u_{zz}$.
> Step 1. $u_x=yz^2+3ze^{3x}$, $u_{xx}=9ze^{3x}$ (the term $yz^2$ has no $x$, its derivative is 0).
> Step 2. $u_y=xz^2$, $u_{yy}=0$ ($xz^2$ has no $y$).
> Step 3. $u_z=2xyz+e^{3x}$, $u_{zz}=2xy$.
> Step 4. Add: $\nabla^2u=9ze^{3x}+0+2xy=2xy+9ze^{3x}$.
> Both results are functions, not numbers. Neither is zero everywhere, so neither $u$ is harmonic.

> [!question]- Check (slide 1, harmonic): Which of these functions are harmonic on the whole plane? (a) $u=x^3-3xy^2$ (b) $u=e^{-3x}\cos(3y)$ (c) $u=x^2y+xy^2$. (d) For which numbers $k$ is $u=\cos(2x)\cosh(ky)$ harmonic?
> Method for each: compute $u_{xx}$ and $u_{yy}$ and add.
> **(a)** $u_x=3x^2-3y^2$, $u_{xx}=6x$. $u_y=-6xy$, $u_{yy}=-6x$.
> $u_{xx}+u_{yy}=6x-6x=0$ for all $(x,y)$. Harmonic.
> **(b)** $u_x=-3e^{-3x}\cos(3y)$, $u_{xx}=9e^{-3x}\cos(3y)$.
> $u_y=-3e^{-3x}\sin(3y)$, $u_{yy}=-9e^{-3x}\cos(3y)$.
> $u_{xx}+u_{yy}=9e^{-3x}\cos(3y)-9e^{-3x}\cos(3y)=0$. Harmonic.
> **(c)** $u_x=2xy+y^2$, $u_{xx}=2y$. $u_y=x^2+2xy$, $u_{yy}=2x$.
> $u_{xx}+u_{yy}=2y+2x$. This is zero only on the line $y=-x$, not on a region. Not harmonic.
> **(d)** $u_x=-2\sin(2x)\cosh(ky)$, $u_{xx}=-4\cos(2x)\cosh(ky)$.
> $u_y=k\cos(2x)\sinh(ky)$, $u_{yy}=k^2\cos(2x)\cosh(ky)$ (because $(\cosh t)'=\sinh t$ and $(\sinh t)'=\cosh t$).
> $u_{xx}+u_{yy}=(k^2-4)\cos(2x)\cosh(ky)$. This is zero everywhere exactly when $k^2-4=0$, so $k=2$ or $k=-2$.
> Pattern to remember: a trigonometric factor with frequency 2 in $x$ needs an exponential or hyperbolic factor with the same number 2 in $y$. The same pattern returns in section 4 as $\sin\dfrac{n\pi x}{L}\sinh\dfrac{n\pi y}{L}$.

> [!question]- Check (slide 1, three dimensions): Show that $u(x,y,z)=\dfrac{1}{\sqrt{x^2+y^2+z^2}}$ is harmonic at every point except the origin.
> Write $r=\sqrt{x^2+y^2+z^2}$, so $u=r^{-1}=(x^2+y^2+z^2)^{-1/2}$.
> Step 1. First derivative in $x$ (chain rule, inner derivative $2x$):
>
> $$u_x=-\tfrac12(x^2+y^2+z^2)^{-3/2}\cdot2x=-x\,r^{-3}.$$
>
> Step 2. Second derivative in $x$ (product rule on $-x\cdot r^{-3}$). First $\dfrac{\partial}{\partial x}r^{-3}=-\tfrac32(x^2+y^2+z^2)^{-5/2}\cdot2x=-3x\,r^{-5}$. Then
>
> $$u_{xx}=-1\cdot r^{-3}+(-x)(-3x\,r^{-5})=-r^{-3}+3x^2r^{-5}.$$
>
> Step 3. The function is symmetric in $x,y,z$. So in the same way $u_{yy}=-r^{-3}+3y^2r^{-5}$ and $u_{zz}=-r^{-3}+3z^2r^{-5}$.
> Step 4. Add and use $x^2+y^2+z^2=r^2$:
>
> $$\nabla^2u=-3r^{-3}+3(x^2+y^2+z^2)r^{-5}=-3r^{-3}+3r^2r^{-5}=-3r^{-3}+3r^{-3}=0.$$
>
> Step 5. The steps need $r\neq0$. At the origin $u$ is not defined. So $u$ is harmonic on space without the origin.
> This $u$ is the potential of a point charge or a point mass (beyond the slides).

## 2. Dirichlet problem and the eigenvalue problem (slides 2-3)
![[math501_lecture_08_math501_chapter_8_p002.jpg]]
![[math501_lecture_08_math501_chapter_8_p003.jpg]]

**Notes.** A **Dirichlet problem** for a region $D$ asks for a function that is harmonic on $D$ and has given values on the boundary $\partial D$:

$$\nabla^2u=0\ \text{ on }D,\qquad u(x,y)=f(x,y)\ \text{ for }(x,y)\text{ in }\partial D.$$

The given function $f$ is the **boundary data**. The unknown is $u$ inside $D$. Picture: $u$ is the steady temperature of a plate, and the edge of the plate is held at the temperature $f$.

The slides solve the Dirichlet problem with **separation of variables** (section 4). That method needs an eigenvalue problem first.

**Two-point boundary value problem (BVP).** An ODE $y''+p(x)y'+q(x)y=h(x)$ with the conditions $y(\alpha)=y_0$ and $y(\beta)=y_1$ at two different points $\alpha\neq\beta$. The two conditions are the **boundary conditions**.

The problem of this chapter is

$$y''+\lambda y=0,\qquad y(0)=0,\qquad y(L)=0\qquad(8.1)$$

with a real number $\lambda$ and $L>0$. The function $y=0$ always solves it: the **trivial solution**. A number $\lambda$ for which (8.1) has a non-trivial solution is an **eigenvalue**. The non-trivial solutions are the **eigenfunctions**. A nonzero constant multiple of an eigenfunction is again an eigenfunction.

Method: treat $\lambda>0$, $\lambda<0$, $\lambda=0$ one by one. In each case write the general solution from the characteristic equation $r^2+\lambda=0$ and apply the two boundary conditions.

- **Case i, $\lambda>0$.** $r=\pm i\sqrt\lambda$, so $y=c_1\cos(\sqrt\lambda\,x)+c_2\sin(\sqrt\lambda\,x)$. $y(0)=0$ gives $c_1=0$. $y(L)=0$ gives $c_2\sin(\sqrt\lambda\,L)=0$. For a non-trivial solution $c_2\neq0$, so $\sin(\sqrt\lambda\,L)=0$, so $\sqrt\lambda\,L=n\pi$ with $n=1,2,3,\dots$
- **Case ii, $\lambda<0$.** $r=\pm\sqrt{-\lambda}$ (real), so $y=c_1\cosh(\sqrt{-\lambda}\,x)+c_2\sinh(\sqrt{-\lambda}\,x)$. $y(0)=0$ gives $c_1=0$. $y(L)=0$ gives $c_2\sinh(\sqrt{-\lambda}\,L)=0$. The number $\sqrt{-\lambda}\,L$ is positive and $\sinh z=0$ only at $z=0$, so $c_2=0$. Only $y=0$.
- **Case iii, $\lambda=0$.** $y''=0$, so $y=c_1x+c_2$. $y(0)=0$ gives $c_2=0$. $y(L)=0$ gives $c_1L=0$, so $c_1=0$. Only $y=0$.

**Summary.**

$$\lambda_n=\frac{n^2\pi^2}{L^2},\qquad y_n=\sin\left(\frac{n\pi x}{L}\right),\qquad n=1,2,3,\dots$$

There are no other real eigenvalues.

Steps the slide skips:
- Why $\cosh$ and $\sinh$ in case ii. Two real roots give $y=a\,e^{sx}+b\,e^{-sx}$ with $s=\sqrt{-\lambda}$. With $\cosh z=\dfrac{e^z+e^{-z}}{2}$ and $\sinh z=\dfrac{e^z-e^{-z}}{2}$ we have $e^{z}=\cosh z+\sinh z$ and $e^{-z}=\cosh z-\sinh z$. So $y=(a+b)\cosh(sx)+(a-b)\sinh(sx)$. This form is easier because $\cosh0=1$ and $\sinh0=0$.
- Why $\sinh z\neq0$ for $z>0$. $\sinh z=0$ means $e^z=e^{-z}$, so $e^{2z}=1$, so $z=0$.
- Why $n$ starts at 1. $n=0$ gives $\lambda=0$, which is not in case i. Negative $n$ gives the same $\lambda_n$ and the eigenfunction $\sin\left(-\dfrac{n\pi x}{L}\right)=-\sin\dfrac{n\pi x}{L}$, a constant multiple of the one we already have.

> [!warning] Watch out
> - An initial value problem for such a linear ODE (both conditions at one point) has exactly one solution. A boundary value problem can have no solution, one solution, or infinitely many (beyond the slides).
> - The summary is for the conditions $y(0)=0$, $y(L)=0$ only. Other boundary conditions give other eigenvalues, and then $\lambda=0$ can be an eigenvalue (beyond the slides, see the info box below).
> - The eigenvalue is $\left(\dfrac{n\pi}{L}\right)^2$, with the square. The number inside the sine is $\dfrac{n\pi}{L}$, without the square.

> [!info] Neumann problem and other boundary conditions (beyond the slides)
> - A **Neumann problem** gives the normal derivative $\dfrac{\partial u}{\partial n}$ on $\partial D$ in place of $u$. Physically: the heat flow through the edge is given, not the temperature. An insulated edge has $\dfrac{\partial u}{\partial n}=0$.
> - In separation of variables an insulated edge at $x=0$ gives the condition $X'(0)=0$ in place of $X(0)=0$. The three cases must then be done again.
> - Results for $y''+\lambda y=0$ (derived the same way): with $y'(0)=0$, $y'(L)=0$ the eigenvalues are $\lambda_0=0$ with $y_0=1$ and $\lambda_n=\dfrac{n^2\pi^2}{L^2}$ with $y_n=\cos\dfrac{n\pi x}{L}$, $n=1,2,3,\dots$ With $y(0)=0$, $y'(L)=0$ they are $\lambda_n=\dfrac{(2n-1)^2\pi^2}{4L^2}$ with $y_n=\sin\dfrac{(2n-1)\pi x}{2L}$, $n=1,2,3,\dots$
> - Uniqueness: a Dirichlet problem on a bounded region has at most one solution. The difference of two solutions is harmonic and is 0 on the boundary. By the maximum principle its largest and smallest values are on the boundary, so it is 0 everywhere.

> [!question]- Check (slide 2, Dirichlet problem): $D$ is the unit disk $x^2+y^2<1$ and the boundary data is $f(x,y)=x^2$. (a) Show that $u=\tfrac12(1+x^2-y^2)$ solves this Dirichlet problem. (b) Why is $u=x^2$ not the solution, although it equals $f$ on the boundary?
> A solution must do two things: satisfy $\nabla^2u=0$ inside $D$, and equal $f$ on $\partial D$.
> **(a)** Step 1. Equation. $u_x=\tfrac12\cdot2x=x$, $u_{xx}=1$. $u_y=\tfrac12\cdot(-2y)=-y$, $u_{yy}=-1$. Sum: $1-1=0$. Harmonic.
> Step 2. Boundary. $\partial D$ is the circle $x^2+y^2=1$. On it $y^2=1-x^2$. Put this into $u$:
>
> $$u=\tfrac12\bigl(1+x^2-(1-x^2)\bigr)=\tfrac12\bigl(1+x^2-1+x^2\bigr)=\tfrac12\cdot2x^2=x^2=f.$$
>
> Both conditions hold, so $u$ solves the Dirichlet problem.
> **(b)** For $u=x^2$: $u_{xx}=2$, $u_{yy}=0$, sum $2\neq0$. It has the right boundary values but it is not harmonic inside $D$.
> Role of the boundary data: Laplace's equation alone has many solutions ($0$, $x^2-y^2$, $x$, $xy$, ...). The boundary condition selects one of them. Here the solution is unique (info box above, beyond the slides).
> Value at the centre: $u(0,0)=\tfrac12$. This is the average of $f=x^2=\cos^2\theta$ over the circle, which is $\tfrac12$ (mean value property, beyond the slides).

> [!question]- Check (slide 2, boundary value problem): For $y''+y=0$ find all solutions with (a) $y(0)=0$, $y(\pi/2)=1$ (b) $y(0)=0$, $y(\pi)=1$ (c) $y(0)=0$, $y(\pi)=0$.
> General solution: characteristic equation $r^2+1=0$, $r=\pm i$, so $y=c_1\cos x+c_2\sin x$.
> First condition in all three parts: $y(0)=c_1\cos0+c_2\sin0=c_1=0$. So $y=c_2\sin x$.
> **(a)** $y(\pi/2)=c_2\sin(\pi/2)=c_2=1$. Exactly one solution: $y=\sin x$.
> **(b)** $y(\pi)=c_2\sin\pi=c_2\cdot0=0$. The condition asks for $1$. $0=1$ is impossible. No solution.
> **(c)** $y(\pi)=c_2\cdot0=0$ is true for every $c_2$. Infinitely many solutions: $y=c_2\sin x$.
> Part (c) is the problem (8.1) with $L=\pi$ and $\lambda=1$. It has non-trivial solutions, so $\lambda=1=\dfrac{1^2\pi^2}{\pi^2}$ is an eigenvalue and $\sin x$ is an eigenfunction.

> [!question]- Check (slides 2-3, case i): Find all eigenvalues $\lambda>0$ and the eigenfunctions of $y''+\lambda y=0$, $y(0)=0$, $y(3)=0$.
> Here $L=3$.
> Step 1. Characteristic equation: $r^2+\lambda=0$, so $r^2=-\lambda<0$ and $r=\pm i\sqrt\lambda$.
> Step 2. General solution (complex roots $0\pm i\sqrt\lambda$): $y=c_1\cos(\sqrt\lambda\,x)+c_2\sin(\sqrt\lambda\,x)$.
> Step 3. $y(0)=0$: $c_1\cos0+c_2\sin0=c_1\cdot1+c_2\cdot0=c_1$. So $c_1=0$ and $y=c_2\sin(\sqrt\lambda\,x)$.
> Step 4. $y(3)=0$: $c_2\sin(3\sqrt\lambda)=0$. With $c_2=0$ we get $y=0$, the trivial solution. So take $c_2\neq0$ and require $\sin(3\sqrt\lambda)=0$.
> Step 5. The sine is zero exactly at integer multiples of $\pi$. $3\sqrt\lambda>0$, so $3\sqrt\lambda=n\pi$ with $n=1,2,3,\dots$ Then $\sqrt\lambda=\dfrac{n\pi}{3}$.
> Step 6. Square:
>
> $$\lambda_n=\frac{n^2\pi^2}{9},\qquad y_n=\sin\left(\frac{n\pi x}{3}\right),\qquad n=1,2,3,\dots$$
>
> First three: $\lambda_1=\dfrac{\pi^2}{9}$, $\lambda_2=\dfrac{4\pi^2}{9}$, $\lambda_3=\pi^2$ with $y_1=\sin\dfrac{\pi x}{3}$, $y_2=\sin\dfrac{2\pi x}{3}$, $y_3=\sin(\pi x)$.
> Step 7. Check for general $n$. $y_n'=\dfrac{n\pi}{3}\cos\dfrac{n\pi x}{3}$, $y_n''=-\dfrac{n^2\pi^2}{9}\sin\dfrac{n\pi x}{3}=-\lambda_ny_n$. So $y_n''+\lambda_ny_n=0$.
> $y_n(0)=\sin0=0$ and $y_n(3)=\sin(n\pi)=0$. Correct.

> [!question]- Check (slide 3, cases ii and iii): Show that $y''+\lambda y=0$, $y(0)=0$, $y(3)=0$ has only the trivial solution for $\lambda=-4$ and for $\lambda=0$.
> **$\lambda=-4$ (case ii).** The ODE is $y''-4y=0$.
> Step 1. $r^2-4=0$, $r=\pm2$ (real roots, $\sqrt{-\lambda}=2$).
> Step 2. General solution: $y=c_1\cosh(2x)+c_2\sinh(2x)$.
> Step 3. $y(0)=0$: $c_1\cosh0+c_2\sinh0=c_1\cdot1+c_2\cdot0=c_1$. So $c_1=0$ and $y=c_2\sinh(2x)$.
> Step 4. $y(3)=0$: $c_2\sinh(6)=0$. Now $\sinh6=\dfrac{e^{6}-e^{-6}}{2}\approx201.7\neq0$. So $c_2=0$.
> Step 5. Both constants are 0, so $y=0$. $\lambda=-4$ is not an eigenvalue.
> The same steps work for every $\lambda<0$: $\sinh(3\sqrt{-\lambda})>0$ because $3\sqrt{-\lambda}>0$.
> **$\lambda=0$ (case iii).** The ODE is $y''=0$.
> Step 1. Integrate twice: $y'=c_1$, $y=c_1x+c_2$.
> Step 2. $y(0)=0$: $c_2=0$.
> Step 3. $y(3)=0$: $3c_1=0$, so $c_1=0$.
> Step 4. $y=0$ only. $\lambda=0$ is not an eigenvalue.
> Picture: for $\lambda\le0$ the solution that starts at 0 is a multiple of $\sinh$ or of $x$. These functions leave zero and never come back. Only a sine comes back to zero.

> [!question]- Check (slide 3, summary): Use the summary. (a) Write the eigenvalues and eigenfunctions for $y(0)=0$, $y(1/2)=0$. (b) For $L=\pi$: is $\lambda=20$ an eigenvalue? Is $\lambda=25$? (c) For which lengths $L$ is $\lambda=9$ an eigenvalue?
> **(a)** $L=\tfrac12$. $\dfrac{n\pi}{L}=2n\pi$. So $\lambda_n=(2n\pi)^2=4n^2\pi^2$ and $y_n=\sin(2n\pi x)$, $n=1,2,3,\dots$
> Check: $y_n(1/2)=\sin(n\pi)=0$. Correct.
> **(b)** $L=\pi$ gives $\lambda_n=\dfrac{n^2\pi^2}{\pi^2}=n^2$: the eigenvalues are $1,4,9,16,25,\dots$
> $20$ is not a square of an integer, so it is not an eigenvalue. Directly: $y=c_2\sin(\sqrt{20}\,x)$ and $\sin(\sqrt{20}\,\pi)=\sin(14.05)\approx0.996\neq0$, so $c_2=0$.
> $25=5^2$ is the eigenvalue $\lambda_5$ with $y_5=\sin(5x)$.
> **(c)** We need $\dfrac{n^2\pi^2}{L^2}=9$ for some positive integer $n$. So $L^2=\dfrac{n^2\pi^2}{9}$ and $L=\dfrac{n\pi}{3}$: $L=\dfrac\pi3,\dfrac{2\pi}3,\pi,\dots$
> Meaning: the solution $\sin(3x)$ of $y''+9y=0$ is zero at $x=\dfrac{n\pi}{3}$. The interval must end at one of these zeros.

> [!question]- Check (slide 3, other boundary conditions, beyond the slides): Find the eigenvalues and eigenfunctions of $y''+\lambda y=0$, $y'(0)=0$, $y'(\pi)=0$. What is different from the summary on the slide?
> The conditions are now on $y'$, so the three cases must be done again.
> **Case $\lambda>0$.** Write $s=\sqrt\lambda>0$. $y=c_1\cos(sx)+c_2\sin(sx)$ and $y'=-c_1s\sin(sx)+c_2s\cos(sx)$.
> - $y'(0)=0$: $-c_1s\cdot0+c_2s\cdot1=c_2s=0$. $s\neq0$, so $c_2=0$.
> - $y'(\pi)=0$: $-c_1s\sin(s\pi)=0$. For a non-trivial solution $c_1\neq0$, so $\sin(s\pi)=0$, $s\pi=n\pi$, $s=n$.
>
> Eigenvalues $\lambda_n=n^2$, eigenfunctions $y_n=\cos(nx)$, $n=1,2,3,\dots$
> **Case $\lambda=0$.** $y=c_1x+c_2$, $y'=c_1$.
> - $y'(0)=0$: $c_1=0$.
> - $y'(\pi)=0$: $c_1=0$ again. Nothing new.
>
> $c_2$ stays free. So $y=c_2$ is a non-trivial solution: $\lambda_0=0$ is an eigenvalue with the eigenfunction $y_0=1$.
> **Case $\lambda<0$.** Write $s=\sqrt{-\lambda}>0$. $y=c_1\cosh(sx)+c_2\sinh(sx)$ and $y'=c_1s\sinh(sx)+c_2s\cosh(sx)$.
> - $y'(0)=0$: $c_1s\cdot0+c_2s\cdot1=c_2s=0$, so $c_2=0$.
> - $y'(\pi)=0$: $c_1s\sinh(s\pi)=0$. $s>0$ and $\sinh(s\pi)>0$, so $c_1=0$.
>
> Only $y=0$. No negative eigenvalues.
> **Result.** $\lambda_0=0$ with $y_0=1$, and $\lambda_n=n^2$ with $y_n=\cos(nx)$.
> Differences: the eigenfunctions are cosines, not sines, and $\lambda=0$ is now an eigenvalue.
> Check for $y_n=\cos(nx)$: $y_n''=-n^2\cos(nx)=-\lambda_ny_n$. $y_n'=-n\sin(nx)$ is $0$ at $x=0$ and at $x=\pi$. Correct.

## 3. Orthogonality of the sines (slide 4)
![[math501_lecture_08_math501_chapter_8_p004.jpg]]

**Notes.** For positive integers $m$ and $n$ and $L>0$:

$$\int_0^L\sin\left(\frac{m\pi x}{L}\right)\sin\left(\frac{n\pi x}{L}\right)dx=\begin{cases}0,&m\neq n\\[2pt]\dfrac L2,&m=n\end{cases}$$

Two different eigenfunctions are **orthogonal** on $[0,L]$. An eigenfunction with itself gives $\dfrac L2$.

The slide proves it with two identities:
- (i) $m=n$: $\sin^2\theta=\tfrac12(1-\cos2\theta)$.
- (ii) $m\neq n$: $\sin a\sin b=\tfrac12[\cos(a-b)-\cos(a+b)]$.

After that every antiderivative is a sine, and a sine of an integer multiple of $\pi$ is 0. The rule used for the antiderivatives is $\int\cos(kx)\,dx=\dfrac1k\sin(kx)$ for $k\neq0$.

Use: orthogonality picks one coefficient out of an infinite sum. Multiply the sum by $\sin\dfrac{m\pi x}{L}$ and integrate from 0 to $L$. Every term disappears except the term with $n=m$.

> [!warning] Slide error
> The slide says "if $m$ is an integer" in (i) and "integers such that $m\neq n$" in (ii). This is too wide: (i) needs $m\neq0$ and (ii) needs also $m\neq-n$. **Positive** integers satisfy both.
> - (i) with $m=0$: the integrand is $\sin^20=0$, so the integral is $0$, not $\dfrac L2$. The formula on the slide also divides by $m$.
> - (ii) with $n=-m$, $m\neq0$: then $m+n=0$ and the slide divides by $m+n$. Example $L=1$, $m=1$, $n=-1$: $\int_0^1\sin(\pi x)\sin(-\pi x)\,dx=-\int_0^1\sin^2(\pi x)\,dx=-\tfrac12$, not $0$.
>
> In this chapter $m,n=1,2,3,\dots$, so the result on the slide is correct where it is used.

> [!question]- Check (slide 4, part i): Compute $\displaystyle\int_0^3\sin^2\left(\frac{2\pi x}{3}\right)dx$ step by step. Compare with the rule.
> Here $L=3$ and $m=n=2$. The rule gives $\dfrac L2=\dfrac32$.
> Step 1. Identity $\sin^2\theta=\tfrac12(1-\cos2\theta)$ with $\theta=\dfrac{2\pi x}{3}$, so $2\theta=\dfrac{4\pi x}{3}$:
>
> $$\int_0^3\sin^2\left(\frac{2\pi x}{3}\right)dx=\int_0^3\frac12\left(1-\cos\frac{4\pi x}{3}\right)dx.$$
>
> Step 2. Antiderivative. $\int\cos(kx)\,dx=\dfrac1k\sin(kx)$ with $k=\dfrac{4\pi}{3}$, so $\dfrac1k=\dfrac{3}{4\pi}$:
>
> $$=\frac12\left[x-\frac{3}{4\pi}\sin\frac{4\pi x}{3}\right]_0^3.$$
>
> Step 3. Upper limit $x=3$: $\tfrac12\left(3-\dfrac{3}{4\pi}\sin(4\pi)\right)=\tfrac12(3-0)=\dfrac32$.
> Step 4. Lower limit $x=0$: $\tfrac12\left(0-\dfrac{3}{4\pi}\sin0\right)=0$.
> Step 5. Result: $\dfrac32-0=\dfrac32$. Same as the rule.

> [!question]- Check (slide 4, part ii): Compute $\displaystyle\int_0^2\sin\left(\frac{\pi x}{2}\right)\sin\left(\frac{3\pi x}{2}\right)dx$ step by step. Compare with the rule.
> Here $L=2$, $m=1$, $n=3$. $m\neq n$, so the rule gives $0$.
> Step 1. Identity $\sin a\sin b=\tfrac12[\cos(a-b)-\cos(a+b)]$ with $a=\dfrac{\pi x}{2}$, $b=\dfrac{3\pi x}{2}$.
> $a-b=-\pi x$ and $\cos(-\pi x)=\cos(\pi x)$. $a+b=2\pi x$.
>
> $$\int_0^2\sin\frac{\pi x}{2}\sin\frac{3\pi x}{2}\,dx=\int_0^2\frac12\bigl[\cos(\pi x)-\cos(2\pi x)\bigr]dx.$$
>
> Step 2. Antiderivative:
>
> $$=\frac12\left[\frac{1}{\pi}\sin(\pi x)-\frac{1}{2\pi}\sin(2\pi x)\right]_0^2.$$
>
> Step 3. Upper limit $x=2$: $\tfrac12\left[\dfrac1\pi\sin(2\pi)-\dfrac{1}{2\pi}\sin(4\pi)\right]=\tfrac12[0-0]=0$.
> Step 4. Lower limit $x=0$: every sine is $\sin0=0$.
> Step 5. Result: $0-0=0$. Same as the rule.

> [!question]- Check (slide 4, use): It is known that $5\sin(2x)-3\sin(7x)=\sum_{n=1}^{\infty}b_n\sin(nx)$ on $[0,\pi]$. Find $b_2$ with the orthogonality rule, not by reading it off.
> Here $L=\pi$, so $\sin\dfrac{n\pi x}{L}=\sin(nx)$ and $\dfrac L2=\dfrac\pi2$.
> Step 1. Multiply both sides by $\sin(2x)$ and integrate from $0$ to $\pi$:
>
> $$5\int_0^\pi\sin^2(2x)\,dx-3\int_0^\pi\sin(7x)\sin(2x)\,dx=\sum_{n=1}^{\infty}b_n\int_0^\pi\sin(nx)\sin(2x)\,dx.$$
>
> Step 2. Left side. First integral: $m=n=2$, value $\dfrac\pi2$. Second integral: $7\neq2$, value $0$. Left side $=5\cdot\dfrac\pi2-3\cdot0=\dfrac{5\pi}{2}$.
> Step 3. Right side. Every integral with $n\neq2$ is $0$. The term $n=2$ gives $b_2\cdot\dfrac\pi2$.
> Step 4. $\dfrac{5\pi}{2}=b_2\dfrac\pi2$, so $b_2=5$.
> In the same way $b_7=-3$ and $b_n=0$ for all other $n$. This is the shortcut "match the coefficients": if the data is already a sum of eigenfunctions, its coefficients can be read off.

## 4. Dirichlet problem for a rectangle: separation of variables (slides 5-7)
![[math501_lecture_08_math501_chapter_8_p005.jpg]]
![[math501_lecture_08_math501_chapter_8_p006.jpg]]
![[math501_lecture_08_math501_chapter_8_p007.jpg]]

**Notes.** The problem: find $u(x,y)$ with

$$u_{xx}+u_{yy}=0\qquad(8.2)$$

in the rectangle $D=\{0<x<L,\ 0<y<K\}$, with $u=0$ on the bottom edge ($u(x,0)=0$), the left edge ($u(0,y)=0$) and the right edge ($u(L,y)=0$), and $u(x,K)=f(x)$ on the top edge. Three edges are **homogeneous** (value 0). One edge carries the data.

Plan: (1) find simple solutions $X(x)Y(y)$ that satisfy the equation and the three zero conditions, (2) add them (superposition) and choose the coefficients so that the top condition holds.

**Step 1. Separate.** Put $u=X(x)Y(y)$ into (8.2). $Y$ is a constant factor for the $x$-derivative, so $u_{xx}=X''Y$. Also $u_{yy}=XY''$. Then $X''Y+XY''=0$. Divide by $XY$:

$$\frac{X''(x)}{X(x)}=-\frac{Y''(y)}{Y(y)}.$$

The left side depends only on $x$. The right side depends only on $y$. Change $x$ and keep $y$ fixed: the right side does not change, so the left side cannot change. So both sides are one constant. The slide calls it $-\lambda$:

$$X''+\lambda X=0\quad(8.3),\qquad Y''-\lambda Y=0\quad(8.4).$$

**Step 2. Boundary conditions.** $u(0,y)=X(0)Y(y)=0$ for all $y$. $Y$ is not the zero function, so $X(0)=0$. In the same way $X(L)=0$ and $Y(0)=0$.

**Step 3. The $X$-problem** is (8.1): $\lambda=\dfrac{n^2\pi^2}{L^2}$, $X_n=\sin\dfrac{n\pi x}{L}$.

**Step 4. The $Y$-problem.** $Y''-\dfrac{n^2\pi^2}{L^2}Y=0$ (8.5) has the roots $r=\pm\dfrac{n\pi}{L}$, so $Y=k_1\cosh\dfrac{n\pi y}{L}+k_2\sinh\dfrac{n\pi y}{L}$. $Y(0)=0$ gives $k_1=0$. So $Y_n=\sinh\dfrac{n\pi y}{L}$.

**Step 5. Fundamental solutions and superposition.**

$$u_n(x,y)=\sin\left(\frac{n\pi x}{L}\right)\sinh\left(\frac{n\pi y}{L}\right),\qquad u(x,y)=\sum_{n=1}^{\infty}c_n\sin\left(\frac{n\pi x}{L}\right)\sinh\left(\frac{n\pi y}{L}\right).$$

**Step 6. Top edge.** Put $y=K$: $f(x)=\sum c_n\sinh\dfrac{n\pi K}{L}\sin\dfrac{n\pi x}{L}$. Multiply by $\sin\dfrac{m\pi x}{L}$, integrate from $0$ to $L$, use orthogonality: only $n=m$ stays, with the factor $\dfrac L2$.

$$\int_0^Lf(x)\sin\frac{m\pi x}{L}\,dx=\frac L2\,c_m\sinh\frac{m\pi K}{L}\quad\Longrightarrow\quad c_n=\frac{2}{L\sinh\left(\frac{n\pi K}{L}\right)}\int_0^Lf(x)\sin\left(\frac{n\pi x}{L}\right)dx.$$

The division is allowed because $\sinh\dfrac{n\pi K}{L}>0$.

> [!warning] Watch out
> - The variable with **two** zero edges gets the eigenvalue problem and the sines. The other variable gets $\sinh$ and $\cosh$.
> - Both factors use the same number $\dfrac{n\pi}{L}$. $L$ is the length of the side with the two zero conditions, also inside the $\sinh$. $K$ appears only in $\sinh\dfrac{n\pi K}{L}$ in the coefficient.
> - Do not forget the factor $\sinh\dfrac{n\pi K}{L}$ in $c_n$. Without it the top edge has the wrong values.
> - The sign of the constant ($-\lambda$ or $\lambda$) is only a name. Choose it so that the factor with two zero conditions gets the form $(\cdot)''+\lambda(\cdot)=0$.

> [!info] Shortcut and Fourier sine series (beyond the slides)
> - If $f$ is already a finite sum of eigenfunctions, $f(x)=\sum b_n\sin\dfrac{n\pi x}{L}$, then no integral is needed: $c_n\sinh\dfrac{n\pi K}{L}=b_n$. The slide examples are all of this type. They do the integrals anyway, and orthogonality gives the same result.
> - For a general $f$ the numbers $b_n=\dfrac2L\int_0^Lf(x)\sin\dfrac{n\pi x}{L}\,dx$ are the **Fourier sine coefficients** of $f$, and $c_n=\dfrac{b_n}{\sinh(n\pi K/L)}$.
> - If $f(0)\neq0$ or $f(L)\neq0$, the data does not fit the zero side edges at the corners. The series still converges to $f(x)$ for $0<x<L$, but slowly near the corners (terms like $\dfrac1n$).
> - Inside the rectangle the series converges very fast: $\dfrac{\sinh(n\pi y/L)}{\sinh(n\pi K/L)}\approx e^{-n\pi(K-y)/L}$ for large $n$.

> [!question]- Check (slide 5): Consider $u_{xx}+u_{yy}=0$ in $0<x<3$, $0<y<5$ with $u(0,y)=0$, $u(3,y)=0$, $u(x,0)=0$ and $u(x,5)=f(x)$. Put $u=X(x)Y(y)$. Find the two ODEs and the conditions on $X$ and $Y$. Which function gets an eigenvalue problem?
> Step 1. Derivatives of the product. For $u_{xx}$ the factor $Y(y)$ is a constant: $u_{xx}=X''(x)Y(y)$. For $u_{yy}$ the factor $X(x)$ is a constant: $u_{yy}=X(x)Y''(y)$.
> Step 2. Equation: $X''Y+XY''=0$.
> Step 3. Divide by $XY$: $\dfrac{X''}{X}+\dfrac{Y''}{Y}=0$, so $\dfrac{X''(x)}{X(x)}=-\dfrac{Y''(y)}{Y(y)}$.
> Step 4. Left side: function of $x$ only. Right side: function of $y$ only. They are equal for all $x$ and $y$, so both are the same constant. Name it $-\lambda$.
> Step 5. $\dfrac{X''}{X}=-\lambda$ gives $X''=-\lambda X$, so $X''+\lambda X=0$.
> $-\dfrac{Y''}{Y}=-\lambda$ gives $Y''=\lambda Y$, so $Y''-\lambda Y=0$.
> Step 6. Zero edges.
> - $u(0,y)=X(0)Y(y)=0$ for all $y$. If $X(0)\neq0$, then $Y(y)=0$ for all $y$ and $u$ is trivial. So $X(0)=0$.
> - $u(3,y)=X(3)Y(y)=0$ gives $X(3)=0$.
> - $u(x,0)=X(x)Y(0)=0$ gives $Y(0)=0$.
>
> Step 7. $X$ has two zero conditions: $X''+\lambda X=0$, $X(0)=0$, $X(3)=0$ is the eigenvalue problem (8.1) with $L=3$. $Y$ has only one condition, $Y(0)=0$.
> The condition $u(x,5)=f(x)$ is not used here. It is not homogeneous, so it does not split into a condition on $Y$ alone. It is used at the end for the coefficients.
> Example of the constant: for $u=\sin(2x)\sinh(2y)$, $\dfrac{X''}{X}=\dfrac{-4\sin2x}{\sin2x}=-4$ and $-\dfrac{Y''}{Y}=-\dfrac{4\sinh2y}{\sinh2y}=-4$. Both sides are the same constant, $\lambda=4$.

> [!question]- Check (slide 6): Continue with $L=3$: solve the $X$-problem and the $Y$-problem, write the fundamental solutions $u_n$, and verify that $u_n$ satisfies Laplace's equation and the three zero conditions.
> Step 1. $X$-problem: $X''+\lambda X=0$, $X(0)=X(3)=0$. From the summary with $L=3$: $\lambda_n=\dfrac{n^2\pi^2}{9}$, $X_n=\sin\dfrac{n\pi x}{3}$, $n=1,2,3,\dots$
> Step 2. $Y$-equation with this $\lambda$: $Y''-\dfrac{n^2\pi^2}{9}Y=0$.
> Step 3. Characteristic equation: $r^2-\dfrac{n^2\pi^2}{9}=0$, so $r=\pm\dfrac{n\pi}{3}$. Two real roots:
>
> $$Y=k_1\cosh\frac{n\pi y}{3}+k_2\sinh\frac{n\pi y}{3}.$$
>
> Step 4. $Y(0)=0$: $k_1\cosh0+k_2\sinh0=k_1\cdot1+k_2\cdot0=k_1$. So $k_1=0$ and $Y_n=\sinh\dfrac{n\pi y}{3}$.
> Step 5. Fundamental solutions:
>
> $$u_n(x,y)=\sin\left(\frac{n\pi x}{3}\right)\sinh\left(\frac{n\pi y}{3}\right),\qquad n=1,2,3,\dots$$
>
> Step 6. Check the equation. Write $a=\dfrac{n\pi}{3}$, so $u_n=\sin(ax)\sinh(ay)$.
> - $(u_n)_x=a\cos(ax)\sinh(ay)$, $(u_n)_{xx}=-a^2\sin(ax)\sinh(ay)=-a^2u_n$.
> - $(u_n)_y=a\sin(ax)\cosh(ay)$, $(u_n)_{yy}=a^2\sin(ax)\sinh(ay)=a^2u_n$.
> - Sum: $-a^2u_n+a^2u_n=0$.
>
> Step 7. Check the zero edges.
> - $x=0$: $\sin0=0$, so $u_n(0,y)=0$.
> - $x=3$: $\sin\dfrac{3n\pi}{3}=\sin(n\pi)=0$, so $u_n(3,y)=0$.
> - $y=0$: $\sinh0=0$, so $u_n(x,0)=0$.
>
> On the top edge $u_n(x,5)=\sinh\dfrac{5n\pi}{3}\sin\dfrac{n\pi x}{3}$. This is not zero. The sum $\sum c_nu_n$ must build $f(x)$ there.

> [!question]- Check (slides 6-7, constant data): Solve $u_{xx}+u_{yy}=0$ in $0<x<2$, $0<y<1$ with $u=0$ on the left, right and bottom edges and $u(x,1)=3$.
> Case: data on the top edge, $L=2$, $K=1$, $f(x)=3$. Use the formula of slide 7.
> Step 1. Form of the solution: $\dfrac{n\pi}{L}=\dfrac{n\pi}{2}$, so
>
> $$u(x,y)=\sum_{n=1}^{\infty}c_n\sin\left(\frac{n\pi x}{2}\right)\sinh\left(\frac{n\pi y}{2}\right),\qquad c_n=\frac{2}{2\sinh\left(\frac{n\pi}{2}\right)}\int_0^23\sin\frac{n\pi x}{2}\,dx.$$
>
> Step 2. The integral. $\int\sin(kx)\,dx=-\dfrac1k\cos(kx)$ with $k=\dfrac{n\pi}{2}$, $\dfrac1k=\dfrac{2}{n\pi}$:
>
> $$\int_0^23\sin\frac{n\pi x}{2}\,dx=3\left[-\frac{2}{n\pi}\cos\frac{n\pi x}{2}\right]_0^2=-\frac{6}{n\pi}\cos(n\pi)+\frac{6}{n\pi}\cos0=\frac{6}{n\pi}\bigl(1-(-1)^n\bigr).$$
>
> Here $\cos(n\pi)=(-1)^n$.
> Step 3. Even and odd $n$.
> - $n$ even: $1-1=0$, so the integral is $0$ and $c_n=0$.
> - $n$ odd: $1-(-1)=2$, so the integral is $\dfrac{12}{n\pi}$.
>
> Step 4. Coefficient for odd $n$: $c_n=\dfrac{1}{\sinh(n\pi/2)}\cdot\dfrac{12}{n\pi}=\dfrac{12}{n\pi\sinh(n\pi/2)}$.
> Step 5. Solution:
>
> $$u(x,y)=\sum_{n=1,3,5,\dots}\frac{12}{n\pi\sinh\left(\frac{n\pi}{2}\right)}\sin\left(\frac{n\pi x}{2}\right)\sinh\left(\frac{n\pi y}{2}\right).$$
>
> Step 6. Check, term by term. Each term is a constant times $\sin(ax)\sinh(ay)$ with $a=\dfrac{n\pi}{2}$: $u_{xx}=-a^2(\cdot)$, $u_{yy}=+a^2(\cdot)$, sum 0. At $x=0$: $\sin0=0$. At $x=2$: $\sin(n\pi)=0$. At $y=0$: $\sinh0=0$.
> At $y=1$ the $\sinh$ factors cancel and the series is $\sum_{n\text{ odd}}\dfrac{12}{n\pi}\sin\dfrac{n\pi x}{2}$. This is the Fourier sine series of the constant 3 on $[0,2]$. At $x=1$: $\dfrac{12}{\pi}\left(1-\dfrac13+\dfrac15-\dots\right)=\dfrac{12}{\pi}\cdot\dfrac\pi4=3$. Correct.
> Numbers: $c_1=\dfrac{12}{\pi\sinh(\pi/2)}\approx1.660$. At the centre $(1,\tfrac12)$ the series gives $u\approx1.335$.
> The data $3$ does not fit the zero side edges at the two top corners. The series still gives $3$ for $0<x<2$ on the top edge, with slow convergence near the corners.

> [!question]- Check (slide 7, formula with $f(x)=x$): For $0<x<1$, $0<y<2$ with $u=0$ on the left, right and bottom edges and $u(x,2)=x$, find the coefficients $c_n$ and write the solution.
> Case: data on the top edge, $L=1$, $K=2$, $f(x)=x$. Then $\dfrac{n\pi}{L}=n\pi$.
> Step 1. Formula:
>
> $$c_n=\frac{2}{1\cdot\sinh(2n\pi)}\int_0^1x\sin(n\pi x)\,dx.$$
>
> Step 2. Integration by parts, $\int u\,dv=uv-\int v\,du$. Take $u=x$, $dv=\sin(n\pi x)\,dx$. Then $du=dx$, $v=-\dfrac{1}{n\pi}\cos(n\pi x)$.
>
> $$\int_0^1x\sin(n\pi x)\,dx=\left[-\frac{x}{n\pi}\cos(n\pi x)\right]_0^1+\frac{1}{n\pi}\int_0^1\cos(n\pi x)\,dx.$$
>
> Step 3. First part: at $x=1$: $-\dfrac{1}{n\pi}\cos(n\pi)=-\dfrac{(-1)^n}{n\pi}$. At $x=0$: $0$. So the first part is $-\dfrac{(-1)^n}{n\pi}=\dfrac{(-1)^{n+1}}{n\pi}$.
> Step 4. Second part: $\dfrac{1}{n\pi}\left[\dfrac{1}{n\pi}\sin(n\pi x)\right]_0^1=\dfrac{1}{n^2\pi^2}\bigl(\sin(n\pi)-\sin0\bigr)=0$.
> Step 5. Integral: $\dfrac{(-1)^{n+1}}{n\pi}$.
> Step 6. Coefficient: $c_n=\dfrac{2(-1)^{n+1}}{n\pi\sinh(2n\pi)}$.
> Step 7. Solution:
>
> $$u(x,y)=\sum_{n=1}^{\infty}\frac{2(-1)^{n+1}}{n\pi\sinh(2n\pi)}\sin(n\pi x)\sinh(n\pi y).$$
>
> Step 8. Check, term by term. With $a=n\pi$: $u_{xx}=-a^2(\cdot)$, $u_{yy}=a^2(\cdot)$, sum 0. $x=0$: $\sin0=0$. $x=1$: $\sin(n\pi)=0$. $y=0$: $\sinh0=0$.
> $y=2$: the series is $\sum\dfrac{2(-1)^{n+1}}{n\pi}\sin(n\pi x)$, the Fourier sine series of $x$ on $[0,1]$. Test at $x=\tfrac12$: $\sin\dfrac{n\pi}{2}$ is $1,0,-1,0,\dots$, so the sum is $\dfrac2\pi\left(1-\dfrac13+\dfrac15-\dots\right)=\dfrac2\pi\cdot\dfrac\pi4=\dfrac12$. Correct.
> First coefficient: $c_1=\dfrac{2}{\pi\sinh(2\pi)}\approx0.00238$. It is small because $\sinh(2\pi)\approx267.7$ is large.

## 5. Example: data on the top edge (slides 7-9)
![[math501_lecture_08_math501_chapter_8_p008.jpg]]
![[math501_lecture_08_math501_chapter_8_p009.jpg]]

**Notes.** The example starts at the bottom of slide 7 (embedded in section 4) and ends at the top of slide 9.

> [!example] Slide example
> $D=\{0<x<\pi,\ 0<y<2\pi\}$, $u(0,y)=u(\pi,y)=0$, $u(x,0)=0$, $u(x,2\pi)=\sin x+\sin(3x)$.
> - Separate: $X''+\lambda X=0$, $Y''-\lambda Y=0$, with $X(0)=0$, $X(\pi)=0$, $Y(0)=0$.
> - $X$-problem ($L=\pi$): $\sin(\sqrt\lambda\,\pi)=0$, so $\lambda=n^2$ and $X_n=\sin(nx)$. Nothing for $\lambda\le0$.
> - $Y''-n^2Y=0$: $Y=\beta_1\cosh(ny)+\beta_2\sinh(ny)$, $Y(0)=0$ gives $\beta_1=0$, $Y_n=\sinh(ny)$.
> - $u=\sum c_n\sin(nx)\sinh(ny)$. Top edge: $\sin x+\sin(3x)=\sum c_n\sinh(2\pi n)\sin(nx)$.
> - Orthogonality: $\int_0^\pi\sin x\sin(mx)\,dx+\int_0^\pi\sin(3x)\sin(mx)\,dx=\dfrac\pi2c_m\sinh(2\pi m)$.
> - $m=1$: left side $\dfrac\pi2+0$, so $c_1=\dfrac{1}{\sinh(2\pi)}$. $m=3$: left side $0+\dfrac\pi2$, so $c_3=\dfrac{1}{\sinh(6\pi)}$. Other $m$: left side $0$, so $c_m=0$.
>
> $$u(x,y)=\frac{1}{\sinh(2\pi)}\sin x\sinh y+\frac{1}{\sinh(6\pi)}\sin(3x)\sinh(3y).$$

The slide does not show why the left side is $\dfrac\pi2$ for $m=1$. It is the orthogonality rule with $L=\pi$: $\int_0^\pi\sin x\sin x\,dx=\dfrac\pi2$ (same index) and $\int_0^\pi\sin(3x)\sin x\,dx=0$ (different indices).

Shortcut: the data is $1\cdot\sin(1x)+1\cdot\sin(3x)$, so $b_1=1$, $b_3=1$. Then $c_1\sinh(2\pi\cdot1)=1$ and $c_3\sinh(2\pi\cdot3)=1$.

> [!warning] Watch out
> The argument of the $\sinh$ in the coefficient is $n$ times the height: $\sinh(2\pi n)$, so $\sinh(2\pi)$ for $n=1$ and $\sinh(6\pi)$ for $n=3$. In the solution the factor is $\sinh(ny)$: $\sinh y$ and $\sinh(3y)$.

> [!question]- Check (slides 7-9): Solve $u_{xx}+u_{yy}=0$ in $0<x<2$, $0<y<3$ with $u(0,y)=0$, $u(2,y)=0$, $u(x,0)=0$ and $u(x,3)=4\sin(\pi x)-\sin\left(\dfrac{5\pi x}{2}\right)$.
> Case: the two zero conditions are in $x$ (left and right edge). So $X$ gets the sines. Data on the top edge, $L=2$, $K=3$.
> **Step 1. Separate.** $u=X(x)Y(y)$ gives $X''Y+XY''=0$, so $\dfrac{X''}{X}=-\dfrac{Y''}{Y}=-\lambda$: $X''+\lambda X=0$ and $Y''-\lambda Y=0$.
> **Step 2. Zero edges.** $X(0)Y(y)=0$, $X(2)Y(y)=0$, $X(x)Y(0)=0$ give $X(0)=0$, $X(2)=0$, $Y(0)=0$.
> **Step 3. $X$-problem.** For $\lambda>0$: $X=\alpha_1\cos(\sqrt\lambda\,x)+\alpha_2\sin(\sqrt\lambda\,x)$. $X(0)=\alpha_1=0$. $X(2)=\alpha_2\sin(2\sqrt\lambda)=0$ with $\alpha_2\neq0$ needs $2\sqrt\lambda=n\pi$. So $\lambda=\dfrac{n^2\pi^2}{4}$ and $X_n=\sin\dfrac{n\pi x}{2}$. For $\lambda\le0$ only $X=0$ (cases ii and iii).
> **Step 4. $Y$-problem.** $Y''-\dfrac{n^2\pi^2}{4}Y=0$: $r=\pm\dfrac{n\pi}{2}$, $Y=\beta_1\cosh\dfrac{n\pi y}{2}+\beta_2\sinh\dfrac{n\pi y}{2}$. $Y(0)=\beta_1=0$. So $Y_n=\sinh\dfrac{n\pi y}{2}$.
> **Step 5. Superposition.**
>
> $$u(x,y)=\sum_{n=1}^{\infty}c_n\sin\left(\frac{n\pi x}{2}\right)\sinh\left(\frac{n\pi y}{2}\right).$$
>
> **Step 6. Top edge $y=3$.**
>
> $$4\sin(\pi x)-\sin\frac{5\pi x}{2}=\sum_{n=1}^{\infty}c_n\sinh\left(\frac{3n\pi}{2}\right)\sin\frac{n\pi x}{2}.$$
>
> **Step 7. Which eigenfunctions are in the data?** $\sin(\pi x)=\sin\dfrac{2\pi x}{2}$ is the eigenfunction $n=2$. $\sin\dfrac{5\pi x}{2}$ is $n=5$.
> **Step 8. Orthogonality.** Multiply by $\sin\dfrac{m\pi x}{2}$ and integrate over $[0,2]$. Here $\dfrac L2=1$. Right side: $c_m\sinh\dfrac{3m\pi}{2}\cdot1$.
> - $m=2$: left side $4\int_0^2\sin^2(\pi x)\,dx-\int_0^2\sin\dfrac{5\pi x}{2}\sin(\pi x)\,dx=4\cdot1-0=4$. So $c_2\sinh(3\pi)=4$, $c_2=\dfrac{4}{\sinh(3\pi)}$.
> - $m=5$: left side $4\cdot0-1=-1$. So $c_5\sinh\dfrac{15\pi}{2}=-1$, $c_5=-\dfrac{1}{\sinh(15\pi/2)}$.
> - Other $m$: left side $0$, so $c_m=0$.
>
> **Step 9. Solution.**
>
> $$u(x,y)=\frac{4}{\sinh(3\pi)}\sin(\pi x)\sinh(\pi y)-\frac{1}{\sinh\left(\frac{15\pi}{2}\right)}\sin\left(\frac{5\pi x}{2}\right)\sinh\left(\frac{5\pi y}{2}\right).$$
>
> **Step 10. Check.**
> - Equation, first term: $u_{xx}=-\pi^2(\cdot)$, $u_{yy}=+\pi^2(\cdot)$, sum 0. Second term: $u_{xx}=-\dfrac{25\pi^2}{4}(\cdot)$, $u_{yy}=+\dfrac{25\pi^2}{4}(\cdot)$, sum 0.
> - $x=0$: $\sin0=0$ in both terms.
> - $x=2$: $\sin(2\pi)=0$ and $\sin(5\pi)=0$.
> - $y=0$: $\sinh0=0$ in both terms.
> - $y=3$: $\dfrac{4\sinh(3\pi)}{\sinh(3\pi)}\sin(\pi x)-\dfrac{\sinh(15\pi/2)}{\sinh(15\pi/2)}\sin\dfrac{5\pi x}{2}=4\sin(\pi x)-\sin\dfrac{5\pi x}{2}$. Correct.

> [!question]- Check (slide 8, find the mistake): For the slide example a student writes $u=\sin x\sinh y+\sin(3x)\sinh(3y)$ ("the coefficients of the data are 1 and 1"). Which conditions does this $u$ satisfy and which one fails?
> Equation: each term has the form $\sin(nx)\sinh(ny)$, so $u_{xx}=-n^2(\cdot)$ and $u_{yy}=n^2(\cdot)$. Laplace's equation holds.
> Zero edges: $x=0$ gives $\sin0=0$. $x=\pi$ gives $\sin\pi=\sin3\pi=0$. $y=0$ gives $\sinh0=0$. All three hold.
> Top edge: $u(x,2\pi)=\sinh(2\pi)\sin x+\sinh(6\pi)\sin(3x)\approx267.7\sin x+7.68\cdot10^{7}\sin(3x)$. The data is $\sin x+\sin(3x)$. This condition fails.
> The mistake: the coefficients of the data are $c_n\sinh(2\pi n)$, not $c_n$. So $c_1\sinh(2\pi)=1$ and $c_3\sinh(6\pi)=1$. Dividing gives the factors $\dfrac{1}{\sinh(2\pi)}$ and $\dfrac{1}{\sinh(6\pi)}$ of the slide.
> Then $u(x,2\pi)=\dfrac{\sinh(2\pi)}{\sinh(2\pi)}\sin x+\dfrac{\sinh(6\pi)}{\sinh(6\pi)}\sin(3x)=\sin x+\sin(3x)$. Correct.

## 6. Example: data on the right edge (slides 9-11)
![[math501_lecture_08_math501_chapter_8_p010.jpg]]
![[math501_lecture_08_math501_chapter_8_p011.jpg]]

**Notes.** The example starts in the middle of slide 9 (embedded in section 5) and ends at the top of slide 11. Now the top and bottom edges are zero, so the two zero conditions are in $y$. The roles of $x$ and $y$ are exchanged: $Y$ gets the sines and $X$ gets the $\sinh$.

For this the slide names the constant $\lambda$ in place of $-\lambda$: $\dfrac{X''}{X}=-\dfrac{Y''}{Y}=\lambda$, so $X''-\lambda X=0$ and $Y''+\lambda Y=0$.

> [!example] Slide example
> $D=\{0<x<\pi,\ 0<y<1\}$, $u(x,0)=u(x,1)=0$, $u(0,y)=0$, $u(\pi,y)=5\sin(\pi y)-\sin(2\pi y)$.
> - Conditions: $Y(0)=0$, $Y(1)=0$, $X(0)=0$.
> - $Y$-problem ($L=1$): $\sin\sqrt\lambda=0$, so $\lambda=n^2\pi^2$, $Y_n=\sin(n\pi y)$.
> - $X''-n^2\pi^2X=0$: $X=\beta_1\cosh(n\pi x)+\beta_2\sinh(n\pi x)$, $X(0)=0$ gives $\beta_1=0$, $X_n=\sinh(n\pi x)$.
> - $u=\sum c_n\sinh(n\pi x)\sin(n\pi y)$. Right edge $x=\pi$: $5\sin(\pi y)-\sin(2\pi y)=\sum c_n\sinh(n\pi^2)\sin(n\pi y)$.
> - Orthogonality on $[0,1]$ (value $\tfrac12$): $m=1$: $\tfrac12c_1\sinh(\pi^2)=\tfrac52$. $m=2$: $\tfrac12c_2\sinh(2\pi^2)=-\tfrac12$. Other $m$: $c_m=0$.
>
> $$u(x,y)=\frac{5}{\sinh(\pi^2)}\sinh(\pi x)\sin(\pi y)-\frac{1}{\sinh(2\pi^2)}\sinh(2\pi x)\sin(2\pi y).$$

Where $\sinh(n\pi^2)$ comes from: $X_n(x)=\sinh(n\pi x)$ at the edge $x=\pi$ is $\sinh(n\pi\cdot\pi)=\sinh(n\pi^2)$.

Where $\tfrac52$ and $-\tfrac12$ come from: for $m=1$ the left side is $5\int_0^1\sin^2(\pi y)\,dy-\int_0^1\sin(\pi y)\sin(2\pi y)\,dy=5\cdot\tfrac12-0$. For $m=2$ it is $5\cdot0-\tfrac12$.

> [!warning] Slide error
> Top of slide 10: "the functions $Y_n(x)=\sin(n\pi y)$". It must be $Y_n(y)=\sin(n\pi y)$. $Y$ is a function of $y$. The same misprint is on slide 11: $Y_n(x)=\sin\left(\dfrac{n\pi y}{2}\right)$ must be $Y_n(y)$.

> [!question]- Check (slides 9-11): Solve $u_{xx}+u_{yy}=0$ in $0<x<2$, $0<y<\pi$ with $u(x,0)=0$, $u(x,\pi)=0$, $u(0,y)=0$ and $u(2,y)=3\sin(4y)$.
> Case: the two zero conditions are in $y$ (bottom and top). So $Y$ gets the sines, and the interval for $y$ has the length $\pi$. Data on the right edge $x=2$.
> **Step 1. Separate.** $X''Y+XY''=0$, $\dfrac{X''}{X}=-\dfrac{Y''}{Y}=\lambda$. So $X''-\lambda X=0$ and $Y''+\lambda Y=0$.
> **Step 2. Zero edges.** $u(x,0)=X(x)Y(0)=0$, $u(x,\pi)=X(x)Y(\pi)=0$, $u(0,y)=X(0)Y(y)=0$ give $Y(0)=0$, $Y(\pi)=0$, $X(0)=0$.
> **Step 3. $Y$-problem.** For $\lambda>0$: $Y=\alpha_1\cos(\sqrt\lambda\,y)+\alpha_2\sin(\sqrt\lambda\,y)$. $Y(0)=\alpha_1=0$. $Y(\pi)=\alpha_2\sin(\sqrt\lambda\,\pi)=0$ with $\alpha_2\neq0$ needs $\sqrt\lambda\,\pi=n\pi$, so $\sqrt\lambda=n$. Eigenvalues $\lambda=n^2$, $Y_n=\sin(ny)$. Nothing for $\lambda\le0$.
> **Step 4. $X$-problem.** $X''-n^2X=0$: $r^2-n^2=0$, $r=\pm n$, $X=\beta_1\cosh(nx)+\beta_2\sinh(nx)$. $X(0)=\beta_1\cdot1+\beta_2\cdot0=\beta_1=0$. So $X_n=\sinh(nx)$.
> **Step 5. Superposition.** $u(x,y)=\sum_{n=1}^{\infty}c_n\sinh(nx)\sin(ny)$.
> **Step 6. Right edge $x=2$.** $3\sin(4y)=\sum_{n=1}^{\infty}c_n\sinh(2n)\sin(ny)$.
> **Step 7. Orthogonality.** Multiply by $\sin(my)$ and integrate over $[0,\pi]$ (value $\dfrac\pi2$ for $m=n$):
>
> $$3\int_0^\pi\sin(4y)\sin(my)\,dy=\frac\pi2\,c_m\sinh(2m).$$
>
> - $m=4$: left side $3\cdot\dfrac\pi2$. So $\dfrac\pi2c_4\sinh8=\dfrac{3\pi}{2}$, $c_4=\dfrac{3}{\sinh8}$.
> - $m\neq4$: left side $0$, so $c_m=0$.
>
> **Step 8. Solution.** The series has one term:
>
> $$u(x,y)=\frac{3}{\sinh8}\sinh(4x)\sin(4y).$$
>
> **Step 9. Check.**
> - $u_x=\dfrac{12}{\sinh8}\cosh(4x)\sin(4y)$, $u_{xx}=\dfrac{48}{\sinh8}\sinh(4x)\sin(4y)=16u$.
> - $u_y=\dfrac{12}{\sinh8}\sinh(4x)\cos(4y)$, $u_{yy}=-\dfrac{48}{\sinh8}\sinh(4x)\sin(4y)=-16u$.
> - $u_{xx}+u_{yy}=16u-16u=0$.
> - $y=0$: $\sin0=0$. $y=\pi$: $\sin(4\pi)=0$. $x=0$: $\sinh0=0$.
> - $x=2$: $\dfrac{3\sinh8}{\sinh8}\sin(4y)=3\sin(4y)$. Correct.

> [!question]- Check (slide 10, data that is not a sum of sines): Same rectangle $0<x<2$, $0<y<\pi$ and the same three zero edges, but now $u(2,y)=y(\pi-y)$. Find $c_n$ and the solution.
> Steps 1 to 5 of the previous check do not use the data. So again $u=\sum c_n\sinh(nx)\sin(ny)$.
> **Step 1. Right edge.** $y(\pi-y)=\sum c_n\sinh(2n)\sin(ny)$. Multiply by $\sin(my)$, integrate over $[0,\pi]$, use orthogonality, rename $m$ to $n$:
>
> $$c_n=\frac{2}{\pi\sinh(2n)}\int_0^\pi(\pi y-y^2)\sin(ny)\,dy.$$
>
> **Step 2. First integration by parts.** $u=\pi y-y^2$, $dv=\sin(ny)\,dy$. Then $du=(\pi-2y)\,dy$, $v=-\dfrac1n\cos(ny)$.
>
> $$\int_0^\pi(\pi y-y^2)\sin(ny)\,dy=\left[-\frac{\pi y-y^2}{n}\cos(ny)\right]_0^\pi+\frac1n\int_0^\pi(\pi-2y)\cos(ny)\,dy.$$
>
> The bracket is $0$: at $y=\pi$ the factor $\pi y-y^2=\pi^2-\pi^2=0$, at $y=0$ it is $0$.
> **Step 3. Second integration by parts.** $u=\pi-2y$, $dv=\cos(ny)\,dy$. Then $du=-2\,dy$, $v=\dfrac1n\sin(ny)$.
>
> $$\int_0^\pi(\pi-2y)\cos(ny)\,dy=\left[\frac{\pi-2y}{n}\sin(ny)\right]_0^\pi+\frac2n\int_0^\pi\sin(ny)\,dy.$$
>
> The bracket is $0$: $\sin(n\pi)=0$ and $\sin0=0$.
> **Step 4. Last integral.** $\int_0^\pi\sin(ny)\,dy=\left[-\dfrac1n\cos(ny)\right]_0^\pi=-\dfrac{(-1)^n}{n}+\dfrac1n=\dfrac{1-(-1)^n}{n}$.
> **Step 5. Put together.** $\int_0^\pi(\pi y-y^2)\sin(ny)\,dy=\dfrac1n\cdot\dfrac2n\cdot\dfrac{1-(-1)^n}{n}=\dfrac{2\bigl(1-(-1)^n\bigr)}{n^3}$.
> - $n$ even: $0$.
> - $n$ odd: $\dfrac{4}{n^3}$.
>
> **Step 6. Coefficients.** $c_n=0$ for even $n$. For odd $n$: $c_n=\dfrac{2}{\pi\sinh(2n)}\cdot\dfrac{4}{n^3}=\dfrac{8}{\pi n^3\sinh(2n)}$.
> **Step 7. Solution.**
>
> $$u(x,y)=\sum_{n=1,3,5,\dots}\frac{8}{\pi n^3\sinh(2n)}\sinh(nx)\sin(ny).$$
>
> **Step 8. Check, term by term.** Each term is a constant times $\sinh(nx)\sin(ny)$: $u_{xx}=n^2(\cdot)$, $u_{yy}=-n^2(\cdot)$, sum 0. $y=0$: $\sin0=0$. $y=\pi$: $\sin(n\pi)=0$. $x=0$: $\sinh0=0$.
> $x=2$: the series is $\sum_{n\text{ odd}}\dfrac{8}{\pi n^3}\sin(ny)$. Test at $y=\dfrac\pi2$, where the data is $\dfrac\pi2\cdot\dfrac\pi2=\dfrac{\pi^2}{4}\approx2.467$: $\dfrac8\pi\left(1-\dfrac1{27}+\dfrac1{125}-\dfrac{1}{343}+\dots\right)\approx\dfrac8\pi(0.9689)\approx2.467$. Correct.
> First coefficient: $c_1=\dfrac{8}{\pi\sinh2}\approx0.702$. The coefficients fall like $\dfrac{1}{n^3}$ because this data is zero at both ends $y=0$ and $y=\pi$ and fits the zero edges.

## 7. Example: data on the left edge (slides 11-13)
![[math501_lecture_08_math501_chapter_8_p012.jpg]]
![[math501_lecture_08_math501_chapter_8_p013.jpg]]

**Notes.** The example starts in the middle of slide 11 (embedded in section 6). Again the two zero conditions are in $y$. New: the single zero condition of $X$ is at the far end, $X(4)=0$, not at $x=0$. Then $\cosh$ does not drop out, and $X_n$ is a combination of $\sinh$ and $\cosh$.

> [!example] Slide example
> $D=\{0<x<4,\ 0<y<2\}$, $u(x,0)=u(x,2)=0$, $u(0,y)=\sin(\pi y)$, $u(4,y)=0$.
> - $X''-\lambda X=0$, $Y''+\lambda Y=0$ with $Y(0)=0$, $Y(2)=0$, $X(4)=0$.
> - $Y$-problem ($L=2$): $\sin(2\sqrt\lambda)=0$, $\lambda=\dfrac{n^2\pi^2}{4}$, $Y_n=\sin\dfrac{n\pi y}{2}$.
> - $X=\beta_1\cosh\dfrac{n\pi x}{2}+\beta_2\sinh\dfrac{n\pi x}{2}$. $X(4)=0$: $\beta_1\cosh(2n\pi)+\beta_2\sinh(2n\pi)=0$, so $\beta_1=-\beta_2\tanh(2n\pi)$.
> - $X_n=\sinh\dfrac{n\pi x}{2}-\tanh(2n\pi)\cosh\dfrac{n\pi x}{2}$.
> - Left edge $x=0$: $X_n(0)=0-\tanh(2n\pi)\cdot1$, so $\sin(\pi y)=-\sum c_n\tanh(2n\pi)\sin\dfrac{n\pi y}{2}$.
> - Orthogonality on $[0,2]$ (value $1$): $\int_0^2\sin\dfrac{m\pi y}{2}\sin(\pi y)\,dy=-c_m\tanh(2m\pi)$. $\sin(\pi y)$ is the eigenfunction $n=2$. So $-c_2\tanh(4\pi)=1$, $c_2=-\coth(4\pi)$, and $c_m=0$ for $m\neq2$.
>
> $$u(x,y)=-\coth(4\pi)\sinh(\pi x)\sin(\pi y)+\cosh(\pi x)\sin(\pi y).$$

A shorter form of the same answer. Use $\sinh(a-b)=\sinh a\cosh b-\cosh a\sinh b$ with $a=4\pi$, $b=\pi x$ and divide by $\sinh4\pi$:

$$\frac{\sinh\bigl(\pi(4-x)\bigr)}{\sinh(4\pi)}=\cosh(\pi x)-\coth(4\pi)\sinh(\pi x),\qquad\text{so}\qquad u(x,y)=\frac{\sinh\bigl(\pi(4-x)\bigr)}{\sinh(4\pi)}\sin(\pi y).$$

General rule: a zero condition at the near end $x=0$ gives $\sinh(ax)$. A zero condition at the far end $x=L$ gives $\sinh\bigl(a(L-x)\bigr)$, which is the $\sinh$, $\cosh$ combination of the slide.

> [!warning] Slide error
> Slide 13, first form of the solution: $u=-\coth(4\pi)\left(\sinh(\pi x)-\tanh(4\pi)\cosh(\pi x)\sin(\pi y)\right)$. The bracket is closed at the wrong place. As printed, $\sin(\pi y)$ multiplies only the $\cosh$ term. That function is not harmonic and is not zero at $x=4$.
> Correct: $u=-\coth(4\pi)\bigl(\sinh(\pi x)-\tanh(4\pi)\cosh(\pi x)\bigr)\sin(\pi y)$. The second form on the slide ("or equivalently") is correct.

> [!info] Data on more than one edge (beyond the slides)
> The slides always have three zero edges. If two or more edges carry data, split the problem.
> - Problem A: keep the data of the first edge and set the other edges to 0. Solution $u_A$.
> - Problem B: keep the data of the second edge and set the other edges to 0. Solution $u_B$.
> - Then $u=u_A+u_B$. The equation is linear, so $u$ is harmonic. On each edge one part gives the data and the other part gives 0.
>
> With data on all four edges there are four such problems. Each one is of the type of sections 5 to 7.

> [!question]- Check (slides 11-13): Solve $u_{xx}+u_{yy}=0$ in $0<x<1$, $0<y<\pi$ with $u(x,0)=0$, $u(x,\pi)=0$, $u(1,y)=0$ and $u(0,y)=2\sin(3y)$.
> Case: two zero conditions in $y$, so $Y$ gets the sines. The zero condition of $X$ is at the far end $x=1$. Data on the left edge $x=0$.
> **Step 1. Separate.** $\dfrac{X''}{X}=-\dfrac{Y''}{Y}=\lambda$: $X''-\lambda X=0$, $Y''+\lambda Y=0$.
> **Step 2. Zero edges.** $Y(0)=0$, $Y(\pi)=0$, $X(1)=0$.
> **Step 3. $Y$-problem.** $Y''+\lambda Y=0$, $Y(0)=Y(\pi)=0$: for $\lambda>0$, $Y=\alpha_1\cos(\sqrt\lambda\,y)+\alpha_2\sin(\sqrt\lambda\,y)$, $\alpha_1=0$, $\sin(\sqrt\lambda\,\pi)=0$, so $\lambda=n^2$ and $Y_n=\sin(ny)$. Nothing for $\lambda\le0$.
> **Step 4. $X$-problem.** $X''-n^2X=0$: $X=\beta_1\cosh(nx)+\beta_2\sinh(nx)$.
> $X(1)=0$: $\beta_1\cosh n+\beta_2\sinh n=0$. Divide by $\cosh n$ (never zero): $\beta_1=-\beta_2\dfrac{\sinh n}{\cosh n}=-\beta_2\tanh n$.
> So $X=\beta_2\bigl(\sinh(nx)-\tanh(n)\cosh(nx)\bigr)$ and $X_n(x)=\sinh(nx)-\tanh(n)\cosh(nx)$.
> **Step 5. Superposition.**
>
> $$u(x,y)=\sum_{n=1}^{\infty}c_n\bigl[\sinh(nx)-\tanh(n)\cosh(nx)\bigr]\sin(ny).$$
>
> **Step 6. Left edge $x=0$.** $X_n(0)=\sinh0-\tanh(n)\cosh0=0-\tanh(n)\cdot1=-\tanh n$. So
>
> $$2\sin(3y)=-\sum_{n=1}^{\infty}c_n\tanh(n)\sin(ny).$$
>
> **Step 7. Orthogonality.** Multiply by $\sin(my)$, integrate over $[0,\pi]$ (value $\dfrac\pi2$):
>
> $$2\int_0^\pi\sin(3y)\sin(my)\,dy=-\frac\pi2\,c_m\tanh(m).$$
>
> - $m=3$: left side $2\cdot\dfrac\pi2=\pi$. So $-\dfrac\pi2c_3\tanh3=\pi$, $c_3=-\dfrac{2}{\tanh3}=-2\coth3$.
> - $m\neq3$: left side $0$, so $c_m=0$.
>
> **Step 8. Solution.**
>
> $$u(x,y)=-2\coth(3)\bigl[\sinh(3x)-\tanh(3)\cosh(3x)\bigr]\sin(3y)=\bigl[2\cosh(3x)-2\coth(3)\sinh(3x)\bigr]\sin(3y).$$
>
> **Step 9. Short form.** $\sinh(3-3x)=\sinh3\cosh(3x)-\cosh3\sinh(3x)$. Divide by $\sinh3$: $\dfrac{\sinh(3(1-x))}{\sinh3}=\cosh(3x)-\coth(3)\sinh(3x)$. So
>
> $$u(x,y)=\frac{2\sinh\bigl(3(1-x)\bigr)}{\sinh3}\sin(3y).$$
>
> **Step 10. Check with the short form.**
> - $u_x=-\dfrac{6\cosh(3(1-x))}{\sinh3}\sin(3y)$, $u_{xx}=\dfrac{18\sinh(3(1-x))}{\sinh3}\sin(3y)=9u$ (chain rule, inner derivative $-3$ twice).
> - $u_{yy}=-9u$. Sum: $9u-9u=0$.
> - $x=0$: $\dfrac{2\sinh3}{\sinh3}\sin(3y)=2\sin(3y)$. Correct.
> - $x=1$: $\sinh0=0$.
> - $y=0$: $\sin0=0$. $y=\pi$: $\sin(3\pi)=0$.

> [!question]- Check (slide 13): Show that the two forms on the slide (with the bracket corrected) are equal, write the solution as one $\sinh$, and check all four boundary conditions and the equation.
> **Step 1. Multiply out the first form.**
> $-\coth(4\pi)\bigl(\sinh(\pi x)-\tanh(4\pi)\cosh(\pi x)\bigr)\sin(\pi y)=-\coth(4\pi)\sinh(\pi x)\sin(\pi y)+\coth(4\pi)\tanh(4\pi)\cosh(\pi x)\sin(\pi y)$.
> $\coth z\tanh z=\dfrac{\cosh z}{\sinh z}\cdot\dfrac{\sinh z}{\cosh z}=1$. So this is $-\coth(4\pi)\sinh(\pi x)\sin(\pi y)+\cosh(\pi x)\sin(\pi y)$, the second form.
> **Step 2. One $\sinh$.** Factor $\sin(\pi y)$ and write $\coth(4\pi)=\dfrac{\cosh4\pi}{\sinh4\pi}$:
>
> $$\cosh(\pi x)-\frac{\cosh4\pi}{\sinh4\pi}\sinh(\pi x)=\frac{\sinh(4\pi)\cosh(\pi x)-\cosh(4\pi)\sinh(\pi x)}{\sinh4\pi}=\frac{\sinh(4\pi-\pi x)}{\sinh4\pi}.$$
>
> The last step is $\sinh(a-b)=\sinh a\cosh b-\cosh a\sinh b$. So $u=\dfrac{\sinh(\pi(4-x))}{\sinh(4\pi)}\sin(\pi y)$.
> **Step 3. Boundary conditions.**
> - $x=0$: $\dfrac{\sinh4\pi}{\sinh4\pi}\sin(\pi y)=\sin(\pi y)$. Correct.
> - $x=4$: $\sinh0=0$, so $u=0$.
> - $y=0$: $\sin0=0$. $y=2$: $\sin(2\pi)=0$.
>
> **Step 4. Equation.** $u_{xx}=\pi^2u$ (two derivatives of $\sinh(\pi(4-x))$ give the factor $(-\pi)^2=\pi^2$). $u_{yy}=-\pi^2u$. Sum 0.
> **Step 5. The form as printed.** $w=-\coth(4\pi)\sinh(\pi x)+\cosh(\pi x)\sin(\pi y)$. Then $w_{xx}=-\pi^2\coth(4\pi)\sinh(\pi x)+\pi^2\cosh(\pi x)\sin(\pi y)$ and $w_{yy}=-\pi^2\cosh(\pi x)\sin(\pi y)$. Sum: $-\pi^2\coth(4\pi)\sinh(\pi x)\neq0$. Also $w(4,y)=-\cosh4\pi+\cosh(4\pi)\sin(\pi y)\neq0$. So the printed bracket is a misprint.

> [!question]- Check (slide 13, two edges with data, beyond the slides): Solve $u_{xx}+u_{yy}=0$ in $0<x<\pi$, $0<y<\pi$ with $u(0,y)=0$, $u(x,0)=0$, $u(x,\pi)=\sin x$ and $u(\pi,y)=2\sin(2y)$.
> Two edges carry data. Split: $u=u_A+u_B$ (info box above).
> **Problem A: data on the top edge only.** $u_A=0$ on the left, right and bottom edges, $u_A(x,\pi)=\sin x$.
> Type of section 5 with $L=\pi$, $K=\pi$: $u_A=\sum c_n\sin(nx)\sinh(ny)$. Top edge: $\sin x=\sum c_n\sinh(n\pi)\sin(nx)$. The data is the eigenfunction $n=1$ with coefficient 1, so $c_1\sinh\pi=1$ and all other $c_n=0$.
>
> $$u_A=\frac{\sin x\,\sinh y}{\sinh\pi}.$$
>
> **Problem B: data on the right edge only.** $u_B=0$ on the bottom, top and left edges, $u_B(\pi,y)=2\sin(2y)$.
> Type of section 6: $Y_n=\sin(ny)$, $X_n=\sinh(nx)$, $u_B=\sum d_n\sinh(nx)\sin(ny)$. Right edge: $2\sin(2y)=\sum d_n\sinh(n\pi)\sin(ny)$. The data is the eigenfunction $n=2$ with coefficient 2, so $d_2\sinh(2\pi)=2$ and all other $d_n=0$.
>
> $$u_B=\frac{2\sinh(2x)\sin(2y)}{\sinh(2\pi)}.$$
>
> **Sum.**
>
> $$u(x,y)=\frac{\sin x\,\sinh y}{\sinh\pi}+\frac{2\sinh(2x)\sin(2y)}{\sinh(2\pi)}.$$
>
> **Check.**
> - Equation: for $u_A$, $u_{xx}=-u_A$ and $u_{yy}=u_A$. For $u_B$, $u_{xx}=4u_B$ and $u_{yy}=-4u_B$. Total 0.
> - $x=0$: $\sin0=0$ and $\sinh0=0$. So $u=0$.
> - $y=0$: $\sinh0=0$ and $\sin0=0$. So $u=0$.
> - $y=\pi$: $u_A=\dfrac{\sinh\pi}{\sinh\pi}\sin x=\sin x$ and $u_B$ has $\sin(2\pi)=0$. So $u=\sin x$. Correct.
> - $x=\pi$: $u_A$ has $\sin\pi=0$ and $u_B=\dfrac{2\sinh(2\pi)}{\sinh(2\pi)}\sin(2y)=2\sin(2y)$. So $u=2\sin(2y)$. Correct.

## Key formulas and terms
| Term | Meaning / formula |
|---|---|
| Laplacian | $\nabla^2u=u_{xx}+u_{yy}$ (2D), $u_{xx}+u_{yy}+u_{zz}$ (3D) |
| Laplace's equation | $\nabla^2u=0$ |
| Harmonic function | A solution of Laplace's equation on a region |
| Dirichlet problem | $\nabla^2u=0$ on $D$, $u=f$ on $\partial D$; $f$ is the boundary data |
| Two-point BVP | ODE with conditions at two points $\alpha\neq\beta$ |
| Eigenvalue problem (8.1) | $y''+\lambda y=0$, $y(0)=0$, $y(L)=0$ |
| Eigenvalues, eigenfunctions | $\lambda_n=\dfrac{n^2\pi^2}{L^2}$, $y_n=\sin\dfrac{n\pi x}{L}$, $n=1,2,3,\dots$ |
| Orthogonality | $\int_0^L\sin\dfrac{m\pi x}{L}\sin\dfrac{n\pi x}{L}\,dx=0$ for $m\neq n$, $\dfrac L2$ for $m=n$ |
| Separation of variables | $u=X(x)Y(y)$, $\dfrac{X''}{X}=-\dfrac{Y''}{Y}=$ constant |
| Fundamental solutions | $u_n=\sin\dfrac{n\pi x}{L}\sinh\dfrac{n\pi y}{L}$ |
| Rectangle, data on top | $u=\sum c_n\sin\dfrac{n\pi x}{L}\sinh\dfrac{n\pi y}{L}$, $c_n=\dfrac{2}{L\sinh(n\pi K/L)}\int_0^Lf(x)\sin\dfrac{n\pi x}{L}\,dx$ |
| Hyperbolic functions | $\cosh z=\dfrac{e^z+e^{-z}}{2}$, $\sinh z=\dfrac{e^z-e^{-z}}{2}$, $\cosh0=1$, $\sinh0=0$ |
| Zero at the far end | $\sinh\bigl(a(L-x)\bigr)$ in place of $\sinh(ax)$ |

## Check yourself
> [!question]- 1. Is $u=\ln(x^2+y^2)$ harmonic for $(x,y)\neq(0,0)$?
> $u_x=\dfrac{2x}{x^2+y^2}$. Quotient rule: $u_{xx}=\dfrac{2(x^2+y^2)-2x\cdot2x}{(x^2+y^2)^2}=\dfrac{2y^2-2x^2}{(x^2+y^2)^2}$.
> By symmetry ($x$ and $y$ exchanged): $u_{yy}=\dfrac{2x^2-2y^2}{(x^2+y^2)^2}$.
> Sum: $\dfrac{2y^2-2x^2+2x^2-2y^2}{(x^2+y^2)^2}=0$. Harmonic on the plane without the origin.

> [!question]- 2. Find the eigenvalues and eigenfunctions of $y''+\lambda y=0$, $y(0)=0$, $y(4)=0$. Write the third eigenfunction and test it.
> $L=4$: $\lambda_n=\dfrac{n^2\pi^2}{16}$, $y_n=\sin\dfrac{n\pi x}{4}$, $n=1,2,3,\dots$
> Third: $\lambda_3=\dfrac{9\pi^2}{16}$, $y_3=\sin\dfrac{3\pi x}{4}$.
> Test: $y_3''=-\dfrac{9\pi^2}{16}\sin\dfrac{3\pi x}{4}=-\lambda_3y_3$. $y_3(0)=\sin0=0$. $y_3(4)=\sin(3\pi)=0$. Correct.

> [!question]- 3. Evaluate $\displaystyle\int_0^4\sin\frac{\pi x}{2}\sin\frac{3\pi x}{4}\,dx$ and $\displaystyle\int_0^4\sin^2\frac{3\pi x}{4}\,dx$ with the orthogonality rule.
> Write both sines in the form $\sin\dfrac{n\pi x}{L}$ with $L=4$: $\sin\dfrac{\pi x}{2}=\sin\dfrac{2\pi x}{4}$ ($m=2$) and $\sin\dfrac{3\pi x}{4}$ ($n=3$).
> First integral: $m\neq n$, value $0$.
> Second integral: $m=n=3$, value $\dfrac L2=2$.

> [!question]- 4. Solve $u_{xx}+u_{yy}=0$ in $0<x<1$, $0<y<1$ with $u=0$ on the left, right and bottom edges and $u(x,1)=\sin(2\pi x)$.
> Data on top, $L=K=1$: $u=\sum c_n\sin(n\pi x)\sinh(n\pi y)$.
> Top edge: $\sin(2\pi x)=\sum c_n\sinh(n\pi)\sin(n\pi x)$. The data is the eigenfunction $n=2$: $c_2\sinh(2\pi)=1$, other $c_n=0$.
> $u=\dfrac{\sin(2\pi x)\sinh(2\pi y)}{\sinh(2\pi)}$.
> Check: $u_{xx}=-4\pi^2u$, $u_{yy}=4\pi^2u$, sum 0. $x=0$, $x=1$: $\sin0=\sin2\pi=0$. $y=0$: $\sinh0=0$. $y=1$: $\sin(2\pi x)$. Correct.

> [!question]- 5. Solve $u_{xx}+u_{yy}=0$ in $0<x<\pi$, $0<y<1$ with $u(0,y)=u(\pi,y)=0$, $u(x,1)=0$ and $u(x,0)=\sin x$ (data on the bottom edge).
> Two zero conditions in $x$: $X_n=\sin(nx)$, $\lambda=n^2$, $Y''-n^2Y=0$, $Y=\beta_1\cosh(ny)+\beta_2\sinh(ny)$.
> The zero condition of $Y$ is at the far end: $Y(1)=0$ gives $\beta_1=-\beta_2\tanh n$. So $Y_n$ is proportional to $\sinh\bigl(n(1-y)\bigr)$, because $\sinh(n-ny)=\sinh n\cosh(ny)-\cosh n\sinh(ny)$.
> $u=\sum c_n\sin(nx)\sinh\bigl(n(1-y)\bigr)$. Bottom edge $y=0$: $\sin x=\sum c_n\sinh(n)\sin(nx)$, so $c_1\sinh1=1$, other $c_n=0$.
> $u=\dfrac{\sin x\,\sinh(1-y)}{\sinh1}$.
> Check: $u_{xx}=-u$, $u_{yy}=u$ (inner derivative $-1$ twice), sum 0. $x=0,\pi$: $\sin0=\sin\pi=0$. $y=1$: $\sinh0=0$. $y=0$: $\dfrac{\sinh1}{\sinh1}\sin x=\sin x$. Correct.

> [!question]- 6. For $0<x<5$, $0<y<3$ with $u(0,y)=0$, $u(x,0)=0$, $u(x,3)=0$ and $u(5,y)=y$: which variable gets the sines? Write the form of the solution and compute $c_n$.
> The two zero conditions are in $y$ (bottom and top), so $Y$ gets the sines with $L=3$: $Y_n=\sin\dfrac{n\pi y}{3}$, $\lambda=\dfrac{n^2\pi^2}{9}$.
> $X''-\dfrac{n^2\pi^2}{9}X=0$ with $X(0)=0$: $X_n=\sinh\dfrac{n\pi x}{3}$.
> $u=\sum c_n\sinh\dfrac{n\pi x}{3}\sin\dfrac{n\pi y}{3}$. Right edge $x=5$: $y=\sum c_n\sinh\dfrac{5n\pi}{3}\sin\dfrac{n\pi y}{3}$.
> Orthogonality on $[0,3]$ (value $\tfrac32$): $c_n=\dfrac{2}{3\sinh(5n\pi/3)}\int_0^3y\sin\dfrac{n\pi y}{3}\,dy$.
> By parts with $u=y$, $v=-\dfrac{3}{n\pi}\cos\dfrac{n\pi y}{3}$: $\left[-\dfrac{3y}{n\pi}\cos\dfrac{n\pi y}{3}\right]_0^3+\dfrac{3}{n\pi}\int_0^3\cos\dfrac{n\pi y}{3}\,dy=-\dfrac{9(-1)^n}{n\pi}+\dfrac{9}{n^2\pi^2}\bigl[\sin(n\pi)-0\bigr]=\dfrac{9(-1)^{n+1}}{n\pi}$.
> $c_n=\dfrac{2}{3\sinh(5n\pi/3)}\cdot\dfrac{9(-1)^{n+1}}{n\pi}=\dfrac{6(-1)^{n+1}}{n\pi\sinh(5n\pi/3)}$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L07 - Linear systems of ODEs]]
- Related: the characteristic equation and the three root cases are in [[MATH501 L02 - Higher order linear ODEs]]
- Full step-by-step notes (PDF): [MATH501_Lecture_08_Laplace_Equation.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_08/MATH501_Lecture_08_Laplace_Equation.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_08/MATH501_Lecture_08_Laplace_Equation.pdf`
- Original chapter notes (PDF): [Math501 Chapter 8.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_08/Math501%20Chapter%208.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_08/Math501 Chapter 8.pdf`

Slides not embedded: none.
