To find a [[General Maximum-Cardinality Matching]], 

Like other [[Bipartite Maximum-Cardinality Matching]] algorithms, Edmonds's starts with either an empty or maximal [[Matching]] (which can me computed in $O(n+m)$ time), then grows it by performing $M = M \oplus P$. 

___

#### Finding an augmenting path $P$ in a general graph $G$

$\Rightarrow$ We start by computing an [[Alternating Forest]] $F$ of $G$, with **all the unmatched vertices** as its roots.

**Claim:** If $y$ and $x$ are both **even** vertices and there exists no edges $(x,y)$ in the computed forest, then the [[Matching]] that exists in the forest, $M$, is a maximum-cardinality [[Matching]]. 
- [ ] #todo the proof for this

Using the above claim, we do the following: 
- Inspect all edges of $G$
- If we find no unmatched edges $(x,y)$ (described above), then $M$ is a maximum-cardinality [[Matching]]
- Otherwise: 
	- $x$ and $y$ belong to different trees. The path $P' = P_{x} \cup P_{y}$ is an [[Augmenting Path]].
	- $x$ and $y$ belong to the same tree. $P_{x}$ and $P_{y}$ share at least one vertex in common: the root of the tree. 
		- We let the set of edges in either $x$ OR $y$ plus $(x,y)$ be the **Blossom** of the tree, while the rest is the stem.
		- ![[Pasted image 20241215194658.png]]
		- Next, we **contract** this blossom. Meaning, we remove all the vertices/edges in it and replace them with a new vertex $v_{B}$. This results in a new [[Matching]] $M / B$ that may contain an edge between some vertex $u$ and $v_{B}$. 
		- We can then recurse on the new graph that this **contraction** gives us such that we assume that $M / B$ is a maximum [[Matching]] of $G / B$ $\iff$ $M$ is a maximum [[Matching]] of $G$. So, if we can't find any augmenting paths we know that we found a maximum [[Matching]]. 
		- We can **construct** a maximum [[Matching]] $M$ from the [[Augmenting Path]] $P$ of $M / B$ by **Expanding** blossoms.

**Expanding blossoms**

![[Pasted image 20241215205126.png]]
(Norbert's work)

Consider the [[Augmenting Path]] $P'$ in $G - B$ whose endpoints are $x$ and $y$. If $v_{B}$ is not on the path, then we're chilling.

Otherwise, let $(v_{B}, w)$ be an unmatched edge. Since $P'$ is an [[Augmenting Path]], $P'_{w}$ (the path from $w$ to $y$) is an odd-length, alternating one. Let $z$ be the **"first"** vertex in $v_{B}$ that is "not on the direction of $w$" in the path. Then, if we were to add the edges in $B$ to the path between $z$ and $y$, we would have an even + odd = odd length path from $z$ to $y$. 
	If $z$ is unmatched, then this new path from $z$ to $y$ is easily an [[Augmenting Path]]. 
	If $z$ is matched by $u$, then it must have been that the edge $(u, v_{B})$ was in the [[Matching]] when the blossom was contracted, which means that $v_{B}$ cannot have been $x$, and that the subpath from $x$ to $u$ is an alternating path whose last edge is unmatched. Concatenating $P'_{x \rightarrow u}$ and $P'_{u \rightarrow v_{B}}$ and $P'_{w \rightarrow y}$ therefore yields an [[Augmenting Path]].

 ----
 ##### Proof of correctness

The very detailed description above shows that if $x \rightarrow y$ is an augmenting path for $G- B$, then expanding the blossom will always give us an augmenting path for $G$ as well.

Assume, that $M$ is not a maximum-cardinality matching and show that this implies that $M - B$ is not a maximum cardinality matching either.
 $\rightarrow$ Consider the graph $M' = M \oplus S$ (every edge that is only in either the stem of the matching), as shown below, $M'$ would be a matching as well, whose size is equivalent to that of $M$
- [ ] #todo 🔺 Incomplete proof

 ---
 
##### Running time

- $O(n + m)$ time to construct the [[Alternating BFS]]
- $O(m)$ time to inspect all the edges and check for unmatched $(x,y)$
- $O(m)$ time to determine whether $x,y$ are on the same tree.
- $O(m)$ time to construct **blossom** $B$ and resulting graph and [[Matching]].
- Since we recurse on the graphs constructed by blossoms, the running time of each blossom recurrence is 
- ![[Pasted image 20241215195936.png]]
- because we remove at least two vertices per blossom, and each blossom has at least $n-2$ vertices. The solution to this recurrence is $O(nm)$







