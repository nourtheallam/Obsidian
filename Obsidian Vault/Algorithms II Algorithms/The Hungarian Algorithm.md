The [[Bipartite Minimum-Weight Perfect Matching LP]] formulation gave us the following property

![[Pasted image 20241215152300.png]]

Now, our goal will be to apply the [[Primal-Dual Schema]] to find an optimal solution (minimum-weight [[Perfect matching]]) to the primal.

1. We initialize all $\pi_{w} = 0$ and $\pi_{u} = min(c_{u,w})$. This is a feasible solution as it satisfies $\pi_{u} + \pi_{w} = c_{u, w}$. 
2. **Look** for a **tight** [[Augmenting Path]] $P$ for $M$ and perform $M = M \oplus P$. 
	1. If there is no tight [[Augmenting Path]], then **adjust** the potential function $\pi$ such that we can find one.

Since a [[Perfect matching]] of a [[Complete Bipartite Graph]] will have exactly $n$ edges in it, we should be able to find a [[Perfect matching]] within $n$ iterations of the steps above.

**Tight:** one that satisfies $\pi_{w} + \pi_{u} = c_{u, w}$ for every edge $x_{u,w}$ on that path. 

**Look:** Using the [[Alternating BFS]] routine, we will construct a an [[Alternating Forest]] based on the subgraph $G^\pi$ that consists only of **tight** edges. We can then look for an [[Augmenting Path]] in $O(n)$ time.

**Adjust:**

![[Pasted image 20241215162433.png]]
We would have to perform the above at most $n$ times to make sure that all the vertices in $W$ are in the **tight** [[Alternating Forest]]. 
	$\rightarrow$ As long as $M$ is not a [[Perfect matching]], as justified in the proof of the [[Alternating BFS]] routine, then there will exist an unmatched vertex in $W$. 

Therefore, during each **phase**, we will have at most $n$ **adjustment** iterations.

**Proofs:**

**1. $\pi'$ is feasible**

Observe that 
![[Pasted image 20241215165038.png]]
Which implies that 
![[Pasted image 20241215165018.png]]
Therefore, unless $u \in X$ and $w \in \bar{Y}$, it will trivially be true that 
$$\pi'_{u} + \pi'_{w} \leq c_{u,w}$$
If $u \in X$ and $w \in \bar{Y}$ then
![[Pasted image 20241215165249.png]]
So, we're good.

**2. Before augmentation, $u \in X \iff w \in Y$**

$\rightarrow$ Assume that $u \in X$. Then there exists a tight alternating path between $u$ and an unmatched vertex $u' \in U$ whose length is **even**. Since $(u,w) \in M$, it must be tight, and therefore, there exists a tight alternating path between $u'$ and $w$, making $u \in Y$. 

$\rightarrow$ Assume that $w \in Y$. Then there exists an **odd**-length tight alternating path between $w$ and an unmatched vertex $u' \in U$. Since $(u, w) \in M$, it is a tight edge, adding it to this path gives a tight alternating path between $u'$ and $u$, which makes $u \in X$. 

**3. Adjustment always increase the number of vertices in the [[Alternating Forest]]**

$\rightarrow$ If consider the vertex $z$ that is in $X \cup Y$ but not in $F^{\pi'}$ but which has the shortest alternating path between itself and a root of the original forest. Then its predecessor $v$ would be in the new [[Alternating Forest]], meaning that there exists an alternating tight path between $v$ and a root of the new forest. Since $(v,z)$ is the old forest, it is tight and $v,z$ would be an $X,Y$ pairing, which means that their **potential function values don't change, which would make them a part of the new [[Alternating Forest]] as well because there would exist a tight alternating path between a root and $z$**. This is a contradiction, which means that every vertex in $X \cup Y$ will exist in $X' \cup Y'$. 

Now, consider $(u,w)$ such that $u \in X$ and $w \in \bar{Y}$. We already know that this edge is tight. Since $u \in X$, it must be true that there exists an even alternating tight path between $u$ and some other vertex $u'$. Since this path has to end in an edge in $M$, and we showed that $(u,w)$ is in $M \iff$ $u \in X, w\in Y$, that that matched edge it ends in must be related to $u'$. So, there exists a tight alternating path between $u'$ and $w$ which means that $w \in Y'$, and therefore, that $Y \subset Y'$. 

**Running time**

We said earlier that we need $O(n)$ phases and each phase is $O(n)$ iterations, so a total of $O(n^2)$ iterations is ran. Running augment/adjust on each iteration takes $O(n^2)$ time because at the very least, we have to inspect every edge in the graph, and since the graph is complete, we have $O(n^2)$ edges.

Therefore, the overall running time is $O(n^4)$. 


