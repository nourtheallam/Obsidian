Consider the LP relaxation of the ILP formulation of the [[Set Cover]] problem
![[Pasted image 20241209210504.png]]
And its [[Dual]]
![[Pasted image 20241209210522.png]]
We can think of this [[Dual]] as **"packing"** the values $y_{e}$ for each element $e$ into $S$ without exceeding its weight capacity $w_{S}$. 

If we apply the [[Set Cover Greedy]] algorithm, it's possible that the sum 
$$\sum_{e \in S}p_{e}$$
**exceeds** the total weight of $S$, $w_{S}$, because there may be some elements in $S$ that were assigned a weight and added to $C$ by some other set. This makes the solution $y_{e} = p_{e}$ infeasible. 

**This makes sense because if it was feasible, then the primal corresponding to it would be optimal, which would give us a solution to the [[Set Cover]] problem that is computable in polynomial time.**

Now, consider the solution 
$$y_{e} = \frac{p_{e}}{H_{n}}$$
**Claim:** this is a feasible solution of the [[Dual]]

**Proof:** 

Order the elements in some set $S$, whose size is $k$, by the order in which they are covered: $e_{1}, \dots, e_{k}$

Consider when $e_{i}$ is added. At this point, at least $e_{i}, \dots, e_{k}$ are uncovered, and so, the cost of adding $S$ to $C$ would be 
$$\frac{w_{S}}{k-i+1} = w_{s}$$
Since each iteration picks the set that would cover $e_{i}$ with minimum cost, we observe that
$$\sum_{e \in S} p_{e} \leq w_{S}\sum_{i = 1}^k \frac{1}{k-i+1} = w_{S} . H_{k}$$
And since $k \leq n$
$$\sum_{e \in S} y_{e} = \frac{\sum_{e \in S}p_{e}}{ H_{n}}\leq w_{S} . \frac{H_{k}}{H_{n}} \leq w_{S} $$
Which means that such a solution is feasible, and therefore, by [[Weak Duality]], that a feasible solution to the primal will be an $H_{n}$-[[Approximation]] to an optimal solution. 

- [ ] Double check the above conclusion #todo
