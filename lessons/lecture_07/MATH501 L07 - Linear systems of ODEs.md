---
course: MATH 501 Advanced Engineering Mathematics
lecture: 7
title: Linear systems of ODEs
tags: [math501, lecture]
slides: lectures/lecture_07/Math501 Chapter 7.pdf
full_notes: lecture_notes/lecture_07/MATH501_Lecture_07_Linear_Systems.pdf
---
# MATH 501 · Lecture 7 · Linear systems of ODEs

> [!summary] In short
> - A linear system is written $X'(t)=A(t)X(t)+F(t)$. Row $i$ of $A$ holds the coefficients of equation $i$.
> - Continuous $A$ and $F$ give exactly one solution for each initial condition.
> - $n$ independent solutions of $X'=AX$ form a fundamental set. As columns they form a fundamental matrix $\Phi(t)$, and $X=\Phi(t)C$.
> - Constant $A$ with $n$ distinct real eigenvalues: $X=\sum c_iw_ie^{\lambda_it}$.
> - Nonhomogeneous: $X=X_h+X_p$ with $X_p=\Phi\int\Phi^{-1}F\,dt$.

The slide numbers below are the pages of the Chapter 7 PDF (page 1 is printed page 100).

## 1. Linear systems, matrix form, initial value problems (slides 1-2)
![[math501_lecture_07_math501_chapter_7_p001.jpg]]
![[math501_lecture_07_math501_chapter_7_p002.jpg]]

**Notes.** A **linear system** has $n$ equations $x_i'=a_{i1}(t)x_1+\dots+a_{in}(t)x_n+f_i(t)$ for $n$ unknown functions. With $X=(x_1,\dots,x_n)^{\mathsf T}$, $A(t)=[a_{ij}(t)]$ and $F=(f_1,\dots,f_n)^{\mathsf T}$:

$$X'(t)=A(t)X(t)+F(t).$$

It is **homogeneous** if $F=\mathbf 0$: $X'(t)=A(t)X(t)$. A **solution** on an interval $J$ is a vector function whose entries satisfy all equations on $J$. An **IVP** adds $X(t_0)=X_0$.

> [!example] Slide examples
> - $x_1'=3x_1-4x_2$, $x_2'=-8x_1+2x_2$ is $X'=\begin{pmatrix}3&-4\\-8&2\end{pmatrix}X$.
> - $x'=2x+y-z+t$, $y'=-8x+6y-3z+2$, $z'=3x-5y+4z+e^{-t}$ has $A=\begin{pmatrix}2&1&-1\\-8&6&-3\\3&-5&4\end{pmatrix}$, $F=\begin{pmatrix}t\\2\\e^{-t}\end{pmatrix}$.

Terms without unknowns go into $F(t)$.

> [!info] A higher-order equation as a first-order system (beyond the slides)
> One equation of order $n$ becomes a system of $n$ first-order equations. Name the function and its derivatives as new unknowns: $x_1=y$, $x_2=y'$, ..., $x_n=y^{(n-1)}$.
> Then $x_1'=x_2$, $x_2'=x_3$, ..., and the last equation is the ODE solved for the highest derivative.
> The initial values $y(t_0),y'(t_0),\dots$ become the vector $X(t_0)$. So everything in this chapter also covers the higher-order equations of the earlier lectures.

> [!question]- Check (slide 1): Write $x_1'=2x_1-t\,x_3+\cos t$, $x_2'=x_1+e^{t}x_2$, $x_3'=-x_2+4x_3-5$ in the form $X'=A(t)X+F(t)$. Is the system homogeneous?
> Step 1. Order the unknowns: $X=(x_1,x_2,x_3)^{\mathsf T}$.
> Step 2. Row $i$ of $A$ holds the coefficients of $x_1,x_2,x_3$ in equation $i$. A missing unknown has the coefficient 0.
> - Equation 1: $2x_1+0x_2-t\,x_3$, so row 1 is $(2,\,0,\,-t)$.
> - Equation 2: $1x_1+e^{t}x_2+0x_3$, so row 2 is $(1,\,e^{t},\,0)$.
> - Equation 3: $0x_1-1x_2+4x_3$, so row 3 is $(0,\,-1,\,4)$.
>
> Step 3. The terms without an unknown go into $F$: $f_1=\cos t$, $f_2=0$, $f_3=-5$.
>
> $$X'=\begin{pmatrix}2&0&-t\\1&e^{t}&0\\0&-1&4\end{pmatrix}X+\begin{pmatrix}\cos t\\0\\-5\end{pmatrix}.$$
>
> Step 4. $F$ is not the zero vector, so the system is **nonhomogeneous**. One nonzero $f_i$ is enough for that.
> Note: $-t\,x_3$ and $e^{t}x_2$ contain an unknown, so they belong to $A(t)$, not to $F$.

> [!question]- Check (slide 2, solution): For $x_1'=3x_1-2x_2$, $x_2'=2x_1-2x_2$, test the two vector functions $Y=(e^{t},\,e^{t})^{\mathsf T}$ and $Z=(2e^{2t},\,e^{2t})^{\mathsf T}$. Which one is a solution?
> A solution must satisfy EVERY equation for every $t$.
> **Test $Y$.** $y_1=e^{t}$, $y_2=e^{t}$, so $y_1'=e^{t}$ and $y_2'=e^{t}$.
> - Equation 1: right side $3e^{t}-2e^{t}=e^{t}$. Left side $e^{t}$. True.
> - Equation 2: right side $2e^{t}-2e^{t}=0$. Left side $e^{t}$. False.
>
> One equation fails, so $Y$ is not a solution.
> **Test $Z$.** $z_1=2e^{2t}$, $z_2=e^{2t}$, so $z_1'=4e^{2t}$ and $z_2'=2e^{2t}$.
> - Equation 1: right side $3(2e^{2t})-2e^{2t}=6e^{2t}-2e^{2t}=4e^{2t}$. Left side $4e^{2t}$. True.
> - Equation 2: right side $2(2e^{2t})-2e^{2t}=4e^{2t}-2e^{2t}=2e^{2t}$. Left side $2e^{2t}$. True.
>
> $Z$ is a solution on $J=(-\infty,\infty)$. It solves the IVP with $X(0)=(2,1)^{\mathsf T}$, because $Z(0)=(2e^{0},e^{0})^{\mathsf T}=(2,1)^{\mathsf T}$.

> [!question]- Check (slide 2, initial value problem): Write $y''+3y'-10y=6e^{t}$, $y(0)=1$, $y'(0)=2$ as an initial value problem $X'=AX+F(t)$, $X(0)=X_0$.
> Step 1. New unknowns: $x_1=y$, $x_2=y'$ (method of the info box above, beyond the slides).
> Step 2. First equation: $x_1'=y'=x_2$.
> Step 3. Solve the ODE for $y''$: $y''=10y-3y'+6e^{t}$. So $x_2'=y''=10x_1-3x_2+6e^{t}$.
> Step 4. Matrix form. Row 1 is $(0,1)$, row 2 is $(10,-3)$, and the term without an unknown goes into $F$:
>
> $$X'=\begin{pmatrix}0&1\\10&-3\end{pmatrix}X+\begin{pmatrix}0\\6e^{t}\end{pmatrix},\qquad X(0)=\begin{pmatrix}y(0)\\y'(0)\end{pmatrix}=\begin{pmatrix}1\\2\end{pmatrix}.$$
>
> Step 5. Check with the characteristic polynomial. $\det(\lambda\mathcal I_2-A)=\lambda(\lambda+3)-(-1)(-10)=\lambda^2+3\lambda-10$. This is the characteristic polynomial $r^2+3r-10$ of the original equation, as it must be.

## 2. Existence, superposition, Wronskian, fundamental matrix (slides 3-4)
![[math501_lecture_07_math501_chapter_7_p003.jpg]]
![[math501_lecture_07_math501_chapter_7_p004.jpg]]

**Notes.**
- **Existence and uniqueness.** If all entries of $A(t)$ and $F(t)$ are continuous on an open interval $J$ containing $t_0$, the IVP has a unique solution on all of $J$.
- **Superposition.** If $X_1,\dots,X_k$ solve the homogeneous system, so does $c_1X_1+\dots+c_kX_k$.
- **Wronskian test.** $n$ solutions $X_1,\dots,X_n$ of $X'=A(t)X$ are linearly independent on $J$ if and only if the determinant with these solutions as columns is nonzero:

