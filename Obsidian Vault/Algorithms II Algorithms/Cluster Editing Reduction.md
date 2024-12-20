Given the [[Cluster Editing]] problem, we employ the following reduction rules: 
	**(1) Many shared neighbours**
	![[Pasted image 20241214132714.png]]
	**(2) Many unique neighbours**
	![[Pasted image 20241214132805.png]]
	**(3) Remove cliques**
		Simple as that.

##### Are the rules sound?

**(1) Many shared neighbours**

Show that $G$ has a cluster edit of size at most $k$ $\iff$ $G' = G \cup (u,v)$ has a cluster edit of size at most $k-1$. 

$\implies$ If $G^*$ is a cluster graph obtainable from $G'$ using at most $k-1$ edits, then it is a cluster graph obtainable from $G$ using at most $k$ edits (with the additional edit being adding $(u,v)$). 

$\implies$ If $G^*$ is a cluster graph obtainable form $G$ using at most $k$ edits, then it must **contain** $(u,v)$. Assume, for the sake of contradiction, that it does not. Then, $u$ and $v$ must belong to different clusters which implies that there exist $k+1$ edge-disjoint paths between $u,v$, and the $w$ edges (see above), which would require more than $k$ edits to handle. 

**(2) Many unique neighbours**

$\implies$ If $G^*$ is a cluster graph obtainable from $G'$ using at most $k-1$ edits, then it is a cluster graph obtainable from $G$ using at most $k$ edits (with the additional edit being removing $(u,v)$). 

$\implies$ If $G^*$ is a cluster graph obtainable form $G$ using at most $k$ edits, then it must **not contain** $(u,v)$. Assume, for the sake of contradiction, that it does. Then, it would take at least $k+1$ edits to make $G^*$ a cluster graph (see above). So, it must be true that $G^*$ does not contain $(u,v)$, which means that we would have to turn $G$ into $G'$ before getting $G^*$. 

**(3) Remove Cliques**

Let $G'$ be the graph produced by removing all the cliques in $G$, and let $M$ be the set of edits needed for $G'$ to be a cluster graph $G'*$. Then, applying $M$ to $G$ would produce $G'* \cup G[clusters]$ which doesn't take any more edits.



##### Two more things to prove

**(1) $M$ is a set of cluster edits that operate solely within connected components of $G$**

Consider the connected components $V_{1}, \dots, V_{t}$ of $G$, and the set of edits $M_{1}, \dots, M_{t}$ employed on each. A cluster graph $G^*[V_{i}]$ can be obtained from $V_{i}$ by applying $M_{i}$. Therefore, $G^*$ can be obtained using $M_{1} \cup M_{2} \dots \cup M_{t}$. Any $M' \supset M_{1} \cup M_{1} \cup \dots \cup M_{t}$ would **not be a minimum cluster edit set.**

**(2) A fully-reduced ==yes== instance $(G,k)$ has at most $(2k +1)2k$ vertices and $\binom{2k+1}{2} 2k+k$ edges**

From **(1)**, we saw that we can partition $M$ into $M_{1} \dots M_{2}$. Since we **removed all cliques**, then we know that each $M_{i}$ has to involve at least one edit. 

**INCOMPLETE**

