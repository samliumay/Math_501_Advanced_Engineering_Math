---
course: MATH 501 Advanced Engineering Mathematics
lesson: MATH501 L07 - Linear systems of ODEs
type: quiz
questions: 20
---

# MATH501 L07 - Linear systems of ODEs - quiz

Lesson note: [[MATH501 L07 - Linear systems of ODEs]]. One question per check question of the lesson. Pick an option, then open the answer.

## 1. Linear systems, matrix form, initial value problems (slides 1-2)

### Q1 (slide 1)

Write the system $x_1'=2x_1-t\,x_3+\cos t$, $x_2'=x_1+e^{t}x_2$, $x_3'=-x_2+4x_3-5$ in the form $X'=A(t)X+F(t)$ with $X=(x_1,x_2,x_3)^{\mathsf T}$. Which matrix is $A(t)$? (The rows are listed from top to bottom.)

- A) Rows $(2,-t,0)$, $(1,e^{t},0)$, $(-1,4,0)$
- B) Rows $(2,1,0)$, $(0,e^{t},-1)$, $(-t,0,4)$
- C) Rows $(2,0,-t)$, $(1,e^{t},0)$, $(0,-1,4)$
- D) Rows $(2,0,0)$, $(1,0,0)$, $(0,-1,4)$

> [!success]- Answer
> **C.** Row $i$ holds the coefficients of $x_1,x_2,x_3$ in equation $i$. A missing unknown has the coefficient 0.
> Equation 1: $2x_1+0x_2-t\,x_3$, row $(2,0,-t)$. Equation 2: $1x_1+e^{t}x_2+0x_3$, row $(1,e^{t},0)$. Equation 3: $0x_1-1x_2+4x_3$, row $(0,-1,4)$.
> The rest goes into $F=(\cos t,0,-5)^{\mathsf T}$. $F\neq\mathbf 0$, so the system is nonhomogeneous.
> - A: The coefficients are written in the order they appear and the zeros are left out. Then $-t$ sits under $x_2$ and $-1$ under $x_1$.
> - B: This is the transpose. Row $i$ must belong to equation $i$, not to unknown $i$.
> - D: $-t\,x_3$ and $e^{t}x_2$ are put into $F$ because they contain $t$. They contain an unknown, so they belong to $A(t)$.

### Q2 (slide 2, solution)

Consider $x_1'=3x_1-2x_2$, $x_2'=2x_1-2x_2$ and the two vector functions $Y=(e^{t},\,e^{t})^{\mathsf T}$ and $Z=(2e^{2t},\,e^{2t})^{\mathsf T}$. Which statement is right?

- A) Only $Z$ is a solution, on $(-\infty,\infty)$
- B) $Y$ and $Z$ are both solutions
- C) Neither $Y$ nor $Z$ is a solution
- D) Only $Z$ is a solution, but only for $t\ge0$

> [!success]- Answer
> **A.** A solution must satisfy every equation for every $t$.
> $Y$: equation 1 gives $3e^{t}-2e^{t}=e^{t}=y_1'$, true. Equation 2 gives $2e^{t}-2e^{t}=0$, but $y_2'=e^{t}$. False, so $Y$ is not a solution.
> $Z$: $z_1'=4e^{2t}$, $z_2'=2e^{2t}$. Equation 1: $6e^{2t}-2e^{2t}=4e^{2t}$. Equation 2: $4e^{2t}-2e^{2t}=2e^{2t}$. Both true for every real $t$.
> - B: Only equation 1 is tested. $Y$ passes equation 1 but fails equation 2.
> - C: The chain rule factor is lost: $z_1'=2e^{2t}$ instead of $4e^{2t}$. Then equation 1 seems to fail for $Z$.
> - D: The entries of $Z$ are defined and the equations hold for all real $t$. Nothing restricts $t$ to $t\ge0$.

### Q3 (slide 2, initial value problem)

Write $y''+3y'-10y=6e^{t}$, $y(0)=1$, $y'(0)=2$ as a system $X'=AX+F(t)$ with $x_1=y$ and $x_2=y'$. Which $A$ and $F$ are right?

- A) $A=\begin{pmatrix}0&1\\-10&3\end{pmatrix}$, $F=\begin{pmatrix}0\\6e^{t}\end{pmatrix}$
- B) $A=\begin{pmatrix}0&1\\10&-3\end{pmatrix}$, $F=\begin{pmatrix}6e^{t}\\0\end{pmatrix}$
- C) $A=\begin{pmatrix}0&1\\-10&3\end{pmatrix}$, $F=\begin{pmatrix}0\\-6e^{t}\end{pmatrix}$
- D) $A=\begin{pmatrix}0&1\\10&-3\end{pmatrix}$, $F=\begin{pmatrix}0\\6e^{t}\end{pmatrix}$