$$W(X_1,\dots,X_n)\neq0 .$$

For solutions of one system, $W$ is nonzero everywhere on $J$ or zero everywhere. So one point is enough.

- A **fundamental set** is a set of $n$ linearly independent solutions. The **fundamental matrix** is $\Phi(t)=(X_1\ X_2\ \cdots\ X_n)$. Properties: $\det\Phi=W$, $\Phi$ is nonsingular, and $\Phi'=A\Phi$.
- **General solution** of $X'=A(t)X$ (section 7.2, bottom of slide 4):

$$X(t)=c_1X_1+\dots+c_nX_n=\Phi(t)\,C,\qquad C=(c_1,\dots,c_n)^{\mathsf T}.$$

> [!warning] Watch out
> Superposition is for the homogeneous system only. The "one point is enough" rule needs the columns to be solutions of the same system.

> [!info] Why $\Phi'=A\Phi$ and how $\Phi$ solves an IVP (beyond the slides)
> - Column $j$ of $\Phi$ is the solution $X_j$. Column $j$ of $\Phi'$ is $X_j'$, and column $j$ of $A\Phi$ is $AX_j$. Each $X_j$ satisfies $X_j'=AX_j$, so the two matrices are equal column by column.
> - $\Phi(t)C$ is the combination $c_1X_1+\dots+c_nX_n$ written as one product: a matrix times a column vector mixes the columns of the matrix.
> - Initial condition $X(t_0)=X_0$: put $t=t_0$ in $X=\Phi(t)C$. This gives the linear system $\Phi(t_0)C=X_0$. $\Phi(t_0)$ is nonsingular, so $C=\Phi(t_0)^{-1}X_0$. There is exactly one $C$, in agreement with the uniqueness theorem.

> [!question]- Check (slide 3, existence): Consider $x_1'=\dfrac{1}{t-3}x_1+x_2$, $x_2'=\ln(t+1)\,x_1+e^{t}$. On which interval does the theorem guarantee a unique solution for $X(1)=X_0$? And for $X(5)=X_0$?
> Step 1. List the entries of $A(t)$ and $F(t)$: $\dfrac{1}{t-3}$, $1$, $\ln(t+1)$, $0$ and $0$, $e^{t}$.
> Step 2. Where is each one continuous?
> - $\dfrac{1}{t-3}$: for $t\neq3$.
> - $\ln(t+1)$: for $t+1>0$, so $t>-1$.
> - $1$, $0$, $e^{t}$: everywhere.
>
> Step 3. All entries are continuous on $(-1,3)$ and on $(3,\infty)$.
> Step 4. $J$ must be an open interval that contains $t_0$.
> - $t_0=1$ lies in $(-1,3)$. Unique solution on $J=(-1,3)$.
> - $t_0=5$ lies in $(3,\infty)$. Unique solution on $J=(3,\infty)$.
>
> The vector $X_0$ plays no role. Only the continuity of the entries and the position of $t_0$ decide the interval.

> [!question]- Check (slide 3, superposition): $Y_1$ and $Y_2$ are two solutions of the NONhomogeneous system $X'=A(t)X+F(t)$. Which system does $Y_1+Y_2$ solve? Which system does $Y_1-Y_2$ solve?
> Given: $Y_1'=AY_1+F$ and $Y_2'=AY_2+F$.
> **Sum.** $(Y_1+Y_2)'=Y_1'+Y_2'=AY_1+F+AY_2+F=A(Y_1+Y_2)+2F$.
> So the sum solves $X'=AX+2F$. It does not solve the original system unless $F=\mathbf 0$. Superposition fails for a nonhomogeneous system.
> **Difference.** $(Y_1-Y_2)'=Y_1'-Y_2'=AY_1+F-AY_2-F=A(Y_1-Y_2)$.
> So the difference solves the homogeneous system $X'=AX$. This is the reason for $X=X_h+X_p$ in section 4.

> [!question]- Check (slide 3, Wronskian): $X_1=(1,2)^{\mathsf T}e^{t}$ and $X_2=(1,-1)^{\mathsf T}e^{4t}$ solve $X'=AX$ for $A$ with the rows $(3,-1)$ and $(-2,2)$. (a) Are they linearly independent? (b) Are $X_1$ and $X_3=(-2,-4)^{\mathsf T}e^{t}$ independent? (c) For $U=(t,1)^{\mathsf T}$ and $V=(t^2,t)^{\mathsf T}$ the determinant is zero for every $t$. Why does this not contradict the theorem?
> **(a)** Put the solutions in the columns:
>
> $$W(X_1,X_2)=\begin{vmatrix}e^{t}&e^{4t}\\2e^{t}&-e^{4t}\end{vmatrix}=e^{t}(-e^{4t})-e^{4t}(2e^{t})=-e^{5t}-2e^{5t}=-3e^{5t}.$$
>
> $-3e^{5t}\neq0$ for every $t$. The two solutions are linearly independent. They form a fundamental set (two independent solutions, $n=2$).
> Short way: $W(0)=(1)(-1)-(1)(2)=-3\neq0$. One point is enough for solutions of one system.
> **(b)**
>
> $$W(X_1,X_3)=\begin{vmatrix}e^{t}&-2e^{t}\\2e^{t}&-4e^{t}\end{vmatrix}=e^{t}(-4e^{t})-(-2e^{t})(2e^{t})=-4e^{2t}+4e^{2t}=0.$$
>
> $W=0$, so they are linearly dependent. Directly: $X_3=-2X_1$, so $2X_1+X_3=\mathbf O$ with constants not all zero.
> **(c)** $\det=t\cdot t-t^2\cdot1=0$ for every $t$. But $U$ and $V$ are independent as functions: $c_1U+c_2V=\mathbf O$ gives in the second row $c_1+c_2t=0$ for all $t$, so $c_1=c_2=0$.
> There is no contradiction. The theorem speaks only about $n$ solutions of ONE homogeneous system $X'=A(t)X$. $U$ and $V$ are not two solutions of one such system on any interval: $V=tU$, so $V'=U+tU'$. If $U'=AU$ and $V'=AV$, then $V'=U+tAU=U+AV$, and this equals $AV$ only if $U=\mathbf O$. But the second entry of $U$ is 1.
> What a zero determinant means: for solutions of one system, $W=0$ means linearly dependent. For other vector functions, dependent functions always have determinant zero, but a zero determinant does not show that they are dependent.

> [!question]- Check (slide 4, fundamental matrix): For $A$ with the rows $(4,1)$ and $(2,3)$, the solutions $X_1=(1,-2)^{\mathsf T}e^{2t}$ and $X_2=(1,1)^{\mathsf T}e^{5t}$ are given. Write $\Phi(t)$ and verify the three properties on the slide.
> $$\Phi(t)=\begin{pmatrix}e^{2t}&e^{5t}\\-2e^{2t}&e^{5t}\end{pmatrix}.$$
>
> **i. $\det\Phi=W$.** $\det\Phi=e^{2t}e^{5t}-e^{5t}(-2e^{2t})=e^{7t}+2e^{7t}=3e^{7t}$. This is the Wronskian of $X_1,X_2$ by definition (same determinant).
> **ii. Nonsingular.** $3e^{7t}\neq0$ for every $t$, so $\Phi(t)$ has an inverse for every $t$.
> **iii. $\Phi'=A\Phi$.** Differentiate each entry:
>
> $$\Phi'=\begin{pmatrix}2e^{2t}&5e^{5t}\\-4e^{2t}&5e^{5t}\end{pmatrix}.$$
>
> Multiply:
> - Row 1, column 1: $4e^{2t}+1(-2e^{2t})=2e^{2t}$.
> - Row 1, column 2: $4e^{5t}+1e^{5t}=5e^{5t}$.
> - Row 2, column 1: $2e^{2t}+3(-2e^{2t})=-4e^{2t}$.
> - Row 2, column 2: $2e^{5t}+3e^{5t}=5e^{5t}$.
>
> $$A\Phi=\begin{pmatrix}2e^{2t}&5e^{5t}\\-4e^{2t}&5e^{5t}\end{pmatrix}=\Phi'.$$
>
> All three properties hold.

