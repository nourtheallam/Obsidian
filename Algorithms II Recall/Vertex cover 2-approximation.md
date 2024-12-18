##### Steps

- Pick an arbitrary edge in $G$
	- Add its endpoints to $C$
	- Remove the edge and **all edge incident to its endpoints**

##### Proof

1. This algorithm computes a maximal matching $M$

Suppose, for the sake of contradiction, that it didn't. Then, at least two of the edges we added share an endpoint. However, this is impossible because we remove each edge we add and all the edges that share its endpoints.

2. If we take all the vertices in $M$, they are a vertex cover of size $\leq 2|M|$

Suppose, for the sake of contradiction, that it wasn't a vertex cover. Then there exists an edge none of whose endpoints was an endpoint of an edge that was added to $M$. However, this is also not possible because we iterate until the graph is empty, etc.

3. Any **optimal** vertex cover of $G$ will have a size $\geq |M|$

Since an edge in a matching acts as a "representative" for all the edges in the neighbourhood of its endpoints, a vertex cover needs to at include at least one vertex per edge in the matching.

##### Approximation

$$\begin{gathered}
|C| \leq 2|M| \\
|M| \leq |C^*| \\
\\
\downdownarrows \\ \\
|C| \leq 2|M|
\end{gathered}$$
