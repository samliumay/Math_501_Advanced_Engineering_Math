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

> [!question]- Check (slide 1): $A$ has the rows $(4,-1,7)$ and $(0,3,-2)$. Give its size and the entries $a_{12}$, $a_{21}$, $a_{23}$. Then find $x$ and $y$ so that the matrix with the rows $(x+1,\,2)$ and $(3,\,2y)$ equals the matrix with the rows $(5,2)$ and $(3,-8)$.
> Size: $A$ has 2 rows and 3 columns, so it is a $2\times3$ matrix.
> $a_{12}$ is row 1, column 2: $a_{12}=-1$.
> $a_{21}$ is row 2, column 1: $a_{21}=0$.
> $a_{23}$ is row 2, column 3: $a_{23}=-2$.
> Equality: both matrices are $2\times2$, so compare entry by entry.
> Position $(1,1)$: $x+1=5$, so $x=5-1=4$.
> Position $(1,2)$: $2=2$, true.
> Position $(2,1)$: $3=3$, true.
> Position $(2,2)$: $2y=-8$, so $y=-8/2=-4$.
> Result: $x=4$, $y=-4$.

> [!question]- Check (slide 2, sums and scalar multiples): $A$ has the rows $(1,-2,3)$ and $(0,4,-1)$. $B$ has the rows $(2,5,-3)$ and $(-1,0,6)$. Compute $3A-2B$.
> Step 1, multiply every entry of $A$ by 3:
> $3A=\begin{pmatrix}3\cdot1&3\cdot(-2)&3\cdot3\\3\cdot0&3\cdot4&3\cdot(-1)\end{pmatrix}=\begin{pmatrix}3&-6&9\\0&12&-3\end{pmatrix}$.
> Step 2, multiply every entry of $B$ by 2:
> $2B=\begin{pmatrix}2\cdot2&2\cdot5&2\cdot(-3)\\2\cdot(-1)&2\cdot0&2\cdot6\end{pmatrix}=\begin{pmatrix}4&10&-6\\-2&0&12\end{pmatrix}$.
> Step 3, subtract entry by entry:
> $3A-2B=\begin{pmatrix}3-4&-6-10&9-(-6)\\0-(-2)&12-0&-3-12\end{pmatrix}=\begin{pmatrix}-1&-16&15\\2&12&-15\end{pmatrix}$.

> [!question]- Check (slide 2, product and order): $A$ has the rows $(1,2)$ and $(3,-1)$. $B$ has the rows $(2,0)$ and $(1,4)$. A student writes $(A+B)^2=A^2+2AB+B^2$. Compute both sides and find the mistake.
> $AB=\begin{pmatrix}1\cdot2+2\cdot1&1\cdot0+2\cdot4\\3\cdot2+(-1)\cdot1&3\cdot0+(-1)\cdot4\end{pmatrix}=\begin{pmatrix}4&8\\5&-4\end{pmatrix}$.
> $BA=\begin{pmatrix}2\cdot1+0\cdot3&2\cdot2+0\cdot(-1)\\1\cdot1+4\cdot3&1\cdot2+4\cdot(-1)\end{pmatrix}=\begin{pmatrix}2&4\\13&-2\end{pmatrix}$. So $AB\neq BA$.
> $A^2=\begin{pmatrix}1\cdot1+2\cdot3&1\cdot2+2\cdot(-1)\\3\cdot1+(-1)\cdot3&3\cdot2+(-1)\cdot(-1)\end{pmatrix}=\begin{pmatrix}7&0\\0&7\end{pmatrix}$.
> $B^2=\begin{pmatrix}2\cdot2+0\cdot1&2\cdot0+0\cdot4\\1\cdot2+4\cdot1&1\cdot0+4\cdot4\end{pmatrix}=\begin{pmatrix}4&0\\6&16\end{pmatrix}$.
> Left side: $A+B=\begin{pmatrix}1+2&2+0\\3+1&-1+4\end{pmatrix}=\begin{pmatrix}3&2\\4&3\end{pmatrix}$ and
> $(A+B)^2=\begin{pmatrix}3\cdot3+2\cdot4&3\cdot2+2\cdot3\\4\cdot3+3\cdot4&4\cdot2+3\cdot3\end{pmatrix}=\begin{pmatrix}17&12\\24&17\end{pmatrix}$.
> Student's right side: $A^2+2AB+B^2=\begin{pmatrix}7+8+4&0+16+0\\0+10+6&7-8+16\end{pmatrix}=\begin{pmatrix}19&16\\16&15\end{pmatrix}$. This is not the left side.
> The mistake: by the distribution rules $(A+B)^2=(A+B)(A+B)=A^2+AB+BA+B^2$. The middle terms are $AB+BA$, and this equals $2AB$ only when $AB=BA$.
> Check: $A^2+AB+BA+B^2=\begin{pmatrix}7+4+2+4&0+8+4+0\\0+5+13+6&7-4-2+16\end{pmatrix}=\begin{pmatrix}17&12\\24&17\end{pmatrix}$, the left side.

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

