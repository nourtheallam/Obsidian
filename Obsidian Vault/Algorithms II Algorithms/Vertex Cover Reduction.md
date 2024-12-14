We employ three reduction rules
	**Singleton:** Remove $0$-degree vertices.
	**Degree-1:** If $u$ is a degree-$1$ vertex, remove $u, v$ **and** all **edges** incident to $v$. **Decrease $k$ by $1$.**
	**High-degree:** If the degree of $u$ is $\geq k+1$, remove $u$ and **all edges incident to it.** **Decrease $k$ by $1$**. 

**If $(G,k)$ is fully-reduced and $G$ is a yes-instance then $|V| \leq k(k+1)$** and $|E| \leq k^2$. 

Since $G$ is fully-reduced, we know that we have at least $2$ edges per vertex and no more than $k$. Therefore, for each vertex in the $k$ vertices that cover $G$, we have at most $k$ edges, adding up to a total of $k^2$ edges. 

if $|C| \leq k$ then, to prove that $$|V| = |V \setminus C | + |C| \leq k(k+1)= k^2 +  k$$we need to show that $|V \setminus C| = k^2$. 

Consider every edge in $G$, there are $k^2$ of them. If an edge $(u,v)$ has that $u \in V \setminus C$ then $v \in C$ must be true. Therefore, there is at most one vertex in $V \setminus C$ per edge, which means that there are at most $k^2$ vertices in $V \setminus C$, which therefore proves our claim. 