> [!success]- Answer
> **D.** First equation: $x_1'=y'=x_2$, row $(0,1)$.
> Solve the ODE for $y''$: $y''=10y-3y'+6e^{t}$. So $x_2'=10x_1-3x_2+6e^{t}$, row $(10,-3)$, and $f_2=6e^{t}$.
> $X(0)=(y(0),y'(0))^{\mathsf T}=(1,2)^{\mathsf T}$. Check: $\det(\lambda\mathcal I_2-A)=\lambda^2+3\lambda-10$, the characteristic polynomial of the ODE.
> - A: The coefficients $3$ and $-10$ of the left side are copied without moving them to the right side.
> - B: The forcing term is put in row 1. It belongs to the equation for $x_2'=y''$.
> - C: The sign of the whole right side is changed: $y''=-10y+3y'-6e^{t}$.

## 2. Existence, superposition, Wronskian, fundamental matrix (slides 3-4)

### Q4 (slide 3, existence)

Consider $x_1'=\dfrac{1}{t-3}x_1+x_2$, $x_2'=\ln(t+1)\,x_1+e^{t}$. On which open interval does the existence and uniqueness theorem guarantee a unique solution for $X(1)=X_0$, and on which for $X(5)=X_0$?

- A) $(0,3)$ for $t_0=1$ and $(3,\infty)$ for $t_0=5$
- B) $(-1,\infty)$ for $t_0=1$ and $(-1,\infty)$ for $t_0=5$
- C) $(-1,3)$ for $t_0=1$ and $(3,\infty)$ for $t_0=5$
- D) $(-1,3)\cup(3,\infty)$ for $t_0=1$ and for $t_0=5$

> [!success]- Answer
> **C.** The entries of $A(t)$ and $F(t)$ are $\tfrac{1}{t-3}$, $1$, $\ln(t+1)$, $0$, $0$, $e^{t}$.
> $\tfrac{1}{t-3}$ is continuous for $t\neq3$. $\ln(t+1)$ needs $t+1>0$, so $t>-1$. The others are continuous everywhere.
> All entries are continuous on $(-1,3)$ and on $(3,\infty)$. Take the one that contains $t_0$: $(-1,3)$ for $t_0=1$, $(3,\infty)$ for $t_0=5$.
> - A: The domain of $\ln(t+1)$ is taken as $t>0$, the domain of $\ln t$.
> - B: The bad point of $\tfrac{1}{t-3}$ is put at $t=-3$. That point lies outside $t>-1$, so no break at 3 is seen.
> - D: The whole set where all entries are continuous is taken. It is not an interval: the solution cannot cross $t=3$, so the theorem gives only the interval that contains $t_0$.

### Q5 (slide 3, superposition)

$Y_1$ and $Y_2$ are two solutions of the nonhomogeneous system $X'=A(t)X+F(t)$ with $F\neq\mathbf 0$. Which systems do $Y_1+Y_2$ and $Y_1-Y_2$ solve?

- A) $Y_1+Y_2$ solves $X'=AX+F$; $Y_1-Y_2$ solves $X'=AX$
- B) $Y_1+Y_2$ solves $X'=AX+2F$; $Y_1-Y_2$ solves $X'=AX+2F$
- C) $Y_1+Y_2$ solves $X'=AX+F$; $Y_1-Y_2$ solves $X'=AX+F$
- D) $Y_1+Y_2$ solves $X'=AX+2F$; $Y_1-Y_2$ solves $X'=AX$

> [!success]- Answer
> **D.** Use $Y_1'=AY_1+F$ and $Y_2'=AY_2+F$.
> $(Y_1+Y_2)'=AY_1+F+AY_2+F=A(Y_1+Y_2)+2F$.
> $(Y_1-Y_2)'=AY_1+F-AY_2-F=A(Y_1-Y_2)$. The difference solves the homogeneous system. This is why $X=X_h+X_p$.
> - A: Superposition is used for the sum. It holds only for the homogeneous system.
> - B: The minus sign is not applied to $F$: $-(AY_2+F)$ is written as $-AY_2+F$.
> - C: Superposition is used for both: every combination of solutions is taken to solve the same system. That holds only for $X'=AX$.

### Q6 (slide 3, Wronskian)

$X_1=(1,2)^{\mathsf T}e^{t}$ and $X_3=(-2,-4)^{\mathsf T}e^{t}$ both solve $X'=AX$ for $A$ with the rows $(3,-1)$ and $(-2,2)$. For $U=(t,1)^{\mathsf T}$ and $V=(t^2,t)^{\mathsf T}$ the determinant with $U,V$ as columns is $0$ for every $t$, but $U$ and $V$ are linearly independent. Which statement is right?

- A) $X_1,X_3$ are independent; no contradiction, as $U$ and $V$ are linearly dependent
- B) $X_1,X_3$ are dependent; no contradiction, as $U,V$ do not solve one system $X'=A(t)X$
- C) $X_1,X_3$ are independent; no contradiction, as $U,V$ do not solve one system $X'=A(t)X$
- D) $X_1,X_3$ are dependent; no contradiction, as $U$ and $V$ are linearly dependent

