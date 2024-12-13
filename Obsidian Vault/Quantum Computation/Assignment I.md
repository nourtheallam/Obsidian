
![[Pasted image 20241004153732.png]]
![[Pasted image 20241004153805.png]]
![[Pasted image 20241004153821.png]]
![[Pasted image 20241004153845.png]]
### Question 4
##### (a)
Let $\lambda$ and $\ket{v}$ be an eigenvalue and its corresponding eigenvector for $M$. Then $$M \ket{v} = \lambda \ket{v}$$
And $$(A\ket{v})^{\dagger} = (\lambda\ket{v} )^{\dagger} = \bra{v}A^{\dagger} = \bra{v} \lambda^{\star} $$
Where $\lambda^{\star}$ is the complex conjugate of $\lambda$. Since $M$ is a Hermitian, we know it is self-adjoint and thus 
$$A = A^{^{\dagger}}$$
$$A \ket{v} = A^{\dagger} \ket{v} $$
$$\bra{v}A^{\dagger} = \bra{v}A  $$
Using this information, we see that since $$\bra{v} (A \ket{v} ) = \bra{v} (\lambda \ket{v} )$$
And $$(\bra{v} A^\dagger ) \ket{v} = (\bra{v} \lambda^\star) \ket{v}  $$
And $$A = A^{\dagger}$$
We see that 
$$\bra{v}A \ket{v} = \bra{v}A^{\dagger}\ket{v} = \bra{v}\lambda^\star\ket{v} = \bra{v} \lambda \ket{v}      $$
And therefore, that 
$$\lambda = \lambda^\star$$
Which can only be true if $\lambda$ is real.

##### (b)

Assume that $M$ is Hermitian, $\ket{v_{1}}$ and $\ket{v_{2}}$ are eigenvectors of $M$ for eigenvalues $\lambda_{1}$ and $\lambda_{2}$,  
respectively, and $\lambda_{1} \neq \lambda_{2}$, and suppose that $\ket{v_{2}}$  and $\ket{v_2}$ are not orthogonal, implying that $\braket{v_{1} | v_{2}} \neq 0$. We see that $$\bra{v_{2}}(M\ket{v_{1}} ) = \bra{v_{2}}(\lambda_{1}\ket{v_{1}})$$ and $$\bra{v_{1}}(M\ket{v_{2}} ) = \bra{v_{1}}(\lambda_{2}\ket{v_{2}})$$ Which, since $\braket{v_{1} | v_{2}} = \braket{v_{2} | v_{1}}$, implies that $\lambda_{1} = \lambda_{2}$ and thus contradicts our assumption that $\lambda_{1} \neq \lambda_{2}$. Therefore, by contradiction, it must be true that if $M$ is Hermitian, $\ket{v_{1}}$ and $\ket{v_{2}}$ are eigenvectors of $M$ for eigenvalues $\lambda_{1}$ and $\lambda_{2}$,  respectively, and $\lambda_{1} \neq \lambda_{2}$, then $\ket{v_{2}}$  and $\ket{v_2}$ are orthogonal.


##### (c)

If $M$ is a projector, then $M = M^2$. Let $\lambda$ and $\ket{v}$ be some eigenvalue and its corresponding eigenvector for $M$, then we have that $$\begin{aligned}  M\ket{v} &= \lambda \ket{v} \\
(M\ket{v})^2 &= (\lambda \ket{v})^2 \\
\bra{v}M^2\ket{v} &= \bra{v} \lambda^2 \ket{v} 
\end{aligned} $$
But since $M\ket{v} = \lambda \ket{v}$,  and $M = M^2$, we know that  $$\bra{v}M^2\ket{v} = \bra{v} \lambda^2 \ket{v} = \bra{v}M\ket{v} = \bra{v} \lambda \ket{v}$$
Which implies that $\lambda = \lambda^2$ which can only be true if $\lambda \in \{0, 1\}$. 

##### (d)

We shall prove this by contrapositive. Assume the $M$ is normal. We want to show that if $M$ is not Hermitian then its eigenvalues are not real. To start, we know that for some eigenvalue of $M$, $\lambda$, and its corresponding eigenvector $\ket{v}$  the following equalities are true $$\begin{align} 
M \ket{v} = \lambda \ket{v}   \\
(M\ket{v} )^{\dagger} = (\lambda \ket{v} )^{\dagger} \\
\bra{v}M ^{\dagger} = \bra{v}\lambda ^\star  
\end{align}
$$
And therefore, that $$\begin{align}
(\bra{v}M^{\dagger})\ket{v} = (\bra{v}\lambda^\star)\ket{v} \\ 
\bra{v}(M\ket{v} ) = \bra{v}(\lambda \ket{v})  
\end{align}$$
Since we are assuming that $M \neq M ^{\dagger}$ then, given the above equalities, it must be true that $\lambda \neq \lambda ^ \star$ which implies that $\lambda$ must not be real. Therefore, by contrapositive, we have proven that if $M$ is normal and its eigenvalues are real, then $M$ must be Hermitian. 
### Question 5

