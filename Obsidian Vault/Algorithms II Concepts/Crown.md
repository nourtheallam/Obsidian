Two sets of vertices, $I, H$. $I$ is an independent set and every neighbour of some vertex $I$ is in $H$. 

![[Pasted image 20241214150115.png]]

The [[Bipartite]] graph between $I$ and $H$ (which possibly excludes edges between vertices in $H$), has a [[Matching]] of size $|H|$. 

**(1) The [[Bipartite]] graph has a [[Matching]] of size $|H|$**
![[Pasted image 20241214150308.png]]
Therefore, no vertex in $H$ is unmatched, which means that the size of the [[Matching]] is exactly the number of vertices in $H$.

**(2) If $G$ is a [[Bipartite]] graph, then it either has a maximum [[Matching]] $M$ that matches every vertex in $I \subseteq U$ or a crown. Determining this takes $O(\sqrt{ n}m)$ time.**

We show that, using  the Hopcroft-Karp algorithm, we can compute the maximum [[Matching]] of a graph in $O(\sqrt{ n }m)$ time. Once we compute this [[Matching]], we can check if every vertex in it belongs to $U$ in $O(n)$ time. If they don't, then we can run [[Alternating BFS]] on it so that we can find $I$ and $H$. 