> [!success]- Answer
> **B.** $W(X_1,X_3)=e^{t}(-4e^{t})-(-2e^{t})(2e^{t})=-4e^{2t}+4e^{2t}=0$. Directly: $X_3=-2X_1$. Dependent.
> The Wronskian test speaks only about $n$ solutions of one system $X'=A(t)X$. $U$ and $V$ are not such solutions: $V=tU$ gives $V'=U+tU'$, which equals $AV=tAU$ only if $U=\mathbf 0$.
> $U,V$ are independent: $c_1U+c_2V=\mathbf 0$ gives $c_1+c_2t=0$ for all $t$ in row 2, so $c_1=c_2=0$.
> - A: Two slips: the determinant is computed as $ad+bc=-8e^{2t}$, and $U,V$ are called dependent. $V=tU$ with a non-constant factor $t$ is not dependence.
> - C: The determinant is computed as $ad+bc=-8e^{2t}\neq0$ instead of $ad-bc$.
> - D: $V=tU$ is read as "$V$ is a multiple of $U$". The factor must be a constant.

### Q7 (slide 4, fundamental matrix)

For $A$ with the rows $(4,1)$ and $(2,3)$, the solutions $X_1=(1,-2)^{\mathsf T}e^{2t}$ and $X_2=(1,1)^{\mathsf T}e^{5t}$ are the columns of $\Phi(t)$. What is $\det\Phi(t)$?

- A) $-e^{7t}$
- B) $3e^{10t}$
- C) $3e^{7t}$
- D) $-3e^{7t}$

> [!success]- Answer
> **C.** $\Phi=\begin{pmatrix}e^{2t}&e^{5t}\\-2e^{2t}&e^{5t}\end{pmatrix}$, so $\det\Phi=e^{2t}e^{5t}-e^{5t}(-2e^{2t})=e^{7t}+2e^{7t}=3e^{7t}$.
> This is the Wronskian $W(X_1,X_2)$. It is never 0, so $\Phi(t)$ is nonsingular for every $t$. One can also check $\Phi'=A\Phi$ column by column.
> - A: $ad+bc$ instead of $ad-bc$: $e^{7t}-2e^{7t}=-e^{7t}$.
> - B: The exponents are multiplied: $e^{2t}e^{5t}$ taken as $e^{10t}$. Exponents add.
> - D: $bc-ad$ instead of $ad-bc$.

### Q8 (slide 4, general solution)

$\Phi(t)$ has the columns $(1,-2)^{\mathsf T}e^{2t}$ and $(1,1)^{\mathsf T}e^{5t}$, a fundamental matrix of $X'=AX$ for $A$ with the rows $(4,1)$ and $(2,3)$. Use $X=\Phi(t)C$ to solve $X'=AX$, $X(0)=(4,1)^{\mathsf T}$.

- A) $x_1=3e^{2t}+9e^{5t}$, $x_2=-6e^{2t}+9e^{5t}$
- B) $x_1=e^{2t}+3e^{5t}$, $x_2=-2e^{2t}+3e^{5t}$
- C) $x_1=2e^{2t}-e^{5t}$, $x_2=-4e^{2t}-e^{5t}$
- D) $x_1=3e^{2t}+e^{5t}$, $x_2=-6e^{2t}+e^{5t}$

> [!success]- Answer
> **B.** $\Phi(0)=\begin{pmatrix}1&1\\-2&1\end{pmatrix}$, $\det\Phi(0)=1+2=3$, $\Phi(0)^{-1}=\tfrac13\begin{pmatrix}1&-1\\2&1\end{pmatrix}$.
> $C=\tfrac13\begin{pmatrix}1&-1\\2&1\end{pmatrix}\begin{pmatrix}4\\1\end{pmatrix}=\tfrac13\begin{pmatrix}3\\9\end{pmatrix}=\begin{pmatrix}1\\3\end{pmatrix}$.
> $X=1\cdot(1,-2)^{\mathsf T}e^{2t}+3\cdot(1,1)^{\mathsf T}e^{5t}$. Check: $X(0)=(1+3,\,-2+3)=(4,1)$.
> - A: The factor $\tfrac13$ of the inverse is forgotten, so $C=(3,9)$. Then $X(0)=(12,3)$.
> - C: The solution vectors are used as rows: $\Phi(0)^{\mathsf T}C=X_0$ gives $C=(2,-1)$. Then $X(0)=(1,-5)$.
> - D: $c_1$ and $c_2$ are swapped, so $c_1=3$ goes with $e^{2t}$. Then $X(0)=(4,-5)$.

## 3. Homogeneous systems with a constant matrix (slides 5-6)

### Q9 (slide 5, theorem)

Take $A$ with the rows $(2,3)$ and $(2,1)$. (a) Is $\phi(t)=(3,2)^{\mathsf T}e^{4t}$ a solution of $X'=AX$? (b) For which number $\lambda$ is $(1,1)^{\mathsf T}e^{\lambda t}$ a solution?

