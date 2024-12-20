---
~
---
##### Ideas

**Observation:** $G$ has a vertex cover of size $\leq k$ **if and only if** $G-(H\cup I)$ has a vertex cover of size $k - |H|$.
- All the edges between $I$ and $H$ are incident to vertices in $H$. 

Using the above observation, we aim to find a **large crown** $(H,I)$ and our kernel becomes $$(G - (H \cup I), k -|H|)$$
##### Steps

We need to find a **large crown by:**

1. Find a maximal matching $M_{1}$. 

This is because all the vertices **not incident to an edge in** $M_{1}$ must form an independent set all together.
![[Pasted image 20241220120539.png]]

2. Examine all the edges between the vertices in $M_{1}$ and the vertices **not in** $M_{1}$, and find a maximum matching $M_{2}$ between them. 

![[Pasted image 20241220120837.png]]

$\rightarrow$ If either of these matchings has more than $k$ edges in it, then this is instantly a **no-instance**. 

3. Consider $I'$ the subset of vertices not matched by $M_{2}$

![[Pasted image 20241220121117.png]]

4. Let $Z$ be the set of vertices reachable from $I'$ via **even-length alternating paths**. 

Then, $$I = Z \cap (V - M_{1})$$ and $$H = Z \in M_{1}$$
And we claim that we have found our **crown.**

- $I$ is an independent set

Again, because $M_{1}$ is a maximal matching.

- All the neighbours of $I$ are in $H$

Any **matched edge** in $I$ has its other endpoint in $H$ because it is on an alternating path between the vertex in $I$ and some vertex in $I'$. 
Any unmatched edge will be directly incident to a vertex that is matched, which is a vertex in $H$

- Every vertex in $H$ is unmatched 

Since there exists an **odd-length** alternating path between vertices in $H$ and $I$, if a vertex in $H$ was unmatched, then there would be an augmenting path for $M_{2}$ which is not possible because it is a maximum matching. 

- Every matched vertex in $H$ in $M_{2}$ has a mate in $I$

If we look at the alternating path from a vertex in $I'$ to one in $H$, then it is odd length, and if we add a matched edge to that, we get an even-length alternating path that must end in $I$. 

##### Analysis

We **claim** that
$$G- (H \cup I)$$
Has $\leq 3k$ vertices.

- Consider

![[Pasted image 20241220123603.png]]


$|\bar{H}| \leq 2|M_{1}|\leq 2k$ because we assumed that the matching has size at most $k$, otherwise, it would be a **no-instance**. 

$I' \subseteq I$ because $I'$ is the set of vertices that are not matched by $M_{2}$, this implies that 
$$|\bar{I}| \leq |M_{2}| \leq k$$
Therefore, $\bar{I} \cup \bar{H}$ have size at most $3k$. x