---
~
---
### 1

Given the definitions of the gates in $\mathcal{G}$:  
$$
H = \frac{1}{\sqrt{2}} \begin{bmatrix}
1 & 1 \\ 
1 & -1
\end{bmatrix}, \quad 
CX = \begin{bmatrix}
1 & 0 & 0 & 0 \\ 
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 \\ 
0 & 0 & 1 & 0
\end{bmatrix}, \quad 
CCX = \begin{bmatrix}
1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 
0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\ 
0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\ 
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 
0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\ 
0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\ 
0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0 & 0 & 0 & 1 & 0
\end{bmatrix}, \quad 
S = \begin{bmatrix}
1 & 0 \\ 
0 & i
\end{bmatrix}
$$
we observe that the elements of the matrices representing these gates are confined to the set $\left\{ 0, 1, -1, \frac{1}{\sqrt{2}}, -\frac{1}{\sqrt{2}}, i \right\}$.

Now, consider a matrix $U$ representing a circuit composed of these gates. This matrix is constructed through vertical compositions (using the Kronecker product) and horizontal compositions (using matrix multiplication) of the gates in $\mathcal{G}$. As a result, the entries of $U$ are linear combinations of the entries of the individual gates in $\mathcal{G}$.  

The set $\{0, 1, -1, i\}$ contains all possible elements of the gates $CX$, $CCX$, and $S$. Since this set is contained in $\mathbb{Z}[i]$, and $\mathbb{Z}[i]$ is closed under both addition and multiplication, any linear combinations involving these elements remain within $\mathbb{Z}[i]$. Therefore, any sufficiently large matrix $M$, whose elements are all entries in $\mathbb{Z}[i]$, can represent these combinations.  

The entries $\frac{1}{\sqrt{2}}$ and $-\frac{1}{\sqrt{2}}$ from the Hadamard gate $H$ introduce factors of $\frac{1}{\sqrt{2}^k}$ when combining gates, where $k$ is a nonnegative integer. Multiplying $M$ with $\frac{1}{\sqrt{2}^k}$ accounts for these factors, ensuring that all possible linear combinations of the entries of all gates in $\mathcal{G}$ are included. 

Therefore, defining $U = \frac{1}{\sqrt{2}^k} M$ ensures that all possible entries of the matrix corresponding to a circuit $C$ over $\mathcal{G}$ can exist in $U$. This definition properly establishes $U$ as the unitary matrix represented by $C$.

### 2

The Pauli group consists of the identity matrix, the Pauli matrices and their products with $\pm 1$ and $\pm i$. 

Considering the action of the $H$ and $S$ matrices on each of the Pauli matrices, we (with the help of an online calculator) see that 
$$
   H Z H^\dagger = X, \quad H X H^\dagger = Z, \quad H Y H^\dagger = - Y \quad S Z S^\dagger = Z, \quad S X S^\dagger = Y \quad S Y S^\dagger = -X
$$
This implies that the conjugation of elements of the Pauli group by the elements of the $\langle H, S\rangle$ subgroup is a mapping of the Pauli group back to itself. Since the Pauli group is finite, then $\langle H,S \rangle$ generates a finite subgroup, and is therefore not dense in $\text{U}(2, \mathbb{C})$. 

### 3

##### (a)

After applying the first set of Hadamard gates, the states of the first and second qubits are each 
$$\frac{1}{\sqrt{ 2 }}\ket{0} + \frac{1}{\sqrt{ 2 }}\ket{1}  $$
The composite state of the system at this point is
$$\frac{1}{2} (\ket{00}\ket{\psi} + \ket{01}\ket{\psi} + \ket{10}\ket{\psi} + \ket{11}\ket{\psi}) $$
Applying the CCNOT gate applies the $X$ gate to the state of the third qubit when the first two qubits are $\ket{1}$
 $$\frac{1}{2} (\ket{00}\ket{\psi} + \ket{01}\ket{\psi} + \ket{10}\ket{\psi} + \ket{11}X\ket{\psi})$$
 Applying the S gate to the third qubit
 $$\frac{1}{2} (\ket{00}S\ket{\psi} + \ket{01}S\ket{\psi} + \ket{10}S\ket{\psi} + \ket{11}SX\ket{\psi})$$
