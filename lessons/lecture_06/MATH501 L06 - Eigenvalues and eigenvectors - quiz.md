---
course: MATH 501 Advanced Engineering Mathematics
lesson: MATH501 L06 - Eigenvalues and eigenvectors
type: quiz
questions: 18
---

# MATH501 L06 - Eigenvalues and eigenvectors - quiz

Lesson note: [[MATH501 L06 - Eigenvalues and eigenvectors]]. One question per check question of the lesson. Pick an option, then open the answer.

## 1. Eigenvalues and the characteristic polynomial (slides 1-3)

### Q1 (slide 1)

$A$ has the rows $(2,0,1)$, $(0,3,0)$ and $(1,0,2)$. Let $v=(1,0,-1)$, $w=(1,0,1)$ and $u=(1,1,0)$. Which of $v$, $w$, $u$ are eigenvectors of $A$, and for which eigenvalue is $5v$ an eigenvector?

- A) $v$, $w$ and $u$; $5v$ has $\lambda=5$
- B) $v$ and $w$ only; $5v$ has $\lambda=5$
- C) $v$, $w$ and $u$; $5v$ has $\lambda=1$
- D) $v$ and $w$ only; $5v$ has $\lambda=1$

> [!success]- Answer
> **D.** Multiply each vector by $A$ and see if the result is a multiple of the vector.
> $Av=(2-1,\ 0,\ 1-2)=(1,0,-1)=1\cdot v$: eigenvector, $\lambda=1$. $Aw=(2+1,\ 0,\ 1+2)=(3,0,3)=3\cdot w$: eigenvector, $\lambda=3$.
> $Au=(2,3,1)$. This is not a multiple of $u=(1,1,0)$: the third entry is 1, not 0. So $u$ is not an eigenvector.
> $A(5v)=5(Av)=5v=1\cdot(5v)$. So $5v$ is an eigenvector for the same $\lambda=1$.
> - A: Two slips: $u$ is judged by its first entry only ($2=2\cdot1$), and the eigenvalue is multiplied by 5 together with the vector.
> - B: Right vectors, but the factor 5 goes into the eigenvalue. A multiple of an eigenvector keeps the same eigenvalue.
> - C: $u$ is judged by the first entry of $Au$ only. The second entry needs $\lambda=3$ and the third does not fit at all.

### Q2 (slide 2, a 2 by 2 matrix)

$A$ has the rows $(1,2)$ and $(3,-4)$. Find the characteristic polynomial $p_A(\lambda)=\det(\lambda\mathcal I_2-A)$ and the eigenvalues.

- A) $p_A=\lambda^2+3\lambda-10$; eigenvalues $2$ and $-5$
- B) $p_A=\lambda^2-3\lambda-10$; eigenvalues $5$ and $-2$
- C) $p_A=\lambda^2+10\lambda-3$; eigenvalues $-5\pm2\sqrt7$
- D) $p_A=\lambda^2+3\lambda+2$; eigenvalues $-1$ and $-2$

> [!success]- Answer
> **A.** $\lambda\mathcal I_2-A=\begin{pmatrix}\lambda-1&-2\\-3&\lambda+4\end{pmatrix}$.
> $p_A(\lambda)=(\lambda-1)(\lambda+4)-(-2)(-3)=\lambda^2+3\lambda-4-6=\lambda^2+3\lambda-10=(\lambda-2)(\lambda+5)$.
> Eigenvalues $2$ and $-5$. Check: sum $-3=\operatorname{tr}(A)=1-4$, product $-10=\det(A)=-4-6$.
> - B: Sign slip in the $\lambda$ term: $\lambda^2+\operatorname{tr}(A)\lambda+\det(A)$ instead of $\lambda^2-\operatorname{tr}(A)\lambda+\det(A)$.
> - C: Trace and determinant swapped: $\lambda^2-\det(A)\,\lambda+\operatorname{tr}(A)=\lambda^2+10\lambda-3$.
> - D: Sign slip in the off-diagonal product: $(\lambda-1)(\lambda+4)+6$ instead of $-6$.

