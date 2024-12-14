Unlike a normal decision problem 
$$\mathcal{L} \subseteq\sum*$$
A **parameterized** decision problem 
$$\mathcal{L} \subseteq\sum* \times \mathbb{N}$$
is a language with instance
$$(x,k) \in \sum* \times \mathbb{N}$$
Where $k$ is the problem's parameter.


**An parameterized problem is [[FPT]] if and only if it has a [[Problem kernel]].**

If a problem has a [[Kernelization]] procedure, then it can be solved in 
$$O(g(k) + |I|^c)$$ time. And 
$$O(g(k) + |I|^c) = O^*(g(k))$$
If a problem is [[FPT]], then we know that its running time is exponentially-dependent on some [[Hardness parameter]] $k$. More specifically, that there exists some [[FPT]] algorithm for it whose running time is $O(f(k) \cdot |I|^c)$. We can get a [[Kernelization]] algorithm from this by: 

##### Option A

Run the first $|I|^{c+1}$ **steps** of the algorithm. If it terminates within these steps, then, by the rules of [[Kernelization]], 
$$f(k) < |I|^c$$
And therefore, we should be certain that it has either a yes or no instance. 

##### Option B

If it does not, then we take $(I,k)$ to be the kernel and since $|I| \leq f(k)$, we can state that $(I,k)$ is a [[Problem kernel]] of **size** $O(f(k))$. 