> [!question]- Check (slide 4, general solution): With the same $\Phi(t)$ (columns $(1,-2)^{\mathsf T}e^{2t}$ and $(1,1)^{\mathsf T}e^{5t}$), use $X=\Phi(t)C$ to solve $X'=AX$, $X(0)=(4,1)^{\mathsf T}$ for $A$ with the rows $(4,1)$ and $(2,3)$.
> Method: $X(0)=\Phi(0)C=X_0$, so $C=\Phi(0)^{-1}X_0$.
> Step 1. $\Phi(0)=\begin{pmatrix}1&1\\-2&1\end{pmatrix}$, $\det\Phi(0)=(1)(1)-(1)(-2)=3$.
> Step 2. Inverse with the $2\times2$ rule: $\Phi(0)^{-1}=\dfrac13\begin{pmatrix}1&-1\\2&1\end{pmatrix}$.
> Step 3. $C=\dfrac13\begin{pmatrix}1&-1\\2&1\end{pmatrix}\begin{pmatrix}4\\1\end{pmatrix}=\dfrac13\begin{pmatrix}4-1\\8+1\end{pmatrix}=\begin{pmatrix}1\\3\end{pmatrix}$. So $c_1=1$, $c_2=3$.
> Step 4. $X(t)=\Phi(t)C=1\begin{pmatrix}1\\-2\end{pmatrix}e^{2t}+3\begin{pmatrix}1\\1\end{pmatrix}e^{5t}$:
>
> $$x_1=e^{2t}+3e^{5t},\qquad x_2=-2e^{2t}+3e^{5t}.$$
>
> Check, initial condition: $x_1(0)=1+3=4$, $x_2(0)=-2+3=1$. Correct.
> Check, equation 1: $x_1'=2e^{2t}+15e^{5t}$. $4x_1+x_2=4e^{2t}+12e^{5t}-2e^{2t}+3e^{5t}=2e^{2t}+15e^{5t}$. Equal.
> Check, equation 2: $x_2'=-4e^{2t}+15e^{5t}$. $2x_1+3x_2=2e^{2t}+6e^{5t}-6e^{2t}+9e^{5t}=-4e^{2t}+15e^{5t}$. Equal.

## 3. Homogeneous systems with a constant matrix (slides 5-6)
![[math501_lecture_07_math501_chapter_7_p005.jpg]]
![[math501_lecture_07_math501_chapter_7_p006.jpg]]

**Notes.** For a constant matrix $A$: if $v$ is an eigenvector for the eigenvalue $\lambda$, then $ve^{\lambda t}$ solves $X'=AX$.

If $A$ has $n$ distinct real eigenvalues $\lambda_i$ with eigenvectors $w_i$, the general solution is

$$X(t)=c_1w_1e^{\lambda_1t}+c_2w_2e^{\lambda_2t}+\dots+c_nw_ne^{\lambda_nt}.$$

Steps: eigenvalues from $\det(\lambda\mathcal I_n-A)=0$, one eigenvector for each, write the sum, and for an IVP put $t=t_0$ and solve for the constants.

> [!example] Slide examples
> - $X'=\begin{pmatrix}5&3\\1&3\end{pmatrix}X$: $\lambda^2-8\lambda+12=(\lambda-6)(\lambda-2)$. $\lambda=6$: $\begin{pmatrix}3\\1\end{pmatrix}$. $\lambda=2$: $\begin{pmatrix}1\\-1\end{pmatrix}$.
>   $X=c_1\begin{pmatrix}3\\1\end{pmatrix}e^{6t}+c_2\begin{pmatrix}1\\-1\end{pmatrix}e^{2t}$.
> - $x_1'=-11x_1-x_2$, $x_2'=6x_1-6x_2$, $X(0)=\begin{pmatrix}5\\-2\end{pmatrix}$: $\lambda^2+17\lambda+72=(\lambda+8)(\lambda+9)$. $\lambda=-8$: $\begin{pmatrix}1\\-3\end{pmatrix}$. $\lambda=-9$: $\begin{pmatrix}1\\-2\end{pmatrix}$.
>   $c_1+c_2=5$, $-3c_1-2c_2=-2$ give $c_1=-8$, $c_2=13$ (top of slide 7).
>   $x_1=-8e^{-8t}+13e^{-9t}$, $x_2=24e^{-8t}-26e^{-9t}$.

> [!warning] Watch out
> This chapter treats only the case of distinct real eigenvalues. The rule says nothing about repeated or complex eigenvalues.

