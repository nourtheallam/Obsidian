## 1

##### (a)
$$
\begin{aligned}
\rho &= \sum_{i = 1}^{k} P_{i} \ket{\psi_{i}}\bra{\psi_{i}} \\
Tr(\rho) &= Tr(\sum_{i = 1}^{k} P_{i} \ket{\psi_{i}}\bra{\psi_{i}}) \\
&= \sum_{i = 1}^{k} P_{i} \ \ Tr(\ket{\psi_{i}}\bra{\psi_{i}}) \\
&= \sum_{i = 1}^{k} P_{i} \\
& = 1
\end{aligned}
$$
As the probabilities of the ensemble have to sum-up to $1$. 
##### (b)

To show that a $n \times n$ matrix $A$ is a positive operator, we need to demonstrate that $\bra{\phi} A \ket{\phi} \geq 0$ for any $n$-length vector $\ket{\phi}$
$$
\begin{aligned}
& \bra{\phi} \rho \ket{\phi} \\ 
=& \bra{\phi} \left(\sum_{i = 1}^{k} P_{i} \ket{\psi_{i}}\bra{\psi_{i}}\right) \ket{\phi} \\ 
= & \sum_{i = 1}^{k} P_{i} \braket{\phi | \psi_{i} } \braket{ \psi_{i} | \phi  } \\
= & \sum_{i = 1}^{k} P_{i} |\braket{\phi | \psi_{i} }|^2
\end{aligned}
$$
Which must evaluate to $\geq1$ because $\sum_{i = 1}^{k} P_{i}$
### 2

Since $\rho$ is a positive operator, it is also self-adjoint. And since every self-adjoint operator is normal, then by the complex spectral theorem,  $\rho = U(\rho')U^{\dagger}$ where $\rho'$ is a diagonal matrix and $U$ is an orthogonal, and therefore unitary, matrix. 

Since the trace is cyclic, $tr(\rho) = tr(U\rho'U^{\dagger}) = tr(UU^{\dagger} \rho') = tr(\rho') = 1$.  

Moreover, since  
$$
\rho' = \sum_{i=0}^{2^n - 1} d_i \ket{i}\bra{i},
$$  
where $\ket{i}$ represents the computational basis states (e.g., $\ket{0^n}, \ket{1}, \dots, \ket{1^n}$),  
we can express $U\rho'U^{\dagger}$ as  
$$
U\rho'U^{\dagger} = \sum_{i=0}^{2^n - 1} d_i U\ket{i}\bra{i}U^{\dagger}.
$$

If we let $\ket{d_i} = U\ket{i}$, this becomes  
$$
U\rho'U^{\dagger} = \sum_{i=0}^{2^n - 1} d_i \ket{d_i}\bra{d_i}.
$$
Which is precisely the definition of the density matrix of an ensemble with each element having a probability $d_{i}$ and a pure state $\ket{d_{i}}$, particularly because we showed that $tr(\rho') = 1$, and therefore, that the probabilities in the ensemble all sum to $1$. Therefore, the given claim is true. 

### 3

$$
\begin{aligned}
tr_{B}((U\otimes I)\circ \rho \circ (U^{\dagger}\otimes I)) = tr_{B}(U\otimes I)\circ tr_{B}(\rho) \circ tr_{B}(U^{\dagger}\otimes I)
\end{aligned}
$$
Since 
$$
tr_{B}(U \otimes I) = U tr_B(I) = U
$$
And similarly
$$
tr_{B}(U^{\dagger} \otimes I) = U^{\dagger} tr_B(I) = U^{\dagger}
$$
We can simplify the given expression to 
$$U \circ tr_{B}(\rho) \circ U^{\dagger} = U (tr_{B}(\rho))U^{\dagger}$$

### 4

Consider the pure state 
$$\ket{\psi} = \begin{bmatrix}
\frac{1}{\sqrt{ 2 }} \\ 0 \\ 0 \\ \frac{1}{\sqrt{ 2 }} \\
\end{bmatrix} $$
Its density matrix $\rho$ is 
$$\ket{\psi}\bra{\psi} = \begin{bmatrix}
\frac{1}{2} & 0 & 0 & \frac{1}{2} \ \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\ 
\frac{1}{2} & 0 & 0 & \frac{1}{2}
\end{bmatrix} $$
Which can be expressed as 
$$\begin{aligned}
\frac{1}{2}(\ket{0}\bra{0} \otimes \ket{0}\bra{0}  + \ket{0}\bra{1} \otimes \ket{0}\bra{1}  + \ket{1}\bra{0} \otimes \ket{1}\bra{0} + \ket{1}\bra{1} \otimes \ket{1}\bra{1})
\end{aligned}$$
And therefore, 
$$\begin{aligned}
Tr_{B}(\rho) &= \frac{1}{2}(\ket{0}\bra{0} \otimes (1)  + \ket{0}\bra{1} \otimes (0)  + \ket{1}\bra{0} \otimes (0) + \ket{1}\bra{1} \otimes (1)) \\
& = \frac{1}{2}(\ket{0}\bra{0} + \ket{1}\bra{1}) \\
& = \begin{bmatrix}
\frac{1}{2} & 0 \\ 0 & \frac{1}{2}
\end{bmatrix}
\end{aligned}$$
$$\begin{aligned}
Tr_{A}(\rho) &=  \frac{1}{2}((1) \otimes\ket{0}\bra{0}   + (0) \otimes \ket{0}\bra{1} + (0) \otimes \ket{1}\bra{0} + (1) \otimes \ket{1}\bra{1} ) \\
& = \frac{1}{2}(\ket{0}\bra{0} + \ket{1}\bra{1}) \\
& = \begin{bmatrix}
\frac{1}{2} & 0 \\ 0 & \frac{1}{2}
\end{bmatrix}
\end{aligned}$$
$$\begin{aligned}
Tr_{B} \otimes Tr_{A} = \begin{bmatrix}
\frac{1}{4} & 0 & 0 & 0 \\ 
0 & \frac{1}{4} & 0 & 0 \\
0 & 0 & \frac{1}{4} & 0  \\
0 & 0 & 0 & \frac{1}{4}
\end{bmatrix} \neq \rho
\end{aligned}$$



