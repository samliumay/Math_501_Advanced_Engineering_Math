---
course: MATH 501 Advanced Engineering Mathematics
lesson: MATH501 L05 - Matrices and determinants
type: quiz
questions: 17
---

# MATH501 L05 - Matrices and determinants - quiz

Lesson note: [[MATH501 L05 - Matrices and determinants]]. One question per check question of the lesson. Pick an option, then open the answer.

## 1. Matrices and their operations (slides 1-3)

### Q1 (slide 1)

$A=[a_{ij}]$ has the rows $(4,-1,7)$ and $(0,3,-2)$. What is the size of $A$, and what are $a_{12}$ and $a_{21}$?

- A) $3\times2$; $a_{12}=-1$, $a_{21}=0$
- B) $3\times2$; $a_{12}=0$, $a_{21}=-1$
- C) $2\times3$; $a_{12}=-1$, $a_{21}=0$
- D) $2\times3$; $a_{12}=0$, $a_{21}=-1$

> [!success]- Answer
> **C.** The size is (number of rows) $\times$ (number of columns). $A$ has 2 rows and 3 columns: $2\times3$.
> In $a_{ij}$ the first index is the row, the second the column.
> $a_{12}$: row 1, column 2, so $a_{12}=-1$. $a_{21}$: row 2, column 1, so $a_{21}=0$.
> - A: Right entries, but the size is written as columns $\times$ rows.
> - B: Two slips, both from reading the column first: the size is columns $\times$ rows, and $a_{12}$ is read as row 2, column 1.
> - D: Right size, but the indices are read as (column, row): $a_{12}$ is taken from row 2, column 1.

### Q2 (slide 2, sums and scalar multiples)

$A$ has the rows $(1,-2,3)$ and $(0,4,-1)$. $B$ has the rows $(2,5,-3)$ and $(-1,0,6)$. Compute $3A-2B$.

- A) $\begin{pmatrix}7&4&3\\-2&12&9\end{pmatrix}$
- B) $\begin{pmatrix}-1&-16&15\\2&12&-15\end{pmatrix}$
- C) $\begin{pmatrix}1&-11&12\\1&12&-9\end{pmatrix}$
- D) $\begin{pmatrix}-3&-21&18\\3&12&-21\end{pmatrix}$

> [!success]- Answer
> **B.** $3A=\begin{pmatrix}3&-6&9\\0&12&-3\end{pmatrix}$ and $2B=\begin{pmatrix}4&10&-6\\-2&0&12\end{pmatrix}$.
> Subtract entry by entry: $3A-2B=\begin{pmatrix}3-4&-6-10&9+6\\0+2&12-0&-3-12\end{pmatrix}=\begin{pmatrix}-1&-16&15\\2&12&-15\end{pmatrix}$.
> - A: $2B$ is added instead of subtracted: this is $3A+2B$.
> - C: The factor 2 of $B$ is forgotten: this is $3A-B$.
> - D: The factor 3 is put in front of both matrices: this is $3(A-B)=3A-3B$.

### Q3 (slide 2, product and order)

$A$ has the rows $(1,2)$ and $(3,-1)$. $B$ has the rows $(2,0)$ and $(1,4)$. Compute $(A+B)^2$.

- A) $\begin{pmatrix}19&16\\16&15\end{pmatrix}$
- B) $\begin{pmatrix}9&4\\16&9\end{pmatrix}$
- C) $\begin{pmatrix}17&12\\24&17\end{pmatrix}$
- D) $\begin{pmatrix}15&8\\32&19\end{pmatrix}$

> [!success]- Answer
> **C.** $A+B=\begin{pmatrix}3&2\\4&3\end{pmatrix}$.
> $(A+B)^2=(A+B)(A+B)=\begin{pmatrix}3\cdot3+2\cdot4&3\cdot2+2\cdot3\\4\cdot3+3\cdot4&4\cdot2+3\cdot3\end{pmatrix}=\begin{pmatrix}17&12\\24&17\end{pmatrix}$.
> In general $(A+B)^2=A^2+AB+BA+B^2$. Here $AB=\begin{pmatrix}4&8\\5&-4\end{pmatrix}\neq BA=\begin{pmatrix}2&4\\13&-2\end{pmatrix}$.
> - A: The scalar rule $A^2+2AB+B^2$ is used. It treats $BA$ as $AB$.
> - B: Every entry of $A+B$ is squared. $A^2$ means $AA$, not the squares of the entries.
> - D: The scalar rule written as $A^2+2BA+B^2$. It treats $AB$ as $BA$.

