Given the cluster editing problem, we employ the following reduction rules: 
	**(1) Many shared neighbours**
	![[Pasted image 20241214132714.png]]
	**(2) Many unique neighbours**
	![[Pasted image 20241214132805.png]]
	**(3) Remove cliques**
		Simple as that.

##### Are the rules sound?

**(1) Many shared neighbours**

Show that $G$ has a cluster edit of size at most $k$ $\iff$ $G' = G \cup (u,,v)$ has a cluster edit of size at most $k-1$. 

$\implies$ If $G^*$ is a cluster graph obtainable from $G'$ using at most $k-1$ edits, then it is a cluster graph obtainable from $G$ using at most $k$ edits (with the additional edit being adding $(u,v)$). 

$\implies$ If $G^*$ is a cluster graph obtainable form $G$ using at most $k$ edits, then it must **contain** $(u,v)$. Assume, for the sake of contradiction, that it does not. Then, $u$ and $v$ must belong to different clusters which implies that there exist $k+1$ edge-disjoint paths between $u,v$, and the $w$ edges (see above), which would require more than $k$ edits to handle. 

**(2) Many unique neighbours**

$\implies$ If $G^*$ is a cluster graph obtainable from $G'$ using at most $k-1$ edits, then it is a cluster graph obtainable from $G$ using at most $k$ edits (with the additional edit being removing $(u,v)$). 

$\implies$ If $G^*$ is a cluster graph obtainable form $G$ using at most $k$ edits, then it must **not contain** $(u,v)$. Assume, for the sake of contradiction, that it does. Then, it would take at least $k+1$ edits to make $G^*$ a cluster graph (see above). So, it must be true that $G^*$ does not contain $(u,v)$, which means that we would have to turn $G$ into $G'$ before getting $G^*$. 