- A) (a) yes; (b) for no $\lambda$
- B) (a) yes; (b) for $\lambda=5$
- C) (a) no; (b) for no $\lambda$
- D) (a) no; (b) for $\lambda=4$

> [!success]- Answer
> **A.** $ve^{\lambda t}$ solves $X'=AX$ exactly when $Av=\lambda v$, because $(ve^{\lambda t})'=\lambda ve^{\lambda t}$ and $A(ve^{\lambda t})=(Av)e^{\lambda t}$.
> (a) $A(3,2)^{\mathsf T}=(6+6,\,6+2)=(12,8)=4\,(3,2)$. So $\phi$ is a solution.
> (b) $A(1,1)^{\mathsf T}=(5,3)$. We would need $5=\lambda$ and $3=\lambda$ at once. Impossible, so no $\lambda$ works.
> - B: Only the first row is checked: $5=\lambda\cdot1$.
> - C: The chain rule factor is lost: $\phi'=(3,2)^{\mathsf T}e^{4t}$, which is not $(12,8)^{\mathsf T}e^{4t}$.
> - D: The vectors are multiplied by the transpose $A^{\mathsf T}$ (columns instead of rows): $A^{\mathsf T}(3,2)=(10,11)$ and $A^{\mathsf T}(1,1)=(4,4)$.

### Q10 (slides 5-6)

Find the general solution of $X'=AX$ for $A$ with the rows $(7,-4)$ and $(2,1)$.

- A) $X=c_1(1,1)^{\mathsf T}e^{5t}+c_2(2,1)^{\mathsf T}e^{3t}$
- B) $X=c_1(1,1)^{\mathsf T}e^{-3t}+c_2(2,1)^{\mathsf T}e^{-5t}$
- C) $X=c_1(1,1)^{\mathsf T}e^{-5t}+c_2(2,1)^{\mathsf T}e^{-3t}$
- D) $X=c_1(1,1)^{\mathsf T}e^{3t}+c_2(2,1)^{\mathsf T}e^{5t}$

> [!success]- Answer
> **D.** $\det(\lambda\mathcal I_2-A)=(\lambda-7)(\lambda-1)-(4)(-2)=\lambda^2-8\lambda+15=(\lambda-3)(\lambda-5)$.
> $\lambda=3$: $3\mathcal I_2-A=\begin{pmatrix}-4&4\\-2&2\end{pmatrix}$, so $v_1=v_2$: $(1,1)^{\mathsf T}$. Test: $A(1,1)=(3,3)$.
> $\lambda=5$: $5\mathcal I_2-A=\begin{pmatrix}-2&4\\-2&4\end{pmatrix}$, so $v_1=2v_2$: $(2,1)^{\mathsf T}$. Test: $A(2,1)=(10,5)$.
> Each eigenvector goes with its own eigenvalue. Both eigenvalues are positive: unstable node.
> - A: Each eigenvector is paired with the other eigenvalue. $A(1,1)=(3,3)\neq5(1,1)$.
> - B: Sign slip: the roots of $\lambda^2+8\lambda+15$, so $-3$ and $-5$. The eigenvalues are $3$ and $5$.
> - C: Two slips: the wrong signs and the swapped pairing.

### Q11 (slide 5, three equations)

Solve $X'=AX$, $X(0)=(4,5,4)^{\mathsf T}$ for $A$ with the rows $(1,1,0)$, $(0,2,1)$ and $(0,0,3)$.

- A) $x_1=e^{t}+e^{2t}+2e^{3t}$, $x_2=e^{2t}+4e^{3t}$, $x_3=4e^{3t}$
- B) $x_1=4e^{t}$, $x_2=5e^{2t}$, $x_3=4e^{3t}$
- C) $x_1=3e^{t}-e^{2t}+2e^{3t}$, $x_2=e^{2t}+4e^{3t}$, $x_3=4e^{3t}$
- D) $x_1=2e^{t}+e^{2t}+e^{3t}$, $x_2=4e^{t}+e^{2t}$, $x_3=4e^{t}$

> [!success]- Answer
> **A.** $A$ is upper triangular, so the eigenvalues are $1,2,3$.
> Eigenvectors: $\lambda=1$: $(1,0,0)$. $\lambda=2$: $v_1-v_2=0$, $v_3=0$, so $(1,1,0)$. $\lambda=3$: $2v_1=v_2$, $v_2=v_3$, so $(1,2,2)$.
> At $t=0$: $2c_3=4$, $c_2+2c_3=5$, $c_1+c_2+c_3=4$. So $c_3=2$, $c_2=1$, $c_1=1$.
> $X=(1,0,0)^{\mathsf T}e^{t}+(1,1,0)^{\mathsf T}e^{2t}+2(1,2,2)^{\mathsf T}e^{3t}$. Check: $x_1'=x_1+x_2$, $x_2'=2x_2+x_3$, $x_3'=3x_3$.
> - B: $A$ is treated as diagonal, with the standard basis vectors as eigenvectors. Then $x_1'=4e^{t}$, but $x_1+x_2=4e^{t}+5e^{2t}$.
> - C: The sign slip $v_2=-v_1$ for $\lambda=2$ gives $(1,-1,0)$ and $C=(3,-1,2)$. Then $x_1'\neq x_1+x_2$.
> - D: The eigenvalues are attached in reverse order: $(1,0,0)$ with $e^{3t}$ and $(1,2,2)$ with $e^{t}$. Then $x_3'=4e^{t}\neq3x_3$.