### Q3 (slide 2, a 3 by 3 matrix)

$A$ has the rows $(4,1,1)$, $(1,4,1)$ and $(1,1,4)$. What is $p_A(\lambda)=\det(\lambda\mathcal I_3-A)$ in factored form?

- A) $(\lambda-3)(\lambda-4)(\lambda-5)$
- B) $(\lambda-3)^2(\lambda-6)$
- C) $(\lambda-4)^3$
- D) $(\lambda-5)^2(\lambda-2)$

> [!success]- Answer
> **B.** $\lambda\mathcal I_3-A$ has $\lambda-4$ on the diagonal and $-1$ everywhere else. Expand along row 1 with the signs $+,-,+$:
> $p_A=(\lambda-4)\bigl[(\lambda-4)^2-1\bigr]-(-1)\bigl[-(\lambda-4)-1\bigr]+(-1)\bigl[1+(\lambda-4)\bigr]=(\lambda-4)(\lambda-5)(\lambda-3)-2(\lambda-3)$.
> Factor out $(\lambda-3)$: $(\lambda-3)(\lambda^2-9\lambda+18)=(\lambda-3)^2(\lambda-6)$.
> Check: $3+3+6=12=\operatorname{tr}(A)$ and $3\cdot3\cdot6=54=\det(A)$.
> - A: The middle cofactor sign is dropped (signs $+,+,+$). The two last terms then cancel.
> - C: The triangular shortcut is used on a matrix that is not triangular.
> - D: The off-diagonal entries of $\lambda\mathcal I_3-A$ are written as $+1$ instead of $-1$.

### Q4 (slide 2, complex roots)

$A$ has the rows $(1,-2)$ and $(1,3)$. Find its eigenvalues. For the eigenvalue with positive imaginary part, find the eigenvector with second entry 1.

- A) $2\pm2i$; $v=(-1-2i,\ 1)$
- B) $2\pm i$; $v=(-1-i,\ 1)$
- C) $2\pm i$; $v=(-1+i,\ 1)$
- D) $2\pm2i$; $v=(-1+2i,\ 1)$

> [!success]- Answer
> **C.** $p_A=(\lambda-1)(\lambda-3)-(2)(-1)=\lambda^2-4\lambda+5$. So $\lambda=\dfrac{4\pm\sqrt{16-20}}{2}=\dfrac{4\pm2i}{2}=2\pm i$.
> For $\lambda=2+i$: $\lambda\mathcal I_2-A=\begin{pmatrix}1+i&2\\-1&-1+i\end{pmatrix}$. Row 2: $-x_1+(-1+i)x_2=0$, so $x_1=(-1+i)x_2$.
> With $x_2=1$: $v=(-1+i,\ 1)$. Check: $Av=(-3+i,\ 2+i)=(2+i)v$.
> - A: Two slips: only the 4 is divided by 2 (so $2\pm2i$), and then the eigenvector of the conjugate eigenvalue is taken.
> - B: This is the eigenvector of $2-i$, the other eigenvalue (all signs of $i$ flipped).
> - D: Only the 4 is divided by 2 in the quadratic formula. $2+2i$ is not an eigenvalue, so this $v$ is not an eigenvector.

## 2. Eigenvectors (slides 3-5)

### Q5 (slide 3, triangular matrices)

(a) $L$ has the rows $(5,0,0)$, $(2,-1,0)$ and $(7,3,5)$. What are its eigenvalues? (b) $B$ has the rows $(0,1)$ and $(1,0)$. What are its eigenvalues?

- A) (a) $5,-1,5$; (b) $1$ and $-1$
- B) (a) $-5,1,-5$; (b) $1$ and $-1$
- C) (a) $5,-1,5$; (b) $0$ and $0$
- D) (a) $-5,1,-5$; (b) $0$ and $0$

