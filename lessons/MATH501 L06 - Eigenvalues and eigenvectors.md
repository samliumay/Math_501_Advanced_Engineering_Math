---
course: MATH 501 Advanced Engineering Mathematics
lecture: 6
title: Eigenvalues and eigenvectors
tags: [math501, lecture]
slides: lectures/lecture_06/Math501 Chapter 6.pdf
full_notes: lecture_notes/lecture_06/MATH501_Lecture_06_Eigenvalues_Eigenvectors.pdf
---
# MATH 501 · Lecture 6 · Eigenvalues and eigenvectors

> [!summary] In short
> - $Av=\lambda v$ with $v\neq\mathbf 0$: $\lambda$ is an eigenvalue, $v$ an eigenvector.
> - Eigenvalues are the roots of the characteristic polynomial $\det(\lambda\mathcal I_n-A)$.
> - Eigenvectors for $\lambda$ are the nonzero solutions of $(\lambda\mathcal I_n-A)x=\mathbf O$.
> - Cayley-Hamilton: $p_A(A)=O$. It gives $A^{-1}$ without row reduction.
> - $A$ is diagonalizable exactly when it has $n$ independent eigenvectors. Then $P^{-1}AP=D$ and $A^k=PD^kP^{-1}$.

The slide numbers below are the pages of the Chapter 6 PDF (page 1 is printed page 89).

## 1. Eigenvalues and the characteristic polynomial (slides 1-3)
![[math501_lecture_06_math501_chapter_6_p001.jpg]]
![[math501_lecture_06_math501_chapter_6_p002.jpg]]

**Notes.** For an $n\times n$ matrix $A$, a number $\lambda$ is an **eigenvalue** if there is a nonzero vector $v$ with

$$Av=\lambda v .$$

$v$ is an **eigenvector** for $\lambda$. Every nonzero multiple $cv$ is also an eigenvector for the same $\lambda$.

$Av=\lambda v$ is the same as $(\lambda\mathcal I_n-A)v=\mathbf O$. A nonzero solution exists only if

$$p_A(\lambda)=\det(\lambda\mathcal I_n-A)=0 .$$

$p_A$ is the **characteristic polynomial**, of degree $n$. Its roots are the eigenvalues.

Shortcut: the eigenvalues of a triangular matrix are its diagonal entries (example at the top of slide 3: $6, 7, 1, 8$).

> [!example] Slide examples
> - $A=\begin{pmatrix}3&0\\8&-1\end{pmatrix}$: $p_A=(\lambda-3)(\lambda+1)$, eigenvalues $3$ and $-1$.
> - $A=\begin{pmatrix}-11&-5&-3\\12&7&2\\12&5&4\end{pmatrix}$: after $R_1+R_3$ a factor $(\lambda-1)$ comes out. $p_A=(\lambda-1)(\lambda+3)(\lambda-2)$, eigenvalues $1,-3,2$.

> [!warning] Watch out
> The diagonal shortcut needs a triangular matrix. Use $\det(\lambda\mathcal I-A)$, never $\det(A)-\lambda$.

> [!info] Trace, determinant and complex eigenvalues (beyond the slides)
> The **trace** $\operatorname{tr}(A)$ is the sum of the main diagonal entries. For $A=\begin{pmatrix}a&b\\c&d\end{pmatrix}$:
> $$p_A(\lambda)=(\lambda-a)(\lambda-d)-bc=\lambda^2-(a+d)\lambda+(ad-bc)=\lambda^2-\operatorname{tr}(A)\,\lambda+\det(A).$$
> If the roots are $\lambda_1,\lambda_2$, then also $p_A(\lambda)=(\lambda-\lambda_1)(\lambda-\lambda_2)=\lambda^2-(\lambda_1+\lambda_2)\lambda+\lambda_1\lambda_2$. Compare the coefficients:
> $$\lambda_1+\lambda_2=\operatorname{tr}(A),\qquad\lambda_1\lambda_2=\det(A).$$
> The same holds for every $n\times n$ matrix: the sum of the eigenvalues (each counted as often as it is a root) is the trace, and their product is the determinant. Use this as a quick check of your eigenvalues. It also shows: $A$ is invertible exactly when 0 is not an eigenvalue.
> The definition on slide 1 allows a complex $\lambda$. A real matrix can have complex eigenvalues. They come in conjugate pairs $\alpha\pm\beta i$, and the eigenvectors then have complex entries.

> [!question]- Check (slide 1): $A$ has the rows $(2,0,1)$, $(0,3,0)$ and $(1,0,2)$. Which of $v=(1,0,-1)$, $w=(1,0,1)$, $u=(1,1,0)$ are eigenvectors of $A$, and for which eigenvalue? Is $5v$ an eigenvector?
> Multiply each vector by $A$ and see if the result is a multiple of the vector.
> $Av=(2\cdot1+0\cdot0+1\cdot(-1),\ 0\cdot1+3\cdot0+0\cdot(-1),\ 1\cdot1+0\cdot0+2\cdot(-1))=(1,0,-1)=1\cdot v$. Eigenvector, $\lambda=1$.
> $Aw=(2\cdot1+0+1\cdot1,\ 0+0+0,\ 1\cdot1+0+2\cdot1)=(3,0,3)=3\cdot w$. Eigenvector, $\lambda=3$.
> $Au=(2\cdot1+0\cdot1+0,\ 0+3\cdot1+0,\ 1\cdot1+0+0)=(2,3,1)$. For $Au=\lambda u=(\lambda,\lambda,0)$ the first entry needs $\lambda=2$, the second needs $\lambda=3$, and the third would have to be 0 but is 1. Not an eigenvector.
> $A(5v)=5(Av)=5\cdot(1\cdot v)=1\cdot(5v)$. So $5v=(5,0,-5)$ is also an eigenvector for the same eigenvalue $\lambda=1$ (the first remark on the slide).

> [!question]- Check (slide 2, a 2 by 2 matrix; the trace check is beyond the slides): $A$ has the rows $(1,2)$ and $(3,-4)$. Find the characteristic polynomial and the eigenvalues. Check them with the trace and the determinant.
> $\lambda\mathcal I_2-A=\begin{pmatrix}\lambda&0\\0&\lambda\end{pmatrix}-\begin{pmatrix}1&2\\3&-4\end{pmatrix}=\begin{pmatrix}\lambda-1&-2\\-3&\lambda+4\end{pmatrix}$.
> $p_A(\lambda)=(\lambda-1)(\lambda+4)-(-2)(-3)=\lambda^2+4\lambda-\lambda-4-6=\lambda^2+3\lambda-10$.
> Factor: two numbers with product $-10$ and sum $3$ are $5$ and $-2$. $p_A(\lambda)=(\lambda+5)(\lambda-2)$.
> $p_A(\lambda)=0$ gives $\lambda_1=2$ and $\lambda_2=-5$.
> Check (info box above): $\operatorname{tr}(A)=1+(-4)=-3$ and $\lambda_1+\lambda_2=2-5=-3$.
> $\det(A)=1\cdot(-4)-2\cdot3=-10$ and $\lambda_1\lambda_2=2\cdot(-5)=-10$. Both agree.

