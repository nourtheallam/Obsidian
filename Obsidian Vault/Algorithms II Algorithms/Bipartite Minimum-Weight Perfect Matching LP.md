To be solved over a [[Complete Bipartite Graph]], we shall use [[Primal-Dual Schema]]. 

Formulate an LP: 
![[Pasted image 20241215133255.png]]
And its [[Dual]]: 
![[Pasted image 20241215140330.png]]
We maintain [[Complementary Slackness]]: 

![[Pasted image 20241215140551.png]]

Now, set $\pi_{u} - nz - y_{u}$ and $\pi_{w} - y_{w}$ to make our Dual look nicer: 
![[Pasted image 20241215151714.png]]
Our complementary slackness conditions then become
![[Pasted image 20241215151741.png]]

$\rightarrow$ We can think of $\pi_{v}$ as the **potential** of a vertex $v$. The condition above tells us that we need to find a matching of the graph $M$ (a feasible solution $x$ for the primal), while maintaining that the potential of every edge in $M$ is **tight** (should not exceed $c_{u,w}$, if it does then, by complementary slackness, $x_{u,w} = 0$, meaning that it is not included in the matching $M$).  
