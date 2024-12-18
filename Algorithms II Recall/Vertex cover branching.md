---
~
---

#### Naïve 

- Look at each edge $(u,v)$ and include one of its endpoints in the vertex cover. 
- Branch on the $G-v$ and $G-u$.

#### A $1.619^n$ algorithm

- Look at each **vertex** $v$. The edges incident to $v$ will have to be covered by either $v$ or its neighbourhood $N(v)$. 
- Branch on $G-v$, with $v$ being in the vertex cover, and $G-N[v]$ with $N(v)$ being in the vertex cover. 
- Return the smaller of $v \cup C(G-v)$ and $N(v) \cup C(G-N[v])$

#### 