> [!question]- Check (slide 2, a 3 by 3 matrix): $A$ has the rows $(4,1,1)$, $(1,4,1)$ and $(1,1,4)$. Find the characteristic polynomial in factored form and the eigenvalues.
> $\lambda\mathcal I_3-A=\begin{pmatrix}\lambda-4&-1&-1\\-1&\lambda-4&-1\\-1&-1&\lambda-4\end{pmatrix}$.
> Expand the determinant along the first row:
> $p_A(\lambda)=(\lambda-4)\begin{vmatrix}\lambda-4&-1\\-1&\lambda-4\end{vmatrix}-(-1)\begin{vmatrix}-1&-1\\-1&\lambda-4\end{vmatrix}+(-1)\begin{vmatrix}-1&\lambda-4\\-1&-1\end{vmatrix}$.
> First minor: $(\lambda-4)^2-(-1)(-1)=(\lambda-4)^2-1=(\lambda-4-1)(\lambda-4+1)=(\lambda-5)(\lambda-3)$.
> Second minor: $(-1)(\lambda-4)-(-1)(-1)=-\lambda+4-1=-(\lambda-3)$.
> Third minor: $(-1)(-1)-(\lambda-4)(-1)=1+\lambda-4=\lambda-3$.
> Put together: $p_A(\lambda)=(\lambda-4)(\lambda-5)(\lambda-3)+1\cdot\bigl(-(\lambda-3)\bigr)-1\cdot(\lambda-3)=(\lambda-4)(\lambda-5)(\lambda-3)-2(\lambda-3)$.
> Factor out $(\lambda-3)$: $p_A(\lambda)=(\lambda-3)\bigl[(\lambda-4)(\lambda-5)-2\bigr]=(\lambda-3)\bigl[\lambda^2-9\lambda+20-2\bigr]=(\lambda-3)(\lambda^2-9\lambda+18)$.
> Factor the quadratic: product $18$, sum $-9$: $-3$ and $-6$. $\lambda^2-9\lambda+18=(\lambda-3)(\lambda-6)$.
> $p_A(\lambda)=(\lambda-3)^2(\lambda-6)$.
> Eigenvalues: $\lambda=3$ (a double root) and $\lambda=6$.
> Check with the trace and the determinant (info box above, beyond the slides): trace $4+4+4=12=3+3+6$. Determinant along row 1: $4\,(16-1)-1\,(4-1)+1\,(1-4)=60-3-3=54=3\cdot3\cdot6$.

> [!question]- Check (slide 2, complex roots, beyond the slides): $A$ has the rows $(1,-2)$ and $(1,3)$. Find its eigenvalues and an eigenvector for one of them. Check $Av=\lambda v$.
> $\lambda\mathcal I_2-A=\begin{pmatrix}\lambda-1&2\\-1&\lambda-3\end{pmatrix}$.
> $p_A(\lambda)=(\lambda-1)(\lambda-3)-2\cdot(-1)=\lambda^2-4\lambda+3+2=\lambda^2-4\lambda+5$.
> Quadratic formula: $\lambda=\dfrac{4\pm\sqrt{16-20}}{2}=\dfrac{4\pm\sqrt{-4}}{2}=\dfrac{4\pm2i}{2}=2\pm i$.
> The discriminant is negative, so there is no real eigenvalue. The eigenvalues are the conjugate pair $2+i$ and $2-i$.
> Eigenvector for $\lambda=2+i$: $(2+i)\mathcal I_2-A=\begin{pmatrix}1+i&2\\-1&-1+i\end{pmatrix}$.
> Row 2: $-x_1+(-1+i)x_2=0$, so $x_1=(-1+i)x_2$. Take $x_2=1$: $v=\begin{pmatrix}-1+i\\1\end{pmatrix}$.
> Row 1 must hold too: $(1+i)(-1+i)+2\cdot1=(-1+i-i+i^2)+2=(-1-1)+2=0$. True.
> Check: $Av=\begin{pmatrix}1\cdot(-1+i)-2\cdot1\\1\cdot(-1+i)+3\cdot1\end{pmatrix}=\begin{pmatrix}-3+i\\2+i\end{pmatrix}$.
> $\lambda v=(2+i)\begin{pmatrix}-1+i\\1\end{pmatrix}=\begin{pmatrix}-2+2i-i+i^2\\2+i\end{pmatrix}=\begin{pmatrix}-3+i\\2+i\end{pmatrix}$. The same.
> For $\lambda=2-i$ replace $i$ by $-i$ everywhere: eigenvector $\begin{pmatrix}-1-i\\1\end{pmatrix}$.
> Trace check: $(2+i)+(2-i)=4=1+3$. Determinant check: $(2+i)(2-i)=4-i^2=5=1\cdot3-(-2)\cdot1$.

## 2. Eigenvectors (slides 3-5)
![[math501_lecture_06_math501_chapter_6_p003.jpg]]
![[math501_lecture_06_math501_chapter_6_p004.jpg]]
![[math501_lecture_06_math501_chapter_6_p005.jpg]]

**Notes.** For each eigenvalue $\lambda_i$: form $\lambda_i\mathcal I_n-A$, solve the homogeneous system, and write the solution with free variables. Pick simple values for the free variables.

> [!example] Slide examples
> - $A=\begin{pmatrix}2&2\\5&-1\end{pmatrix}$: $p_A=\lambda^2-\lambda-12=(\lambda-4)(\lambda+3)$.
>   $\lambda=4$: $2x_1-2x_2=0$, eigenvector $\begin{pmatrix}1\\1\end{pmatrix}$. $\lambda=-3$: $-5x_1-2x_2=0$, eigenvector $\begin{pmatrix}-2/5\\1\end{pmatrix}$.
> - $A=\begin{pmatrix}0&0&-2\\1&2&1\\1&0&3\end{pmatrix}$: $p_A=(\lambda-2)^2(\lambda-1)$.
>   $\lambda=1$: $x_1=-2x_3$, $x_2=x_3$, eigenvector $\begin{pmatrix}-2\\1\\1\end{pmatrix}$.
>   $\lambda=2$: only $x_1=-x_3$, so $x_2$ and $x_3$ are free: eigenvectors $\begin{pmatrix}0\\1\\0\end{pmatrix}$ and $\begin{pmatrix}-1\\0\\1\end{pmatrix}$.