##### (a)  

The collection $\mathbb{C}^{2 \times 2}$ is a vector space as it possesses the properties of a vector space as follows

**commutativity**

Since matrix addition is commutative, so is the addition of any $A, B \in \mathbb{C}^{2 \times 2}$. 

**associativity**

Since matrix addition is associative, so is the addition of any $A, B \in \mathbb{C}^{2 \times 2}$. 

**additive identity**

Let $M = \begin{bmatrix}0 & 0 \\ 0 & 0\end{bmatrix} \in \mathbb{C}^{2 \times 2}$ then for any $A \in \mathbb{C}^{2 \times 2}$, $A + M = A$. 

**additive inverse**

Consider $A = \begin{bmatrix}A_{1} & A_{2} \\ A_{3} & A_{4}\end{bmatrix} \in \mathbb{C}^{2 \times 2}$ and let $A' = \begin{bmatrix} -A_{1} & -A_{2} \\ - A_{3} & - A_{4}\end{bmatrix} \in \mathbb{C}^{2 \times 2}$. We can then see that $A + A' = \begin{bmatrix}0 & 0 \\ 0 & 0\end{bmatrix} = M$. 

**multiplicative identity**

Since for any matrix $A = \begin{bmatrix}A_{1} & A_{2} \\ A_{3} & A_{4}\end{bmatrix}$,  $\sigma A = \sigma \begin{bmatrix}A_{1} & A_{2} \\ A_{3} & A_{4}\end{bmatrix} = \begin{bmatrix}\sigma A_{1} & \sigma A_{2} \\ \sigma A_{3} & \sigma A_{4}\end{bmatrix}$, we have that $1A = A$. 
And therefore, it must be true that for $A \in \mathbb{C}^{2 \times 2}$, $1A = 1$. 

**distributive properties**

Since, for any two matrices $A, B$ of the same size and scalars $\sigma, \beta$ we have that $\alpha (A + B) = \alpha A + \alpha B$ and $(\alpha + \beta) A = \alpha A + \beta A$. We know this must be true for $A, B \in \mathbb{C}^{2 \times 2}$ and $\alpha, \beta \in \mathbb{C}$.  


##### (b) 

To prove that a set of matrices span $\mathbb{C}^{2 \times 2}$, we need to show that these matrices span $\mathbb{C}^{2 \times 2}$ and are linearly independent. 

To show that the $I, X, Y, Z$ matrices span $\mathbb{C}^{2 \times 2}$, we need to show that any matrix $A \in \mathbb{C}^{2 \times 2}$ can be written as a linear combination of these matrices. So, $$A = \begin{bmatrix}
a & b \\ c & d
\end{bmatrix} = \alpha \begin{bmatrix}
0 & 1 \\ 1 & 0
\end{bmatrix} + 
\beta \begin{bmatrix}
0 & -i \\ i & 0
\end{bmatrix} + 
\sigma \begin{bmatrix}
1 & 0 \\ 0 & -1
\end{bmatrix} + \rho \begin{bmatrix}
1 & 0 \\ 0 & 1
\end{bmatrix}$$
Which presents us with the following system of equations 
$$\begin{align}
a = \sigma + \rho \\
b = \alpha - i \beta  \\
c = \alpha + i \beta \\
d = - \sigma + \rho
\end{align}$$
Which can be represented by the following augmented matrix $$\left( \begin{array}{cccc | c}
0 & 0 & 1 & 1 &  a \\
1 & -i & 0 & 0 & b \\
1 & i & 0 & 0 & c \\
0 & 0 & -1 & 1 & d
\end{array} \right)$$
Whose solution is $$\begin{align} \\
\rho = \frac{d+a}{2} \\
\sigma = a - \frac{d+a}{2}\\
\beta = \frac{c-b}{2i} \\
\alpha = b + \frac{c-b}{2}
\end{align} \\
$$
The existence of this solution implies that any matrix $A \in \mathbb{C}^{2 \times 2}$ can be represented using the $I, X, Y, Z$ matrices and therefore, that these matrices span $\mathbb{C}^{2 \times 2}$.

