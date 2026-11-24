---
course: MATH 501 Advanced Engineering Mathematics
lecture: 5
title: Matrices and determinants
tags: [math501, lecture]
slides: lectures/lecture_05/Math501 Chapter 5.pdf
full_notes: lecture_notes/lecture_05/MATH501_Lecture_05_Matrices_Determinants.pdf
---
# MATH 501 · Lecture 5 · Matrices and determinants

> [!summary] In short
> - Add and scale matrices entry by entry. Multiply row by column. The inner sizes must match, and $AB\neq BA$ in general.
> - The transpose turns rows into columns, and $(AB)^{\mathsf T}=B^{\mathsf T}A^{\mathsf T}$.
> - $\det\begin{pmatrix}a&b\\c&d\end{pmatrix}=ad-bc$. A matrix is invertible exactly when its determinant is not zero.
> - Larger determinants: cofactor expansion along any row or column, or row reduction to triangular form.
> - Row swap: sign flips. Factor pulled out of a row: multiplies. Adding a multiple of a row: no change.

The slide numbers below are the pages of the Chapter 5 PDF (page 1 is printed page 80).

## 1. Matrices and their operations (slides 1-3)
![[math501_lecture_05_math501_chapter_5_p001.jpg]]
![[math501_lecture_05_math501_chapter_5_p002.jpg]]

**Notes.** An $n\times m$ matrix has $n$ rows and $m$ columns. $A=[a_{ij}]$ means the entry in row $i$, column $j$ is $a_{ij}$. Two matrices are equal when they have the same size and the same entries.

- Addition (same size): $A+B=[a_{ij}+b_{ij}]$. Scalar multiple: $cA=[ca_{ij}]$.
- Product: if $A$ is $n\times k$ and $B$ is $k\times m$, then $AB$ is $n\times m$ with

$$c_{ij}=\sum_{r=1}^{k}a_{ir}b_{rj}\qquad\text{(row $i$ of $A$ times column $j$ of $B$).}$$

Properties: $A+B=B+A$, $A(B+C)=AB+AC$, $(A+B)C=AC+BC$, $(AB)C=A(BC)$, $c(AB)=(cA)B=A(cB)$.

> [!example] Slide examples
> - $A=\begin{pmatrix}2&8&-4\\5&-1&0\end{pmatrix}$, $B=\begin{pmatrix}-3&-5&1\\4&2&2\end{pmatrix}$: $2A+B=\begin{pmatrix}1&11&-7\\14&0&2\end{pmatrix}$, $4B-2A=\begin{pmatrix}-16&-36&12\\6&10&8\end{pmatrix}$.
> - $A=\begin{pmatrix}-2&3\\1&1\end{pmatrix}$, $B=\begin{pmatrix}0&8\\-5&1\end{pmatrix}$: $A^2=\begin{pmatrix}7&-3\\-1&4\end{pmatrix}$, $AB=\begin{pmatrix}-15&-13\\-5&9\end{pmatrix}$, $A^2+2AB=\begin{pmatrix}-23&-29\\-11&22\end{pmatrix}$.
> - $(2\times3)(3\times2)$ product at the top of slide 3: $\begin{pmatrix}3&5&-1\\0&1&4\end{pmatrix}\begin{pmatrix}1&-3\\4&2\\-6&1\end{pmatrix}=\begin{pmatrix}29&0\\-20&6\end{pmatrix}$.

> [!warning] Watch out
> - $AB$ is defined only when the number of columns of $A$ equals the number of rows of $B$.
> - $A^2$ means $AA$, not "square every entry".

## 2. Special matrices, transpose, symmetric matrices (slides 3-4)
![[math501_lecture_05_math501_chapter_5_p003.jpg]]
![[math501_lecture_05_math501_chapter_5_p004.jpg]]

**Notes.**
- **Zero matrix** $O_{n\times m}$: all entries zero. **Square**: as many rows as columns.
- **Identity** $\mathcal I_n$: ones on the main diagonal, zeros elsewhere.
- **Diagonal**: $a_{ij}=0$ for $i\neq j$, written $\operatorname{diag}(d_1,\dots,d_n)$.
- **Upper triangular**: zeros below the diagonal ($a_{ij}=0$ for $i>j$). **Lower triangular**: zeros above it.
- **Transpose** $A^{\mathsf T}=[a_{ji}]$: rows become columns.