> [!success]- Answer
> **A.** (a) $L$ is lower triangular, so $\lambda\mathcal I_3-L$ is triangular with the diagonal $\lambda-5$, $\lambda+1$, $\lambda-5$. $p_L=(\lambda-5)^2(\lambda+1)$: eigenvalues $5,-1,5$.
> (b) $B$ is not triangular ($b_{12}=b_{21}=1$), so the diagonal shortcut does not apply.
> $p_B=\lambda\cdot\lambda-(-1)(-1)=\lambda^2-1=(\lambda-1)(\lambda+1)$: eigenvalues $1$ and $-1$.
> - B: Sign slip in (a): the diagonal of $\lambda\mathcal I_3-L$ is written as $\lambda+5$, $\lambda-1$, $\lambda+5$.
> - C: In (b) the diagonal is read off a matrix that is not triangular.
> - D: Both slips: the sign slip in (a) and the diagonal shortcut in (b).

### Q6 (slides 3-4)

$A$ has the rows $(2,1)$ and $(3,4)$. Find the eigenvalues, then an eigenvector for each, scaled so that its first entry is 1. The first vector belongs to the larger eigenvalue.

- A) $(1,-7)$ and $(1,-3)$
- B) $(1,-1)$ and $(1,3)$
- C) $(1,3)$ and $(1,-1)$
- D) $(1,-3)$ and $(1,1)$

> [!success]- Answer
> **C.** $p_A=(\lambda-2)(\lambda-4)-3=\lambda^2-6\lambda+5=(\lambda-5)(\lambda-1)$. The eigenvalues are $5$ and $1$.
> $\lambda=5$: $5\mathcal I_2-A=\begin{pmatrix}3&-1\\-3&1\end{pmatrix}$, so $3x_1-x_2=0$ and $x_2=3x_1$. With $x_1=1$: $(1,3)$.
> $\lambda=1$: $\mathcal I_2-A=\begin{pmatrix}-1&-1\\-3&-3\end{pmatrix}$, so $x_2=-x_1$. With $x_1=1$: $(1,-1)$.
> Check: $A(1,3)^{\mathsf T}=(5,15)^{\mathsf T}=5(1,3)^{\mathsf T}$ and $A(1,-1)^{\mathsf T}=(1,-1)^{\mathsf T}$.
> - A: Row 1 of $A+\lambda\mathcal I_2$ is used instead of $\lambda\mathcal I_2-A$: $7x_1+x_2=0$ and $3x_1+x_2=0$.
> - B: The right vectors, matched to the wrong eigenvalues.
> - D: Sign slip when solving each equation: $x_2=-3x_1$ and $x_2=x_1$.

### Q7 (slides 4-5, a double root with two eigenvectors)

$A$ has the rows $(2,0,0)$, $(0,3,1)$ and $(0,1,3)$, with $p_A(\lambda)=(\lambda-2)^2(\lambda-4)$. Solve $(2\mathcal I_3-A)x=\mathbf O$, writing $x_2$ in terms of $x_3$. Set each free variable to 1 in turn (the others 0). Which eigenvectors for $\lambda=2$ do you get, and what is the geometric multiplicity of $\lambda=2$?

- A) only $(0,1,1)$; geometric multiplicity 1
- B) $(1,0,0)$ and $(0,1,1)$; geometric multiplicity 2
- C) only $(0,-1,1)$; geometric multiplicity 1
- D) $(1,0,0)$ and $(0,-1,1)$; geometric multiplicity 2

