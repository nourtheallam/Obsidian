
##### Main idea:

We formulate the minimum-weight perfect matching problem as an LP, then take a modified version of the dual of that LP, and apply the [[Primal-dual schema]].

##### Description:

- The dual LP has the constraint that $\pi_{u} + \pi_{w} \leq c_{u,w}$
- The primal has the constraints that 
$$\begin{aligned}
\sum x_{e} \geq n \\
\sum x_{u,w} \leq 1 \\
\sum x_{u,w} \leq 1
\end{aligned}$$

We use the [[Alternating BFS]] on the **tight potential** subgraph of $G$, $G^\pi$, such that in each **phase** we add one more edge to the matching while maintaining the feasibility of the dual.

- We initialize $\pi$ to be feasible for all constraints, and tight for some.
- Build the [[Alternating forest]] of $G^\pi$, then attempt to find a **tight augmenting path** in it.
	- If none exist, then we need to adjust the potential function $\pi$ to be $\pi'$
	- We do that by

![[Pasted image 20241217182918.png]]
- Which results in a vertex in $\bar{Y}$ being added to $G^\pi$

##### Proof of correctness:

1. $\pi'$ is feasible

The way we define $\pi'$ implies that 
- $\pi'_{u} + \pi'_{w} \leq c_{u,w}$ if $u \in X$, $w \in Y$
- $\pi'_{u} + \pi'_{w} = c_{u,w}$ if $u \in X, w \in \bar{Y}$

2. Adjustment always increases the number of edges in the [[Alternating forest]].

Since we add $\delta$ to one of $\pi_{u}, \pi_{w}$ and remove it from the other for $u \in X, w \in Y$, we can see that $\pi_{u} + \pi_{w} = \pi_{u}' + \pi_{w}'$, and therefore, they would be included in the new [[Alternating forest]].

If $u \in X, w \in \bar{Y}$, then the edge is defined as tight, which makes sure that it is in the [[Alternating forest]].

As a property of the [[Primal-dual schema]], once our primal solution is feasible (which happens after we run $n$ phases), our dual solution becomes feasible, too.
##### Running time 

- We will run each phase $O(n)$ times $=$ size of a perfect matching
	- [[Alternating forest]] in $O(n+m) = O(n^2)$ because $G$ is complete
	- Run $O(n)$ iterations because we add all the edges in $W$ at most
		- Adjustment takes $O(n^2)$ because we might have to look at every edge

Overall running time: $O(n^4)$