### Q12 (slide 5, complex eigenvalues, beyond the slides)

$A$ has the rows $(-1,-4)$ and $(1,-1)$. Its eigenvalues are complex, so the slide theorem (distinct real eigenvalues) does not apply. Solve $X'=AX$, $X(0)=(2,3)^{\mathsf T}$ with the real and imaginary parts of one complex solution.

- A) $x_1=e^{-t}(2\cos2t+6\sin2t)$, $x_2=e^{-t}(3\cos2t-\sin2t)$
- B) $x_1=e^{-t}(2\cos2t-6\sin2t)$, $x_2=e^{-t}(3\cos2t+\sin2t)$
- C) $x_1=e^{t}(2\cos2t-6\sin2t)$, $x_2=e^{t}(3\cos2t+\sin2t)$
- D) $x_1=e^{-t}(2\cos2t+6\sin2t)$, $x_2=e^{-t}(3\cos2t+\sin2t)$

> [!success]- Answer
> **B.** $\det(\lambda\mathcal I_2-A)=(\lambda+1)^2+4=\lambda^2+2\lambda+5$, so $\lambda=-1\pm2i$.
> $\lambda=-1+2i$: row 2 of $\lambda\mathcal I_2-A$ gives $-v_1+2iv_2=0$, so $v=(2i,1)^{\mathsf T}$.
> $ve^{\lambda t}=e^{-t}\bigl(2i\cos2t-2\sin2t,\ \cos2t+i\sin2t\bigr)^{\mathsf T}$, using $i^2=-1$. So $U=e^{-t}(-2\sin2t,\cos2t)^{\mathsf T}$ and $V=e^{-t}(2\cos2t,\sin2t)^{\mathsf T}$.
> $X=c_1U+c_2V$. At $t=0$: $2c_2=2$ and $c_1=3$. So $x_1=e^{-t}(2\cos2t-6\sin2t)$, $x_2=e^{-t}(3\cos2t+\sin2t)$.
> - A: The eigenvector $(-2i,1)$ of $-1-2i$ is used with $e^{(-1+2i)t}$. This gives $c_1=3$, $c_2=-1$, and the function fails the ODE.
> - C: The real part $\alpha=-1$ is taken as $+1$. The decay factor must be $e^{-t}$.
> - D: $i^2$ is taken as $+1$, so the first entry of $U$ becomes $+2\sin2t$. The initial values still fit, but the ODE fails.

### Q13 (slide 5, repeated eigenvalue, beyond the slides)

$A$ has the rows $(3,1)$ and $(-1,1)$. It has one repeated eigenvalue with only one independent eigenvector. Solve $X'=AX$, $X(0)=(2,1)^{\mathsf T}$ with a generalized eigenvector.

- A) $x_1=2e^{2t}$, $x_2=e^{2t}$
- B) $x_1=e^{2t}(2-3t)$, $x_2=e^{2t}(1+3t)$
- C) $x_1=e^{-2t}(2+3t)$, $x_2=e^{-2t}(1-3t)$
- D) $x_1=e^{2t}(2+3t)$, $x_2=e^{2t}(1-3t)$

> [!success]- Answer
> **D.** $\det(\lambda\mathcal I_2-A)=(\lambda-3)(\lambda-1)+1=(\lambda-2)^2$, so $\lambda=2$ twice.
> $2\mathcal I_2-A$ gives $v_1+v_2=0$: $v=(1,-1)^{\mathsf T}$. Solve $(A-2\mathcal I_2)w=v$: $w_1+w_2=1$, take $w=(1,0)^{\mathsf T}$.
> $X=c_1(1,-1)^{\mathsf T}e^{2t}+c_2(t+1,-t)^{\mathsf T}e^{2t}$. At $t=0$: $c_1+c_2=2$, $-c_1=1$, so $c_1=-1$, $c_2=3$.
> $x_1=e^{2t}(-1+3t+3)=e^{2t}(2+3t)$, $x_2=e^{2t}(1-3t)$. Check: $x_1'=e^{2t}(7+6t)=3x_1+x_2$.
> - A: The $t\,v$ term is left out: $X_2=we^{2t}$. But $w$ is not an eigenvector, and $A(2,1)^{\mathsf T}=(7,-1)\neq2(2,1)$.
> - B: The generalized vector is solved from $(2\mathcal I_2-A)w=v$, so $w=(-1,0)$. The initial values fit, but the ODE fails.
> - C: Sign slip in the characteristic polynomial, $(\lambda+2)^2$. The eigenvalue is $+2$.