> [!success]- Answer
> **D.** $2\mathcal I_3-A=\begin{pmatrix}0&0&0\\0&-1&-1\\0&-1&-1\end{pmatrix}$. The only equation is $-x_2-x_3=0$, so $x_2=-x_3$.
> $x_1$ appears in no equation, so $x_1$ and $x_3$ are free. $(x_1,x_3)=(1,0)$ gives $(1,0,0)$, and $(0,1)$ gives $(0,-1,1)$.
> Two free variables: geometric multiplicity 2, equal to the algebraic multiplicity 2. This fits the symmetry $A^{\mathsf T}=A$.
> The eigenvector for $\lambda=4$ is $(0,1,1)$. It is orthogonal to both: $(0,1,1)\cdot(1,0,0)=0$ and $(0,1,1)\cdot(0,-1,1)=0$.
> - A: The system of the other eigenvalue is solved: $(4\mathcal I_3-A)x=\mathbf O$ gives $x_1=0$ and $x_2=x_3$. $(0,1,1)$ belongs to $\lambda=4$.
> - B: Sign slip: $x_2=x_3$. Then $(0,1,1)$ is the eigenvector of $\lambda=4$, not of $\lambda=2$.
> - C: The zero row is read as $x_1=0$. A zero row gives no condition, so $x_1$ is free.

### Q8 (slide 5, a double root with one eigenvector)

$A$ has the rows $(3,1,0)$, $(0,3,0)$ and $(0,0,5)$. The eigenvalue $\lambda=3$ is a double root of $p_A$. What is its geometric multiplicity, and what are its eigenvectors?

- A) Geometric multiplicity 2; combinations of $(1,0,0)$ and $(0,1,0)$
- B) Geometric multiplicity 1; the nonzero multiples of $(0,1,0)$
- C) Geometric multiplicity 1; the nonzero multiples of $(1,0,0)$
- D) Geometric multiplicity 2; combinations of $(1,0,0)$ and $(0,0,1)$

> [!success]- Answer
> **C.** $3\mathcal I_3-A=\begin{pmatrix}0&-1&0\\0&0&0\\0&0&-2\end{pmatrix}$.
> Row 1: $-x_2=0$, so $x_2=0$. Row 3: $-2x_3=0$, so $x_3=0$. Only $x_1$ is free.
> Eigenvectors: $x_1(1,0,0)$ with $x_1\neq0$. One free variable: geometric multiplicity 1, less than the algebraic multiplicity 2.
> - A: The geometric multiplicity is taken equal to the algebraic one, and $x_2$ is treated as free. Row 1 forces $x_2=0$.
> - B: Row 1, $-x_2=0$, is read as "$x_1=0$, $x_2$ free". Check: $A(0,1,0)^{\mathsf T}=(1,3,0)^{\mathsf T}$, not a multiple of $(0,1,0)$.
> - D: $(0,0,1)$ is the eigenvector of $\lambda=5$. It does not belong to $\lambda=3$: $A(0,0,1)^{\mathsf T}=5(0,0,1)^{\mathsf T}$.

## 3. Cayley-Hamilton theorem and linear independence of vectors (slides 5-7)

### Q9 (slides 5-6, inverse)

$A$ has the rows $(1,0,2)$, $(0,1,1)$ and $(1,0,1)$. Use the Cayley-Hamilton theorem to find $A^{-1}$.

- A) $\begin{pmatrix}1&0&-2\\1&-1&-1\\-1&0&1\end{pmatrix}$
- B) $\begin{pmatrix}-1&0&2\\-1&1&1\\1&0&-1\end{pmatrix}$
- C) $\begin{pmatrix}0&0&2\\-1&2&1\\1&0&0\end{pmatrix}$
- D) $\begin{pmatrix}1&0&2\\-1&3&1\\1&0&1\end{pmatrix}$

> [!success]- Answer
> **B.** Expand $\det(\lambda\mathcal I_3-A)$ along column 2: $p_A=(\lambda-1)\bigl[(\lambda-1)^2-2\bigr]=\lambda^3-3\lambda^2+\lambda+1$.
> Cayley-Hamilton: $A^3-3A^2+A+\mathcal I_3=O$, so $A(A^2-3A+\mathcal I_3)=-\mathcal I_3$ and $A^{-1}=-A^2+3A-\mathcal I_3$.
> $A^2=\begin{pmatrix}3&0&4\\1&1&2\\2&0&3\end{pmatrix}$, so $A^{-1}=\begin{pmatrix}-3+3-1&0&-4+6\\-1&-1+3-1&-2+3\\-2+3&0&-3+3-1\end{pmatrix}=\begin{pmatrix}-1&0&2\\-1&1&1\\1&0&-1\end{pmatrix}$.
> Check: row 1 of $AA^{-1}$ is $(-1+2,\ 0,\ 2-2)=(1,0,0)$, and so on.
> - A: The minus sign of $-\mathcal I_3$ is forgotten: this is $A^2-3A+\mathcal I_3=-A^{-1}$.
> - C: The $\mathcal I_3$ term is dropped: this is $-A^2+3A$.
> - D: Only the $A^2$ and $A$ terms change sign: this is $-A^2+3A+\mathcal I_3$.

