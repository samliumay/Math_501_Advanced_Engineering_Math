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
> [!question]- 1. Find the eigenvalues of $B=\begin{pmatrix}1&4\\1&1\end{pmatrix}$.
> $p_B=(\lambda-1)^2-4=\lambda^2-2\lambda-3=(\lambda-3)(\lambda+1)$.
> Eigenvalues $3$ and $-1$.

> [!question]- 2. Find the eigenvalues and eigenvectors of $A=\begin{pmatrix}4&1\\2&3\end{pmatrix}$.
> $p_A=\lambda^2-7\lambda+10=(\lambda-5)(\lambda-2)$.
> $\lambda=5$: $x_1-x_2=0$, $\begin{pmatrix}1\\1\end{pmatrix}$. $\lambda=2$: $2x_1+x_2=0$, $\begin{pmatrix}1\\-2\end{pmatrix}$.

> [!question]- 3. Use Cayley-Hamilton to find the inverse of $A=\begin{pmatrix}2&1\\1&1\end{pmatrix}$.
> $p_A=\lambda^2-3\lambda+1$, so $A^2-3A+\mathcal I_2=O$ and $A(3\mathcal I_2-A)=\mathcal I_2$.
> $A^{-1}=3\mathcal I_2-A=\begin{pmatrix}1&-1\\-1&2\end{pmatrix}$.

> [!question]- 4. Are $(4,0,1,-2)$, $(-3,4,0,3)$, $(-5,12,1,7)$ linearly independent?
> Row reducing the matrix with these columns gives $\alpha_1+\alpha_3=0$, $\alpha_2+3\alpha_3=0$, with $\alpha_3$ free.
> Dependent: $v_3=v_1+3v_2$.

> [!question]- 5. Is $A=\begin{pmatrix}1&1\\0&1\end{pmatrix}$ diagonalizable?
> $\lambda=1$ twice. $\mathcal I_2-A=\begin{pmatrix}0&-1\\0&0\end{pmatrix}$ gives $x_2=0$: every eigenvector is a multiple of $\begin{pmatrix}1\\0\end{pmatrix}$.
> Only one independent eigenvector, so not diagonalizable.

> [!question]- 6. For $A=\begin{pmatrix}2&-1\\-2&3\end{pmatrix}$ with $P=\begin{pmatrix}1&-1\\1&2\end{pmatrix}$, $D=\operatorname{diag}(1,4)$, find $A^3$.
> $P^{-1}=\tfrac13\begin{pmatrix}2&1\\-1&1\end{pmatrix}$, $D^3=\operatorname{diag}(1,64)$.
> $A^3=PD^3P^{-1}=\begin{pmatrix}22&-21\\-42&43\end{pmatrix}$. Eigenvalues of $A^3$: $1$ and $64$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L05 - Matrices and determinants]]. Next: [[MATH501 L07 - Linear systems of ODEs]]
- Full step-by-step notes (PDF): [MATH501_Lecture_06_Eigenvalues_Eigenvectors.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_06/MATH501_Lecture_06_Eigenvalues_Eigenvectors.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_06/MATH501_Lecture_06_Eigenvalues_Eigenvectors.pdf`
- Original chapter notes (PDF): [Math501 Chapter 6.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_06/Math501%20Chapter%206.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_06/Math501 Chapter 6.pdf`

Slides not embedded: none.
