##### Idea

A naive implementation: 
- Considers all permutations of vertices, 
- Check if the cycle represented by each actually exists 
- Remember the cheapest cycle
This yields $O^*(n!)$ time. 

$\rightarrow$ Maybe we can find the TST of the graph without each vertex $u$ then reincorporate $u$ as cheaply as possible?
	 **No. An optimal TST isn't composed of smaller TSTs.** 

Instead, consider:
	A cycle that "starts" with $v_{1}$ and ends with $v_{i}$ before $v_{1}$ **must include** the edge $(v_{i}, v_{1})$. 

Therefore, we recurse on the following: 
$$\min_{2 \leq i \leq n}(P(V, i) + w(v_{i}, v_{1}))$$
Where $P(V,i)$ is the length of the path that starts with $v_{1}$ and ends with $v_{i}$. 

##### Steps/Running time

We build a table storing $P(V,i)$ for $2 \leq i \leq n$. 
	The size of this table is bounded by $2^{n-1}\cdot n$ as for every vertex except our "$v_{1}$", we either choose for it to be in the subset or not. The times $n$ term is because we have $n$ choices for our "$v_{1}$" vertex.
	It can be

Each individual entry can be computed in constant because: 

- If $v_{1}$ is the only vertex in the subset, then $P(V,i) = 0$ if $i=1$. 
- If we have more vertices, then $P(V, i) = \min(P(V - v_{i}, j) + w(v_{j}, v_{i}))$ where $v_{j}$ is the vertex preceding $v_{i}$,  