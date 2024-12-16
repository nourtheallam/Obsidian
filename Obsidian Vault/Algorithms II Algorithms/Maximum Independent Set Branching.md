Very similar to the [[Vertex Cover]] [[Branching]] algorithm, our "elementary choice" is whether a vertex should be the independent set or not. 

At each iteration, we compute the independent set of $G-v$ and $G-N[v]$, call them $I_{N[v]}$, respectively, and we output the larger of $I_{v} \cup N[v]$ and $I_{V[v]} \cup \{ v \}$.

The biggest difference between this and the [[Vertex Cover]] [[Branching]] is that if $G$ is an isolated graph, then we simply return all the vertices in it.

The running time analysis of this is exactly the same as the [[Vertex Cover]] running time analysis. 