### Q10 (slide 6, higher powers)

$A$ has the rows $(3,1)$ and $(2,-1)$. Use the Cayley-Hamilton theorem to write $A^2$ and $A^3$ in the form $\alpha A+\beta\mathcal I_2$.

- A) $A^2=-2A+5\mathcal I_2$, $A^3=9A-10\mathcal I_2$
- B) $A^2=-5A-2\mathcal I_2$, $A^3=23A+10\mathcal I_2$
- C) $A^2=2A-5\mathcal I_2$, $A^3=-A-10\mathcal I_2$
- D) $A^2=2A+5\mathcal I_2$, $A^3=9A+10\mathcal I_2$

> [!success]- Answer
> **D.** $p_A=(\lambda-3)(\lambda+1)-2=\lambda^2-2\lambda-5$. Cayley-Hamilton: $A^2-2A-5\mathcal I_2=O$, so $A^2=2A+5\mathcal I_2$.
> $A^3=A\cdot A^2=2A^2+5A=2(2A+5\mathcal I_2)+5A=9A+10\mathcal I_2$.
> Check: $A^2=\begin{pmatrix}11&2\\4&3\end{pmatrix}=2A+5\mathcal I_2$, and $A^3=\begin{pmatrix}37&9\\18&1\end{pmatrix}=9A+10\mathcal I_2$.
> - A: Sign slip in the $\lambda$ term: $p_A=\lambda^2+2\lambda-5$.
> - B: Trace and determinant swapped: $p_A=\lambda^2-\det(A)\lambda+\operatorname{tr}(A)=\lambda^2+5\lambda+2$.
> - C: $-5\mathcal I_2$ is moved to the other side without changing its sign: $A^2=2A-5\mathcal I_2$.

### Q11 (slides 6-7, linear dependence)

Are $\vec v_1=(1,2,3)$, $\vec v_2=(2,-1,1)$, $\vec v_3=(4,3,7)$ linearly independent? If not, which relation holds?

- A) Dependent: $\vec v_3=\vec v_1+2\vec v_2$
- B) Independent: only $\alpha_1=\alpha_2=\alpha_3=0$
- C) Dependent: $\vec v_3=2\vec v_1+\vec v_2$
- D) Dependent: $\vec v_3=-2\vec v_1-\vec v_2$

> [!success]- Answer
> **C.** Solve $\alpha_1\vec v_1+\alpha_2\vec v_2+\alpha_3\vec v_3=\vec 0$: (1) $\alpha_1+2\alpha_2+4\alpha_3=0$, (2) $2\alpha_1-\alpha_2+3\alpha_3=0$, (3) $3\alpha_1+\alpha_2+7\alpha_3=0$.
> (2) minus 2 times (1): $-5\alpha_2-5\alpha_3=0$, so $\alpha_2=-\alpha_3$. Then (1) gives $\alpha_1=-2\alpha_3$. (3) gives $-6\alpha_3-\alpha_3+7\alpha_3=0$: no condition.
> With $\alpha_3=1$: $-2\vec v_1-\vec v_2+\vec v_3=\vec 0$, so the vectors are dependent and $\vec v_3=2\vec v_1+\vec v_2$.
> Check: $2(1,2,3)+(2,-1,1)=(4,3,7)$.
> - A: The two coefficients are swapped: $\vec v_1+2\vec v_2=(5,0,5)$.
> - B: Sign slip $\alpha_2=\alpha_3$. Then $\alpha_1=-6\alpha_3$, and (3) gives $-10\alpha_3=0$, so only the zero solution seems to remain.
> - D: The relation $-2\vec v_1-\vec v_2+\vec v_3=\vec 0$ is solved for $\vec v_3$ without moving the terms to the other side.