## 2. Special matrices, transpose, symmetric matrices (slides 3-4)

### Q4 (slide 3, product sizes)

$A$ has the rows $(1,0,2)$ and $(-1,3,1)$. $B$ has the rows $(2,1)$, $(0,-1)$ and $(4,3)$. Is $BA$ defined? If it is, what is it?

- A) $BA=\begin{pmatrix}1&3&5\\1&-3&-1\\1&9&11\end{pmatrix}$
- B) $BA$ is not defined, because $B$ has 2 columns and $A$ has 3 columns
- C) $BA=\begin{pmatrix}10&7\\2&-1\end{pmatrix}$
- D) $BA=\begin{pmatrix}1&1&1\\3&-3&9\\5&-1&11\end{pmatrix}$

> [!success]- Answer
> **A.** $B$ is $3\times2$ and $A$ is $2\times3$. The inner sizes are 2 and 2, so $BA$ is defined and it is $3\times3$.
> Row 1: $(2\cdot1+1\cdot(-1),\ 2\cdot0+1\cdot3,\ 2\cdot2+1\cdot1)=(1,3,5)$.
> Row 2: $(0+1,\ 0-3,\ 0-1)=(1,-3,-1)$. Row 3: $(4-3,\ 0+9,\ 8+3)=(1,9,11)$.
> - B: The columns of $B$ are compared with the columns of $A$. The rule compares the columns of $B$ with the rows of $A$: 2 and 2.
> - C: This is $AB$, not $BA$. The order of the factors is swapped.
> - D: Entry $(i,j)$ is computed as row $j$ of $B$ times column $i$ of $A$. This gives $(BA)^{\mathsf T}$.

### Q5 (slide 3, special matrices)

$U$ has the rows $(2,1)$ and $(0,3)$. $V$ has the rows $(1,-4)$ and $(0,5)$. Compute $UV$.

- A) $\begin{pmatrix}2&-11\\0&15\end{pmatrix}$
- B) $\begin{pmatrix}2&-3\\0&15\end{pmatrix}$
- C) $\begin{pmatrix}-2&5\\-12&15\end{pmatrix}$
- D) $\begin{pmatrix}2&-4\\0&15\end{pmatrix}$

> [!success]- Answer
> **B.** $UV=\begin{pmatrix}2\cdot1+1\cdot0&2\cdot(-4)+1\cdot5\\0\cdot1+3\cdot0&0\cdot(-4)+3\cdot5\end{pmatrix}=\begin{pmatrix}2&-3\\0&15\end{pmatrix}$.
> $U$ and $V$ are upper triangular, and so is $UV$. Its diagonal is $2\cdot1$ and $3\cdot5$.
> - A: This is $VU$. The order of the factors is swapped.
> - C: Row $i$ of $U$ is multiplied by row $j$ of $V$. This is $UV^{\mathsf T}$.
> - D: The entries are multiplied position by position. That is not the matrix product.

### Q6 (slide 4, transpose)

$A$ has the rows $(1,2)$ and $(0,3)$. $B$ has the rows $(4,-1)$ and $(2,5)$. Compute $(AB)^{\mathsf T}$.

- A) $\begin{pmatrix}4&2\\5&19\end{pmatrix}$
- B) $\begin{pmatrix}8&9\\6&15\end{pmatrix}$
- C) $\begin{pmatrix}8&6\\9&15\end{pmatrix}$
- D) $\begin{pmatrix}4&5\\2&19\end{pmatrix}$