> [!info] Symmetric and skew-symmetric parts (beyond the slides)
> Every square matrix $A$ is the sum of a symmetric matrix and a skew-symmetric matrix:
> $$A=S+K,\qquad S=\tfrac12\left(A+A^{\mathsf T}\right),\qquad K=\tfrac12\left(A-A^{\mathsf T}\right).$$
> Why $S$ is symmetric: $S^{\mathsf T}=\tfrac12(A^{\mathsf T}+(A^{\mathsf T})^{\mathsf T})=\tfrac12(A^{\mathsf T}+A)=S$.
> Why $K$ is skew-symmetric: $K^{\mathsf T}=\tfrac12(A^{\mathsf T}-(A^{\mathsf T})^{\mathsf T})=\tfrac12(A^{\mathsf T}-A)=-K$.
> Why they add up to $A$: $S+K=\tfrac12A+\tfrac12A^{\mathsf T}+\tfrac12A-\tfrac12A^{\mathsf T}=A$.
> Both steps use $(A^{\mathsf T})^{\mathsf T}=A$ from slide 4.

> [!question]- Check (slide 3, product sizes): $A$ has the rows $(1,0,2)$ and $(-1,3,1)$. $B$ has the rows $(2,1)$, $(0,-1)$ and $(4,3)$. Are $AB$ and $BA$ defined? Give their sizes and compute both.
> $A$ is $2\times3$ and $B$ is $3\times2$.
> $AB$: $(2\times3)(3\times2)$. The inner sizes are 3 and 3, so $AB$ is defined and it is $2\times2$.
> $AB=\begin{pmatrix}1\cdot2+0\cdot0+2\cdot4&1\cdot1+0\cdot(-1)+2\cdot3\\(-1)\cdot2+3\cdot0+1\cdot4&(-1)\cdot1+3\cdot(-1)+1\cdot3\end{pmatrix}=\begin{pmatrix}10&7\\2&-1\end{pmatrix}$.
> $BA$: $(3\times2)(2\times3)$. The inner sizes are 2 and 2, so $BA$ is defined and it is $3\times3$.
> Row 1 of $BA$: $(2\cdot1+1\cdot(-1),\ 2\cdot0+1\cdot3,\ 2\cdot2+1\cdot1)=(1,3,5)$.
> Row 2 of $BA$: $(0\cdot1+(-1)\cdot(-1),\ 0\cdot0+(-1)\cdot3,\ 0\cdot2+(-1)\cdot1)=(1,-3,-1)$.
> Row 3 of $BA$: $(4\cdot1+3\cdot(-1),\ 4\cdot0+3\cdot3,\ 4\cdot2+3\cdot1)=(1,9,11)$.
> $BA=\begin{pmatrix}1&3&5\\1&-3&-1\\1&9&11\end{pmatrix}$.
> $AB$ and $BA$ do not even have the same size here, so they cannot be equal.

