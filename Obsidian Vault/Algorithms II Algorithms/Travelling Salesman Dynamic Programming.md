
We can use [[Dynamic Programming]] to obtain nice solution to the TSP.

--- 
##### Definitions 

Let $U$ be a subset of $V$. 

We call a path that visit **all and only** the vertices in $U$ a $U$-path.

Let $V$ be some subset of vertices that starts at $v_{1}$, and consider the hamiltonian cycle that starts and ends at $v_{1}$. We call the path from $v_{1}$ to the vertex right before it, $v_{i}$, a **v-path** from $v_{1}$ to $v_{i}$. 

Now, let $P(U,i)$ be the length of the **shortest v-path** between $v_{1}$ snd $v_{i}$ in the subset $U$. 

Then, an optimal TSP has length:
$$\min_{2 \leq i \leq n}(P(V,i), + w(v_{i}, v_{1}))$$
So, we consider each possible $P$.

--- 
##### Description 

We consider every possible subset $P$ and vertex $v$ in our computation of 
$$P(V,i) + w(v_{i}, v)$$
We fill a table whose entries are dependent on the size of $S$, and the vertex $v$. 

![[Pasted image 20241216001433.png]]

--- 

**We then recurse on the entries of the table using the following definition:** 

**Base case:** $U = \{ v_{1} \}$. 

In this case, $P(U,i) = 0$ if $i = 1$ and $\infty$ otherwise.

**Inductive step:** $|U| > 1$

In this case, $P(U,i) = \min_{j \notin \{ 1,i \}}(P(U - \{ v_{i} \}) + w(v_{j}, v_{i}))$

---- 
