---
~
---
**Problem:** Find the minimum weight tree that includes all **terminal** vertices. 

##### Ideas

A **naive** approach would be to compute all possible minimum spanning trees of **subsets** that are bigger than or exactly equal to our set of **terminals**. 
	However, this yields $O^*(2^n)$.

- We choose to **parameterize the algorithm** with $k$ being the size of the set of terminals $|T|$.
- Moreover, we **simplify the input** by **turning every terminal into a leaf**. ![[Pasted image 20241218181347.png]]
- Instead of considering every possible tree, we consider all possible subsets of $k-1$ vertices of $T$, call such a subset $U$ paired with **any vertex** not in $U$, $v$:
$$S(U,v)$$
- We can use this to eventually get the answer to $S(\{ t_{1}, \dots t_{k-1} \}, t_{k})$
- Since there are $2^{k-1}$ choices of subsets $U$ and $n$ choices of the vertex $v$.
##### Steps

If $U$ contains just **one** vertex, $t_{i}$, then the weight of the Steiner tree is just the weight of the edge $(t_{i}, t_{k})$. 

Otherwise, we let $S(U, t_{k})$ be defined as 
$$\min_{\emptyset \subset W \subset U} \min_{w \notin T} \left(S(W,w) + S(U - W, w) + dist(v,w) \right)$$
Where $W$ is **some partition** of $U$ that satisfies the minimization above. 
![[Pasted image 20241219191554.png]]
##### Correctness

We need to show that $S(U,v)$ is indeed a Steiner tree for $U$.
- $dist(v,w)$ is a shortest path from $v$ to $w$.
- $w$ is **not a terminal** because we ==defined every terminal to be a leaf, and it has to have at least two incident edges.== 
- 
##### Analysis

The table has $O(2^{k-1}n)$ entries.

Each entry takes $O(2^{|U|})\cdot n$ time to compute each entry because we have to consider **all possible subsets** $W$ of $U$ and all possible $w$ but we can use previously computed answers to lookup the answer to $S(W,w), S(U-W,w)$ in polynomial time. 

Therefore, the total running time is 

![[Pasted image 20241219203539.png]]