> [!question]- Check (slide 3, special matrices): $U$ has the rows $(2,1)$ and $(0,3)$. $V$ has the rows $(1,-4)$ and $(0,5)$. What type are $U$ and $V$? Compute $UV$ and say what type it is. What is $\mathcal I_2U$?
> In both matrices the entry below the main diagonal is $a_{21}=0$. So $U$ and $V$ are upper triangular. They are not diagonal, because $a_{12}\neq0$.
> $UV=\begin{pmatrix}2\cdot1+1\cdot0&2\cdot(-4)+1\cdot5\\0\cdot1+3\cdot0&0\cdot(-4)+3\cdot5\end{pmatrix}=\begin{pmatrix}2&-3\\0&15\end{pmatrix}$.
> $UV$ is upper triangular again. Its diagonal entries are the products of the diagonal entries: $2\cdot1=2$ and $3\cdot5=15$.
> $\mathcal I_2U=\begin{pmatrix}1\cdot2+0\cdot0&1\cdot1+0\cdot3\\0\cdot2+1\cdot0&0\cdot1+1\cdot3\end{pmatrix}=\begin{pmatrix}2&1\\0&3\end{pmatrix}=U$. The identity matrix changes nothing, like the number 1.

> [!question]- Check (slide 4, transpose): $A$ has the rows $(1,2)$ and $(0,3)$. $B$ has the rows $(4,-1)$ and $(2,5)$. Verify $(AB)^{\mathsf T}=B^{\mathsf T}A^{\mathsf T}$ and show that $A^{\mathsf T}B^{\mathsf T}$ is a different matrix.
> $AB=\begin{pmatrix}1\cdot4+2\cdot2&1\cdot(-1)+2\cdot5\\0\cdot4+3\cdot2&0\cdot(-1)+3\cdot5\end{pmatrix}=\begin{pmatrix}8&9\\6&15\end{pmatrix}$.
> Rows become columns: $(AB)^{\mathsf T}=\begin{pmatrix}8&6\\9&15\end{pmatrix}$.
> $A^{\mathsf T}=\begin{pmatrix}1&0\\2&3\end{pmatrix}$, $B^{\mathsf T}=\begin{pmatrix}4&2\\-1&5\end{pmatrix}$.
> $B^{\mathsf T}A^{\mathsf T}=\begin{pmatrix}4\cdot1+2\cdot2&4\cdot0+2\cdot3\\(-1)\cdot1+5\cdot2&(-1)\cdot0+5\cdot3\end{pmatrix}=\begin{pmatrix}8&6\\9&15\end{pmatrix}$. This equals $(AB)^{\mathsf T}$.
> $A^{\mathsf T}B^{\mathsf T}=\begin{pmatrix}1\cdot4+0\cdot(-1)&1\cdot2+0\cdot5\\2\cdot4+3\cdot(-1)&2\cdot2+3\cdot5\end{pmatrix}=\begin{pmatrix}4&2\\5&19\end{pmatrix}$. This is different. It is $(BA)^{\mathsf T}$, not $(AB)^{\mathsf T}$.

> [!question]- Check (slide 4, symmetric and skew-symmetric parts, beyond the slides): $A$ has the rows $(2,7,-1)$, $(3,0,4)$ and $(5,-2,6)$. Write $A=S+K$ with $S$ symmetric and $K$ skew-symmetric (use the info box above).
> Step 1, transpose: $A^{\mathsf T}=\begin{pmatrix}2&3&5\\7&0&-2\\-1&4&6\end{pmatrix}$.
> Step 2, sum: $A+A^{\mathsf T}=\begin{pmatrix}2+2&7+3&-1+5\\3+7&0+0&4-2\\5-1&-2+4&6+6\end{pmatrix}=\begin{pmatrix}4&10&4\\10&0&2\\4&2&12\end{pmatrix}$.
> Step 3, half of it: $S=\begin{pmatrix}2&5&2\\5&0&1\\2&1&6\end{pmatrix}$. It is symmetric: $s_{12}=s_{21}=5$, $s_{13}=s_{31}=2$, $s_{23}=s_{32}=1$.
> Step 4, difference: $A-A^{\mathsf T}=\begin{pmatrix}2-2&7-3&-1-5\\3-7&0-0&4+2\\5+1&-2-4&6-6\end{pmatrix}=\begin{pmatrix}0&4&-6\\-4&0&6\\6&-6&0\end{pmatrix}$.
> Step 5, half of it: $K=\begin{pmatrix}0&2&-3\\-2&0&3\\3&-3&0\end{pmatrix}$. It is skew-symmetric: $k_{21}=-k_{12}=-2$, $k_{31}=-k_{13}=3$, $k_{32}=-k_{23}=-3$, and the diagonal is zero (property (iv) on the slide).
> Check: $S+K=\begin{pmatrix}2+0&5+2&2-3\\5-2&0+0&1+3\\2+3&1-3&6+0\end{pmatrix}=\begin{pmatrix}2&7&-1\\3&0&4\\5&-2&6\end{pmatrix}=A$.

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

