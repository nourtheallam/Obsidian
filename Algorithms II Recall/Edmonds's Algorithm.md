---
~
---

##### Main idea 

Start with an empty or maximal matching, grow it by finding augmenting paths.
We find a way to deal with **blossoms** 

![[Pasted image 20241217201849.png]]


##### Steps

- We run [[Alternating BFS]] to construct an [[Alternating forest]] **with all unmatched vertices as its root.**
- We call an edge **even-even** if it connects two vertices $(u,v)$ of even depth. **While such an edge exists:**
	- If $u$ and $v$ belong to different trees, no worries. The union of their paths is an augmenting path **(1)**. 
![[Pasted image 20241217202233.png]]
	- If $u$ and $v$ belong to the same tree, then we have a **blossom** to deal with.
		- Recursively contract blossoms and look for augmenting path. 


##### Proof of correctness

**(1)** This is an augmenting path because, by definition of an [[Alternating forest]]:
- the roots are going to be unmatched
- $u,v$ will be matched because they are an at an even depth
- $u,v$ are connected by an unmatched edge

**Claim:** While there exists an augmenting path, there will be an even-even edge in it.
**Proof:**
Given an augmenting path $P$, partition it into subpaths whose edges stay in the same tree. 

![[Pasted image 20241217203712.png]]

**Observe**: 
- The endpoints of this path $(x_{o}, y_{k})$ have to be roots because they are unmatched, they also must be even.
- The last vertex of the first subpath $(y_{o})$ and the first vertex of the last subpath $(x_{k})$ are both even because they are matched.
- The subpaths are always connected by an unmatched edge because otherwise, they would've belong to the same tree.
- Any subpath that is not the first or last subpath will have one of its endpoints be odd. 
	- Follows from both endpoints being matched.
- Therefore, there will exist an even-even edge.

**Claim:** If $M$ is a maximum matching of $G$ $\iff$ $M - B$ is a maximum matching of $G - B$. 

**Proof:** 

Assume, for the sake of contrapositive, that $M-B$ is not maximum. Show that this implies that $M$ is not maximum either. 

If $M-B$ is not maximum, then there exists an augmenting path. This augmenting path is either:
- Isolated from $v_{B}$, and therefore, it would be an augmenting path of $M$ as well.
- Includes $v_{B}$, there will always exist an even path through the cycle that connects the two endpoints:
![[Pasted image 20241217213235.png]]
To prove the other direction, consider the matching $M'$ that flips the matching of the stem. 
	**Observe:** $M$ is a maximum matching $\iff M'$ is because the stem is even-length.
	This implies that $M-B$ is maximum $\iff M' - B$ is maximum.
	
![[Pasted image 20241217213940.png]]

Now, consider an augmenting path for $M'$. Since the first edge in the stem is now unmatched, **at least one** of the endpoints of the augmenting path is not a part of the blossom. 

![[Pasted image 20241217215623.png]]

In fact, it would have to be both of them because of the fact that the stem now starts with an unmatched edge. This ensures that the alternating path, highlighted above, always exists.

- [ ] #lacking Does the stem always start with a matched edge?

##### Running time

We get the following recurrence for finding just one augmenting path

![[Pasted image 20241217221602.png]]
- [ ] #basics How do we solve a recurrence?

Since we have to find $O\left( \frac{n}{2} \right)$ augmenting paths for it to be a maximum-cardinality matching, the total running time is: $O(n^2m)$.