#### Naive, $O^*(2^n)$ exponential algorithm

A naive [[Exponential]] algorithm is to find all possible subsets of the set of vertices $V$ with size $n$. There are $2^n$ such subsets, and for each, we check if all the edges are covered which takes $O(m)$ time. Therefore, the overall running time is 
$$O(2^n m) = O^*(2^n)$$

#### An $O^*(2^n)$ branching algorithm

For each edge $(u,v)$, return the smaller of $C_{u} \cup \{  u \}$ and $C_{v } \cup \{ v \}$. 

Each recursive call is implemented in $O(n)$ time, and we have one less vertex to work with in the following call, this gives us
$$T(n) = O(n) + 2T(n-1) = O(2^n n) = O^*(2^n)$$
#### An $O^*(1.619^n)$ branching algorithm

The above algorithm can be redundant if the optimal [[Vertex Cover]] contains both vertices of some edge (as both branches would potentially compute the same [[Vertex Cover]]). 

A better approach is to return the smaller of $C_{v} \cup \{ v \}$ and $C_{N[v]} \cup N[v]$ where $C_v$ is the [[Vertex Cover]] of $C - v$, etc. for each vertex $v$ of **maximum degree**. 

Since $v$ is of maximum degree, $|N[v]| \geq 2$, which gives us the recurrence 
$$T(n) = O(n) + T(n-1) + T(n-2)$$
Whose solution happens to be $O^*(1.619^n)$. 