$$(A^{\mathsf T})^{\mathsf T}=A,\qquad(AB)^{\mathsf T}=B^{\mathsf T}A^{\mathsf T},\qquad\mathcal I_n^{\mathsf T}=\mathcal I_n .$$

- **Symmetric**: $A^{\mathsf T}=A$. **Skew-symmetric**: $A^{\mathsf T}=-A$. Both must be square. A skew-symmetric matrix has a zero diagonal.

> [!warning] Watch out
> In $(AB)^{\mathsf T}=B^{\mathsf T}A^{\mathsf T}$ the order reverses. Every diagonal matrix is triangular, but not the other way round.

## 3. Determinant of a 2 by 2 matrix, minors, cofactors (slide 5)
![[math501_lecture_05_math501_chapter_5_p005.jpg]]

**Notes.** For $A=\begin{pmatrix}a&b\\c&d\end{pmatrix}$: $\det(A)=|A|=ad-bc$. $A$ is **nonsingular** (invertible) if and only if $\det(A)\neq0$, and then

$$A^{-1}=\frac{1}{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}.$$

For an $n\times n$ matrix, the **minor** $M_{ij}$ is the determinant left after deleting row $i$ and column $j$. The **cofactor** of $a_{ij}$ is $(-1)^{i+j}M_{ij}$ (checkerboard signs, $+$ in the top left corner).

> [!example] Slide examples
> - $A=\begin{pmatrix}2&3\\-1&4\end{pmatrix}$: $\det A=8+3=11$, $A^{-1}=\dfrac{1}{11}\begin{pmatrix}4&-3\\1&2\end{pmatrix}$.
> - $A=\begin{pmatrix}3&1&-4\\2&5&6\\-1&4&8\end{pmatrix}$: $M_{11}=5\cdot8-6\cdot4=16$, $M_{32}=3\cdot6-(-4)\cdot2=26$. Cofactors: $+16$ and $-26$.

> [!warning] Watch out
> Bars around a matrix mean the determinant, one number that can be negative. It is not an absolute value.

## 4. Cofactor expansion, zero rows, triangular matrices (slides 6-7)
![[math501_lecture_05_math501_chapter_5_p006.jpg]]
![[math501_lecture_05_math501_chapter_5_p007.jpg]]

**Notes.** Expansion along row $k$ (the same formula works along any column):

$$\det(A)=\sum_{j=1}^{n}(-1)^{k+j}a_{kj}M_{kj}.$$

Every row and every column gives the same number. Choose the row or column with the most zeros.

- A zero row or zero column gives $\det(A)=0$.
- Triangular matrix (upper, lower or diagonal): $\det(A)=a_{11}a_{22}\cdots a_{nn}$.

> [!example] Slide examples
> - $3\times3$ matrix of section 3, first row: $3\cdot16-1\cdot22+(-4)\cdot13=-26$. Second column: $-1\cdot22+5\cdot20-4\cdot26=-26$.
> - $4\times4$ matrix $\begin{pmatrix}1&0&0&-1\\3&1&2&2\\1&0&-2&1\\2&0&0&1\end{pmatrix}$, first row: $\det=M_{11}+M_{14}=-2+(-4)=-6$.
> - $\begin{vmatrix}8&3&-3\\0&2&4\\0&0&-1\end{vmatrix}=8\cdot2\cdot(-1)=-16$.

> [!warning] Watch out
> A zero row forces $\det=0$, but $\det=0$ does not need a zero row: $\begin{vmatrix}1&2\\2&4\end{vmatrix}=0$.

## 5. Transpose and row operations (slides 8-9)
![[math501_lecture_05_math501_chapter_5_p008.jpg]]
![[math501_lecture_05_math501_chapter_5_p009.jpg]]

**Notes.** $\det(A)=\det(A^{\mathsf T})$, so every rule for rows also holds for columns.

| Operation | Effect on the determinant |
|---|---|
| Interchange two rows (or columns) | multiplied by $-1$ |
| Multiply one row (or column) by $k$ | multiplied by $k$ |
| Add $c$ times one row to another row | no change |

Two proportional rows or columns give $\det(A)=0$.

Row reduction: bring the matrix to upper triangular form, track the swaps and the factors pulled out, then multiply the diagonal.