> [!success]- Answer
> **C.** $AB=\begin{pmatrix}1\cdot4+2\cdot2&1\cdot(-1)+2\cdot5\\0\cdot4+3\cdot2&0\cdot(-1)+3\cdot5\end{pmatrix}=\begin{pmatrix}8&9\\6&15\end{pmatrix}$.
> Rows become columns: $(AB)^{\mathsf T}=\begin{pmatrix}8&6\\9&15\end{pmatrix}$. The same comes from $B^{\mathsf T}A^{\mathsf T}$.
> - A: $(AB)^{\mathsf T}$ is taken as $A^{\mathsf T}B^{\mathsf T}$. The order must reverse: $A^{\mathsf T}B^{\mathsf T}=(BA)^{\mathsf T}$.
> - B: This is $AB$ itself. The transpose is not taken.
> - D: This is $BA$: the order is reversed, but the transpose is not taken.

### Q7 (slide 4, symmetric and skew-symmetric parts, beyond the slides)

$A$ has the rows $(2,7,-1)$, $(3,0,4)$ and $(5,-2,6)$. Write $A=S+K$ with $S$ symmetric ($S^{\mathsf T}=S$) and $K$ skew-symmetric ($K^{\mathsf T}=-K$). What is $K$?

- A) $\begin{pmatrix}2&5&2\\5&0&1\\2&1&6\end{pmatrix}$
- B) $\begin{pmatrix}0&4&-6\\-4&0&6\\6&-6&0\end{pmatrix}$
- C) $\begin{pmatrix}0&-2&3\\2&0&-3\\-3&3&0\end{pmatrix}$
- D) $\begin{pmatrix}0&2&-3\\-2&0&3\\3&-3&0\end{pmatrix}$

> [!success]- Answer
> **D.** $K=\tfrac12(A-A^{\mathsf T})$. With $A^{\mathsf T}=\begin{pmatrix}2&3&5\\7&0&-2\\-1&4&6\end{pmatrix}$:
> $A-A^{\mathsf T}=\begin{pmatrix}0&4&-6\\-4&0&6\\6&-6&0\end{pmatrix}$, so $K=\begin{pmatrix}0&2&-3\\-2&0&3\\3&-3&0\end{pmatrix}$.
> Check: $S=\tfrac12(A+A^{\mathsf T})=\begin{pmatrix}2&5&2\\5&0&1\\2&1&6\end{pmatrix}$ and $S+K=A$.
> - A: This is $S$, the symmetric part. It is not skew-symmetric: its diagonal is not zero.
> - B: The factor $\tfrac12$ is forgotten: this is $A-A^{\mathsf T}=2K$.
> - C: The difference is taken the wrong way: $\tfrac12(A^{\mathsf T}-A)=-K$. Then $S+(-K)=A^{\mathsf T}$, not $A$.

## 3. Determinant of a 2 by 2 matrix, minors, cofactors (slide 5)

### Q8 (slide 5, determinant and inverse)

$A$ has the rows $(5,3)$ and $(4,2)$. What is $A^{-1}$?

- A) $\begin{pmatrix}2&-3\\-4&5\end{pmatrix}$
- B) $\begin{pmatrix}-1&3/2\\2&-5/2\end{pmatrix}$
- C) $\begin{pmatrix}-1&-3/2\\-2&-5/2\end{pmatrix}$
- D) $\begin{pmatrix}1&-3/2\\-2&5/2\end{pmatrix}$

> [!success]- Answer
> **B.** $\det(A)=5\cdot2-3\cdot4=-2\neq0$. Swap the diagonal entries, change the sign of the other two, divide by $\det(A)$:
> $A^{-1}=\dfrac{1}{-2}\begin{pmatrix}2&-3\\-4&5\end{pmatrix}=\begin{pmatrix}-1&3/2\\2&-5/2\end{pmatrix}$.
> Check: row 1 of $AA^{-1}$ is $(-5+6,\ \tfrac{15}{2}-\tfrac{15}{2})=(1,0)$, row 2 is $(-4+4,\ 6-5)=(0,1)$.
> - A: The division by $\det(A)$ is forgotten. This is only $\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$.
> - C: The diagonal is swapped, but the signs of $b$ and $c$ are not changed: $\tfrac{1}{-2}\begin{pmatrix}2&3\\4&5\end{pmatrix}$.
> - D: The sign of $\det(A)$ is lost: the matrix is divided by $2$ instead of $-2$.