> [!info] Complex and repeated eigenvalues, type of the equilibrium (beyond the slides)
> The slides stop at distinct real eigenvalues. The two other cases of a $2\times2$ matrix work like this.
> - **Complex eigenvalues $\lambda=\alpha\pm i\beta$.** Take $\lambda=\alpha+i\beta$ and one complex eigenvector $v$. The complex solution is $ve^{\lambda t}=ve^{\alpha t}(\cos\beta t+i\sin\beta t)$ (Euler's formula). Multiply out and split it: $ve^{\lambda t}=U(t)+iV(t)$. Because $A$ is real, the real part $U$ and the imaginary part $V$ are two independent real solutions. General solution: $X=c_1U+c_2V$. The second eigenvalue $\alpha-i\beta$ gives nothing new.
> - **Repeated eigenvalue $\lambda$ with only one independent eigenvector $v$.** The first solution is $X_1=ve^{\lambda t}$. For the second one solve $(A-\lambda\mathcal I)w=v$. The vector $w$ is a **generalized eigenvector**. Then $X_2=(vt+w)e^{\lambda t}$. Check: $X_2'=ve^{\lambda t}+\lambda(vt+w)e^{\lambda t}$ and $AX_2=(\lambda vt+Aw)e^{\lambda t}=(\lambda vt+\lambda w+v)e^{\lambda t}$. Equal.
> - **Type of the equilibrium $X=\mathbf 0$.** Both eigenvalues real and negative: stable node (all solutions go to $\mathbf 0$). Both positive: unstable node. Opposite signs: saddle (unstable). Complex with $\alpha<0$: stable spiral. $\alpha>0$: unstable spiral. $\alpha=0$: centre (closed curves; stable, but the solutions do not go to $\mathbf 0$).

> [!question]- Check (slide 5, theorem): Take $A$ with the rows $(2,3)$ and $(2,1)$. (a) Show that $\phi(t)=(3,2)^{\mathsf T}e^{4t}$ solves $X'=AX$. (b) Why can $(1,1)^{\mathsf T}e^{\lambda t}$ never be a solution, for any number $\lambda$?
> General reason: for $\phi=ve^{\lambda t}$ we have $\phi'=\lambda ve^{\lambda t}$ and $A\phi=(Av)e^{\lambda t}$. These are equal for all $t$ exactly when $Av=\lambda v$.
> **(a)** $Av=\begin{pmatrix}2&3\\2&1\end{pmatrix}\begin{pmatrix}3\\2\end{pmatrix}=\begin{pmatrix}6+6\\6+2\end{pmatrix}=\begin{pmatrix}12\\8\end{pmatrix}=4\begin{pmatrix}3\\2\end{pmatrix}$.
> So $v=(3,2)^{\mathsf T}$ is an eigenvector for $\lambda=4$.
> Left side: $\phi'=4\begin{pmatrix}3\\2\end{pmatrix}e^{4t}=\begin{pmatrix}12\\8\end{pmatrix}e^{4t}$. Right side: $A\phi=\begin{pmatrix}12\\8\end{pmatrix}e^{4t}$. Equal, so $\phi$ is a solution.
> **(b)** $A\begin{pmatrix}1\\1\end{pmatrix}=\begin{pmatrix}2+3\\2+1\end{pmatrix}=\begin{pmatrix}5\\3\end{pmatrix}$. For a solution we need $\begin{pmatrix}5\\3\end{pmatrix}=\lambda\begin{pmatrix}1\\1\end{pmatrix}$, so $\lambda=5$ and $\lambda=3$ at the same time. Impossible. $(1,1)^{\mathsf T}$ is not an eigenvector, so no exponent $\lambda$ works.

> [!question]- Check (slides 5-6): Find the general solution of $X'=AX$ for $A$ with the rows $(7,-4)$ and $(2,1)$.
> Case and method: constant matrix, look for distinct real eigenvalues, then $X=c_1w_1e^{\lambda_1t}+c_2w_2e^{\lambda_2t}$.
> **Step 1. Characteristic polynomial.**
>
> $$\det(\lambda\mathcal I_2-A)=\begin{vmatrix}\lambda-7&4\\-2&\lambda-1\end{vmatrix}=(\lambda-7)(\lambda-1)-(4)(-2)=\lambda^2-8\lambda+7+8=\lambda^2-8\lambda+15.$$
>
> **Step 2. Roots.** $\lambda^2-8\lambda+15=(\lambda-3)(\lambda-5)$, so $\lambda_1=3$, $\lambda_2=5$. Real and distinct.
> **Step 3. Eigenvector for $\lambda_1=3$.** $3\mathcal I_2-A=\begin{pmatrix}-4&4\\-2&2\end{pmatrix}$. The system is $-4v_1+4v_2=0$ and $-2v_1+2v_2=0$. Both say $v_1=v_2$. With $v_2=1$: $w_1=\begin{pmatrix}1\\1\end{pmatrix}$.
> Test: $Aw_1=\begin{pmatrix}7-4\\2+1\end{pmatrix}=\begin{pmatrix}3\\3\end{pmatrix}=3w_1$. Correct.
> **Step 4. Eigenvector for $\lambda_2=5$.** $5\mathcal I_2-A=\begin{pmatrix}-2&4\\-2&4\end{pmatrix}$. The system is $-2v_1+4v_2=0$ twice. So $v_1=2v_2$. With $v_2=1$: $w_2=\begin{pmatrix}2\\1\end{pmatrix}$.
> Test: $Aw_2=\begin{pmatrix}14-4\\4+1\end{pmatrix}=\begin{pmatrix}10\\5\end{pmatrix}=5w_2$. Correct.
> **Step 5. General solution.**
>
> $$X(t)=c_1\begin{pmatrix}1\\1\end{pmatrix}e^{3t}+c_2\begin{pmatrix}2\\1\end{pmatrix}e^{5t},\qquad x_1=c_1e^{3t}+2c_2e^{5t},\quad x_2=c_1e^{3t}+c_2e^{5t}.$$
>
> **Step 6. Check.** $x_1'=3c_1e^{3t}+10c_2e^{5t}$. $7x_1-4x_2=7c_1e^{3t}+14c_2e^{5t}-4c_1e^{3t}-4c_2e^{5t}=3c_1e^{3t}+10c_2e^{5t}$. Equal.
> $x_2'=3c_1e^{3t}+5c_2e^{5t}$. $2x_1+x_2=2c_1e^{3t}+4c_2e^{5t}+c_1e^{3t}+c_2e^{5t}=3c_1e^{3t}+5c_2e^{5t}$. Equal.
> Both eigenvalues are positive, so every nonzero solution grows: unstable node (beyond the slides).

> [!question]- Check (slide 5, three equations): The theorem holds for any $n$. Solve $X'=AX$, $X(0)=(4,5,4)^{\mathsf T}$ for $A$ with the rows $(1,1,0)$, $(0,2,1)$ and $(0,0,3)$.
> Case and method: constant $3\times3$ matrix, three distinct real eigenvalues, $X=c_1w_1e^{\lambda_1t}+c_2w_2e^{\lambda_2t}+c_3w_3e^{\lambda_3t}$.
> **Step 1. Eigenvalues.** $\lambda\mathcal I_3-A=\begin{pmatrix}\lambda-1&-1&0\\0&\lambda-2&-1\\0&0&\lambda-3\end{pmatrix}$ is upper triangular. Its determinant is the product of the diagonal: $(\lambda-1)(\lambda-2)(\lambda-3)$. So $\lambda_1=1$, $\lambda_2=2$, $\lambda_3=3$.
> **Step 2. $\lambda_1=1$.** $\mathcal I_3-A=\begin{pmatrix}0&-1&0\\0&-1&-1\\0&0&-2\end{pmatrix}$. Equations: $-v_2=0$, $-v_2-v_3=0$, $-2v_3=0$. So $v_2=0$, $v_3=0$, and $v_1$ is free. With $v_1=1$: $w_1=(1,0,0)^{\mathsf T}$.
> **Step 3. $\lambda_2=2$.** $2\mathcal I_3-A=\begin{pmatrix}1&-1&0\\0&0&-1\\0&0&-1\end{pmatrix}$. Equations: $v_1-v_2=0$, $-v_3=0$, $-v_3=0$. So $v_3=0$ and $v_1=v_2$. With $v_2=1$: $w_2=(1,1,0)^{\mathsf T}$.
> **Step 4. $\lambda_3=3$.** $3\mathcal I_3-A=\begin{pmatrix}2&-1&0\\0&1&-1\\0&0&0\end{pmatrix}$. Equations: $2v_1-v_2=0$, $v_2-v_3=0$. So $v_2=2v_1$ and $v_3=v_2$. With $v_1=1$: $w_3=(1,2,2)^{\mathsf T}$.
> **Step 5. General solution.**
>
> $$X(t)=c_1\begin{pmatrix}1\\0\\0\end{pmatrix}e^{t}+c_2\begin{pmatrix}1\\1\\0\end{pmatrix}e^{2t}+c_3\begin{pmatrix}1\\2\\2\end{pmatrix}e^{3t}.$$
>
> **Step 6. Initial condition.** At $t=0$:
> - Row 1: $c_1+c_2+c_3=4$
> - Row 2: $c_2+2c_3=5$
> - Row 3: $2c_3=4$
>
> From row 3: $c_3=2$. Row 2: $c_2=5-4=1$. Row 1: $c_1=4-1-2=1$.
> **Step 7. Solution.** $x_1=e^{t}+e^{2t}+2e^{3t}$, $x_2=e^{2t}+4e^{3t}$, $x_3=4e^{3t}$.
> **Step 8. Check.** $X(0)=(1+1+2,\ 1+4,\ 4)=(4,5,4)$. Correct.
> $x_1'=e^{t}+2e^{2t}+6e^{3t}$ and $x_1+x_2=e^{t}+e^{2t}+2e^{3t}+e^{2t}+4e^{3t}=e^{t}+2e^{2t}+6e^{3t}$. Equal.
> $x_2'=2e^{2t}+12e^{3t}$ and $2x_2+x_3=2e^{2t}+8e^{3t}+4e^{3t}=2e^{2t}+12e^{3t}$. Equal.
> $x_3'=12e^{3t}$ and $3x_3=12e^{3t}$. Equal.

> [!question]- Check (slide 5, complex eigenvalues, beyond the slides): Solve $X'=AX$, $X(0)=(2,3)^{\mathsf T}$ for $A$ with the rows $(-1,-4)$ and $(1,-1)$. The theorem on the slide does not apply. Why not, and what replaces it?
> Case and method: the eigenvalues are complex, so the slide theorem (distinct REAL eigenvalues) does not apply. Use the real and the imaginary part of one complex solution (info box above).
> **Step 1. Characteristic polynomial.**
>
> $$\det(\lambda\mathcal I_2-A)=\begin{vmatrix}\lambda+1&4\\-1&\lambda+1\end{vmatrix}=(\lambda+1)^2-(4)(-1)=\lambda^2+2\lambda+1+4=\lambda^2+2\lambda+5.$$
>
> **Step 2. Roots.** $\lambda=\dfrac{-2\pm\sqrt{4-20}}{2}=\dfrac{-2\pm\sqrt{-16}}{2}=\dfrac{-2\pm4i}{2}=-1\pm2i$. So $\alpha=-1$, $\beta=2$.
> **Step 3. Eigenvector for $\lambda=-1+2i$.** $\lambda\mathcal I_2-A=\begin{pmatrix}2i&4\\-1&2i\end{pmatrix}$. Row 2: $-v_1+2iv_2=0$, so $v_1=2iv_2$. With $v_2=1$: $v=\begin{pmatrix}2i\\1\end{pmatrix}$.
> Row 1 as a test: $2i(2i)+4(1)=4i^2+4=-4+4=0$. Correct.
> **Step 4. Complex solution.** $e^{(-1+2i)t}=e^{-t}(\cos2t+i\sin2t)$.
> - First entry: $2i(\cos2t+i\sin2t)=2i\cos2t+2i^2\sin2t=-2\sin2t+2i\cos2t$.
> - Second entry: $\cos2t+i\sin2t$.
>
> **Step 5. Real and imaginary parts.**
>
> $$U(t)=e^{-t}\begin{pmatrix}-2\sin2t\\\cos2t\end{pmatrix},\qquad V(t)=e^{-t}\begin{pmatrix}2\cos2t\\\sin2t\end{pmatrix}.$$
>
> **Step 6. General solution.** $X=c_1U+c_2V$:
> $x_1=e^{-t}(-2c_1\sin2t+2c_2\cos2t)$, $x_2=e^{-t}(c_1\cos2t+c_2\sin2t)$.
> **Step 7. Initial condition.** At $t=0$: $\sin0=0$, $\cos0=1$, $e^{0}=1$.
> - $x_1(0)=2c_2=2$, so $c_2=1$.
> - $x_2(0)=c_1=3$.
>
> **Step 8. Solution.**
>
> $$x_1(t)=e^{-t}(2\cos2t-6\sin2t),\qquad x_2(t)=e^{-t}(3\cos2t+\sin2t).$$
>
> **Step 9. Check.** $x_1(0)=2$, $x_2(0)=3$. Correct.
> Product rule: $x_1'=-e^{-t}(2\cos2t-6\sin2t)+e^{-t}(-4\sin2t-12\cos2t)=e^{-t}(-14\cos2t+2\sin2t)$.
> $-x_1-4x_2=e^{-t}(-2\cos2t+6\sin2t-12\cos2t-4\sin2t)=e^{-t}(-14\cos2t+2\sin2t)$. Equal.
> $x_2'=-e^{-t}(3\cos2t+\sin2t)+e^{-t}(-6\sin2t+2\cos2t)=e^{-t}(-\cos2t-7\sin2t)$.
> $x_1-x_2=e^{-t}(2\cos2t-6\sin2t-3\cos2t-\sin2t)=e^{-t}(-\cos2t-7\sin2t)$. Equal.
> Type: $\alpha=-1<0$, so the solution turns around the origin and its size decays like $e^{-t}$: stable spiral.

> [!question]- Check (slide 5, repeated eigenvalue, beyond the slides): Solve $X'=AX$, $X(0)=(2,1)^{\mathsf T}$ for $A$ with the rows $(3,1)$ and $(-1,1)$. Why does the slide theorem give only one solution here?
> Case and method: one repeated eigenvalue with only one independent eigenvector. The slide theorem needs $n$ distinct eigenvalues. Use a generalized eigenvector and the $te^{\lambda t}$ term (info box above).
> **Step 1. Characteristic polynomial.**
>
> $$\det(\lambda\mathcal I_2-A)=\begin{vmatrix}\lambda-3&-1\\1&\lambda-1\end{vmatrix}=(\lambda-3)(\lambda-1)-(-1)(1)=\lambda^2-4\lambda+3+1=\lambda^2-4\lambda+4=(\lambda-2)^2.$$
>
> **Step 2. Root.** $\lambda=2$, twice.
> **Step 3. Eigenvectors.** $2\mathcal I_2-A=\begin{pmatrix}-1&-1\\1&1\end{pmatrix}$. The system is $-v_1-v_2=0$ and $v_1+v_2=0$. So $v_2=-v_1$. With $v_1=1$: $v=\begin{pmatrix}1\\-1\end{pmatrix}$. Every eigenvector is a multiple of $v$, so there is only one independent solution of the form $ve^{2t}$.
> **Step 4. Generalized eigenvector.** Solve $(A-2\mathcal I_2)w=v$: $\begin{pmatrix}1&1\\-1&-1\end{pmatrix}\begin{pmatrix}w_1\\w_2\end{pmatrix}=\begin{pmatrix}1\\-1\end{pmatrix}$. Both rows say $w_1+w_2=1$. Choose $w_2=0$: $w=\begin{pmatrix}1\\0\end{pmatrix}$.
> **Step 5. Two solutions.** $X_1=\begin{pmatrix}1\\-1\end{pmatrix}e^{2t}$, $X_2=(vt+w)e^{2t}=\begin{pmatrix}t+1\\-t\end{pmatrix}e^{2t}$.
> **Step 6. General solution.**
>
> $$X(t)=c_1\begin{pmatrix}1\\-1\end{pmatrix}e^{2t}+c_2\begin{pmatrix}t+1\\-t\end{pmatrix}e^{2t}.$$
>
> **Step 7. Initial condition.** At $t=0$:
> - Row 1: $c_1+c_2=2$
> - Row 2: $-c_1=1$
>
> So $c_1=-1$ and $c_2=2-(-1)=3$.
> **Step 8. Solution.** $x_1=e^{2t}(-1+3(t+1))=e^{2t}(2+3t)$, $x_2=e^{2t}(1-3t)$.
> **Step 9. Check.** $x_1(0)=2$, $x_2(0)=1$. Correct.
> $x_1'=2e^{2t}(2+3t)+3e^{2t}=e^{2t}(7+6t)$. $3x_1+x_2=e^{2t}(6+9t+1-3t)=e^{2t}(7+6t)$. Equal.
> $x_2'=2e^{2t}(1-3t)-3e^{2t}=e^{2t}(-1-6t)$. $-x_1+x_2=e^{2t}(-2-3t+1-3t)=e^{2t}(-1-6t)$. Equal.
> Type: $\lambda=2>0$, so the solutions grow: unstable (improper) node.

> [!question]- Check (slide 6): Solve the initial value problem $x_1'=-2x_1+x_2$, $x_2'=4x_1-5x_2$, $X(0)=(3,-2)^{\mathsf T}$.
> Case and method: constant matrix $A=\begin{pmatrix}-2&1\\4&-5\end{pmatrix}$, eigenvalue method, then the constants from $X(0)$.
> **Step 1. Characteristic polynomial.**
>
> $$\det(\lambda\mathcal I_2-A)=\begin{vmatrix}\lambda+2&-1\\-4&\lambda+5\end{vmatrix}=(\lambda+2)(\lambda+5)-(-1)(-4)=\lambda^2+7\lambda+10-4=\lambda^2+7\lambda+6.$$
>
> **Step 2. Roots.** $\lambda^2+7\lambda+6=(\lambda+1)(\lambda+6)$, so $\lambda_1=-1$, $\lambda_2=-6$. Real and distinct.
> **Step 3. Eigenvector for $\lambda_1=-1$.** $-\mathcal I_2-A=\begin{pmatrix}-1+2&-1\\-4&-1+5\end{pmatrix}=\begin{pmatrix}1&-1\\-4&4\end{pmatrix}$. The system is $v_1-v_2=0$ and $-4v_1+4v_2=0$. So $v_2=v_1$. With $v_1=1$: $w_1=\begin{pmatrix}1\\1\end{pmatrix}$.
> **Step 4. Eigenvector for $\lambda_2=-6$.** $-6\mathcal I_2-A=\begin{pmatrix}-6+2&-1\\-4&-6+5\end{pmatrix}=\begin{pmatrix}-4&-1\\-4&-1\end{pmatrix}$. The system is $-4v_1-v_2=0$ twice. So $v_2=-4v_1$. With $v_1=1$: $w_2=\begin{pmatrix}1\\-4\end{pmatrix}$.
> **Step 5. General solution.**
>
> $$X(t)=c_1\begin{pmatrix}1\\1\end{pmatrix}e^{-t}+c_2\begin{pmatrix}1\\-4\end{pmatrix}e^{-6t}=\begin{pmatrix}c_1e^{-t}+c_2e^{-6t}\\c_1e^{-t}-4c_2e^{-6t}\end{pmatrix}.$$
>
> **Step 6. Initial condition.** At $t=0$ every exponential is 1:
> - $c_1+c_2=3$
> - $c_1-4c_2=-2$
>
> Subtract the second equation from the first: $(c_1+c_2)-(c_1-4c_2)=3-(-2)$, so $5c_2=5$ and $c_2=1$. Then $c_1=3-1=2$.
> **Step 7. Solution.**
>
> $$x_1(t)=2e^{-t}+e^{-6t},\qquad x_2(t)=2e^{-t}-4e^{-6t}.$$
>
> **Step 8. Check.** $x_1(0)=2+1=3$, $x_2(0)=2-4=-2$. Correct.
> $x_1'=-2e^{-t}-6e^{-6t}$. $-2x_1+x_2=-4e^{-t}-2e^{-6t}+2e^{-t}-4e^{-6t}=-2e^{-t}-6e^{-6t}$. Equal.
> $x_2'=-2e^{-t}+24e^{-6t}$. $4x_1-5x_2=8e^{-t}+4e^{-6t}-10e^{-t}+20e^{-6t}=-2e^{-t}+24e^{-6t}$. Equal.
> Both eigenvalues are negative, so $X(t)\to\mathbf 0$ as $t\to\infty$: stable node (beyond the slides).

## 4. Nonhomogeneous systems, variation of parameters (slides 7-10)
![[math501_lecture_07_math501_chapter_7_p007.jpg]]
![[math501_lecture_07_math501_chapter_7_p008.jpg]]
![[math501_lecture_07_math501_chapter_7_p009.jpg]]
![[math501_lecture_07_math501_chapter_7_p010.jpg]]

**Notes.** For $X'=A(t)X+F(t)$ the general solution is $X=X_h+X_p$: the general solution of the homogeneous system plus one particular solution.

**Variation of parameters.** With a fundamental matrix $\Phi$ of the homogeneous system:

$$X_p(t)=\Phi(t)\int\Phi^{-1}(t)F(t)\,dt,\qquad X(t)=\Phi(t)C+\Phi(t)\int\Phi^{-1}(t)F(t)\,dt .$$

Steps: (1) solve the homogeneous system and build $\Phi$, (2) compute $\Phi^{-1}$, (3) multiply $\Phi^{-1}F$ and integrate each entry with integration constants 0, (4) multiply by $\Phi$ and add $X_h$.

> [!example] Slide example
> $x_1'=-3x_1+x_2+3t$, $x_2'=2x_1-4x_2+e^{-t}$.
> - $\lambda^2+7\lambda+10=(\lambda+2)(\lambda+5)$. $\lambda=-2$: $\begin{pmatrix}1\\1\end{pmatrix}$. $\lambda=-5$: $\begin{pmatrix}1\\-2\end{pmatrix}$.
> - $\Phi=\begin{pmatrix}e^{-2t}&e^{-5t}\\e^{-2t}&-2e^{-5t}\end{pmatrix}$, $\det\Phi=-3e^{-7t}$, $\Phi^{-1}=\begin{pmatrix}\tfrac23e^{2t}&\tfrac13e^{2t}\\\tfrac13e^{5t}&-\tfrac13e^{5t}\end{pmatrix}$.
> - $\Phi^{-1}F=\begin{pmatrix}2te^{2t}+\tfrac13e^{t}\\te^{5t}-\tfrac13e^{4t}\end{pmatrix}$, integrated by parts: $\begin{pmatrix}te^{2t}-\tfrac12e^{2t}+\tfrac13e^{t}\\\tfrac15te^{5t}-\tfrac1{25}e^{5t}-\tfrac1{12}e^{4t}\end{pmatrix}$.
> - $X_p=\begin{pmatrix}\tfrac65t+\tfrac14e^{-t}-\tfrac{27}{50}\\\tfrac35t+\tfrac12e^{-t}-\tfrac{21}{50}\end{pmatrix}$.
>
> Answer: $x_1=c_1e^{-2t}+c_2e^{-5t}+\tfrac65t+\tfrac14e^{-t}-\tfrac{27}{50}$, $x_2=c_1e^{-2t}-2c_2e^{-5t}+\tfrac35t+\tfrac12e^{-t}-\tfrac{21}{50}$.

> [!warning] Watch out
> - Order of multiplication: $\Phi^{-1}$ before $F$, and $\Phi$ in front of the integral.
> - For an IVP with a forcing term, find $C$ after adding $X_p$.
> - The eigenvalue order must match the eigenvector order in $\Phi$.

> [!info] Where the formula $X_p=\Phi\int\Phi^{-1}F\,dt$ comes from (beyond the slides)
> The slide states the formula without a derivation. It takes four lines.
> 1. The homogeneous solution is $\Phi(t)C$ with a constant vector $C$. Replace the constant by an unknown vector function: try $X_p=\Phi(t)U(t)$. This is the "variation" of the parameters.
> 2. Product rule: $X_p'=\Phi'U+\Phi U'$. Use $\Phi'=A\Phi$: $X_p'=A\Phi U+\Phi U'$.
> 3. We need $X_p'=AX_p+F=A\Phi U+F$. Compare with line 2: the terms $A\Phi U$ cancel and $\Phi U'=F$ is left.
> 4. $\Phi$ is nonsingular, so $U'=\Phi^{-1}F$ and $U=\int\Phi^{-1}F\,dt$. Then $X_p=\Phi U=\Phi\int\Phi^{-1}F\,dt$.
>
> An integration constant vector $D$ in $U$ only adds $\Phi D$, a homogeneous solution. So the constants may be set to 0.
> **Undetermined coefficients.** For a constant matrix and a simple $F$ there is a shorter way: guess $X_p$ in the shape of $F$ with unknown constant vectors (constant $F$: $X_p=K$; polynomial of degree 1: $X_p=Kt+L$; $e^{at}$ with $a$ not an eigenvalue: $X_p=Ke^{at}$), put the guess into the system and compare coefficients. The constant and the polynomial guess need $\det A\neq0$ (0 is not an eigenvalue).

> [!question]- Check (slide 7, theorem, with undetermined coefficients beyond the slides): Solve $x_1'=-2x_1+x_2+6$, $x_2'=4x_1-5x_2$, $X(0)=(8,2)^{\mathsf T}$. The homogeneous part has the solution $X_h=c_1(1,1)^{\mathsf T}e^{-t}+c_2(1,-4)^{\mathsf T}e^{-6t}$ (check for slide 6).
> Case and method: nonhomogeneous, constant forcing $F=(6,0)^{\mathsf T}$. Use $X=X_h+X_p$. For a constant $F$ try a constant vector $X_p=K=(k_1,k_2)^{\mathsf T}$ (undetermined coefficients, beyond the slides).
> **Step 1. Particular solution.** $K'=\mathbf 0$, so the system gives
> - $0=-2k_1+k_2+6$
> - $0=4k_1-5k_2$
>
> From the first equation: $k_2=2k_1-6$. Put it into the second: $4k_1-5(2k_1-6)=0$, so $4k_1-10k_1+30=0$, $-6k_1=-30$, $k_1=5$. Then $k_2=2(5)-6=4$.
> $X_p=\begin{pmatrix}5\\4\end{pmatrix}$. Test: $-2(5)+4+6=0$ and $4(5)-5(4)=0$. Correct.
> **Step 2. General solution.**
>
> $$X(t)=c_1\begin{pmatrix}1\\1\end{pmatrix}e^{-t}+c_2\begin{pmatrix}1\\-4\end{pmatrix}e^{-6t}+\begin{pmatrix}5\\4\end{pmatrix}.$$
>
> **Step 3. Initial condition, applied to $X_h+X_p$.** At $t=0$:
> - $c_1+c_2+5=8$, so $c_1+c_2=3$
> - $c_1-4c_2+4=2$, so $c_1-4c_2=-2$
>
> Subtract: $5c_2=5$, $c_2=1$, $c_1=2$.
> **Step 4. Solution.** $x_1=2e^{-t}+e^{-6t}+5$, $x_2=2e^{-t}-4e^{-6t}+4$.
> **Step 5. Check.** $x_1(0)=2+1+5=8$, $x_2(0)=2-4+4=2$. Correct.
> $x_1'=-2e^{-t}-6e^{-6t}$. $-2x_1+x_2+6=-4e^{-t}-2e^{-6t}-10+2e^{-t}-4e^{-6t}+4+6=-2e^{-t}-6e^{-6t}$. Equal.
> $x_2'=-2e^{-t}+24e^{-6t}$. $4x_1-5x_2=8e^{-t}+4e^{-6t}+20-10e^{-t}+20e^{-6t}-20=-2e^{-t}+24e^{-6t}$. Equal.
> As $t\to\infty$ the exponentials die out and $X(t)\to(5,4)^{\mathsf T}$, the constant solution.

> [!question]- Check (slide 7, find the mistake): A student solves the homogeneous problem with $X_h(0)=X_0$ first, gets $c_1,c_2$, and then adds $X_p$. Why is the result wrong in general? Use the numbers of the previous check.
> The initial condition is for the full solution $X=X_h+X_p$, not for $X_h$ alone.
> If the constants come from $X_h(0)=X_0$, then $X(0)=X_h(0)+X_p(0)=X_0+X_p(0)$. This equals $X_0$ only when $X_p(0)=\mathbf 0$.
> Numbers: $X_h(0)=(8,2)^{\mathsf T}$ gives $c_1+c_2=8$, $c_1-4c_2=2$, so $5c_2=6$, $c_2=\tfrac65$, $c_1=\tfrac{34}{5}$. After adding $X_p=(5,4)^{\mathsf T}$: $X(0)=(8+5,\ 2+4)=(13,6)$, not $(8,2)$.
> Correct order: find $X_p$, add it, and only then put $t=t_0$ and solve for $C$.

> [!question]- Check (slide 8): Use the formula for one equation ($n=1$): find a particular solution of $x'=2x+e^{5t}$ with $X_p=\Phi\int\Phi^{-1}F\,dt$.
> For $n=1$ the matrix $A$ is the number 2 and $F=e^{5t}$.
> Step 1. Homogeneous equation $x'=2x$: solution $e^{2t}$, so $\Phi=e^{2t}$.
> Step 2. $\Phi^{-1}=e^{-2t}$.
> Step 3. $\Phi^{-1}F=e^{-2t}e^{5t}=e^{3t}$.
> Step 4. $\int e^{3t}\,dt=\tfrac13e^{3t}$ (constant 0).
> Step 5. $x_p=\Phi\cdot\tfrac13e^{3t}=e^{2t}\cdot\tfrac13e^{3t}=\tfrac13e^{5t}$.
> Check: $x_p'=\tfrac53e^{5t}$. $2x_p+e^{5t}=\tfrac23e^{5t}+e^{5t}=\tfrac53e^{5t}$. Equal.
> General solution: $x=ce^{2t}+\tfrac13e^{5t}$. This is the integrating-factor method of first-order linear equations. The matrix formula is its extension to systems.

> [!question]- Check (slide 9): For $\Phi(t)$ with the columns $(1,2)^{\mathsf T}e^{t}$ and $(1,-1)^{\mathsf T}e^{4t}$, compute $\det\Phi$ and $\Phi^{-1}(t)$. Test the result.
> $$\Phi=\begin{pmatrix}e^{t}&e^{4t}\\2e^{t}&-e^{4t}\end{pmatrix}.$$
>
> Step 1. $\det\Phi=e^{t}(-e^{4t})-e^{4t}(2e^{t})=-e^{5t}-2e^{5t}=-3e^{5t}$.
> Step 2. $2\times2$ rule: swap the diagonal entries, change the sign of the other two, divide by the determinant:
>
> $$\Phi^{-1}=\frac{1}{-3e^{5t}}\begin{pmatrix}-e^{4t}&-e^{4t}\\-2e^{t}&e^{t}\end{pmatrix}.$$
>
> Step 3. Divide each entry. Use $e^{4t}/e^{5t}=e^{-t}$ and $e^{t}/e^{5t}=e^{-4t}$:
>
> $$\Phi^{-1}=\begin{pmatrix}\tfrac13e^{-t}&\tfrac13e^{-t}\\\tfrac23e^{-4t}&-\tfrac13e^{-4t}\end{pmatrix}.$$
>
> Step 4. Test $\Phi^{-1}\Phi=\mathcal I_2$:
> - Row 1, column 1: $\tfrac13e^{-t}e^{t}+\tfrac13e^{-t}(2e^{t})=\tfrac13+\tfrac23=1$.
> - Row 1, column 2: $\tfrac13e^{-t}e^{4t}+\tfrac13e^{-t}(-e^{4t})=\tfrac13e^{3t}-\tfrac13e^{3t}=0$.
> - Row 2, column 1: $\tfrac23e^{-4t}e^{t}-\tfrac13e^{-4t}(2e^{t})=\tfrac23e^{-3t}-\tfrac23e^{-3t}=0$.
> - Row 2, column 2: $\tfrac23e^{-4t}e^{4t}-\tfrac13e^{-4t}(-e^{4t})=\tfrac23+\tfrac13=1$.
>
> Pattern: row 1 of $\Phi^{-1}$ carries $e^{-\lambda_1t}$ and row 2 carries $e^{-\lambda_2t}$. The same pattern is on the slide ($e^{2t}$ and $e^{5t}$ for $\lambda=-2,-5$).

> [!question]- Check (slides 8-10): Solve $x_1'=2x_1+x_2+2t$, $x_2'=x_1+2x_2$, $x_1(0)=0$, $x_2(0)=0$ by variation of parameters.
> Case and method: nonhomogeneous, constant matrix $A=\begin{pmatrix}2&1\\1&2\end{pmatrix}$, $F=\begin{pmatrix}2t\\0\end{pmatrix}$. Solve the homogeneous system, build $\Phi$, then $X_p=\Phi\int\Phi^{-1}F\,dt$, then the constants.
> **Step 1. Eigenvalues.** $\det(\lambda\mathcal I_2-A)=\begin{vmatrix}\lambda-2&-1\\-1&\lambda-2\end{vmatrix}=(\lambda-2)^2-(-1)(-1)=\lambda^2-4\lambda+4-1=\lambda^2-4\lambda+3=(\lambda-3)(\lambda-1)$. So $\lambda_1=3$, $\lambda_2=1$.
> **Step 2. Eigenvectors.**
> - $\lambda_1=3$: $3\mathcal I_2-A=\begin{pmatrix}1&-1\\-1&1\end{pmatrix}$, so $v_1-v_2=0$, $v_1=v_2$: $w_1=\begin{pmatrix}1\\1\end{pmatrix}$.
> - $\lambda_2=1$: $\mathcal I_2-A=\begin{pmatrix}-1&-1\\-1&-1\end{pmatrix}$, so $-v_1-v_2=0$, $v_2=-v_1$: $w_2=\begin{pmatrix}1\\-1\end{pmatrix}$.
>
> **Step 3. Homogeneous solution and $\Phi$.** $X_h=c_1\begin{pmatrix}1\\1\end{pmatrix}e^{3t}+c_2\begin{pmatrix}1\\-1\end{pmatrix}e^{t}$,
>
> $$\Phi=\begin{pmatrix}e^{3t}&e^{t}\\e^{3t}&-e^{t}\end{pmatrix},\qquad\det\Phi=e^{3t}(-e^{t})-e^{t}e^{3t}=-2e^{4t}.$$
>
> **Step 4. Inverse.**
>
> $$\Phi^{-1}=\frac{1}{-2e^{4t}}\begin{pmatrix}-e^{t}&-e^{t}\\-e^{3t}&e^{3t}\end{pmatrix}=\begin{pmatrix}\tfrac12e^{-3t}&\tfrac12e^{-3t}\\\tfrac12e^{-t}&-\tfrac12e^{-t}\end{pmatrix}.$$
>
> **Step 5. $\Phi^{-1}F$.** Row 1: $\tfrac12e^{-3t}(2t)+\tfrac12e^{-3t}(0)=te^{-3t}$. Row 2: $\tfrac12e^{-t}(2t)-\tfrac12e^{-t}(0)=te^{-t}$.
> **Step 6. Integrate by parts** ($\int u\,dv=uv-\int v\,du$), constants 0.
> - $u=t$, $dv=e^{-3t}dt$, so $du=dt$, $v=-\tfrac13e^{-3t}$: $\int te^{-3t}dt=-\tfrac13te^{-3t}+\tfrac13\int e^{-3t}dt=-\tfrac13te^{-3t}-\tfrac19e^{-3t}$.
> - $u=t$, $dv=e^{-t}dt$, so $du=dt$, $v=-e^{-t}$: $\int te^{-t}dt=-te^{-t}+\int e^{-t}dt=-te^{-t}-e^{-t}$.
>
> **Step 7. Multiply by $\Phi$.**
> - Row 1: $e^{3t}\left(-\tfrac13te^{-3t}-\tfrac19e^{-3t}\right)+e^{t}\left(-te^{-t}-e^{-t}\right)=-\tfrac13t-\tfrac19-t-1=-\tfrac43t-\tfrac{10}{9}$.
> - Row 2: $e^{3t}\left(-\tfrac13te^{-3t}-\tfrac19e^{-3t}\right)-e^{t}\left(-te^{-t}-e^{-t}\right)=-\tfrac13t-\tfrac19+t+1=\tfrac23t+\tfrac89$.
>
> $$X_p=\begin{pmatrix}-\tfrac43t-\tfrac{10}{9}\\\tfrac23t+\tfrac89\end{pmatrix}.$$
>
> **Step 8. General solution.** $x_1=c_1e^{3t}+c_2e^{t}-\tfrac43t-\tfrac{10}{9}$, $x_2=c_1e^{3t}-c_2e^{t}+\tfrac23t+\tfrac89$.
> **Step 9. Initial condition (after adding $X_p$).** At $t=0$:
> - $c_1+c_2-\tfrac{10}{9}=0$, so $c_1+c_2=\tfrac{10}{9}$
> - $c_1-c_2+\tfrac89=0$, so $c_1-c_2=-\tfrac89$
>
> Add: $2c_1=\tfrac29$, $c_1=\tfrac19$. Subtract: $2c_2=\tfrac{18}{9}=2$, $c_2=1$.
> **Step 10. Solution.**
>
> $$x_1(t)=\tfrac19e^{3t}+e^{t}-\tfrac43t-\tfrac{10}{9},\qquad x_2(t)=\tfrac19e^{3t}-e^{t}+\tfrac23t+\tfrac89.$$
>
> **Step 11. Check.** $x_1(0)=\tfrac19+1-\tfrac{10}{9}=0$, $x_2(0)=\tfrac19-1+\tfrac89=0$. Correct.
> $x_1'=\tfrac13e^{3t}+e^{t}-\tfrac43$. $2x_1+x_2+2t=\left(\tfrac29+\tfrac19\right)e^{3t}+(2-1)e^{t}+\left(-\tfrac83+\tfrac23+2\right)t+\left(-\tfrac{20}{9}+\tfrac89\right)=\tfrac13e^{3t}+e^{t}+0t-\tfrac43$. Equal.
> $x_2'=\tfrac13e^{3t}-e^{t}+\tfrac23$. $x_1+2x_2=\left(\tfrac19+\tfrac29\right)e^{3t}+(1-2)e^{t}+\left(-\tfrac43+\tfrac43\right)t+\left(-\tfrac{10}{9}+\tfrac{16}{9}\right)=\tfrac13e^{3t}-e^{t}+\tfrac23$. Equal.

> [!question]- Check (slide 10): The slide chooses $d_1=0$ and $d_2=0$. What changes in the final answer if you keep $d_1$ and $d_2$?
> Keep the constants: $\int\Phi^{-1}F\,dt=G(t)+D$ with $D=(d_1,d_2)^{\mathsf T}$, where $G$ is the integral with constants 0.
> Then $\Phi\,(G+D)=\Phi G+\Phi D$.
> $\Phi D=d_1X_1+d_2X_2=d_1\begin{pmatrix}1\\1\end{pmatrix}e^{-2t}+d_2\begin{pmatrix}1\\-2\end{pmatrix}e^{-5t}$ is a solution of the homogeneous system.
> The general solution becomes $X=\Phi C+\Phi D+\Phi G=\Phi(C+D)+\Phi G$. $C$ is arbitrary, so $C+D$ is again an arbitrary constant vector.
> Nothing changes: the same family of solutions. $d_1=d_2=0$ is the simplest choice. Any other choice gives a different but equally valid $X_p$.

## Key formulas and terms
| Term | Meaning / formula |
|---|---|
| Matrix form | $X'(t)=A(t)X(t)+F(t)$ |
| Homogeneous system | $F=\mathbf 0$ |
| Wronskian | Determinant with the solutions as columns; nonzero means independent |
| Fundamental set | $n$ linearly independent solutions of $X'=AX$ |
| Fundamental matrix | $\Phi=(X_1\ \cdots\ X_n)$, $\Phi'=A\Phi$, $\det\Phi=W$ |
| General solution, homogeneous | $X=\Phi(t)C$ |
| Eigenpair solution | $X=we^{\lambda t}$ when $Aw=\lambda w$ |
| Distinct real eigenvalues | $X=\sum c_iw_ie^{\lambda_it}$ |
| Variation of parameters | $X_p=\Phi\int\Phi^{-1}F\,dt$ |
| $2\times2$ inverse | $\dfrac{1}{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$ |

## Check yourself
> [!question]- 1. Show that $X=\begin{pmatrix}-1\\2\end{pmatrix}e^{-3t/2}$ solves $x_1'=-x_1+\tfrac14x_2$, $x_2'=x_1-x_2$.
> Left: $X'=\begin{pmatrix}3/2\\-3\end{pmatrix}e^{-3t/2}$.
> Right: $\begin{pmatrix}-1&1/4\\1&-1\end{pmatrix}\begin{pmatrix}-1\\2\end{pmatrix}e^{-3t/2}=\begin{pmatrix}3/2\\-3\end{pmatrix}e^{-3t/2}$. Equal.

> [!question]- 2. Are $X_1=\begin{pmatrix}1\\1\end{pmatrix}e^{-2t}$ and $X_2=\begin{pmatrix}1\\-2\end{pmatrix}e^{-5t}$ independent?
> $W=e^{-2t}(-2e^{-5t})-e^{-5t}e^{-2t}=-3e^{-7t}\neq0$. Independent.

> [!question]- 3. Solve $X'=\begin{pmatrix}1&2\\3&2\end{pmatrix}X$, $X(0)=\begin{pmatrix}3\\2\end{pmatrix}$.
> $\lambda^2-3\lambda-4=(\lambda-4)(\lambda+1)$. $\lambda=4$: $\begin{pmatrix}2\\3\end{pmatrix}$. $\lambda=-1$: $\begin{pmatrix}1\\-1\end{pmatrix}$.
> $2c_1+c_2=3$, $3c_1-c_2=2$: $c_1=c_2=1$. Answer: $x_1=2e^{4t}+e^{-t}$, $x_2=3e^{4t}-e^{-t}$.

> [!question]- 4. Solve $x_1'=6x_1+x_2+6t$, $x_2'=4x_1+3x_2-10t+4$, $x_1(0)=x_2(0)=1$.
> $\lambda=2$: $\begin{pmatrix}1\\-4\end{pmatrix}$. $\lambda=7$: $\begin{pmatrix}1\\1\end{pmatrix}$. $\det\Phi=5e^{9t}$.
> $X_p=\begin{pmatrix}-2t-\tfrac47\\6t+\tfrac{10}{7}\end{pmatrix}$. Initial condition: $c_1=\tfrac25$, $c_2=\tfrac{41}{35}$.
> Answer: $x_1=\tfrac25e^{2t}+\tfrac{41}{35}e^{7t}-2t-\tfrac47$, $x_2=-\tfrac85e^{2t}+\tfrac{41}{35}e^{7t}+6t+\tfrac{10}{7}$.

> [!question]- 5. Show that $X_p=\begin{pmatrix}1\\1\end{pmatrix}e^t+\begin{pmatrix}1\\-1\end{pmatrix}te^t$ solves $X'=\begin{pmatrix}2&1\\3&4\end{pmatrix}X-\begin{pmatrix}1\\7\end{pmatrix}e^t$.
> $X_p=\begin{pmatrix}(1+t)e^t\\(1-t)e^t\end{pmatrix}$, so $X_p'=\begin{pmatrix}(2+t)e^t\\-te^t\end{pmatrix}$.
> Right side: $\begin{pmatrix}2+2t+1-t-1\\3+3t+4-4t-7\end{pmatrix}e^t=\begin{pmatrix}2+t\\-t\end{pmatrix}e^t$. Equal.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L06 - Eigenvalues and eigenvectors]]. Next: [[MATH501 L08 - Laplace's equation]]
- Related: systems solved with the Laplace transform are in [[MATH501 L03 - The Laplace transform]]
- Full step-by-step notes (PDF): [MATH501_Lecture_07_Linear_Systems.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_07/MATH501_Lecture_07_Linear_Systems.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_07/MATH501_Lecture_07_Linear_Systems.pdf`
- Original chapter notes (PDF): [Math501 Chapter 7.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_07/Math501%20Chapter%207.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_07/Math501 Chapter 7.pdf`
- Quiz: [[MATH501 L07 - Linear systems of ODEs - quiz]]

Slides not embedded: none.