### Q14 (slide 6)

Solve the initial value problem $x_1'=-3x_1+x_2$, $x_2'=2x_1-2x_2$, $X(0)=(3,0)^{\mathsf T}$.

- A) $x_1=e^{-t}+2e^{-4t}$, $x_2=2e^{-t}-2e^{-4t}$
- B) $x_1=2e^{-t}+e^{-4t}$, $x_2=2e^{-4t}-2e^{-t}$
- C) $x_1=e^{t}+2e^{4t}$, $x_2=2e^{t}-2e^{4t}$
- D) $x_1=2e^{-t}+e^{-4t}$, $x_2=4e^{-t}-e^{-4t}$

> [!success]- Answer
> **A.** $\det(\lambda\mathcal I_2-A)=(\lambda+3)(\lambda+2)-2=\lambda^2+5\lambda+4=(\lambda+1)(\lambda+4)$.
> $\lambda=-1$: $-\mathcal I_2-A=\begin{pmatrix}2&-1\\-2&1\end{pmatrix}$, so $v_2=2v_1$: $(1,2)^{\mathsf T}$. $\lambda=-4$: $\begin{pmatrix}-1&-1\\-2&-2\end{pmatrix}$, so $v_2=-v_1$: $(1,-1)^{\mathsf T}$.
> At $t=0$: $c_1+c_2=3$, $2c_1-c_2=0$. Add: $3c_1=3$, so $c_1=1$, $c_2=2$.
> $X=(1,2)^{\mathsf T}e^{-t}+2(1,-1)^{\mathsf T}e^{-4t}$. Both eigenvalues are negative: stable node.
> - B: Each eigenvector gets the other eigenvalue: $(1,2)^{\mathsf T}e^{-4t}+2(1,-1)^{\mathsf T}e^{-t}$. The initial values fit, but the ODE fails.
> - C: Sign slip: the roots of $\lambda^2-5\lambda+4$, so $1$ and $4$. The eigenvalues are $-1$ and $-4$.
> - D: The constants are swapped, $c_1=2$, $c_2=1$. Then $X(0)=(3,3)$, not $(3,0)$.

## 4. Nonhomogeneous systems, variation of parameters (slides 7-10)

### Q15 (slide 7, theorem, with undetermined coefficients beyond the slides)

Solve $x_1'=-2x_1+x_2+6$, $x_2'=4x_1-5x_2$, $X(0)=(8,2)^{\mathsf T}$. The homogeneous part has the solution $X_h=c_1(1,1)^{\mathsf T}e^{-t}+c_2(1,-4)^{\mathsf T}e^{-6t}$. Use a constant particular solution $X_p$. Which $X_p$ and which constants are right?

- A) $X_p=(-5,-4)^{\mathsf T}$, $c_1=\tfrac{58}{5}$, $c_2=\tfrac75$
- B) $X_p=(5,4)^{\mathsf T}$, $c_1=\tfrac{58}{5}$, $c_2=\tfrac75$
- C) $X_p=(-5,-4)^{\mathsf T}$, $c_1=2$, $c_2=1$
- D) $X_p=(5,4)^{\mathsf T}$, $c_1=2$, $c_2=1$

> [!success]- Answer
> **D.** For $X_p=K$ we have $K'=\mathbf 0$: $0=-2k_1+k_2+6$ and $0=4k_1-5k_2$. So $k_2=2k_1-6$, $4k_1-10k_1+30=0$, $k_1=5$, $k_2=4$.
> The initial condition is for $X_h+X_p$: $c_1+c_2+5=8$ and $c_1-4c_2+4=2$. So $c_1+c_2=3$, $c_1-4c_2=-2$, $5c_2=5$, $c_2=1$, $c_1=2$.
> $x_1=2e^{-t}+e^{-6t}+5$, $x_2=2e^{-t}-4e^{-6t}+4$.
> - A: Sign slip in $K$: $0=AK-F$ gives $K=(-5,-4)$. Then $X_h(0)=X_0-K=(13,6)$ gives these constants.
> - B: Right $X_p$, but $X_p(0)$ is added to $X_0$ instead of subtracted: $X_h(0)=(13,6)$.
> - C: Two slips: the sign in $K$ and the sign in $X_h(0)=X_0+K=(3,-2)$.

### Q16 (slide 7, find the mistake)

The system $x_1'=-2x_1+x_2$, $x_2'=4x_1-5x_2+6$ has $X_h=c_1(1,1)^{\mathsf T}e^{-t}+c_2(1,-4)^{\mathsf T}e^{-6t}$ and the particular solution $X_p=(1,2)^{\mathsf T}$. The initial condition is $X(0)=(4,1)^{\mathsf T}$. A student finds $c_1,c_2$ from $X_h(0)=(4,1)^{\mathsf T}$ and then adds $X_p$. What is $X(0)$ for the student's function?