### Q9 (slide 5, minors and cofactors)

$A$ has the rows $(2,-1,3)$, $(0,4,1)$ and $(5,2,-2)$. The cofactor of $a_{ij}$ is $C_{ij}=(-1)^{i+j}M_{ij}$, where the minor $M_{ij}$ is the determinant left after deleting row $i$ and column $j$. What are $C_{12}$, $C_{23}$, $C_{31}$?

- A) $C_{12}=5$, $C_{23}=-9$, $C_{31}=-13$
- B) $C_{12}=5$, $C_{23}=-9$, $C_{31}=13$
- C) $C_{12}=-5$, $C_{23}=9$, $C_{31}=13$
- D) $C_{12}=-5$, $C_{23}=9$, $C_{31}=-13$

> [!success]- Answer
> **A.** $M_{12}=\begin{vmatrix}0&1\\5&-2\end{vmatrix}=-5$, $M_{23}=\begin{vmatrix}2&-1\\5&2\end{vmatrix}=9$, $M_{31}=\begin{vmatrix}-1&3\\4&1\end{vmatrix}=-13$.
> $1+2$ and $2+3$ are odd, so $C_{12}=5$ and $C_{23}=-9$. $3+1$ is even, so $C_{31}=M_{31}=-13$.
> - B: Every cofactor is taken as $-M_{ij}$. For $C_{31}$ the sign is $(-1)^4=+1$.
> - C: The checkerboard is started with $-$ in the top left corner, so every sign is the wrong one.
> - D: These are the minors. The sign $(-1)^{i+j}$ is forgotten.

### Q10 (slide 5, inverse from cofactors, beyond the slides)

$A$ has the rows $(1,2,3)$, $(0,1,4)$ and $(5,6,0)$, and $\det(A)=1$. Find $A^{-1}$ with the adjugate formula $A^{-1}=\dfrac{1}{\det(A)}\operatorname{adj}(A)$.

- A) $\begin{pmatrix}-24&20&-5\\18&-15&4\\5&-4&1\end{pmatrix}$
- B) $\begin{pmatrix}24&-18&-5\\-20&15&4\\5&-4&-1\end{pmatrix}$
- C) $\begin{pmatrix}-24&-18&5\\-20&-15&4\\-5&-4&1\end{pmatrix}$
- D) $\begin{pmatrix}-24&18&5\\20&-15&-4\\-5&4&1\end{pmatrix}$

> [!success]- Answer
> **D.** Cofactors $C_{ij}=(-1)^{i+j}M_{ij}$, row by row: $(-24,20,-5)$, $(18,-15,4)$, $(5,-4,1)$.
> The adjugate is the transpose of this cofactor matrix: $\operatorname{adj}(A)=\begin{pmatrix}-24&18&5\\20&-15&-4\\-5&4&1\end{pmatrix}$. Divide by $\det(A)=1$.
> Check, row 3 of $AA^{-1}$: $(5\cdot(-24)+6\cdot20,\ 5\cdot18+6\cdot(-15),\ 5\cdot5+6\cdot(-4))=(0,0,1)$.
> - A: The cofactor matrix is used without the transpose.
> - B: The checkerboard is started with $-$ in the top left corner, so every cofactor has the wrong sign. This gives $-\operatorname{adj}(A)$.
> - C: The signs $(-1)^{i+j}$ are left out: this is the transpose of the matrix of minors.

## 4. Cofactor expansion, zero rows, triangular matrices (slides 6-7)

### Q11 (slide 6)

$A$ has the rows $(2,-1,3)$, $(0,4,1)$ and $(5,2,-2)$. Compute $\det(A)$ by cofactor expansion along the second row.

- A) $-85$
- B) $35$
- C) $85$
- D) $-67$