### Q12 (slide 7, the three quick rules)

Decide without solving a system. (i) $(2,-6,4)$ and $(-3,9,-6)$. (ii) $(1,2,3)$ and $(2,4,5)$.

- A) (i) dependent; (ii) independent
- B) (i) independent; (ii) dependent
- C) (i) dependent; (ii) dependent
- D) (i) independent; (ii) independent

> [!success]- Answer
> **A.** Two vectors are dependent exactly when one is a multiple of the other. Compare the ratios of all entries.
> (i) $\dfrac{-3}{2}=\dfrac{9}{-6}=\dfrac{-6}{4}=-\dfrac32$. So $(-3,9,-6)=-\tfrac32(2,-6,4)$: dependent.
> (ii) $\dfrac21=\dfrac42=2$, but $\dfrac53\neq2$. Not multiples: independent.
> (The third quick rule: a set that contains the zero vector is always dependent.)
> - B: Both slips: in (i) the sign change is taken as "not a multiple", and in (ii) only the first two ratios are compared.
> - C: In (ii) only the first two ratios are compared. The third ratio is $\tfrac53$, not 2.
> - D: In (i) the different signs are taken as "not a multiple". A negative factor $-\tfrac32$ is allowed.

### Q13 (slide 7, determinant test)

For which $k$ are $\vec v_1=(1,0,2)$, $\vec v_2=(2,1,0)$, $\vec v_3=(0,1,k)$ linearly dependent, and which relation holds for that $k$?

- A) $k=4$; $\vec v_3=2\vec v_1+\vec v_2$
- B) $k=-4$; $\vec v_3=2\vec v_1+\vec v_2$
- C) $k=4$; $\vec v_3=-2\vec v_1+\vec v_2$
- D) $k=-4$; $\vec v_3=-2\vec v_1+\vec v_2$

> [!success]- Answer
> **D.** Put the vectors as columns: $V=\begin{pmatrix}1&2&0\\0&1&1\\2&0&k\end{pmatrix}$. Along row 1: $\det(V)=1\cdot(k-0)-2\cdot(0-2)+0=k+4$.
> Dependent exactly when $\det(V)=0$: $k=-4$.
> Then $a\vec v_1+b\vec v_2=(0,1,-4)$: entry 2 gives $b=1$, entry 3 gives $2a=-4$, so $a=-2$. Entry 1: $-2+2=0$. True.
> So $\vec v_3=-2\vec v_1+\vec v_2$.
> - A: Cofactor sign slip ($+2$ instead of $-2$) gives $\det(V)=k-4$ and $k=4$. Then $2a=4$ from entry 3, and entry 1 ($2+2=4\neq0$) is not checked.
> - B: Right $k$, but sign slip in $2a=-4$: $a=2$. Entry 1 fails: $2+2\neq0$.
> - C: Cofactor sign slip ($k=4$). The relation is then found from entries 1 and 2 only, which do not contain $k$. Entry 3 is not checked: $2\cdot(-2)=-4\neq4$.

## 4. Diagonalization (slides 8-9)

### Q14 (slide 8, similar matrices)

$A$ has the rows $(1,2)$ and $(0,3)$. $P$ has the rows $(1,1)$ and $(1,2)$. Compute $B=P^{-1}AP$.

- A) $\begin{pmatrix}-3&4\\-6&7\end{pmatrix}$
- B) $\begin{pmatrix}3&4\\0&1\end{pmatrix}$
- C) $\begin{pmatrix}9&16\\6&11\end{pmatrix}$
- D) $\begin{pmatrix}0&-1\\3&7\end{pmatrix}$