- A) $(4,1)^{\mathsf T}$
- B) $(5,3)^{\mathsf T}$
- C) $(3,-1)^{\mathsf T}$
- D) $(1,2)^{\mathsf T}$

> [!success]- Answer
> **B.** The student's function is $X=X_h+X_p$ with $X_h(0)=(4,1)$. So $X(0)=X_h(0)+X_p(0)=(4+1,\,1+2)=(5,3)$.
> This is not the given $(4,1)$. The initial condition is for the full solution: find $X_p$ first, then solve $X_h(0)+X_p(0)=X_0$ for $C$.
> - A: $X_p(0)$ is taken as $\mathbf 0$. It is $(1,2)$, so adding it moves the initial value.
> - C: $X_p(0)$ is subtracted instead of added.
> - D: The exponentials are set to 0 at $t=0$. They are 0 only in the limit $t\to\infty$; at $t=0$ they are 1.

### Q17 (slide 8)

Use $X_p=\Phi\int\Phi^{-1}F\,dt$ for one equation ($n=1$): find a particular solution of $x'=2x+e^{5t}$. Take the integration constant 0.

- A) $x_p=\tfrac13e^{3t}$
- B) $x_p=\tfrac13e^{5t}$
- C) $x_p=3e^{5t}$
- D) $x_p=\tfrac17e^{9t}$

> [!success]- Answer
> **B.** For $n=1$: $\Phi=e^{2t}$ (solution of $x'=2x$), $\Phi^{-1}=e^{-2t}$, $\Phi^{-1}F=e^{3t}$.
> $\int e^{3t}\,dt=\tfrac13e^{3t}$, and $x_p=e^{2t}\cdot\tfrac13e^{3t}=\tfrac13e^{5t}$.
> Check: $x_p'=\tfrac53e^{5t}$ and $2x_p+e^{5t}=\tfrac23e^{5t}+e^{5t}=\tfrac53e^{5t}$.
> - A: The last step is missing: the integral is not multiplied by $\Phi$.
> - C: $\int e^{3t}\,dt$ is taken as $3e^{3t}$. One must divide by 3, not multiply.
> - D: $\Phi$ is used instead of $\Phi^{-1}$: $\int e^{7t}dt=\tfrac17e^{7t}$, times $e^{2t}$.

### Q18 (slide 9)

$\Phi(t)$ has the columns $(1,3)^{\mathsf T}e^{t}$ and $(1,-1)^{\mathsf T}e^{3t}$. What is $\Phi^{-1}(t)$?

- A) $\begin{pmatrix}\tfrac14e^{3t}&\tfrac14e^{3t}\\\tfrac34e^{t}&-\tfrac14e^{t}\end{pmatrix}$
- B) $\begin{pmatrix}\tfrac14e^{-t}&-\tfrac14e^{-t}\\-\tfrac34e^{-3t}&-\tfrac14e^{-3t}\end{pmatrix}$
- C) $\begin{pmatrix}\tfrac14e^{-t}&\tfrac14e^{-t}\\\tfrac34e^{-3t}&-\tfrac14e^{-3t}\end{pmatrix}$
- D) $\begin{pmatrix}e^{-t}&e^{-3t}\\\tfrac13e^{-t}&-e^{-3t}\end{pmatrix}$

> [!success]- Answer
> **C.** $\Phi=\begin{pmatrix}e^{t}&e^{3t}\\3e^{t}&-e^{3t}\end{pmatrix}$, $\det\Phi=-e^{4t}-3e^{4t}=-4e^{4t}$.
> $2\times2$ rule: swap the diagonal, change the sign of the other two, divide by $\det\Phi$:
> $\Phi^{-1}=\dfrac{1}{-4e^{4t}}\begin{pmatrix}-e^{3t}&-e^{3t}\\-3e^{t}&e^{t}\end{pmatrix}=\begin{pmatrix}\tfrac14e^{-t}&\tfrac14e^{-t}\\\tfrac34e^{-3t}&-\tfrac14e^{-3t}\end{pmatrix}$.
> Test, row 1 times column 1: $\tfrac14+\tfrac34=1$. Row 2 times column 1: $\tfrac34e^{-2t}-\tfrac34e^{-2t}=0$.
> - A: Division by $-4$ only. The factor $e^{4t}$ of the determinant is forgotten.
> - B: The signs of the off-diagonal entries are not changed.
> - D: The inverse is taken entry by entry ($1/\text{entry}$). That is not the matrix inverse.

### Q19 (slides 8-10)