> [!success]- Answer
> **A.** The signs of row 2 are $-,+,-$. Since $a_{21}=0$, the first term is 0.
> $M_{22}=\begin{vmatrix}2&3\\5&-2\end{vmatrix}=-4-15=-19$ and $M_{23}=\begin{vmatrix}2&-1\\5&2\end{vmatrix}=4+5=9$.
> $\det(A)=0+4\cdot(-19)-1\cdot9=-76-9=-85$. Column 1 gives the same: $2\cdot(-10)+5\cdot(-13)=-85$.
> - B: $M_{22}$ is computed as $ad+bc=-4+15=11$: $4\cdot11-9=35$.
> - C: The signs $+,-,+$ of row 1 are used on row 2: $-4\cdot(-19)+1\cdot9=85$.
> - D: The cofactor signs are left out: $4\cdot(-19)+1\cdot9=-67$.

### Q12 (slide 7, a 4 by 4 determinant)

$A$ has the rows $(2,0,1,0)$, $(1,3,-1,2)$, $(0,0,4,0)$ and $(3,1,2,1)$. Compute $\det(A)$.

- A) $8$
- B) $2$
- C) $-8$
- D) $24$

> [!success]- Answer
> **A.** Row 3 has one nonzero entry, $a_{33}=4$. Expand along row 3: $\det(A)=(-1)^{3+3}\cdot4\cdot M_{33}$.
> $M_{33}$ has the rows $(2,0,0)$, $(1,3,2)$, $(3,1,1)$. Along its first row: $M_{33}=2\begin{vmatrix}3&2\\1&1\end{vmatrix}=2\,(3-2)=2$.
> $\det(A)=4\cdot2=8$.
> - B: The entry $a_{33}=4$ is forgotten: only $M_{33}=2$ is kept.
> - C: Cofactor sign slip: $(-1)^{3+3}$ is taken as $-1$. But $3+3$ is even.
> - D: The diagonal entries are multiplied: $2\cdot3\cdot4\cdot1=24$. That rule holds only for triangular matrices, and $A$ is not triangular.

### Q13 (slide 7, zero rows and triangular matrices)

Find the determinant of the matrix with the rows $(0,0,3)$, $(0,2,1)$ and $(4,5,6)$.

- A) $0$
- B) $24$
- C) $21$
- D) $-24$

> [!success]- Answer
> **D.** The matrix is not triangular: $a_{13}=3$ is above and $a_{31}=4$ is below the main diagonal (top left to bottom right).
> Expand along row 1, where only $a_{13}=3$ is nonzero:
> $\det=(-1)^{1+3}\cdot3\cdot\begin{vmatrix}0&2\\4&5\end{vmatrix}=3\,(0\cdot5-2\cdot4)=-24$.
> - A: The triangular rule is used on a matrix that is not triangular: $0\cdot2\cdot6=0$.
> - B: Cofactor sign slip: $(-1)^{1+3}$ is taken as $-1$, so $-3\cdot(-8)=24$.
> - C: The wrong minor: row 1 and column 1 are deleted instead of row 1 and column 3, so $3\begin{vmatrix}2&1\\5&6\end{vmatrix}=3\cdot7=21$.

## 5. Transpose and row operations (slides 8-9)

### Q14 (slide 8, the rules)

$A$ is a $3\times3$ matrix with $\det(A)=5$. $B$ is $A$ with rows 1 and 3 interchanged. What are $\det(B)$ and $\det(2A)$?

- A) $\det(B)=5$, $\det(2A)=10$
- B) $\det(B)=-5$, $\det(2A)=10$
- C) $\det(B)=-5$, $\det(2A)=40$
- D) $\det(B)=5$, $\det(2A)=40$

> [!success]- Answer
> **C.** Interchanging two rows multiplies the determinant by $-1$: $\det(B)=-5$.
> $2A$ multiplies each of the 3 rows by 2, and each row gives one factor 2: $\det(2A)=2^3\cdot5=40$.
> - A: Two slips: the row swap is taken to keep the sign, and $\det(2A)$ is taken as $2\det(A)$.
> - B: $\det(kA)$ is taken as $k\det(A)$. For an $n\times n$ matrix it is $k^n\det(A)$.
> - D: The row swap is taken to keep the sign of the determinant.