> [!info] Inverse of a larger matrix from cofactors (beyond the slides)
> The slide gives the inverse only for a $2\times2$ matrix. The same idea works for $n\times n$. Let $C_{ij}=(-1)^{i+j}M_{ij}$ be the cofactor of $a_{ij}$. Put all cofactors in a matrix and transpose it. The result is the **adjugate** $\operatorname{adj}(A)=[C_{ji}]$. If $\det(A)\neq0$:
> $$A^{-1}=\frac{1}{\det(A)}\operatorname{adj}(A).$$
> For $A=\begin{pmatrix}a&b\\c&d\end{pmatrix}$ the cofactors are $C_{11}=d$, $C_{12}=-c$, $C_{21}=-b$, $C_{22}=a$. Transposing the cofactor matrix $\begin{pmatrix}d&-c\\-b&a\end{pmatrix}$ gives $\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$, the matrix in the slide formula.
> Always check the result with $AA^{-1}=\mathcal I_n$.

> [!question]- Check (slide 5, determinant and inverse): $A$ has the rows $(5,3)$ and $(4,2)$. Find $\det(A)$ and $A^{-1}$, and check $AA^{-1}=\mathcal I_2$. For which $t$ is the matrix with the rows $(t,2)$ and $(8,t)$ singular?
> $\det(A)=ad-bc=5\cdot2-3\cdot4=10-12=-2$. It is not zero, so $A$ is invertible.
> Swap the diagonal entries and change the sign of the other two:
> $A^{-1}=\dfrac{1}{-2}\begin{pmatrix}2&-3\\-4&5\end{pmatrix}=\begin{pmatrix}-1&3/2\\2&-5/2\end{pmatrix}$.
> Check: $AA^{-1}=\begin{pmatrix}5\cdot(-1)+3\cdot2&5\cdot\tfrac32+3\cdot(-\tfrac52)\\4\cdot(-1)+2\cdot2&4\cdot\tfrac32+2\cdot(-\tfrac52)\end{pmatrix}=\begin{pmatrix}-5+6&\tfrac{15}{2}-\tfrac{15}{2}\\-4+4&6-5\end{pmatrix}=\begin{pmatrix}1&0\\0&1\end{pmatrix}$.
> Second matrix: $\det=t\cdot t-2\cdot8=t^2-16$. Singular means $\det=0$: $t^2=16$, so $t=4$ or $t=-4$.
> For every other $t$ the matrix is invertible.

> [!question]- Check (slide 5, minors and cofactors): $A$ has the rows $(2,-1,3)$, $(0,4,1)$ and $(5,2,-2)$. Find the minors $M_{12}$, $M_{23}$, $M_{31}$ and the three cofactors.
> $M_{12}$: delete row 1 and column 2. Left: rows $(0,1)$ and $(5,-2)$. $M_{12}=0\cdot(-2)-1\cdot5=-5$.
> Cofactor: $(-1)^{1+2}M_{12}=(-1)\cdot(-5)=5$.
> $M_{23}$: delete row 2 and column 3. Left: rows $(2,-1)$ and $(5,2)$. $M_{23}=2\cdot2-(-1)\cdot5=4+5=9$.
> Cofactor: $(-1)^{2+3}M_{23}=(-1)\cdot9=-9$.
> $M_{31}$: delete row 3 and column 1. Left: rows $(-1,3)$ and $(4,1)$. $M_{31}=(-1)\cdot1-3\cdot4=-1-12=-13$.
> Cofactor: $(-1)^{3+1}M_{31}=(+1)\cdot(-13)=-13$.
> The sign changes only when $i+j$ is odd.