> [!warning] Watch out
> - The zero vector is never an eigenvector, but $\lambda=0$ can be an eigenvalue.
> - If the system has only the zero solution, the $\lambda$ is wrong.
> - A double root does not promise two independent eigenvectors. $\begin{pmatrix}1&1\\0&1\end{pmatrix}$ has only one.

> [!info] Two multiplicities, and symmetric matrices (beyond the slides)
> - **Algebraic multiplicity** of $\lambda$: how often $\lambda$ is a root of $p_A$. In $(\lambda-2)^2(\lambda-1)$ the eigenvalue 2 has algebraic multiplicity 2.
> - **Geometric multiplicity** of $\lambda$: the number of free variables in $(\lambda\mathcal I_n-A)x=\mathbf O$. This is the number of linearly independent eigenvectors for $\lambda$.
> - Always: $1\le$ geometric multiplicity $\le$ algebraic multiplicity. In the slide example ($\lambda=2$) both are 2. For $\begin{pmatrix}1&1\\0&1\end{pmatrix}$ they are 1 and 2.
> - A real **symmetric** matrix ($A^{\mathsf T}=A$) is the good case: all eigenvalues are real, both multiplicities are equal for every eigenvalue, and eigenvectors for two **different** eigenvalues are orthogonal (their dot product is 0).

> [!question]- Check (slide 3, triangular matrices): (a) $L$ has the rows $(5,0,0)$, $(2,-1,0)$ and $(7,3,5)$. Read off its eigenvalues. (b) A student reads the eigenvalues $0$ and $0$ off the diagonal of the matrix with the rows $(0,1)$ and $(1,0)$. Find the mistake and the correct eigenvalues.
> (a) All entries above the main diagonal are zero, so $L$ is lower triangular. The eigenvalues are the diagonal entries: $5$, $-1$, $5$. So $\lambda=5$ is a double root and $\lambda=-1$ a simple root.
> Reason: $\lambda\mathcal I_3-L$ is also triangular, with the diagonal $\lambda-5$, $\lambda+1$, $\lambda-5$. Its determinant is the product $(\lambda-5)^2(\lambda+1)$.
> (b) The matrix is not triangular: $a_{12}=1$ and $a_{21}=1$ are both nonzero. The shortcut does not apply.
> Correct: $\lambda\mathcal I_2-A=\begin{pmatrix}\lambda&-1\\-1&\lambda\end{pmatrix}$, $p_A(\lambda)=\lambda\cdot\lambda-(-1)(-1)=\lambda^2-1=(\lambda-1)(\lambda+1)$.
> Eigenvalues: $1$ and $-1$.

> [!question]- Check (slides 3-4): $A$ has the rows $(1,2)$ and $(3,-4)$, with the eigenvalues $2$ and $-5$. Find an eigenvector for each eigenvalue and check $Av=\lambda v$.
> $\lambda_1=2$: $2\mathcal I_2-A=\begin{pmatrix}2-1&-2\\-3&2+4\end{pmatrix}=\begin{pmatrix}1&-2\\-3&6\end{pmatrix}$.
> System: $x_1-2x_2=0$ and $-3x_1+6x_2=0$. The second equation is $-3$ times the first, so only one equation counts.
> $x_1=2x_2$. Take $x_2=1$: $x_1=2$. Eigenvector $v_1=\begin{pmatrix}2\\1\end{pmatrix}$.
> Check: $Av_1=\begin{pmatrix}1\cdot2+2\cdot1\\3\cdot2+(-4)\cdot1\end{pmatrix}=\begin{pmatrix}4\\2\end{pmatrix}=2\begin{pmatrix}2\\1\end{pmatrix}$.
> $\lambda_2=-5$: $-5\mathcal I_2-A=\begin{pmatrix}-5-1&-2\\-3&-5+4\end{pmatrix}=\begin{pmatrix}-6&-2\\-3&-1\end{pmatrix}$.
> System: $-6x_1-2x_2=0$ and $-3x_1-x_2=0$. The first equation is 2 times the second.
> $x_2=-3x_1$. Take $x_1=1$: $x_2=-3$. Eigenvector $v_2=\begin{pmatrix}1\\-3\end{pmatrix}$.
> Check: $Av_2=\begin{pmatrix}1\cdot1+2\cdot(-3)\\3\cdot1+(-4)\cdot(-3)\end{pmatrix}=\begin{pmatrix}-5\\15\end{pmatrix}=-5\begin{pmatrix}1\\-3\end{pmatrix}$.
> In both systems one equation is a multiple of the other. This must happen, because $\det(\lambda\mathcal I_2-A)=0$.

> [!question]- Check (slides 4-5, a double root with two eigenvectors; multiplicities and symmetry are beyond the slides): $A$ has the rows $(4,1,1)$, $(1,4,1)$ and $(1,1,4)$, with $p_A(\lambda)=(\lambda-3)^2(\lambda-6)$. Find the eigenvectors. Give both multiplicities of $\lambda=3$. What does the symmetry of $A$ predict?
> $\lambda=6$: $6\mathcal I_3-A=\begin{pmatrix}2&-1&-1\\-1&2&-1\\-1&-1&2\end{pmatrix}$.
> Equations: (1) $2x_1-x_2-x_3=0$, (2) $-x_1+2x_2-x_3=0$, (3) $-x_1-x_2+2x_3=0$.
> (1) minus (2): $3x_1-3x_2=0$, so $x_1=x_2$.
> Put this in (1): $2x_1-x_1-x_3=0$, so $x_3=x_1$.
> Equation (3): $-x_1-x_1+2x_1=0$. True, no new condition.
> Take $x_1=1$: eigenvector $\begin{pmatrix}1\\1\\1\end{pmatrix}$. Check: $A\begin{pmatrix}1\\1\\1\end{pmatrix}=\begin{pmatrix}4+1+1\\1+4+1\\1+1+4\end{pmatrix}=\begin{pmatrix}6\\6\\6\end{pmatrix}=6\begin{pmatrix}1\\1\\1\end{pmatrix}$.
> $\lambda=3$: $3\mathcal I_3-A=\begin{pmatrix}-1&-1&-1\\-1&-1&-1\\-1&-1&-1\end{pmatrix}$.
> All three equations are the same: $-x_1-x_2-x_3=0$, so $x_1=-x_2-x_3$. $x_2$ and $x_3$ are free variables.
> $x_2=1$, $x_3=0$: $x_1=-1$, eigenvector $\begin{pmatrix}-1\\1\\0\end{pmatrix}$.
> $x_2=0$, $x_3=1$: $x_1=-1$, eigenvector $\begin{pmatrix}-1\\0\\1\end{pmatrix}$.
> Check: $A\begin{pmatrix}-1\\1\\0\end{pmatrix}=\begin{pmatrix}-4+1+0\\-1+4+0\\-1+1+0\end{pmatrix}=\begin{pmatrix}-3\\3\\0\end{pmatrix}=3\begin{pmatrix}-1\\1\\0\end{pmatrix}$ and $A\begin{pmatrix}-1\\0\\1\end{pmatrix}=\begin{pmatrix}-4+0+1\\-1+0+1\\-1+0+4\end{pmatrix}=\begin{pmatrix}-3\\0\\3\end{pmatrix}=3\begin{pmatrix}-1\\0\\1\end{pmatrix}$.
> Multiplicities of $\lambda=3$: algebraic 2 (double root), geometric 2 (two free variables). They are equal.
> Symmetry ($A^{\mathsf T}=A$) predicts real eigenvalues, equal multiplicities, and orthogonal eigenvectors for different eigenvalues. Test: $(1,1,1)\cdot(-1,1,0)=-1+1+0=0$ and $(1,1,1)\cdot(-1,0,1)=-1+0+1=0$.
> The two eigenvectors for the same $\lambda=3$ need not be orthogonal: $(-1,1,0)\cdot(-1,0,1)=1$.