> [!success]- Answer
> **B.** $\det(P)=2-1=1$, so $P^{-1}=\begin{pmatrix}2&-1\\-1&1\end{pmatrix}$.
> $AP=\begin{pmatrix}3&5\\3&6\end{pmatrix}$ and $B=P^{-1}(AP)=\begin{pmatrix}6-3&10-6\\-3+3&-5+6\end{pmatrix}=\begin{pmatrix}3&4\\0&1\end{pmatrix}$.
> $A$ and $B$ have the same eigenvalues ($1$ and $3$), trace ($4$) and determinant ($3$). $B$ is not diagonal, because the column $(1,2)$ of $P$ is not an eigenvector of $A$.
> - A: The order is reversed: this is $PAP^{-1}$.
> - C: In $P^{-1}$ the off-diagonal signs are not changed: $\begin{pmatrix}2&1\\1&1\end{pmatrix}AP$.
> - D: In $P^{-1}$ the diagonal entries are not swapped: $\begin{pmatrix}1&-1\\-1&2\end{pmatrix}AP$.

### Q15 (slides 8-9)

$A$ has the rows $(5,-2)$ and $(4,-1)$. Find $P$ and a diagonal $D$ with $P^{-1}AP=D$. Put the eigenvalues in increasing order along $D$, and scale each column of $P$ so that its first entry is 1. What is $P$?

- A) $P=\begin{pmatrix}1&1\\2&1\end{pmatrix}$
- B) $P=\begin{pmatrix}1&1\\1&2\end{pmatrix}$
- C) $P=\begin{pmatrix}1&1\\3&4\end{pmatrix}$
- D) $P=\begin{pmatrix}1&1\\-2&-1\end{pmatrix}$

> [!success]- Answer
> **A.** $p_A=(\lambda-5)(\lambda+1)+8=\lambda^2-4\lambda+3=(\lambda-1)(\lambda-3)$, so $D=\operatorname{diag}(1,3)$.
> $\lambda=1$: $\mathcal I_2-A=\begin{pmatrix}-4&2\\-4&2\end{pmatrix}$, $x_2=2x_1$: $(1,2)$. $\lambda=3$: $3\mathcal I_2-A=\begin{pmatrix}-2&2\\-4&4\end{pmatrix}$, $x_2=x_1$: $(1,1)$.
> $P=\begin{pmatrix}1&1\\2&1\end{pmatrix}$, $P^{-1}=\begin{pmatrix}-1&1\\2&-1\end{pmatrix}$, and $P^{-1}AP=\begin{pmatrix}1&0\\0&3\end{pmatrix}$.
> Swapping the columns of $P$ would swap the entries of $D$ to $\operatorname{diag}(3,1)$.
> - B: The eigenvectors are put in the wrong columns: column 1 is the eigenvector of $\lambda=3$.
> - C: Row 1 of $A+\lambda\mathcal I_2$ is used: $6x_1-2x_2=0$ and $8x_1-2x_2=0$.
> - D: Sign slip when solving each equation: $x_2=-2x_1$ and $x_2=-x_1$.

### Q16 (slide 8, a 3 by 3 matrix)

$A$ has the rows $(0,0,-2)$, $(1,2,1)$ and $(1,0,3)$. Its eigenvectors are $(-2,1,1)$ for $\lambda=1$, and $(0,1,0)$ and $(-1,0,1)$ for $\lambda=2$. $P$ has these three vectors as columns, in this order. Is $A$ diagonalizable, and if so, what is $P^{-1}AP$?

- A) Yes; $P^{-1}AP=\operatorname{diag}(1,2,2)$
- B) No; the eigenvalue 2 is repeated
- C) Yes; $P^{-1}AP=\operatorname{diag}(2,2,1)$
- D) No; the eigenvectors are not orthogonal

