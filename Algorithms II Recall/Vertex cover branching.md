---
~
---

#### Naïve $2^n$ algorithm

- Look at each edge $(u,v)$ and include one of its endpoints in the vertex cover. 
- Branch on the $G-v$ and $G-u$.
---
#### A $1.619^n$ algorithm

- Look at each **vertex** $v$. The edges incident to $v$ will have to be covered by either $v$ or its neighbourhood $N(v)$. 
- Branch on $G-v$, with $v$ being in the vertex cover, and $G-N[v]$ with $N(v)$ being in the vertex cover. 
- Return the smaller of $v \cup C(G-v)$ and $N(v) \cup C(G-N[v])$
---
#### Parameterized $2^k$ algorithm

- The same as the above except that we keep track of the hardness parameter $k$ and subtract either $1$ or $|N(v)|$ (the size of what we're adding to the VC) at each iteration.
- If at any point $k < 0$, we have a no-instance.
- If either of the branches returns yes (the edge set becomes empty), we have a yes-instance. 

**Why is this $2^k$ when the above is $1.619^n$??**

Because how long we branch is also dependant on $k$ in this case, if the open neighbourhood of $v$, $N(v)$, contains just one other vertex, then we only decrease $k$ by $1$ on either branch.

---
#### 