> [!question]- Check (slide 5, a double root with one eigenvector; the multiplicities are beyond the slides): $A$ has the rows $(3,1,0)$, $(0,3,0)$ and $(0,0,5)$. Find the eigenvalues and all eigenvectors. Compare with the slide example, where $\lambda=2$ gave two eigenvectors.
> $A$ is upper triangular, so the eigenvalues are the diagonal entries: $\lambda=3$ (double) and $\lambda=5$.
> $\lambda=3$: $3\mathcal I_3-A=\begin{pmatrix}0&-1&0\\0&0&0\\0&0&-2\end{pmatrix}$.
> Row 1: $-x_2=0$, so $x_2=0$. Row 3: $-2x_3=0$, so $x_3=0$. $x_1$ does not appear, so it is the only free variable.
> Take $x_1=1$: eigenvector $\begin{pmatrix}1\\0\\0\end{pmatrix}$. Check: $A\begin{pmatrix}1\\0\\0\end{pmatrix}=\begin{pmatrix}3\\0\\0\end{pmatrix}$.
> $\lambda=5$: $5\mathcal I_3-A=\begin{pmatrix}2&-1&0\\0&2&0\\0&0&0\end{pmatrix}$.
> Row 2: $2x_2=0$, so $x_2=0$. Row 1: $2x_1-x_2=0$, so $x_1=0$. $x_3$ is free.
> Take $x_3=1$: eigenvector $\begin{pmatrix}0\\0\\1\end{pmatrix}$. Check: $A\begin{pmatrix}0\\0\\1\end{pmatrix}=\begin{pmatrix}0\\0\\5\end{pmatrix}$.
> Comparison: here $\lambda=3$ is a double root (algebraic multiplicity 2) but gives only one free variable (geometric multiplicity 1). On the slide the double root $\lambda=2$ gave two free variables.
> This matrix has only 2 independent eigenvectors in total, fewer than $n=3$.

Section 6.3 starts at the bottom of slide 5.

## 3. Cayley-Hamilton theorem and linear independence of vectors (slides 5-7)
![[math501_lecture_06_math501_chapter_6_p006.jpg]]
![[math501_lecture_06_math501_chapter_6_p007.jpg]]

**Notes.** **Cayley-Hamilton.** Every square matrix satisfies its characteristic equation: $p_A(A)=O_{n\times n}$. Replace $\lambda^k$ by $A^k$ and the constant $c_0$ by $c_0\mathcal I_n$.

To get $A^{-1}$: move $c_0\mathcal I_n$ to the right and factor out $A$. This works when $c_0\neq0$, which is exactly when $A$ is invertible.

> [!example] Slide example
> $A=\begin{pmatrix}1&1&1\\1&0&1\\1&-1&0\end{pmatrix}$: $p_A=\lambda^3-\lambda^2-\lambda-1$, so $A^3-A^2-A-\mathcal I_3=O$ and $A(A^2-A-\mathcal I_3)=\mathcal I_3$.
> $$A^{-1}=A^2-A-\mathcal I_3=\begin{pmatrix}1&-1&1\\1&-1&0\\-1&2&-1\end{pmatrix}$$

**Linear independence of vectors.** $\vec v_1,\dots,\vec v_k$ are **linearly independent** if $\alpha_1\vec v_1+\dots+\alpha_k\vec v_k=\vec 0$ holds only for $\alpha_1=\dots=\alpha_k=0$. Otherwise they are dependent: one vector is a combination of the others.

- A set containing the zero vector is dependent.
- Two vectors are independent exactly when neither is a multiple of the other.

> [!example] Slide examples
> - $\begin{pmatrix}-2\\0\\3\end{pmatrix}$, $\begin{pmatrix}1\\1\\-1\end{pmatrix}$, $\begin{pmatrix}-1\\3\\4\end{pmatrix}$: the system gives $\alpha_2=-3\alpha_3$, $\alpha_1=-2\alpha_3$, then $\alpha_3=0$. Independent.
> - $\begin{pmatrix}3\\4\\4\end{pmatrix}$ and $\begin{pmatrix}2\\5\\1\end{pmatrix}$: $\tfrac32\neq\tfrac45$, not multiples. Independent.

> [!info] Determinant test for $n$ vectors in $\mathbb R^n$ (beyond the slides)
> Put the $n$ vectors as the columns of a square matrix $V$. Then $\alpha_1\vec v_1+\dots+\alpha_n\vec v_n=\vec 0$ is the system $V\alpha=\mathbf O$.
> - $\det(V)\neq0$: $V$ is invertible, so $\alpha=V^{-1}\mathbf O=\mathbf O$ is the only solution. The vectors are independent.
> - $\det(V)=0$: there is a nonzero solution. The vectors are dependent.
> - The test needs as many vectors as entries. For other cases solve the system as on slide 7.