> [!success]- Answer
> **A.** Expand $\det(P)$ along column 2 (only the entry 1 in position $(2,2)$): $\det(P)=\begin{vmatrix}-2&-1\\1&1\end{vmatrix}=-2+1=-1\neq0$.
> So the three eigenvectors are independent, and $A$ is diagonalizable.
> $D$ lists the eigenvalues in the order of the columns of $P$: $D=\operatorname{diag}(1,2,2)$. Check column 1: $A(-2,1,1)^{\mathsf T}=(-2,1,1)^{\mathsf T}$.
> - B: A repeated eigenvalue does not decide it. What counts is the number of independent eigenvectors: here 3.
> - C: The eigenvalues are put in decreasing order, not in the order of the columns of $P$.
> - D: Orthogonal eigenvectors are a property of symmetric matrices. Diagonalizable only needs independent eigenvectors.

## 5. Powers of a diagonalizable matrix (slides 10-11)

### Q17 (slide 10)

(a) $D=\operatorname{diag}(2,-1,\tfrac12)$. Find $D^4$. (b) $A$ has the eigenvalue $-2$ with eigenvector $v$. Find $A^5v$.

- A) $D^4=\operatorname{diag}(16,1,\tfrac1{16})$; $A^5v=-10\,v$
- B) $D^4=\operatorname{diag}(16,1,\tfrac1{16})$; $A^5v=-32\,v$
- C) $D^4=\operatorname{diag}(8,-4,2)$; $A^5v=-10\,v$
- D) $D^4=\operatorname{diag}(8,-4,2)$; $A^5v=-32\,v$

> [!success]- Answer
> **B.** (a) Raise each diagonal entry to the power 4: $2^4=16$, $(-1)^4=1$, $(\tfrac12)^4=\tfrac1{16}$.
> (b) $A^2v=A(-2v)=-2Av=(-2)^2v$, and so on: $A^5v=(-2)^5v=-32\,v$.
> (Why $A^k=PD^kP^{-1}$: $D^2=(P^{-1}AP)(P^{-1}AP)=P^{-1}A^2P$, since the inner $PP^{-1}$ cancels.)
> - A: In (b) the power is replaced by a product: $5\cdot(-2)=-10$.
> - C: Both parts use multiplication instead of the power: $4D$ and $5\cdot(-2)$.
> - D: In (a) the power is replaced by a product: $4D=\operatorname{diag}(8,-4,2)$.

### Q18 (slides 10-11)

$A$ has the rows $(-1,3)$ and $(-2,4)$. $P$ has the rows $(3,1)$ and $(2,1)$, $D=\operatorname{diag}(1,2)$, and $P^{-1}AP=D$. $P^{-1}$ has the rows $(1,-1)$ and $(-2,3)$. Compute $A^5$.

- A) $\begin{pmatrix}-5&15\\-10&20\end{pmatrix}$
- B) $\begin{pmatrix}-61&93\\-62&94\end{pmatrix}$
- C) $\begin{pmatrix}-61&-31\\186&94\end{pmatrix}$
- D) $\begin{pmatrix}-1&243\\-32&1024\end{pmatrix}$

> [!success]- Answer
> **B.** $A^5=PD^5P^{-1}$ with $D^5=\operatorname{diag}(1,32)$.
> $PD^5=\begin{pmatrix}3&32\\2&32\end{pmatrix}$, and $A^5=\begin{pmatrix}3&32\\2&32\end{pmatrix}\begin{pmatrix}1&-1\\-2&3\end{pmatrix}=\begin{pmatrix}3-64&-3+96\\2-64&-2+96\end{pmatrix}=\begin{pmatrix}-61&93\\-62&94\end{pmatrix}$.
> In general $A^k=\begin{pmatrix}3-2\cdot2^k&3\cdot2^k-3\\2-2\cdot2^k&3\cdot2^k-2\end{pmatrix}$. $k=1$ gives $A$. The eigenvalues of $A^5$ are $1$ and $32$.
> - A: $D^5$ is taken as $5D$, which gives $5A$.
> - C: The order is reversed: this is $P^{-1}D^5P$.
> - D: Each entry of $A$ is raised to the power 5. Matrix powers do not work entry by entry.