> [!question]- Check (slide 5, inverse from cofactors, beyond the slides): $A$ has the rows $(1,2,3)$, $(0,1,4)$ and $(5,6,0)$. Find $A^{-1}$ with the adjugate formula of the info box above, and check $AA^{-1}=\mathcal I_3$.
> Cofactors of row 1:
> $C_{11}=+\begin{vmatrix}1&4\\6&0\end{vmatrix}=1\cdot0-4\cdot6=-24$.
> $C_{12}=-\begin{vmatrix}0&4\\5&0\end{vmatrix}=-(0\cdot0-4\cdot5)=20$.
> $C_{13}=+\begin{vmatrix}0&1\\5&6\end{vmatrix}=0\cdot6-1\cdot5=-5$.
> Cofactors of row 2:
> $C_{21}=-\begin{vmatrix}2&3\\6&0\end{vmatrix}=-(2\cdot0-3\cdot6)=18$.
> $C_{22}=+\begin{vmatrix}1&3\\5&0\end{vmatrix}=1\cdot0-3\cdot5=-15$.
> $C_{23}=-\begin{vmatrix}1&2\\5&6\end{vmatrix}=-(1\cdot6-2\cdot5)=4$.
> Cofactors of row 3:
> $C_{31}=+\begin{vmatrix}2&3\\1&4\end{vmatrix}=2\cdot4-3\cdot1=5$.
> $C_{32}=-\begin{vmatrix}1&3\\0&4\end{vmatrix}=-(1\cdot4-3\cdot0)=-4$.
> $C_{33}=+\begin{vmatrix}1&2\\0&1\end{vmatrix}=1\cdot1-2\cdot0=1$.
> Determinant along row 1: $\det(A)=1\cdot(-24)+2\cdot20+3\cdot(-5)=-24+40-15=1$.
> Cofactor matrix: $\begin{pmatrix}-24&20&-5\\18&-15&4\\5&-4&1\end{pmatrix}$. Transpose it: $\operatorname{adj}(A)=\begin{pmatrix}-24&18&5\\20&-15&-4\\-5&4&1\end{pmatrix}$.
> $A^{-1}=\dfrac11\operatorname{adj}(A)=\begin{pmatrix}-24&18&5\\20&-15&-4\\-5&4&1\end{pmatrix}$.
> Check, row 1 of $AA^{-1}$: $(1\cdot(-24)+2\cdot20+3\cdot(-5),\ 1\cdot18+2\cdot(-15)+3\cdot4,\ 1\cdot5+2\cdot(-4)+3\cdot1)=(1,0,0)$.
> Row 2: $(0+1\cdot20+4\cdot(-5),\ 0+1\cdot(-15)+4\cdot4,\ 0+1\cdot(-4)+4\cdot1)=(0,1,0)$.
> Row 3: $(5\cdot(-24)+6\cdot20+0,\ 5\cdot18+6\cdot(-15)+0,\ 5\cdot5+6\cdot(-4)+0)=(0,0,1)$.
> So $AA^{-1}=\mathcal I_3$.

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

