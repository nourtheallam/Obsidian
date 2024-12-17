
##### Main idea:

We formulate the minimum-weight perfect matching problem as an LP, then take a modified version of the dual of that LP, and apply the primal-dual schema.

##### Description:

- The dual LP has the constraint that $\pi_{u} + \pi_{w} \leq c_{u,w}$
- The primal has the constraints that 
$$\begin{aligned}
\sum x_{e} \geq n \\
\sum x_{u,w} \leq 1 \\
\sum x_{u,w} \leq 1
\end{aligned}$$

We use the alternating BFS on the **tight potential** subgraph of $G$, $G^\pi$, such that in each **phase** we add one more edge to the matching while maintaining the feasibility of the dual.

- We initialize $\pi$ to be feasible for all constraints, and tight for some.
- Build the alternating forest of $G^\pi$, then attempt to find a **tight augmenting path** in it.
	- If none exist, then we need to adjust the potential function $\pi$ to be $\pi'$
	- We do that by

![[Pasted image 20241217182918.png]]
- Which results in a vertex in $\bar{Y}$ being added to $G^\pi$

##### Proof of correctness:

1. $\pi'$ is feasible

The way we define $\pi'$ implies that 
- $\pi'_{u} + \pi'_{w} \leq c_{u,w}$ if $u \in X$, $w \in Y$
- $\pi'_{u} + \pi'_{w} = c_{u,w}$ if $u \in X, w \in \bar{Y}$

2. Adjustment always increases the number of vertices in the alternating forest.