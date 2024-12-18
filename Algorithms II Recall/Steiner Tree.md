---
~
---
**Problem:** Find the minimum weight tree that includes all **terminal** vertices. 

##### Ideas

A **naive** approach would be to compute all possible minimum spanning trees of **subsets** that are bigger than or exactly equal to our set of **terminals**. 
	However, this yields $O^*(2^n)$.

- We choose to **parameterize the algorithm** with $k$ being the size of the set of terminals $|T|$.
- Moreover, we **simplify the input** by **turning every terminal into a leaf**. ![[Pasted image 20241218181347.png]]
- Instead of considering every possible tree, we consider all possible subsets of $k-1$ vertices of $T$, paired with the only vertex not included.

##### 