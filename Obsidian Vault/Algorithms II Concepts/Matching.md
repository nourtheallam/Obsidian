A subset of edges of a graph such that no two edges in it share an endpoint.

##### Properties

**For two matchings $M_{1}$ and $M_{2}$, $M' = M_{1} \oplus M_{2}$ is a collection of alternating paths and cycles such that if there are $a_{1}$ augmenting paths for $M_{1}$ and $a_{2}$ for $M_{2}$ in $M'$ then** 
$$|M_{1}| = |M_{2}| - a_{1} + a_{2}$$
$\rightarrow$ Any even length path and any even-length cycle (which is all the cycles) in $M'$ contains an equal amount of edges in $M_{1}$ and $M_{2}$. 
$\rightarrow$ An odd-length path is in $M'$ $\iff$ it is an [[Augmenting Path]] for one of the two matchings.
	Consider an odd-length path in $M'$ that contains one more edge in $M_{2}$.
	![[Pasted image 20241214212900.png]]
	Therefore, all the odd-length paths that contain one more edge in $M_{2}$ than $M_{1}$ in $M_{1} \oplus M_{2}$ are augmenting paths of $M_{1}$, and vice versa. 

- [ ] #todo final remark to show that this is complete

**As long as there exists an alternating path $P$ in $M$, $M' = P \oplus M$ is a matching whose size is greater than $|M|$ by one**

If $M'$ is not a matching, then there exists a vertex in it that is attached to two edges. Since $M$ is a matching, at most one of these edges is in $M$. 

![[Pasted image 20241214220431.png]]
By the thing we proved before this, $|M'| = |M| + 1$. 