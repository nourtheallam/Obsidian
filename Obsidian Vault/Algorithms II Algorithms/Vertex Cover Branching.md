---
~
---
Since the [[Vertex Cover]] of some graph $G$ must include a vertex $v$ or all its neighbours, one [[Branching]] algorithm to compute the [[Vertex Cover]] of $G$ recursively computes the [[Vertex Cover]] of $G - N[v]$ and $G - v$ then returns the smaller of $C_{N(v)} \cup N[v]$ and $C_v \cup v$.

**Proof:** If there existed a [[Vertex Cover]] $C$ of $G$ that was smaller than the one produced by the algorithm above, then $|C - v| = |C| - 1 < |C_v|$ which is a contradiction because $C_v$ is the smallest [[Vertex Cover]] of $G - v$.

**Running time:** We make two recursive calls on $G-v$ and $G - N[v]$, each with input size at most $(n-1)$, so our [[Branching vector]] is $(1,1)$ and therefore $c$ is the root of the polynomial $c - 1 - 1 = 2$. Therefore, we make $O(2^{n})$ recursive calls. Since each call would take $O(n+m)$ time, the overall running time is $O(2^n(n+m)) = O^\star(2^n)$ time.

--- 
