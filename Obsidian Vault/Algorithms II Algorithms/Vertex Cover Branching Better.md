$\rightarrow$ If $|N[v]| \geq 2$ then the difference between $G$ and $G - N[v]$ is not just $1$, making our [[Branching vector]] of $(1,1)$ overly pessimistic.

$\rightarrow$ If $|N[v]| = 1$ then $v$ is the only vertex in its neighbourhood, so it has no edges, and therefore, any [[Vertex Cover]] of $G-v$ is also a [[Vertex Cover]] of $G$. 

$\rightarrow$ The same logic applies to the [[Maximum Independent Set Branching]]. An independent set of $G$ will be exactly and independent of $G-v$ plus $v$.

So, a s a better [[Branching]] rule, we only branch when $|N[v]| \geq 2$, where this gives us the [[Branching vector]] $(1,2)$, and a [[Branching number]] of $1.62$. 

$\rightarrow$ We can do even better by considering the fact that any degree $1$ vertex will have to be the one covering its edge (or its neighbour would). 

$\rightarrow$ Therefore, we don't even branch if $v$ is a degree-$1$ vertex, meaning that the size of the neighbourhood of $N[v]$ would have to be $\geq 2$, and therefore, that the [[Branching vector]] becomes $(1,3)$ with a [[Branching number]] of $1.47$. 