Solve $x_1'=2x_1+x_2+2t$, $x_2'=x_1+2x_2$, $x_1(0)=0$, $x_2(0)=0$ by variation of parameters. ($A$ has the eigenvalues 3 and 1 with the eigenvectors $(1,1)^{\mathsf T}$ and $(1,-1)^{\mathsf T}$.)

- A) $x_1=\tfrac19e^{3t}-e^{t}+\tfrac23t+\tfrac89$, $x_2=\tfrac19e^{3t}+e^{t}-\tfrac43t-\tfrac{10}{9}$
- B) $x_1=-\tfrac19e^{3t}-e^{t}-\tfrac43t+\tfrac{10}{9}$, $x_2=-\tfrac19e^{3t}+e^{t}+\tfrac23t-\tfrac89$
- C) $x_1=\tfrac19e^{3t}+e^{t}-\tfrac43t-\tfrac{10}{9}$, $x_2=\tfrac19e^{3t}-e^{t}+\tfrac23t+\tfrac89$
- D) $x_1=\tfrac29e^{3t}+2e^{t}-\tfrac83t-\tfrac{20}{9}$, $x_2=\tfrac29e^{3t}-2e^{t}+\tfrac43t+\tfrac{16}{9}$

> [!success]- Answer
> **C.** $\Phi=\begin{pmatrix}e^{3t}&e^{t}\\e^{3t}&-e^{t}\end{pmatrix}$, $\det\Phi=-2e^{4t}$, $\Phi^{-1}=\begin{pmatrix}\tfrac12e^{-3t}&\tfrac12e^{-3t}\\\tfrac12e^{-t}&-\tfrac12e^{-t}\end{pmatrix}$.
> $\Phi^{-1}F=(te^{-3t},\,te^{-t})^{\mathsf T}$. By parts: $\int te^{-3t}dt=-\tfrac13te^{-3t}-\tfrac19e^{-3t}$, $\int te^{-t}dt=-te^{-t}-e^{-t}$.
> Multiply by $\Phi$: $X_p=\bigl(-\tfrac43t-\tfrac{10}{9},\ \tfrac23t+\tfrac89\bigr)^{\mathsf T}$.
> At $t=0$: $c_1+c_2=\tfrac{10}{9}$, $c_1-c_2=-\tfrac89$, so $c_1=\tfrac19$, $c_2=1$. Then $x_1=\tfrac19e^{3t}+e^{t}-\tfrac43t-\tfrac{10}{9}$, $x_2=\tfrac19e^{3t}-e^{t}+\tfrac23t+\tfrac89$.
> - A: $F$ is written as $(0,2t)^{\mathsf T}$, so the forcing sits in the wrong equation. This solves $x_2'=x_1+2x_2+2t$, not our system.
> - B: Sign slip in the parts formula: $\int te^{-3t}dt=-\tfrac13te^{-3t}+\tfrac19e^{-3t}$ and $\int te^{-t}dt=-te^{-t}+e^{-t}$.
> - D: The factor $\tfrac12$ of $\Phi^{-1}$ is forgotten. Everything doubles, which is the solution for the forcing $4t$.

### Q20 (slide 10)

The slide solves $x_1'=-3x_1+x_2+3t$, $x_2'=2x_1-4x_2+e^{-t}$ with $\Phi(t)$ with the columns $(1,1)^{\mathsf T}e^{-2t}$ and $(1,-2)^{\mathsf T}e^{-5t}$. It writes $X=\Phi C+\Phi\int\Phi^{-1}F\,dt$ and sets the integration constants $d_1=d_2=0$. Suppose you keep them: $\int\Phi^{-1}F\,dt=G(t)+D$ with $D=(d_1,d_2)^{\mathsf T}$. What changes?

- A) $X_p$ gains $\Phi D$, a solution of the homogeneous system; the family of solutions stays the same
- B) $X_p$ gains $\Phi D$, and the general solution becomes a larger family with four free constants
- C) $X_p$ gains the constant vector $D$; the family of solutions stays the same
- D) $X_p$ gains the constant vector $D$, so every solution is shifted and the slide's answer is wrong

> [!success]- Answer
> **A.** $\Phi(G+D)=\Phi G+\Phi D$, and $\Phi D=d_1(1,1)^{\mathsf T}e^{-2t}+d_2(1,-2)^{\mathsf T}e^{-5t}$ solves the homogeneous system.
> So $X=\Phi C+\Phi D+\Phi G=\Phi(C+D)+\Phi G$. $C+D$ is again an arbitrary constant vector.
> The family is the same. $d_1=d_2=0$ is only the simplest choice of $X_p$.
> - B: $C$ and $D$ are counted as four independent constants. They enter only as the sum $C+D$, so there are still two.
> - C: The factor $\Phi$ is forgotten. Also, a constant vector $D\neq\mathbf 0$ is not a homogeneous solution here ($\det A=10\neq0$, so $AD\neq\mathbf 0$).
> - D: The factor $\Phi$ is forgotten. $D$ must be multiplied by $\Phi$, which turns it into a homogeneous solution.
