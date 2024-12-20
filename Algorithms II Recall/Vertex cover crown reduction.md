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




##### Analysis

We **claim** that
$$G- (H \cup I)$$
Has $\leq 3k$ vertices.