> [!question]- Check (slides 5-6, inverse): $A$ has the rows $(1,0,2)$, $(0,1,1)$ and $(1,0,1)$. Find $A^{-1}$ with the Cayley-Hamilton theorem and check $AA^{-1}=\mathcal I_3$.
> $\lambda\mathcal I_3-A=\begin{pmatrix}\lambda-1&0&-2\\0&\lambda-1&-1\\-1&0&\lambda-1\end{pmatrix}$.
> Column 2 has two zeros. Expand along column 2: only the entry $\lambda-1$ in position $(2,2)$ counts, with the sign $(-1)^{2+2}=+1$.
> $p_A(\lambda)=(\lambda-1)\begin{vmatrix}\lambda-1&-2\\-1&\lambda-1\end{vmatrix}=(\lambda-1)\bigl[(\lambda-1)^2-(-2)(-1)\bigr]=(\lambda-1)(\lambda^2-2\lambda+1-2)=(\lambda-1)(\lambda^2-2\lambda-1)$.
> Multiply out: $\lambda^3-2\lambda^2-\lambda-\lambda^2+2\lambda+1=\lambda^3-3\lambda^2+\lambda+1$.
> Cayley-Hamilton: $A^3-3A^2+A+\mathcal I_3=O$.
> Move $\mathcal I_3$ to the right: $A^3-3A^2+A=-\mathcal I_3$. Factor out $A$: $A(A^2-3A+\mathcal I_3)=-\mathcal I_3$. Multiply by $-1$: $A(-A^2+3A-\mathcal I_3)=\mathcal I_3$.
> So $A^{-1}=-A^2+3A-\mathcal I_3$.
> $A^2$, row 1: $(1\cdot1+0+2\cdot1,\ 0+0+0,\ 1\cdot2+0\cdot1+2\cdot1)=(3,0,4)$.
> Row 2: $(0+0+1\cdot1,\ 0+1\cdot1+0,\ 0+1\cdot1+1\cdot1)=(1,1,2)$.
> Row 3: $(1\cdot1+0+1\cdot1,\ 0,\ 1\cdot2+0+1\cdot1)=(2,0,3)$.
> $A^{-1}=-\begin{pmatrix}3&0&4\\1&1&2\\2&0&3\end{pmatrix}+\begin{pmatrix}3&0&6\\0&3&3\\3&0&3\end{pmatrix}-\begin{pmatrix}1&0&0\\0&1&0\\0&0&1\end{pmatrix}=\begin{pmatrix}-3+3-1&0&-4+6\\-1+0&-1+3-1&-2+3\\-2+3&0&-3+3-1\end{pmatrix}=\begin{pmatrix}-1&0&2\\-1&1&1\\1&0&-1\end{pmatrix}$.
> Check, row 1 of $AA^{-1}$: $(1\cdot(-1)+0+2\cdot1,\ 0,\ 1\cdot2+0+2\cdot(-1))=(1,0,0)$.
> Row 2: $(0+1\cdot(-1)+1\cdot1,\ 1\cdot1,\ 0+1\cdot1+1\cdot(-1))=(0,1,0)$.
> Row 3: $(1\cdot(-1)+0+1\cdot1,\ 0,\ 1\cdot2+0+1\cdot(-1))=(0,0,1)$.
> So $AA^{-1}=\mathcal I_3$.

> [!question]- Check (slide 6, higher powers): $A$ has the rows $(1,2)$ and $(3,-4)$, with $p_A(\lambda)=\lambda^2+3\lambda-10$. Use the Cayley-Hamilton theorem to write $A^2$ and $A^3$ in the form $\alpha A+\beta\mathcal I_2$. Check $A^2$ by direct multiplication.
> Cayley-Hamilton: $A^2+3A-10\,\mathcal I_2=O$, so $A^2=-3A+10\,\mathcal I_2$.
> $-3A+10\,\mathcal I_2=\begin{pmatrix}-3+10&-6\\-9&12+10\end{pmatrix}=\begin{pmatrix}7&-6\\-9&22\end{pmatrix}$.
> Direct: $A^2=\begin{pmatrix}1\cdot1+2\cdot3&1\cdot2+2\cdot(-4)\\3\cdot1+(-4)\cdot3&3\cdot2+(-4)\cdot(-4)\end{pmatrix}=\begin{pmatrix}7&-6\\-9&22\end{pmatrix}$. The same.
> $A^3=A\cdot A^2=A(-3A+10\,\mathcal I_2)=-3A^2+10A$.
> Replace $A^2$ again: $-3(-3A+10\,\mathcal I_2)+10A=9A-30\,\mathcal I_2+10A=19A-30\,\mathcal I_2$.
> $A^3=\begin{pmatrix}19-30&38\\57&-76-30\end{pmatrix}=\begin{pmatrix}-11&38\\57&-106\end{pmatrix}$.
> Every power of a $2\times2$ matrix reduces in this way to a combination of $A$ and $\mathcal I_2$.

> [!question]- Check (slides 6-7, linear dependence): Are $\vec v_1=(1,2,3)$, $\vec v_2=(2,-1,1)$, $\vec v_3=(4,3,7)$ linearly independent? If not, write one vector as a combination of the others.
> Equation: $\alpha_1\vec v_1+\alpha_2\vec v_2+\alpha_3\vec v_3=\vec 0$. Entry by entry:
> (1) $\alpha_1+2\alpha_2+4\alpha_3=0$, (2) $2\alpha_1-\alpha_2+3\alpha_3=0$, (3) $3\alpha_1+\alpha_2+7\alpha_3=0$.
> (2) minus 2 times (1): $(2-2)\alpha_1+(-1-4)\alpha_2+(3-8)\alpha_3=0$, so $-5\alpha_2-5\alpha_3=0$ and $\alpha_2=-\alpha_3$.
> Put this in (1): $\alpha_1-2\alpha_3+4\alpha_3=0$, so $\alpha_1=-2\alpha_3$.
> Put both in (3): $3(-2\alpha_3)+(-\alpha_3)+7\alpha_3=-6\alpha_3-\alpha_3+7\alpha_3=0$. This is true for every $\alpha_3$.
> So $\alpha_3$ is free. Take $\alpha_3=1$: $\alpha_1=-2$, $\alpha_2=-1$. A nonzero solution exists, so the vectors are linearly dependent.
> The relation $-2\vec v_1-\vec v_2+\vec v_3=\vec 0$ gives $\vec v_3=2\vec v_1+\vec v_2$.
> Check: $2(1,2,3)+(2,-1,1)=(2+2,\ 4-1,\ 6+1)=(4,3,7)$.
> Compare with the slide example: there the third equation forced $\alpha_3=0$. Here it gives no condition.

> [!question]- Check (slide 7, the three quick rules): Decide without solving a system. (a) $(1,2)$ and $(0,0)$. (b) $(2,-6,4)$ and $(-3,9,-6)$. (c) $(1,2,3)$ and $(2,4,5)$.
> (a) The set contains the zero vector, so it is dependent (part a of the theorem). Indeed $0\cdot(1,2)+1\cdot(0,0)=(0,0)$ with a nonzero coefficient.
> (b) Two vectors: compare the ratios of the entries. $\dfrac{-3}{2}=-\dfrac32$, $\dfrac{9}{-6}=-\dfrac32$, $\dfrac{-6}{4}=-\dfrac32$. All equal, so $(-3,9,-6)=-\tfrac32(2,-6,4)$. Dependent.
> (c) $\dfrac21=2$, $\dfrac42=2$, but $\dfrac53\neq2$. Neither vector is a multiple of the other. Independent.
> In (c) the first two ratios agree. You must compare all entries before you decide.

