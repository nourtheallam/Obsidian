While it is not as simple as the [[Vertex Cover Half-Integrality]], we can still find a half-integral solution for the [[Multiway Vertex Cut]] problem.

Let $\tilde{x}$ be an optimal fractional solution, and let $R_{i}$ be the **region** of vertices **whose solution is $\tilde{x}_{v = 0}$,** reachable from terminal $t_{i}$. Lastly, let $B_{i}$ be the set of vertices reachable from vertices in $R_{i}$.

Lastly lastly, let $Q_{1}$ be all the vertices that exist in exactly one boundary while $Q_{2}$ is all the **vertices that exist in more than one boundary.**

![[Pasted image 20241216125739.png]]

And define $\hat{x}$ as the solution

![[Pasted image 20241216125845.png]]

We **claim** that $\hat{x}$ is a feasible solution.

**Proof:** 

When looking at the path $P$ between two terminals, you will always encounter at least one vertex in $Q_{2}$, or two vertices in $Q_{1}$. 

Therefore, 
![[Pasted image 20241216130513.png]]

We also **claim** that it is an optimal solution. We shall prove this using [[Complementary Slackness]]. 

**Primal:**

![[Pasted image 20241216130706.png]]

**[[Dual]]:**

![[Pasted image 20241216130746.png]]


Our **[[Complementary Slackness]]** conditions are: 
![[Pasted image 20241216130828.png]]

Observe that 

![[Pasted image 20241216131101.png]]

