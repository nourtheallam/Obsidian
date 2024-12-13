---
~
---
## 6: Quantum Algorithms

#### Tools

- Any classical function $f$ can be represented using a quantum circuit $U_{f}$ built on the gate set $\{ C, CX, CCX \}$ where $$U_{f}\ket{\vec{a}}\ket{\vec{b}}  = \ket{\vec{a}} \ket{ \vec{b} \oplus f(\vec{a})}$$
 - Note that $$H\ket{0} = \frac{1}{\sqrt{ 2 }} \sum_{x \in \mathbb{Z}_{2}}\ket{x} $$
 - Combining the above information:$$U_{f} (H^{\otimes m} \otimes I)\ket{0}^{\otimes m} \ket{0}^{\otimes n} = U_{f} \left( \frac{1}{\sqrt{ 2 }^m} \sum_{x \in \mathbb{Z}_{2}^m}\ket{x}\ket{0}^{\otimes n} \right) = \frac{1}{\sqrt{ 2 }^m} \sum_{x \in \mathbb{Z}_{2}^m} \ket{x} \ket{f(x)} $$
 - "Phase Kickback"$$U_{f} \ket{\vec{a}}\ket{-} = (-1)^{f(\vec{a})}\ket{a}\ket{-}$$
 - $$H^{\otimes n}\ket{x} = \frac{1}{\sqrt{ 2 }} \sum_{y \in \mathbb{Z}_{2}^m} (-1)^{x\cdot y} \ket{y}  $$
 
### Deutsch's Problem

Determine whether $f$ has some property $P$

**Example:** Is $f: \mathbb{Z}_{2} \rightarrow \mathbb{Z}_{2}$ constant?

***Solution:***

Assume the input is $\ket{0}\ket{1}$
![[Pasted image 20241206191101.png]]
Applying $U_{f}$ after the first set of $H$ is applied 
$$U_{f}\left( \frac{1}{\sqrt{ 2 }}(\ket{0}+\ket{1})\ket{-} \right) = \frac{(-1)^{f(0)}}{\sqrt{ 2 }}\ket{0} \ket{-}\frac{(-1)^{f(1)}}{\sqrt{ 2 }}\ket{1} \ket{-} $$
We can then use rearrange this expression, apply the second set of Hadamard gates, and measure the first qubit to determine whether $f$ is constant. 

### Bernstein-Vazirani 

Given that represents $f(x) = x \cdot a$ for some unknown $a$, determine $a$. 

***Solution:***

Assume that the first $n$ inputs are  $\ket{0}$
![[Pasted image 20241206192136.png]]
This circuit works as 

$$\begin{aligned}
\ket{\vec{0}} \ket{1} & \mapsto \frac{1}{\sqrt{ 2 }^n} \sum_{x} \ket{x}\ket{-} \quad \text{(Applying H)} \\ 
& \mapsto \frac{1}{\sqrt{ 2 }^n} \sum_{x} (-1)^{f(x)} \ket{x} \ket{-} \quad \text{(Applying $U_{f}$)} \\
& \mapsto \frac{1}{2} \sum_{y} \sum_{x} (-1)^{x\cdot a + x \cdot y} \ket{y}\ket{1} \quad \text{(Applying H again)} \\
& = \ket{a}\ket{1} \quad \text{(After some simplification)}
\end{aligned}$$

### Deutsch-Joza
![[Pasted image 20241206194329.png]]
### Simon's Problem
![[Pasted image 20241206194440.png]]






## 7: Searching 

#### Tools
 - Diffusion operator 
 $$\begin{aligned}
D \begin{bmatrix}
a_1 \\ \vdots \\ a_{n}
\end{bmatrix} = \begin{bmatrix}
2m - a_1 \\ \vdots \\ 2m - a_{n}
\end{bmatrix}
\end{aligned}$$
- Uniform superposition using $H^{\otimes n}$
![[Pasted image 20241207200219.png]]
- Oracle $U_{f}$
![[Pasted image 20241207200401.png]]

#### Problem

Find $x^*$ such that $f(x) = 1 \iff x = x^\star$

#### Solution
![[Pasted image 20241207200603.png]]


### Quantum Error Correction

#### Problem 1:
When we send bits they may get flipped

#### Tools

- We call $\ket{\psi}$ a **fixpoint** of some matrix if it is an eigenvector of eigenvalue $1$ for it.
- ![[Pasted image 20241211135331.png]]
- ![[Pasted image 20241211135402.png]]

#### Solution 1

Apply the following circuit

![[Pasted image 20241211134058.png]]
Note that this does **not** equate copying the original states three times, but for the sake of this example, an error on the first, second, or third qubit will correspond to having at most one error occur. 

**But how do we know that an error occurred without measuring, and consequently, collapsing the state of the system?**

We add two ancillary qubits
![[Pasted image 20241211134346.png]]
Such that if the state of the ancillary qubits is: 
- $\ket{00}$: no error
- $\ket{01}, \ket{10}, \ket{11}$: error

To **correct** these errors, we apply 

![[Pasted image 20241211134858.png]]
Where $X^{x \bar{y}}$ means "apply the $X$ gate if $x =0, y=1$". 

#### Problem 2:

We consider the concept of an environment, a separable state that affects the qubit somehow

$$\ket{e} \ket{x} $$
The environment and qubit may evolve as follows

![[Pasted image 20241211140123.png]]
Where an error could occur, for example, when 
$$\ket{e_{0}} = \ket{e_{3}} = 0 $$
