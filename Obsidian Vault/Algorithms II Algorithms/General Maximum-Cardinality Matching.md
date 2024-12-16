---
~
---
While we can still use the algorithms described to compute a [[Bipartite Maximum-Cardinality Matching]], it would take us longer to find an [[Augmenting Path]]. 

**The main two problems are:** 

1. We relied on the fact that every [[Augmenting Path]] will have an **odd length**, **start with an unmatched** vertex $u \in U$, and **end with an unmatched vertex** $w \in W$, which allowed us to find such a path in $O(m)$ time.
2. **More importantly,** the existence of **odd-length cycles** makes the behaviour of the alternating DFS/BFS unpredictable. The algorithm would have to traverse such cycles "in the right direction" to be able to find an [[Augmenting Path]].

We will be using [[Edmonds's Algorithm]] to find our [[Matching]].