Applying another CCNOT gate
 $$\frac{1}{2} (\ket{00}S\ket{\psi} + \ket{01}S\ket{\psi} + \ket{10}S\ket{\psi} + \ket{11}XSX\ket{\psi})$$
 And finally, applying a Hadamard gate to the first two qubits again
  $$\begin{aligned}
\frac{1}{4} [(\ket{00} + \ket{01} + \ket{10} + \ket{11})S\ket{\psi} + 
\\(\ket{00} - \ket{01} + \ket{10} - \ket{11})S\ket{\psi} + \\
(\ket{00} + \ket{01} - \ket{10} - \ket{11})S\ket{\psi} + \\
(\ket{00} - \ket{01} - \ket{10} + \ket{11})XSX\ket{\psi}]
\end{aligned}$$
Cancelling out some terms, the state of the composite system becomes 
$$\begin{aligned}
& \frac{1}{4} [(\ket{00})S\ket{\psi} + \\
& (\ket{00} + \ket{10})S\ket{\psi} + \\
& (\ket{00} + \ket{01} - \ket{11})S\ket{\psi} + \\
& (\ket{00} - \ket{01} - \ket{10} + \ket{11})XSX\ket{\psi}] \\
= 
& \frac{1}{4} [(3\ket{00} + \ket{10} + \ket{01} - \ket{11})S\ket{\psi} + \\
& (\ket{00} - \ket{01} - \ket{10} + \ket{11})XSX\ket{\psi}] \\
\end{aligned}$$
----

If the first two qubits were measured as $0$, then we know that the state of the third qubit is 
$$(\frac{3}{4}S + \frac{1}{4}XSX)\ket{\psi} $$
Calculating the matrix for $(\frac{3}{4}S + \frac{1}{4}XSX)$:

$$\begin{bmatrix}
\frac{3}{4} & 0 \\ 0 & \frac{3i}{4}
\end{bmatrix} + 
\frac{1}{4} \begin{bmatrix}
i & 0 \\ 0 & 1 
\end{bmatrix} = 
\frac{1}{4}
\begin{bmatrix}
3 + i & 0 \\ 0 & 3i + 1
\end{bmatrix}
$$
Given that $\cos\left( \theta \right) = \frac{3}{5}$, we can use trigonometric identities to find that $\cos\left( \frac{\theta}{2} \right) = \frac{2}{\sqrt{ 5 }}$ and $\sin\left( \frac{\theta}{2} \right) = \frac{1}{\sqrt{ 5 }}$. The $R_{z}(\theta)$ matrix therefore evaluates to 
$$\begin{bmatrix}
\frac{2 - i}{\sqrt{ 5 }} & 0 \\ \\
0 & \frac{2+i}{\sqrt{5 }} 
\end{bmatrix}$$
To prove that $\frac{1}{4}(3S + XSX)$ and $R_{z}(\theta)$ are equivalent up to a global phase, we need to show that there exists some some $\alpha \in \mathbb{C}$ such that
$$(\frac{3}{4}S + \frac{1}{4}XSX) = \alpha R_{z}(\theta)$$
We can normalize the matrix $(3S + XSX)$ by dividing it by the magnitude of the entries of its matrix, which is $\sqrt{ 1 + 3^2 } = \sqrt{ 10 }$ for both entries
$$\begin{bmatrix}
\frac{3+i}{\sqrt{ 10 }} & 0 \\ 0 & \frac{3i + 1}{\sqrt{ 10 }}
\end{bmatrix}$$
$\frac{1}{4}(3S + XSX)$ thus becomes 
$$\frac{\sqrt{ 10 }}{4}\begin{bmatrix}
\frac{3+i}{\sqrt{ 10 }} & 0 \\ 0 & \frac{3i + 1}{\sqrt{ 10 }}
\end{bmatrix} = \sqrt{ \frac{5}{8} }\begin{bmatrix}
\frac{3+i}{\sqrt{ 10 }} & 0 \\ 0 & \frac{3i + 1}{\sqrt{ 10 }}
\end{bmatrix}$$
I then used an online calculator to solve for the following
$$\alpha = \frac{3 +  i}{\sqrt{ 10 }}\cdot \frac{\sqrt{ 5 }}{2- i} = e^{i\pi/4}$$
And to confirm that this works for the bottom right entry 
$$\frac{2+i}{\sqrt{ 5 }} e^{i \pi /4}$$
Therefore, since $\frac{1}{4}(3S + XSX) = e^{i \pi/4}$, applying $\frac{1}{4}(3S + XSX) = e^{i \pi/4}$ to a qubit is equivalent to applying $R_{z}(\theta)$ up to a global phase. 

