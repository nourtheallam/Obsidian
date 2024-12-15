---
~
---
We construct an [[Alternating Forest]] using the [[Alternating BFS]] routine in $O(n+m)$ time.

We, then, inspect every vertex in $O(n)$ time, and if it happens to be **a vertex in $W$ that is unmatched**, then we are guaranteed to have an alternating path between it and the root of its tree. Perform $M = M \oplus P$. 

Since a [[Matching]] cannot have more than $m$ edges, we do this $m$ times, so total running time is $O((n+m)m)$ (?). 

We can shortcut this running time by removing isolated vertices beforehand, yielding a $O(nm)$ running time.