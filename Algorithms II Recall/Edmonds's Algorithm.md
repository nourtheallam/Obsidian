---
~
---

##### Main idea 

Start with an empty or maximal matching, grow it by finding augmenting paths.
We find a way to deal with **blossoms** 

![[Pasted image 20241217201849.png]]


##### Steps

- We run alternating BFS to construct an alternating forest **with all unmatched vertices as its root.**
- We call an edge **even-even** if it connects two vertices $(u,v)$ of even depth.
	- If $u$ and $v$ belong to different trees, no worries. The union of their paths is an augmenting path **(1)**. 
![[Pasted image 20241217202233.png]]
	- If $u$ and $v$ belong to the same tree, then we have a **blossom** to deal with.
		- Contract the blossom


##### Proof of correctness

**(1)** This is an augmenting path because, by definition of an alternating forest:
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