Next, we want to show that the $I, X, Y, Z$ matrices are linearly independent. If we take an arbitrary linear combination of the $I, X, Y, Z$ matrices (where $\alpha, \beta,, \sigma, \rho \in \mathbb{C}$)

$$\alpha \begin{bmatrix}
0 & 1 \\ 1 & 0
\end{bmatrix} + 
\beta \begin{bmatrix}
0 & -i \\ i & 0
\end{bmatrix} + 
\sigma \begin{bmatrix}
1 & 0 \\ 0 & -1
\end{bmatrix} + \rho \begin{bmatrix}
1 & 0 \\ 0 & 1
\end{bmatrix} = \begin{bmatrix}
\sigma + \rho & \alpha - i \beta \\ \alpha + i \beta & - \sigma + \rho
\end{bmatrix}
$$

Then this resulting matrix will always have a non-zero entry unless $\alpha = \beta = \sigma = \rho = 0$, which implies that the Pauli matrices are linearly independent. 

Since the $I, X, Y, Z$ matrices are linearly independent and span $\mathbb{C}^{2 \times 2}$, it must be true that they are a basis of $\mathbb{C}^{2 \times 2}$.  

##### (c) 

Let $M = \begin{bmatrix}a & b \\ c & d\end{bmatrix}$ and $N = \begin{bmatrix}e & f \\ g & h\end{bmatrix}$. Then, $M ^{\dagger} N = \begin{bmatrix}a^\star & c^\star \\ b^\star & d^\star \end{bmatrix}\begin{bmatrix}e & f\\ g & h\end{bmatrix} = \begin{bmatrix}a^\star e + c^\star g & a^\star f + c^\star h \\ b^\star e + d^\star g & b^\star f + d^\star h\end{bmatrix}$ and thus $Tr(M^{\dagger}N) = a^\star e + c^\star g + b^\star f + d^\star h$. 

In order to show that $(M, N ) → Tr(M^{\dagger} N )$ defines an inner product on $\mathbb{C}^{2 \times 2}$, we need to show that it possesses the following properties

**non-negativity**

If we let $N = M$, then the trace we calculated above becomes $a^\star a + c^\star c + b^\star b + d^\star d$ which is $\geq 0$ as a complex number multiplied by its complex conjugate will always yield a real nonnegative number ($(\alpha _+ i\beta)(a-i\beta) = \alpha^2 - (i\beta)^2 = \alpha^2 + \beta^2$), and we also know that this sum will equal $0$ if and only if all the entries in $M$ were $0$.

**linearity in the second argument**

For some $\alpha \in \mathbb{C}^2$, we have that $$\begin{gathered}
Tr(M^{\dagger} (N \alpha) ) = Tr (\begin{bmatrix} a^\star & c^\star \\ b^\star & d^\star \end{bmatrix}\begin{bmatrix}\alpha e & \alpha  f\\ \alpha  g & \alpha h\end{bmatrix}) \\
= a^\star \alpha  e +  c^\star \alpha  g +  b^\star \alpha  f +  d^\star \alpha  h \\
= \alpha (a^\star e + c^\star g + b^\star f + d^\star h) \\
= \alpha Tr(M ^{\dagger} N)\end{gathered}$$
We also have 

$$\begin{gathered}
Tr(M^{\dagger} (N + \alpha) ) = Tr (\begin{bmatrix} a^\star & c^\star \\ b^\star & d^\star \end{bmatrix}\begin{bmatrix} e & f\\ g & h\end{bmatrix} + \begin{bmatrix} \alpha a^\star & \alpha c^\star \\ \alpha b^\star & \alpha d^\star \end{bmatrix})\\
= Tr(\begin{bmatrix}
a^\star e+c^\star g  + \alpha a^\star & a^\star f + c^\star h + \alpha c^\star\\
b^\star e + d^\star g + \alpha b^\star & b^\star f + d^\star h + \alpha d^\star\end{bmatrix})\\
= a^\star e+c^\star g  + \alpha a^\star + b^\star f + d^\star h + \alpha d^\star
= Tr(\alpha M^{\dagger}) + Tr(M^{\dagger}N)
\end{gathered}$$

 **conjugate symmetry**

Consider
$$\begin{aligned}
Tr(N^{\dagger}M) = Tr (\begin{bmatrix} e^\star & f^\star\\ g^\star & h^\star\end{bmatrix}\begin{bmatrix} a & c \\ b & d\end{bmatrix}) \\
= e^\star a + f^\star b + g^\star c + h^\star d
\end{aligned}$$
Taking the complex conjugate of this expression yields 
$$a^\star e + b^\star f + c^\star g + d^\star h$$
Which is precisely the value of $Tr(M^{\dagger}N)$.


