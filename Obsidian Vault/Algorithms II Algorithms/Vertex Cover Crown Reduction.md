---
~
---
In [[Vertex Cover]] reduction, we obtained a kernel of size $k(k+1)$, which is not good because the running time of [[Vertex Cover]] is $O^*(2^n) \implies O^*(2^{k^2})$. 

We want a kernel of size $ak \implies O^*(2^{ak}) \implies O(c^k)$ instead, using [[Crown]] reduction.

Our **only** rule is:
	Compute a maximal matching $M$
	Then compute a matching between all the vertices in $M$ and those **not in** $M$
		If that matching matches all the vertices **not in** $M$, then $(G,k)$ is our kernel.
		Otherwise, $G - (I \cup H) \cap k - |H|$ is our kernel. 

**Is this a sound reduction?**

If we find the matching, the $(G,k)$ is the kernel. Since $(G,k)$ remains unchanged, we don't have to worry about that part. 

If we don't find the matching then
	If $|H| > k$, then $G$ has no [[Vertex Cover]] of size $\leq k$, and we have a no-instance. 
	Else if $|H| \geq k$, then $G$ **might** be a yes-instance. We need to prove that if $(G - (I,H), k - |H|)$ is a yes-instance $\iff$ $(G,k)$ is a yes-instance.

Let $G' = G-(I,H)$ and $k' = k - |H|$

If $(G', k')$ is a yes-instance then there exists a [[Vertex Cover]] $C'$ of $G'$ whose size is at most $k'$. 
But, more importantly, the set $C' \cup H$ is a [[Vertex Cover]] of $G$ because every vertex in $H$ is matched by such a matching, and as we showed in the description of [[Crown]]. 

If $(G,k)$ is a yes-instance with [[Vertex Cover]] $C$, then $(G', k')$ is a yes-instance if $H \subseteq C$. 

- [ ] #todo incomplete 🔺 

**If $(G,k)$ is a yes-instance then it has $\leq 3k$ vertices**

