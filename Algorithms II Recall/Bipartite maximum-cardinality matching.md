---
~
---

**Steps:** 
- Construct an [[Alternating Forest]] using the [[Alternating BFS]] routine in $O(n+m)$ time.
- Inspect every vertex in $O(n)$ time, and if it happens to be **a vertex in $W$ that is unmatched**, then we are guaranteed to have an **odd-length** alternating path between it and the root of its tree. Perform $M = M \oplus P$. 

**Running time:** 

- Constructing an alternating forest takes $O(n+m)$. 
- We can get that down to $O(m)$ if we remove all isolated vertices beforehand.
- It takes $O(n)$ time to look for an unmatched vertex in $W$ after each forest is constructed.
- Since we need to add $O(m)$ edges to the matching, the overall running time is 
$$O(m) \cdot (O(m) + O(n))) = O(nm)$$