---

If the first two qubits are not measured to be $0$, then the composite state of the system is 
$$\begin{aligned}
& \frac{1}{4} [(\ket{10} + \ket{01} - \ket{11})S\ket{\psi} + \\
& (- \ket{01} - \ket{10} + \ket{11})XSX\ket{\psi}] 
\end{aligned}$$

Calculating the matrix for ($\frac{1}{4}(S - XSX)$): 
$$\frac{1}{4}\begin{bmatrix}
1 - i & 0 \\ 0 & i - 1
\end{bmatrix}$$
Which can also be expressed as 

$$\frac{1}{4} \frac{2}{\sqrt{ 2 }} \begin{bmatrix}
e^\left( -i \frac{\pi}{4} \right) & 0 \\ \\
0 & - e^{-i \frac{\pi}{4}}
\end{bmatrix} = \frac{1}{2 \sqrt{ 2 }} \begin{bmatrix}
e^\left( -i \frac{\pi}{4} \right) & 0 \\ \\
0 & - e^{-i \frac{\pi}{4}}
\end{bmatrix}$$
Since the $Z$ matrix can be expressed as 
$$\begin{bmatrix}
e^{i 2 \pi} & 0 \\ 0 & - e^{i 2 \pi} \\
\end{bmatrix}$$
We see that $\frac{1}{4}(S - XSX) = \frac{1}{4}e^{-8} Z$, and therefore, $\frac{1}{4}(S - XSX)$ is equivalent to $Z$ up to a global phase.

##### (b) 

Looking at the composite state of just the first two qubits prior to measurement: 
$$\begin{aligned}
& \frac{1}{4} [(3\ket{00} + \ket{10} + \ket{01} - \ket{11}) + \\
& (\ket{00} - \ket{01} - \ket{10} + \ket{11})] \\ \\
= & \frac{3}{4}\ket{00} + \frac{1}{4}\ket{10} + \frac{1}{4}\ket{01} - \frac{1}{4}\ket{11} + \\
& \frac{1}{4}\ket{00} - \frac{1}{4}\ket{01} - \frac{1}{4}\ket{10} + \frac{1}{4}\ket{11} \\ \\
\end{aligned}$$
The probability that the first two qubits are both $0$ is the sum of the square of the amplitudes of all $\ket{00}$ states divided by that of all available states:

$$\frac{\frac{9}{16} + \frac{1}{16}}{\frac{6 + 9 + 1}{16}} = \frac{10}{16} = \frac{5}{8}$$
##### (c)