> [!example] Slide examples
> - $A=\begin{pmatrix}-1&0&1\\2&3&0\\0&1&4\end{pmatrix}$: $\det A=-12+2=-10$ and $\det A^{\mathsf T}=-12-2\cdot(-1)=-10$.
> - $\begin{pmatrix}2&-1&4\\1&8&0\\6&-3&12\end{pmatrix}$: row 3 is 3 times row 1, $\det=0$.
> - $A=\begin{pmatrix}0&1&5\\3&-6&9\\2&6&1\end{pmatrix}$: swap rows 1 and 2 (factor $-1$), pull 3 out of row 1, $R_3-2R_1$, $R_3-10R_2$. $\det A=(-3)\cdot1\cdot1\cdot(-55)=165$.

> [!warning] Watch out
> Scaling one row by $k$ multiplies the determinant by $k$. Scaling the whole $n\times n$ matrix gives $\det(kA)=k^n\det(A)$.

## Key formulas and terms
| Term | Meaning / formula |
|---|---|
| Product $AB$ | $c_{ij}=\sum_r a_{ir}b_{rj}$, needs columns of $A$ = rows of $B$ |
| Transpose | $A^{\mathsf T}=[a_{ji}]$, $(AB)^{\mathsf T}=B^{\mathsf T}A^{\mathsf T}$ |
| Symmetric, skew-symmetric | $A^{\mathsf T}=A$, $A^{\mathsf T}=-A$ |
| $2\times2$ determinant | $ad-bc$ |
| $2\times2$ inverse | $\dfrac{1}{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$ |
| Minor $M_{ij}$ | Determinant after deleting row $i$ and column $j$ |
| Cofactor | $(-1)^{i+j}M_{ij}$ |
| Cofactor expansion | $\det A=\sum_j(-1)^{k+j}a_{kj}M_{kj}$ |
| Triangular matrix | $\det A$ = product of the diagonal entries |
| $\det(kA)$ | $k^n\det(A)$ for $n\times n$ |

## Check yourself
> [!question]- 1. $A=\begin{pmatrix}1&2\\0&1\end{pmatrix}$, $B=\begin{pmatrix}0&1\\1&0\end{pmatrix}$. Is $AB=BA$?
> $AB=\begin{pmatrix}2&1\\1&0\end{pmatrix}$, $BA=\begin{pmatrix}0&1\\1&2\end{pmatrix}$. Not equal.

> [!question]- 2. Classify $\begin{pmatrix}0&2\\-2&0\end{pmatrix}$, $\begin{pmatrix}1&4\\4&0\end{pmatrix}$, $\begin{pmatrix}1&2\\3&1\end{pmatrix}$.
> First: skew-symmetric ($a_{21}=-a_{12}$, zero diagonal). Second: symmetric. Third: neither.

> [!question]- 3. Find the inverse of $\begin{pmatrix}3&1\\5&2\end{pmatrix}$. Is $\begin{pmatrix}2&4\\1&2\end{pmatrix}$ invertible?
> $\det=6-5=1$, inverse $\begin{pmatrix}2&-1\\-5&3\end{pmatrix}$.
> Second matrix: $\det=4-4=0$, not invertible.

> [!question]- 4. Compute $\begin{vmatrix}2&0&1\\1&3&0\\0&1&4\end{vmatrix}$ along the first row.
> $2\,(12-0)-0+1\,(1-0)=25$.

> [!question]- 5. Why is $\begin{vmatrix}1&2&3\\4&5&6\\2&4&6\end{vmatrix}=0$?
> Row 3 is 2 times row 1. Proportional rows give determinant 0.

> [!question]- 6. Compute $\begin{vmatrix}1&2&3\\2&5&7\\1&3&5\end{vmatrix}$ by row reduction.
> $R_2-2R_1=(0,1,1)$, $R_3-R_1=(0,1,2)$, then $R_3-R_2=(0,0,1)$. No swaps, no factors.
> $\det=1\cdot1\cdot1=1$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L04 - Series solutions of ODEs]]. Next: [[MATH501 L06 - Eigenvalues and eigenvectors]]
- Full step-by-step notes (PDF): [MATH501_Lecture_05_Matrices_Determinants.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_05/MATH501_Lecture_05_Matrices_Determinants.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_05/MATH501_Lecture_05_Matrices_Determinants.pdf`
- Original chapter notes (PDF): [Math501 Chapter 5.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_05/Math501%20Chapter%205.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_05/Math501 Chapter 5.pdf`

Slides not embedded: none.