> [!question]- Check (slide 6): $A$ has the rows $(2,-1,3)$, $(0,4,1)$ and $(5,2,-2)$. Compute $\det(A)$ by cofactor expansion along the second row, then along the first column. Why are these two good choices?
> Both contain the zero entry $a_{21}=0$, so one term drops out.
> Along row 2 ($k=2$): $\det(A)=(-1)^{2+1}a_{21}M_{21}+(-1)^{2+2}a_{22}M_{22}+(-1)^{2+3}a_{23}M_{23}$.
> $a_{21}=0$, so the first term is 0.
> $M_{22}$: delete row 2 and column 2. Left: rows $(2,3)$ and $(5,-2)$. $M_{22}=2\cdot(-2)-3\cdot5=-4-15=-19$.
> $M_{23}$: delete row 2 and column 3. Left: rows $(2,-1)$ and $(5,2)$. $M_{23}=2\cdot2-(-1)\cdot5=9$.
> $\det(A)=0+(+1)\cdot4\cdot(-19)+(-1)\cdot1\cdot9=-76-9=-85$.
> Along column 1 ($k=1$): $\det(A)=(-1)^{1+1}a_{11}M_{11}+(-1)^{2+1}a_{21}M_{21}+(-1)^{3+1}a_{31}M_{31}$.
> $M_{11}$: left are rows $(4,1)$ and $(2,-2)$. $M_{11}=4\cdot(-2)-1\cdot2=-8-2=-10$.
> $M_{31}$: left are rows $(-1,3)$ and $(4,1)$. $M_{31}=(-1)\cdot1-3\cdot4=-13$.
> $\det(A)=(+1)\cdot2\cdot(-10)+0+(+1)\cdot5\cdot(-13)=-20-65=-85$.
> Both expansions give $-85$, as the theorem says.

> [!question]- Check (slide 7, a 4 by 4 determinant): $A$ has the rows $(2,0,1,0)$, $(1,3,-1,2)$, $(0,0,4,0)$ and $(3,0,2,1)$. Compute $\det(A)$. Choose the row first.
> Row 3 has only one nonzero entry, $a_{33}=4$. Expand along row 3:
> $\det(A)=(-1)^{3+3}a_{33}M_{33}=4\,M_{33}$. The other three terms have the factor 0.
> $M_{33}$: delete row 3 and column 3. Left: rows $(2,0,0)$, $(1,3,2)$ and $(3,0,1)$.
> Expand this $3\times3$ determinant along its first row, which has two zeros:
> $M_{33}=2\begin{vmatrix}3&2\\0&1\end{vmatrix}-0+0=2\,(3\cdot1-2\cdot0)=2\cdot3=6$.
> $\det(A)=4\cdot6=24$.

> [!question]- Check (slide 7, zero rows and triangular matrices): Find the determinants. (a) Rows $(3,0,0)$, $(7,-2,0)$, $(1,5,5)$. (b) Rows $(4,0,-1)$, $(2,0,6)$, $(-3,0,8)$. (c) A student says the matrix with the rows $(0,0,3)$, $(0,2,1)$, $(4,5,6)$ is triangular, so its determinant is $0\cdot2\cdot6=0$. Is that right?
> (a) All entries above the main diagonal are zero: lower triangular. $\det=3\cdot(-2)\cdot5=-30$.
> (b) Column 2 is a zero column, so $\det=0$.
> (c) Wrong. Triangular means zeros below (or above) the **main** diagonal, which runs from top left to bottom right. Here $a_{31}=4$ and $a_{13}=3$ are both nonzero, so the matrix is not triangular and the rule does not apply.
> Correct value, expansion along row 1 (only $a_{13}=3$ is nonzero):
> $\det=(-1)^{1+3}\cdot3\cdot\begin{vmatrix}0&2\\4&5\end{vmatrix}=3\,(0\cdot5-2\cdot4)=3\cdot(-8)=-24$.

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

> [!info] Determinant of a product and of an inverse (beyond the slides)
> For two $n\times n$ matrices: $\det(AB)=\det(A)\det(B)$. There is no such rule for a sum: in general $\det(A+B)\neq\det(A)+\det(B)$.
> If $A$ is invertible, then $AA^{-1}=\mathcal I_n$ gives $\det(A)\det(A^{-1})=\det(\mathcal I_n)=1$, so $\det(A^{-1})=\dfrac{1}{\det(A)}$.
> Where $\det(kA)=k^n\det(A)$ comes from: $kA$ multiplies each of the $n$ rows by $k$. By rule (ii) on slide 8 each row gives one factor $k$, so there are $n$ factors.