> [!question]- Check (slide 7, determinant test, beyond the slides): For which $k$ are $\vec v_1=(1,0,2)$, $\vec v_2=(2,1,0)$, $\vec v_3=(0,1,k)$ linearly dependent? Use the determinant test of the info box above, then write $\vec v_3$ as a combination of the other two for that $k$.
> Columns $\vec v_1,\vec v_2,\vec v_3$: $V=\begin{pmatrix}1&2&0\\0&1&1\\2&0&k\end{pmatrix}$.
> Expand along row 1: $\det(V)=1\begin{vmatrix}1&1\\0&k\end{vmatrix}-2\begin{vmatrix}0&1\\2&k\end{vmatrix}+0=(k-0)-2\,(0-2)=k+4$.
> Dependent exactly when $\det(V)=0$: $k=-4$. For every other $k$ the vectors are independent.
> For $k=-4$ look for $a\vec v_1+b\vec v_2=\vec v_3=(0,1,-4)$:
> entry 2: $0\cdot a+1\cdot b=1$, so $b=1$. Entry 3: $2a+0=-4$, so $a=-2$. Entry 1: $a+2b=-2+2=0$. True.
> $\vec v_3=-2\vec v_1+\vec v_2$.

## 4. Diagonalization (slides 8-9)
![[math501_lecture_06_math501_chapter_6_p008.jpg]]
![[math501_lecture_06_math501_chapter_6_p009.jpg]]

**Notes.** $B$ is **similar** to $A$ if $B=P^{-1}AP$ for an invertible $P$. $A$ is **diagonalizable** if it is similar to a diagonal matrix.

**Theorem.** An $n\times n$ matrix is diagonalizable if and only if it has $n$ linearly independent eigenvectors.

Procedure:
1. Find $n$ independent eigenvectors $\mathbf p_1,\dots,\mathbf p_n$. If there are fewer, $A$ is not diagonalizable.
2. Put them as columns: $P=(\mathbf p_1\ \cdots\ \mathbf p_n)$.
3. Then $P^{-1}AP=\operatorname{diag}(\lambda_1,\dots,\lambda_n)$, with the eigenvalues in the same order as the columns.

> [!example] Slide example
> $A=\begin{pmatrix}2&-1\\-2&3\end{pmatrix}$: $p_A=\lambda^2-5\lambda+4=(\lambda-1)(\lambda-4)$.
> $\lambda=1$: $\begin{pmatrix}1\\1\end{pmatrix}$. $\lambda=4$: $2x_1+x_2=0$, $\begin{pmatrix}-1/2\\1\end{pmatrix}$.
> $P=\begin{pmatrix}1&-1/2\\1&1\end{pmatrix}$, $D=\begin{pmatrix}1&0\\0&4\end{pmatrix}$.

> [!warning] Watch out
> $n$ different eigenvalues always give a diagonalizable matrix. A repeated eigenvalue may or may not: count the independent eigenvectors.

> [!info] Why the procedure works, and what similar matrices share (beyond the slides)
> Let the columns of $P$ be eigenvectors: $A\mathbf p_i=\lambda_i\mathbf p_i$. Multiply column by column:
> $$AP=(A\mathbf p_1\ \cdots\ A\mathbf p_n)=(\lambda_1\mathbf p_1\ \cdots\ \lambda_n\mathbf p_n)=PD .$$
> If the columns are independent, $P$ is invertible, and $AP=PD$ gives $P^{-1}AP=D$ and $A=PDP^{-1}$. So you can check a diagonalization with $AP=PD$, without computing $P^{-1}$.
> Similar matrices have the same characteristic polynomial, so the same eigenvalues, trace and determinant. Reason, for $B=P^{-1}AP$: $\lambda\mathcal I-B=P^{-1}(\lambda\mathcal I-A)P$, and $\det(P^{-1})\det(P)=1$.

> [!question]- Check (slide 8, similar matrices): $A$ has the rows $(1,2)$ and $(0,3)$. $P$ has the rows $(1,1)$ and $(1,2)$. Compute $B=P^{-1}AP$. Compare the eigenvalues, the trace and the determinant of $A$ and $B$.
> $\det(P)=1\cdot2-1\cdot1=1$, so $P^{-1}=\dfrac11\begin{pmatrix}2&-1\\-1&1\end{pmatrix}=\begin{pmatrix}2&-1\\-1&1\end{pmatrix}$.
> $AP=\begin{pmatrix}1\cdot1+2\cdot1&1\cdot1+2\cdot2\\0\cdot1+3\cdot1&0\cdot1+3\cdot2\end{pmatrix}=\begin{pmatrix}3&5\\3&6\end{pmatrix}$.
> $B=P^{-1}(AP)=\begin{pmatrix}2\cdot3+(-1)\cdot3&2\cdot5+(-1)\cdot6\\(-1)\cdot3+1\cdot3&(-1)\cdot5+1\cdot6\end{pmatrix}=\begin{pmatrix}3&4\\0&1\end{pmatrix}$.
> $A$ is upper triangular: eigenvalues $1$ and $3$. $B$ is upper triangular: eigenvalues $3$ and $1$. The same.
> Trace: $1+3=4$ and $3+1=4$. Determinant: $1\cdot3-2\cdot0=3$ and $3\cdot1-4\cdot0=3$.
> $B$ is similar to $A$ but it is not diagonal. $P$ diagonalizes $A$ only if its columns are eigenvectors of $A$. Here the column $(1,1)$ is one, since $A(1,1)^{\mathsf T}=(3,3)^{\mathsf T}$, but $(1,2)$ is not: $A(1,2)^{\mathsf T}=(5,6)^{\mathsf T}$.

