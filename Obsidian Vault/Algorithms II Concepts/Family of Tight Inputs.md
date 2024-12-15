---
~
---

A way for us to ensure that our analysis of the [[Approximation]] guarantee of an [[Approximation]] algorithm is tight.

Given an [[Approximation]] algorithm, does there exist an infinite family of inputs for which the algorithm cannot perform significantly better than the upper/lower bound proven?

**Example:** [[Vertex Cover 2-Approximation]] 

Consider the set of complete [[Bipartite]] graphs over $2n$ vertices, a maximal [[Matching]] of any such graph includes all $2n$ vertices, and therefore the algorithm computes a [[Vertex Cover]] of size $2n$. However, a [[Vertex Cover]] of size $n$ does exist as the graph is complete. 