### Q15 (slide 8, proportional rows)

$A$ has the rows $(1,2,-1)$, $(3,t,-3)$ and $(0,1,4)$. Compute $\det(A)$ as a function of $t$ by expansion along the first row.

- A) $4t+24$
- B) $24-4t$
- C) $4t-24$
- D) $4t-18$

> [!success]- Answer
> **C.** The minors of row 1: $\begin{vmatrix}t&-3\\1&4\end{vmatrix}=4t+3$, $\begin{vmatrix}3&-3\\0&4\end{vmatrix}=12$, $\begin{vmatrix}3&t\\0&1\end{vmatrix}=3$.
> $\det(A)=1\cdot(4t+3)-2\cdot12+(-1)\cdot3=4t-24$.
> It is 0 for $t=6$: then row 2 is $(3,6,-3)=3\cdot$ row 1, and proportional rows give determinant 0.
> - A: The minus sign of the middle cofactor is forgotten: $(4t+3)+2\cdot12-3=4t+24$.
> - B: The checkerboard is started with $-$: signs $-,+,-$ give $-(4t+3)+24+3=24-4t$.
> - D: The minus sign of the entry $a_{13}=-1$ is lost: $(4t+3)-24+3=4t-18$.

### Q16 (slide 8, products, beyond the slides)

$A$ has the rows $(2,1)$ and $(1,3)$. $B$ has the rows $(1,4)$ and $(2,-1)$. What are $\det(AB)$ and $\det(A^{-1})$?

- A) $\det(AB)=-4$, $\det(A^{-1})=5$
- B) $\det(AB)=-45$, $\det(A^{-1})=1/5$
- C) $\det(AB)=-45$, $\det(A^{-1})=5$
- D) $\det(AB)=-4$, $\det(A^{-1})=1/5$

> [!success]- Answer
> **B.** $\det(A)=6-1=5$ and $\det(B)=-1-8=-9$, so $\det(AB)=\det(A)\det(B)=-45$.
> Direct check: $AB=\begin{pmatrix}4&7\\7&1\end{pmatrix}$, $\det(AB)=4-49=-45$.
> From $AA^{-1}=\mathcal I_2$: $\det(A)\det(A^{-1})=1$, so $\det(A^{-1})=\tfrac15$.
> - A: Two slips: the product rule is used as a sum, $5+(-9)=-4$, and $A^{-1}$ is given the determinant of $A$.
> - C: $A^{-1}$ is given the same determinant as $A$. It has $1/\det(A)$.
> - D: The product rule is used as a sum: $\det(A)+\det(B)=-4$.

### Q17 (slide 9)

$A$ has the rows $(0,2,-4)$, $(2,4,6)$ and $(3,1,5)$. Compute $\det(A)$ by row reduction to triangular form.

- A) $-56$
- B) $14$
- C) $7/2$
- D) $56$

> [!success]- Answer
> **D.** Swap rows 1 and 2 (factor $-1$). Pull 2 out of the new row 1 (factor 2): rows $(1,2,3)$, $(0,2,-4)$, $(3,1,5)$.
> $R_3-3R_1$ gives $(0,-5,-4)$ (no change). Pull 2 out of row 2 (factor 2): $(0,1,-2)$. $R_3+5R_2$ gives $(0,0,-14)$ (no change).
> $\det(A)=(-1)\cdot2\cdot2\cdot(1\cdot1\cdot(-14))=56$. Check along row 1: $-2\,(10-18)-4\,(2-12)=16+40=56$.
> - A: The row swap is taken to keep the sign: $2\cdot2\cdot(-14)=-56$.
> - B: The two factors 2 are pulled out but not put in front: $(-1)\cdot(-14)=14$.
> - C: The factor $\tfrac12$ is put in front instead of 2 for each pulled-out row: $(-1)\cdot\tfrac12\cdot\tfrac12\cdot(-14)=\tfrac72$.