> [!question]- Check (slides 8-9): $A$ has the rows $(5,-2)$ and $(4,-1)$. Find $P$ and $D$ with $P^{-1}AP=D$ and verify the product. What changes if you swap the two columns of $P$?
> Eigenvalues: $\det(\lambda\mathcal I_2-A)=\begin{vmatrix}\lambda-5&2\\-4&\lambda+1\end{vmatrix}=(\lambda-5)(\lambda+1)-2\cdot(-4)=\lambda^2-4\lambda-5+8=\lambda^2-4\lambda+3=(\lambda-1)(\lambda-3)$.
> $\lambda_1=1$, $\lambda_2=3$.
> $\lambda_1=1$: $\mathcal I_2-A=\begin{pmatrix}-4&2\\-4&2\end{pmatrix}$. Equation: $-4x_1+2x_2=0$, so $x_2=2x_1$. Take $x_1=1$: $\mathbf p_1=\begin{pmatrix}1\\2\end{pmatrix}$.
> $\lambda_2=3$: $3\mathcal I_2-A=\begin{pmatrix}-2&2\\-4&4\end{pmatrix}$. Equation: $-2x_1+2x_2=0$, so $x_1=x_2$. Take $x_2=1$: $\mathbf p_2=\begin{pmatrix}1\\1\end{pmatrix}$.
> The two eigenvectors are not multiples of each other, so there are $n=2$ independent eigenvectors and $A$ is diagonalizable.
> $P=\begin{pmatrix}1&1\\2&1\end{pmatrix}$, $D=\begin{pmatrix}1&0\\0&3\end{pmatrix}$.
> Verify: $\det(P)=1\cdot1-1\cdot2=-1$, $P^{-1}=\dfrac{1}{-1}\begin{pmatrix}1&-1\\-2&1\end{pmatrix}=\begin{pmatrix}-1&1\\2&-1\end{pmatrix}$.
> $AP=\begin{pmatrix}5\cdot1+(-2)\cdot2&5\cdot1+(-2)\cdot1\\4\cdot1+(-1)\cdot2&4\cdot1+(-1)\cdot1\end{pmatrix}=\begin{pmatrix}1&3\\2&3\end{pmatrix}$.
> $P^{-1}AP=\begin{pmatrix}(-1)\cdot1+1\cdot2&(-1)\cdot3+1\cdot3\\2\cdot1+(-1)\cdot2&2\cdot3+(-1)\cdot3\end{pmatrix}=\begin{pmatrix}1&0\\0&3\end{pmatrix}=D$.
> Swapped columns: $P=\begin{pmatrix}1&1\\1&2\end{pmatrix}$ gives $D=\begin{pmatrix}3&0\\0&1\end{pmatrix}$. The order of the eigenvalues in $D$ follows the order of the columns in $P$.

> [!question]- Check (slide 8, a 3 by 3 matrix): $A$ has the rows $(4,1,1)$, $(1,4,1)$ and $(1,1,4)$. Its eigenvectors are $(1,1,1)$ for $\lambda=6$, and $(-1,1,0)$ and $(-1,0,1)$ for $\lambda=3$. Is $A$ diagonalizable? Give $P$ and $D$ and verify with $AP=PD$.
> Take the eigenvectors as columns: $P=\begin{pmatrix}1&-1&-1\\1&1&0\\1&0&1\end{pmatrix}$.
> Are the three columns independent? Use the determinant test (info box in section 3, beyond the slides). Expand $\det(P)$ along row 1:
> $\det(P)=1\begin{vmatrix}1&0\\0&1\end{vmatrix}-(-1)\begin{vmatrix}1&0\\1&1\end{vmatrix}+(-1)\begin{vmatrix}1&1\\1&0\end{vmatrix}=1\cdot1+1\cdot1-1\cdot(0-1)=1+1+1=3\neq0$.
> So $A$ has 3 independent eigenvectors and is diagonalizable, although the eigenvalue 3 is repeated.
> $D=\operatorname{diag}(6,3,3)$, in the order of the columns.
> $AP$, column by column: $A(1,1,1)^{\mathsf T}=(6,6,6)^{\mathsf T}$, $A(-1,1,0)^{\mathsf T}=(-4+1,\,-1+4,\,-1+1)^{\mathsf T}=(-3,3,0)^{\mathsf T}$, $A(-1,0,1)^{\mathsf T}=(-4+1,\,-1+1,\,-1+4)^{\mathsf T}=(-3,0,3)^{\mathsf T}$.
> $AP=\begin{pmatrix}6&-3&-3\\6&3&0\\6&0&3\end{pmatrix}$.
> $PD$ multiplies column 1 of $P$ by 6 and columns 2 and 3 by 3: $PD=\begin{pmatrix}6&-3&-3\\6&3&0\\6&0&3\end{pmatrix}$.
> $AP=PD$, so $P^{-1}AP=D$.

## 5. Powers of a diagonalizable matrix (slides 10-11)
![[math501_lecture_06_math501_chapter_6_p010.jpg]]
![[math501_lecture_06_math501_chapter_6_p011.jpg]]

**Notes.** If $D=P^{-1}AP$ is diagonal, then

$$A^k=PD^kP^{-1},\qquad D^k=\operatorname{diag}(\lambda_1^k,\dots,\lambda_n^k).$$

If $\lambda$ is an eigenvalue of $A$ with eigenvector $v$, then $\lambda^k$ is an eigenvalue of $A^k$ with the same $v$.

> [!example] Slide examples
> - $D=\operatorname{diag}(-3,2,-1)$: $D^5=\operatorname{diag}(-243,32,-1)$.
> - $A=\begin{pmatrix}1&0\\-1&2\end{pmatrix}$ (lower triangular, eigenvalues 1 and 2): eigenvectors $\begin{pmatrix}1\\1\end{pmatrix}$ and $\begin{pmatrix}0\\1\end{pmatrix}$, $P=\begin{pmatrix}1&0\\1&1\end{pmatrix}$, $P^{-1}=\begin{pmatrix}1&0\\-1&1\end{pmatrix}$.
>   $$A^{10}=P\begin{pmatrix}1&0\\0&2^{10}\end{pmatrix}P^{-1}=\begin{pmatrix}1&0\\-1023&1024\end{pmatrix}$$
>   Eigenvalues of $A^{10}$: $1$ and $1024$.

> [!warning] Watch out
> $A^k=PD^kP^{-1}$, not $P^{-1}D^kP$. Check with $k=1$.

> [!question]- Check (slide 10): (a) $D=\operatorname{diag}(2,-1,\tfrac12)$. Find $D^4$. (b) Show why $D^2=P^{-1}A^2P$ when $D=P^{-1}AP$. (c) $A$ has the eigenvalue $-2$ with eigenvector $v$. What is $A^5v$?
> (a) Raise each diagonal entry to the power 4: $2^4=16$, $(-1)^4=1$, $\left(\tfrac12\right)^4=\tfrac1{16}$. $D^4=\operatorname{diag}(16,1,\tfrac1{16})$.
> (b) $D^2=(P^{-1}AP)(P^{-1}AP)=P^{-1}A(PP^{-1})AP=P^{-1}A\,\mathcal I_n\,AP=P^{-1}A^2P$. The inner pair $PP^{-1}$ cancels. With $k$ factors all inner pairs cancel, so $D^k=P^{-1}A^kP$.
> Multiply by $P$ on the left and by $P^{-1}$ on the right: $PD^kP^{-1}=A^k$.
> (c) Apply $Av=-2v$ five times. $A^2v=A(Av)=A(-2v)=-2(Av)=(-2)^2v$, and so on.
> $A^5v=(-2)^5v=-32\,v$. So $-32$ is an eigenvalue of $A^5$ with the same eigenvector $v$.