Since the probability that both of the first two qubits are $0$ after one trial is $\frac{5}{8}$, the probability of 
either qubit being $1$ is $1 - \frac{5}{8}$. Applying the circuit $n$ times results in a probability of success of $1-\frac{5}{8}^n$. Taking the limit of this expression as $n$ approaches $\infty$: 
$$\lim_{n \rightarrow \infty} 1- \left(\frac{5}{8} \right)^n = 1 - \lim_{ n \to \infty} \frac{5}{8} = 1 - 0 = 1$$
 Hence, the probability of either qubit being measured as $1$ approaches $1$ as a function of the number of trials. Since we have proven that the $R_{z}(\theta)$ gate is applied to the third qubit when either of the first two qubits are measured as $1$, we can conclude that repeatedly applying this circuit applies the $R_{z}(\theta)$ gate to the third qubit with probability approaching $1$. 
 
 If we want to show that repeatedly applying this circuit and the $S^2 = Z$ gate yields the same effect, we can enforce that each time the $Z$ gate is applied by the circuit, we apply $S^2$ after. Since $Z^2 = I$, applying $Z$ in this way has no effect on the probability calculation above, and therefore, we can claim applying a combination of this circuit and the $Z$ gate also applies the $R_{z}(\theta)$ gate to the third qubit with probability approaching $1$. 

### 4

##### (a)
$$\cos(\theta) = \frac{3}{5} \implies \sin(\theta) = \sqrt{1 - \left( \frac{3}{5} \right)^2} = \frac{4}{5}$$
$$e^{i \theta} = \cos(\theta) + i \sin(\theta) = \frac{3}{5} + \frac{4i}{5} = \frac{3 + 4i}{5}$$

##### (b) 

If $\theta$ is a rational multiple of $2\pi$ then
$$\theta = \frac{a}{b} 2 \pi \quad \text{for} \quad a,b \in \mathbb{Z}$$
Which implies 
$$3 + 4i = 5 e^{i \theta} = 5 e^{i 2 \pi a /b}$$
If we let $m = |b|$, then $(3+4i)^5$ becomes 
$$5^m (\cos(2 \pi) - i \sin(2\pi)) = 5^m$$

##### (c)

**Base Cases:**  

For $m = 1$:  
$$
(3+4i)^1 = 3+4i \equiv 3+4i \mod 5.
$$  
The claim holds.  

For $m = 2$:  
$$
(3+4i)^2 = -7 + 24i = 3 + 4i \mod 5.
$$  
The claim holds.

**Inductive Hypothesis:**  

Assume $(3+4i)^m \equiv 3+4i \mod 5$ for all positive integers $m$ up to some $k$.  

**Inductive Step:**  

We need to show that $(3+4i)^{k+1} \equiv 3+4i \mod 5$.  Given that:
$$
(3+4i)^{k+1} = (3+4i)^k \cdot (3+4i).
$$ And, using the inductive hypothesis:
$$
(3+4i)^k \equiv 3+4i \mod 5.
$$  
Substituting:  
$$
(3+4i)^{k+1} \equiv (3+4i) \cdot (3+4i) \mod 5.
$$  
From the base case $(3+4i)^2 \equiv 3+4i \mod 5$:  
$$
(3+4i)^{k+1} \equiv 3+4i \mod 5.
$$  
**Conclusion:**  

By induction, $(3+4i)^m \equiv 3+4i \mod 5$ for all $m \geq 1$.  

##### (d)

Let $\theta \in \left[ 0, \frac{\pi}{2} \right]$ such that $\cos(\theta) = \frac{3}{5}$ and consider, for the sake of contradiction, that $\theta$ was a rational multiple of $2 \pi$. In $(b)$, we showed that if $\theta$ was a rational multiple of $2 \pi$ then $(3+4i)^{m} = 5^m$ (where $e^{i \theta} = \frac{3 + 4i}{5}$). However, in $(c)$, we showed that $(3+4i)^m = 3+4i \mod{5}$ for all positive integers $m$, which leads to a contradiction. Therefore, by contradiction, it must be true that $\theta$ is a rational multiple of $2\pi$.