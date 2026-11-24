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

Slides not embedded: none.