> [!question]- Check (slide 8, the rules): $A$ is a $3\times3$ matrix with $\det(A)=5$. Find the determinant after each change (each one starts from $A$): (a) rows 1 and 3 interchanged, (b) row 2 multiplied by 4, (c) 7 times row 1 added to row 3, (d) $A^{\mathsf T}$, (e) $2A$. Then confirm (e) on the $2\times2$ matrix with the rows $(3,1)$ and $(4,2)$ and the factor 3.
> (a) An interchange multiplies by $-1$: $-5$.
> (b) One row times 4 multiplies by 4: $4\cdot5=20$.
> (c) Adding a multiple of a row to another row changes nothing: $5$.
> (d) $\det(A^{\mathsf T})=\det(A)=5$.
> (e) $2A$ multiplies all 3 rows by 2. Each row gives a factor 2: $2\cdot2\cdot2\cdot5=2^3\cdot5=40$. It is not $2\cdot5=10$.
> The $2\times2$ check: $\det\begin{pmatrix}3&1\\4&2\end{pmatrix}=3\cdot2-1\cdot4=2$.
> $3A=\begin{pmatrix}9&3\\12&6\end{pmatrix}$, $\det(3A)=9\cdot6-3\cdot12=54-36=18$.
> Rule: $3^2\cdot2=9\cdot2=18$. The same.

> [!question]- Check (slide 8, proportional rows): $A$ has the rows $(1,2,-1)$, $(3,t,-3)$ and $(0,1,4)$. Compute $\det(A)$ as a function of $t$ by expansion along the first row. For which $t$ is it zero, and how can you see this value without computing?
> $\det(A)=1\begin{vmatrix}t&-3\\1&4\end{vmatrix}-2\begin{vmatrix}3&-3\\0&4\end{vmatrix}+(-1)\begin{vmatrix}3&t\\0&1\end{vmatrix}$.
> First minor: $t\cdot4-(-3)\cdot1=4t+3$.
> Second minor: $3\cdot4-(-3)\cdot0=12$.
> Third minor: $3\cdot1-t\cdot0=3$.
> $\det(A)=(4t+3)-2\cdot12-3=4t+3-24-3=4t-24$.
> $\det(A)=0$ gives $4t=24$, so $t=6$.
> Without computing: for $t=6$ row 2 is $(3,6,-3)=3\cdot(1,2,-1)$, which is 3 times row 1. Proportional rows give determinant 0 (the remark on the slide).

> [!question]- Check (slide 8, products, beyond the slides): $A$ has the rows $(2,1)$ and $(1,3)$. $B$ has the rows $(1,4)$ and $(2,-1)$. Verify $\det(AB)=\det(A)\det(B)$ (info box above) and find $\det(A^{-1})$ without computing $A^{-1}$.
> $\det(A)=2\cdot3-1\cdot1=6-1=5$.
> $\det(B)=1\cdot(-1)-4\cdot2=-1-8=-9$.
> $AB=\begin{pmatrix}2\cdot1+1\cdot2&2\cdot4+1\cdot(-1)\\1\cdot1+3\cdot2&1\cdot4+3\cdot(-1)\end{pmatrix}=\begin{pmatrix}4&7\\7&1\end{pmatrix}$.
> $\det(AB)=4\cdot1-7\cdot7=4-49=-45$.
> $\det(A)\det(B)=5\cdot(-9)=-45$. The same.
> $\det(A^{-1})=\dfrac{1}{\det(A)}=\dfrac15$.

