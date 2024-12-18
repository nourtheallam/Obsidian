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
	- If $u$ and $v$ belong to different trees, no worries. The union of their paths is an augmenting path (1). 
![[Pasted image 20241217202233.png]]
	- If $u$ and $v$ belong to the same tree, then we have a **blossom** to deal with.
	- 


##### Proof of correctness

(1) This is an augmenting path because, by definition of an alternating forest:
- the roots are going to be unmatched
- $u,v$ will be matched because they are an at an even depth
- $u,v$ are connected by an unmatched edge

**Claim:** If $M$ is not maximum, then there exists an even-even edge.
**Proof:**
Given an augmenting path $P$, partition it into subpaths whose edges stay in the same tree. 

![[Pasted image 20241217203712.png]]

