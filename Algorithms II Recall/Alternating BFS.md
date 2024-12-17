---
~
---
Mark every vertex as unexplored. 

Mark vertices in $R$ as explored. 

Insert $R$ into a queue $Q$, make them the roots of $F$. 

While $Q$ is not empty, remove $u$ from it.
	For every unexplored neighbour $w$, mark it as explored and make it $u$'s child. 
		If $w$ is matched by another vertex $u'$, then also mark $u'$ as explored and make it $w$'s child, then add $u'$ to $Q$. 
		$\rightarrow$ We add $u'$ to $Q$ to make sure it's even (defined in [[Alternating Forest]]).
		$\rightarrow$ No need to worry about $u'$ being explored as it would only get marked as so if a neighbour in $W$ already was.


