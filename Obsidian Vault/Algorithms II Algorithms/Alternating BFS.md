Mark every vertex as unexplored. 

Mark vertices in $R$ as explored. 

Insert $R$ into a queue $Q$, make them the roots of $F$. 

While $Q$ is not empty, remove $u$ from it.
	For every unexplored neighbour $w$, mark it as explored and make it $u$'s child. 
		If $w$ is matched by another vertex $u'$, then also mark $u'$ as explored and make it $w$'s child, then add $u'$ to $Q$. 
		$\rightarrow$ We add $u'$ to $Q$ to make sure it's even (defined in [[Alternating Forest]]).
		$\rightarrow$ No need to worry about $u'$ being explored as it would only get marked as so if a neighbour in $W$ already was.

**The computed forest is maximum for $R$ (as defined in [[Alternating Forest]])**

From the above definition, the child edges of even vertices will always be unmatched while those of odd vertices will be matched. 

But is $F$ maximum (also defined in [[Alternating Forest]])?

$\rightarrow$ If a vertex $x$ is in $F$ then, again, by the above definition, it must be reachable from its root.

$\rightarrow$ If there exists an alternating path between a vertex in $R$ and $x$, the consider the shortest alternating path between $x$ and some vertex in $R$, prove by induction on the size of this path.
	$\rightarrow$ If the size is $0$, then $x = r$, and so, it must belong to $F$. 
	$\rightarrow$ If the size is $> 0$, then consider the vertex right before $x$ in this path, call it $y$. The path between $y$ and $r$ must also be the shortest alternating path between $y$ and a vertex in $r$. By induction hypothesis, $y \in F$. 
		$\rightarrow$ If $x \in W$ and $r \in U$, and the graph is [[Bipartite]], it must be true that the path between $x$ and $r$ is even, and moreover, that $x$ is also unmatched.
		This makes $y$ even, and therefore, alternating BFS will discover $x$ from $y$ unless $(x)$ is already in $F. 
		$\rightarrow$ If $x \in U$, then $x$ is even and unmatched (again, because the graph is [[Bipartite]]), and it will therefore get added to $F$ alongside $y$. 