> [!question]- Check (slides 10-11): $A$ has the rows $(5,-2)$ and $(4,-1)$. From the check for slides 8-9: $P$ has the rows $(1,1)$ and $(2,1)$, $D=\operatorname{diag}(1,3)$, and $P^{-1}$ has the rows $(-1,1)$ and $(2,-1)$. Compute $A^5$ and a formula for $A^k$. Give the eigenvalues of $A^5$.
> $A^5=PD^5P^{-1}$ with $D^5=\begin{pmatrix}1^5&0\\0&3^5\end{pmatrix}=\begin{pmatrix}1&0\\0&243\end{pmatrix}$.
> Step 1: $PD^5=\begin{pmatrix}1\cdot1+1\cdot0&1\cdot0+1\cdot243\\2\cdot1+1\cdot0&2\cdot0+1\cdot243\end{pmatrix}=\begin{pmatrix}1&243\\2&243\end{pmatrix}$.
> Step 2: $A^5=\begin{pmatrix}1&243\\2&243\end{pmatrix}\begin{pmatrix}-1&1\\2&-1\end{pmatrix}=\begin{pmatrix}-1+486&1-243\\-2+486&2-243\end{pmatrix}=\begin{pmatrix}485&-242\\484&-241\end{pmatrix}$.
> General $k$: $PD^k=\begin{pmatrix}1&3^k\\2&3^k\end{pmatrix}$ and
> $A^k=\begin{pmatrix}1&3^k\\2&3^k\end{pmatrix}\begin{pmatrix}-1&1\\2&-1\end{pmatrix}=\begin{pmatrix}2\cdot3^k-1&1-3^k\\2\cdot3^k-2&2-3^k\end{pmatrix}$.
> Check with $k=1$: $\begin{pmatrix}6-1&1-3\\6-2&2-3\end{pmatrix}=\begin{pmatrix}5&-2\\4&-1\end{pmatrix}=A$.
> Check with $k=5$: $2\cdot243-1=485$, $1-243=-242$, $2\cdot243-2=484$, $2-243=-241$.
> Eigenvalues of $A^5$: $1^5=1$ and $3^5=243$. Trace check (beyond the slides): $485+(-241)=244=1+243$.

## Key formulas and terms
| Term | Meaning / formula |
|---|---|
| Eigenvalue, eigenvector | $Av=\lambda v$, $v\neq\mathbf 0$ |
| Characteristic polynomial | $p_A(\lambda)=\det(\lambda\mathcal I_n-A)$ |
| Eigenvectors for $\lambda$ | Nonzero solutions of $(\lambda\mathcal I_n-A)x=\mathbf O$ |
| Triangular matrix | Eigenvalues are the diagonal entries |
| Cayley-Hamilton | $p_A(A)=O_{n\times n}$ |
| Linearly independent | $\sum\alpha_i\vec v_i=\vec 0$ only for all $\alpha_i=0$ |
| Similar matrices | $B=P^{-1}AP$ |
| Diagonalizable | $n$ independent eigenvectors, $P^{-1}AP=D$ |
| Powers | $A^k=PD^kP^{-1}$ |

## Check yourself
> [!question]- 1. $B$ has the rows $(1,4)$ and $(1,1)$. Find the eigenvalues of $B$.
> $p_B=(\lambda-1)^2-4=\lambda^2-2\lambda-3=(\lambda-3)(\lambda+1)$.
> Eigenvalues $3$ and $-1$.

> [!question]- 2. $A$ has the rows $(4,1)$ and $(2,3)$. Find the eigenvalues and eigenvectors of $A$.
> $p_A=\lambda^2-7\lambda+10=(\lambda-5)(\lambda-2)$.
> $\lambda=5$: $x_1-x_2=0$, $\begin{pmatrix}1\\1\end{pmatrix}$. $\lambda=2$: $2x_1+x_2=0$, $\begin{pmatrix}1\\-2\end{pmatrix}$.

> [!question]- 3. $A$ has the rows $(2,1)$ and $(1,1)$. Use Cayley-Hamilton to find the inverse of $A$.
> $p_A=\lambda^2-3\lambda+1$, so $A^2-3A+\mathcal I_2=O$ and $A(3\mathcal I_2-A)=\mathcal I_2$.
> $A^{-1}=3\mathcal I_2-A=\begin{pmatrix}1&-1\\-1&2\end{pmatrix}$.

> [!question]- 4. Are $(4,0,1,-2)$, $(-3,4,0,3)$, $(-5,12,1,7)$ linearly independent?
> Row reducing the matrix with these columns gives $\alpha_1+\alpha_3=0$, $\alpha_2+3\alpha_3=0$, with $\alpha_3$ free.
> Dependent: $v_3=v_1+3v_2$.

> [!question]- 5. $A$ has the rows $(1,1)$ and $(0,1)$. Is $A$ diagonalizable?
> $\lambda=1$ twice. $\mathcal I_2-A=\begin{pmatrix}0&-1\\0&0\end{pmatrix}$ gives $x_2=0$: every eigenvector is a multiple of $\begin{pmatrix}1\\0\end{pmatrix}$.
> Only one independent eigenvector, so not diagonalizable.

> [!question]- 6. $A$ has the rows $(2,-1)$ and $(-2,3)$. $P$ has the rows $(1,-1)$ and $(1,2)$, and $D=\operatorname{diag}(1,4)$. Find $A^3$.
> $P^{-1}=\tfrac13\begin{pmatrix}2&1\\-1&1\end{pmatrix}$, $D^3=\operatorname{diag}(1,64)$.
> $A^3=PD^3P^{-1}=\begin{pmatrix}22&-21\\-42&43\end{pmatrix}$. Eigenvalues of $A^3$: $1$ and $64$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L05 - Matrices and determinants]]. Next: [[MATH501 L07 - Linear systems of ODEs]]
- Full step-by-step notes (PDF): [MATH501_Lecture_06_Eigenvalues_Eigenvectors.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_06/MATH501_Lecture_06_Eigenvalues_Eigenvectors.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_06/MATH501_Lecture_06_Eigenvalues_Eigenvectors.pdf`
- Original chapter notes (PDF): [Math501 Chapter 6.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_06/Math501%20Chapter%206.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_06/Math501 Chapter 6.pdf`

Slides not embedded: none.