> [!question]- Check (slide 9): $A$ has the rows $(0,2,-4)$, $(2,4,6)$ and $(3,1,5)$. Compute $\det(A)$ by row reduction to triangular form. Write the effect of every row operation. Check the result with a cofactor expansion.
> Start: $\det(A)=\begin{vmatrix}0&2&-4\\2&4&6\\3&1&5\end{vmatrix}$. The entry $a_{11}$ is 0, so first bring a nonzero entry to the top.
> Step 1, interchange rows 1 and 2 (factor $-1$): $\det(A)=-\begin{vmatrix}2&4&6\\0&2&-4\\3&1&5\end{vmatrix}$.
> Step 2, pull the factor 2 out of row 1 (the row is multiplied by $\tfrac12$, so 2 goes in front): $\det(A)=-2\begin{vmatrix}1&2&3\\0&2&-4\\3&1&5\end{vmatrix}$.
> Step 3, add $-3$ times row 1 to row 3 (no change): new row 3 is $(3-3,\ 1-6,\ 5-9)=(0,-5,-4)$.
> $\det(A)=-2\begin{vmatrix}1&2&3\\0&2&-4\\0&-5&-4\end{vmatrix}$.
> Step 4, pull the factor 2 out of row 2: $\det(A)=-2\cdot2\begin{vmatrix}1&2&3\\0&1&-2\\0&-5&-4\end{vmatrix}=-4\begin{vmatrix}1&2&3\\0&1&-2\\0&-5&-4\end{vmatrix}$.
> Step 5, add 5 times row 2 to row 3 (no change): new row 3 is $(0,\ -5+5,\ -4-10)=(0,0,-14)$.
> $\det(A)=-4\begin{vmatrix}1&2&3\\0&1&-2\\0&0&-14\end{vmatrix}$.
> The matrix is upper triangular: $\det(A)=-4\cdot(1\cdot1\cdot(-14))=56$.
> Check, expansion of the original matrix along row 1:
> $\det(A)=0-2\begin{vmatrix}2&6\\3&5\end{vmatrix}+(-4)\begin{vmatrix}2&4\\3&1\end{vmatrix}=-2\,(10-18)-4\,(2-12)=16+40=56$.

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
> [!question]- 1. $A$ has the rows $(1,2)$ and $(0,1)$. $B$ has the rows $(0,1)$ and $(1,0)$. Is $AB=BA$?
> $AB=\begin{pmatrix}2&1\\1&0\end{pmatrix}$, $BA=\begin{pmatrix}0&1\\1&2\end{pmatrix}$. Not equal.

> [!question]- 2. Classify three matrices. First: rows $(0,2)$ and $(-2,0)$. Second: rows $(1,4)$ and $(4,0)$. Third: rows $(1,2)$ and $(3,1)$.
> First: skew-symmetric ($a_{21}=-a_{12}$, zero diagonal). Second: symmetric. Third: neither.

> [!question]- 3. Find the inverse of the matrix with the rows $(3,1)$ and $(5,2)$. Is the matrix with the rows $(2,4)$ and $(1,2)$ invertible?
> $\det=6-5=1$, inverse $\begin{pmatrix}2&-1\\-5&3\end{pmatrix}$.
> Second matrix: $\det=4-4=0$, not invertible.

> [!question]- 4. Compute the determinant of the matrix with the rows $(2,0,1)$, $(1,3,0)$ and $(0,1,4)$ along the first row.
> $2\,(12-0)-0+1\,(1-0)=25$.

> [!question]- 5. Why is the determinant of the matrix with the rows $(1,2,3)$, $(4,5,6)$ and $(2,4,6)$ equal to 0?
> Row 3 is 2 times row 1. Proportional rows give determinant 0.

> [!question]- 6. Compute the determinant of the matrix with the rows $(1,2,3)$, $(2,5,7)$ and $(1,3,5)$ by row reduction.
> $R_2-2R_1=(0,1,1)$, $R_3-R_1=(0,1,2)$, then $R_3-R_2=(0,0,1)$. No swaps, no factors.
> $\det=1\cdot1\cdot1=1$.

## Links
- Course index, quizzes and labs: [[MATH501 Home]]
- Previous: [[MATH501 L04 - Series solutions of ODEs]]. Next: [[MATH501 L06 - Eigenvalues and eigenvectors]]
- Full step-by-step notes (PDF): [MATH501_Lecture_05_Matrices_Determinants.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_05/MATH501_Lecture_05_Matrices_Determinants.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_05/MATH501_Lecture_05_Matrices_Determinants.pdf`
- Original chapter notes (PDF): [Math501 Chapter 5.pdf](file:///home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_05/Math501%20Chapter%205.pdf) `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_05/Math501 Chapter 5.pdf`
- Quiz: [[MATH501 L05 - Matrices and determinants - quiz]]

Slides not embedded: none.
