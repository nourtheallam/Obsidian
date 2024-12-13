### Question 1
##### (1)

The algorithm initializes $S$ to $\{ s \}$ and $T$ to $\{ t \}$ then iteratively adds each vertex in $V \setminus \{ s,t \}$ to either $S$ or $T$, effectively computing two non-empty subsets $S$ and $T$ where $T = V \setminus S$, which is precisely the definition of a cut over a graph $G = (V,E)$. 
##### (2)

I will use induction to proof that the algorithm computes a solution whose objective function value if $\geq \frac{1}{2} l$ where $l$ is the upper bound on $w(S^\star)$. Let $\omega(x)$ denote the 

**Base case:**

If $V = \{ s, t \}$, the algorithm stops after initializing $S = \{ s \}$ and $T = \{ t \}$, which forms the only possible cut, thus ensuring $w(S) = w(S^*)$, and therefore, $w(S) \geq \frac{\omega(S^\star)}{2}$ must hold. 

**Inductive Step:** 

Assume $w(S) \geq \frac{\omega(S^*)}{2}$ holds for all graphs with $k$ vertices. Prove that $w(S) \geq \frac{\omega(S^*)}{2}$ holds for all graphs with $k + 1$ vertices.

Given a graph $G = (V, E)$, compute a cut $S_k$ over $V \setminus \{ u \}$ for an arbitrary vertex $u \notin \{ s, t \}$ (and let $V \setminus (S_k \cup \{ u \}) = T_k$). By the inductive step, $w(S_k) \geq \frac{\omega(S_k^*)}{2}$, where $S_k^*$ is the maximum $st$-cut of $V \setminus \{ u \}$ (with $V \setminus (S_k^* \cup \{ u \}) = T_k^*$). 

Define $E_{u} \subseteq E$ as the set of edges connected to $u$ and note that $w(S^\star_{k}) \leq w(E) - w(E_{u})$, and therefore 
$$w(S_{k}) \geq \frac{w(E) - w(E_{u})}{2}$$

To compute a cut $S$ over $V$, add $u$ to either $S_k$ or $T_k$. Since the algorithm adds $u$ to $S$ if  
$$\sum_{v \in S} w_{u, v} \leq \sum_{v \in T} w_{u, v}$$
making $w(S) = w(S_k) + \sum_{v \in T} w_{u, v}$. While adding $u$ to $T$ otherwise such that $w(S) = w(S_k) + \sum_{v \in S} w_{u, v}$, we can state that $$w(S) = w(S_k) + \max\left( \sum_{v \in S} w_{u, v}, \sum_{v \in T} w_{u, v} \right)$$
Let the set of edges that this step of the algorithm adds to the cut be $\hat{E_{u}}$. Then $$w(\hat{E_{u}}) = \max\left( \sum_{v \in S} w_{u, v}, \sum_{v \in T} w_{u, v} \right) \geq \frac{w(E_{u})}{2}$$
Which implies
$$w(S) = w(S_{k}) + w(\hat{E}_{u}) \geq \frac{w(E) - w(E_{u})}{2} + \frac{w(E_{u})}{2}$$
And therefore 
$$w(S) \geq \frac{w(E)}{2}$$
And since $w(S^\star) \leq w(E)$, 
$$w(S) \geq \frac{\omega(S^\star)}{2}$$
**Conclusion**

Therefore, by induction, the weight of the cut computed by the given algorithm will always be $\geq \frac{1}{2}$ the upper bound of the maximum-weight cut of the graph. Since this implies that the algorithm will always compute a solution whose objective function value is at least $\frac{1}{2}$ the optimal objective function value of the maximum cut problem, then the given algorithm must be a $\frac{1}{2}$ [[Approximation]] of the maximum cut problem.

### Question 2

##### (1)

**Claim:**

Given a travelling salesman tour, $H$, of a graph $G$, we can obtain a spanning tree of $G$
$$T = H \setminus e$$ Where $e$ is an arbitrarily-chosen edge in $H$.

**Proof:** 

To prove that $T$ is a spanning tree, we need to prove that it has no cycle and that it is connected. 

**Acyclic:** Since $H$ is a cycle that visits each vertex at most once, then it cannot contain any sub-cycles, and therefore, removing any edges from it ensures that it is no longer a cycle, and therefore, $T$ is acyclic. 

**Connected:** Moreover, removing exactly one edge from $H$ does not isolate any of its vertices or break its connectivity. Let the edge being removed be $e = (u, v)$. Since $H$ is a cycle, we know that $u$ is connected to some vertex $k \neq v$ and $v$ is connected to some vertex $l \neq u$ in it. Therefore, $u$ and $v$ would still have connections in $H$.

Therefore, $T$ is a spanning tree.

Since $T$ is a spanning tree, we know that the weight of any minimum spanning tree of $G$ will be $\leq$ that of $T$, and since $w(T) = w(H) - w(e)$, it will also be $\leq$ that of $H$. 
#### (2)

The sum of all vertex degrees in any graph $G=(V,E)$ twice the number of its edges:
$$
\sum_{v \in V} \deg(v) = 2|E|.
$$
Assume, for contradiction, that $G$ has an odd number of odd-degree vertices. Since each of these vertices has an odd degree, their combined degree sum is odd. Vertices with even degrees, regardless of their count, contribute an even sum to the total. Thus, the overall sum of vertex degrees in $G$ would be the sum of an odd and an even number, which is odd.

This contradicts the fact that the sum of all vertex degrees must be even (since it equals $2|E|$). Therefore, $G$, and by extension, any minimum spanning tree of $G$, cannot have an odd number of odd-degree vertices.
####  (3)

We construct a Hamiltonian cycle $S_o$ of $G[O]$ from $S$ by either retaining an edge from $S$ when it directly connects two vertices in $O$, or replacing a sequence of edges in $S$ that connects two vertices in $O$ with a single edge that directly connects those vertices. This process ensures that every vertex in $O$ is visited exactly once before returning to the starting vertex, thereby producing a Hamiltonian cycle of $G[O]$.

----

**Claim:** Given two vertices $u, v \in O$ that are $k$ edges apart in $S$ (in a chosen direction of traversal), the edge $(u, v)$ has a weight of at most the sum of the weights of the edges connecting $u$ and $v$ in $S$.

**Proof:**  

We will use induction on the number of edges $k$ between $u$ and $v$ in $S$, where $k$ is measured in a chosen direction of traversal.

**Base case:** $k = 2$  

Let $w$ be the vertex between $u$ and $v$ in the direction where they are two edges apart. By the triangle inequality, $w_{u,v} \leq w_{u,w} + w_{w,v}$. Thus, the weight of $(u, v)$ is at most the sum of the weights of the edges connecting $u$ and $v$ in $S$, so the claim holds.

**Inductive step:**  

Assume the claim holds for $k = l$ edges. Consider $u$ and $v$ separated by $l+1$ edges in the chosen direction of traversal. Let $w$ be the vertex $l$ edges away from $u$ in this direction. By the inductive hypothesis, the weight of $(u, w)$ is at most the sum of the weights of the edges between $u$ and $w$. Applying the triangle inequality to $u$, $w$, and $v$, we have:

$$
w_{u,v} \leq w_{u,w} + w_{w,v}.
$$

Substituting the inductive hypothesis for $w_{u,w}$, we find that $w_{u,v}$ is at most the sum of the weights of the edges between $u$ and $w$, plus the weight of the edge $(w, v)$, which is precisely the sum of the weights of the edges connecting $u$ and $v$ in $S$.  

Thus, the claim holds for $k = l + 1$.

**Note:** Since the direction of traversal only affects the value of $k$ and since the above proof is not actually dependent on the value of $k$, this claim holds regardless of the chosen direction  of traversal. 

Therefore, by induction, given any two vertices $u, v \in O$ that are some number of edges apart in $S$, the edge $(u, v)$ has a weight of at most the sum of the weights of the edges connecting $u$ and $v$ in $S$. 
 
----
 
This is relevant to the weight of $S_{o}$ because it implies that replacing a sequence of edges in $S$ by connecting two vertices in $O$ with a single edge directly connecting them removes the summed weight of the sequence and introduces at most the same weight to $S_{o}$. Since $S_o$ is constructed by a combination of either this replacement or retaining an edge from $S$ in $S_o$, we can conclude that **the total weight of $S_{o}$ is at most the total weight of $S$.**

---

**Claim:** An even-length cycle $C$ yields exactly two perfect matchings of its edges.

**Proof:**  

Since $C$ has an even number of vertices, label the vertices consecutively as $v_1, v_2, \dots, v_{k}$ in a chosen direction of traversal.  

**First Perfect Matching:** Pair each vertex with the next vertex in the cycle until every vertex is paired i.e., $(v_1, v_2)$, $(v_3, v_4)$, ..., $(v_{k-1}, v_{k})$. This forms a perfect matching, as each vertex is included in exactly one pair.  

**Second Perfect Matching:** Pair each vertex with the next vertex until every vertex is paired, but in the opposite direction of traversal. For example, $(v_{1}, v_{k}), (v_{k-1}, v_{k-2}), \dots (v_{3}, v_{2})$. 

Since each vertex can be matched with only one of the two vertices adjacent to it in the cycle, and since a matching cannot include edges whose endpoints overlap, these are the only two possible perfect matchings. Moreover, since every edge in the cycle has a nonnegative weight, one of these two perfect matchings must be the minimum perfect matching **of the edges in the cycle.**

Thus, the any even-length cycle yields exactly two perfect matchings, one of which is its minimum perfect matching.

---

The claim above proves that we can obtain a perfect matching $M'$ of $G[O]$ by picking the lighter perfect matching of $S_{o}$ (which we know has an even number of vertices). 

---

**Claim:** the weight of $M'$ is at most half the weight of $S_o$

**Proof:** Since we pick half of the edges in $S_o$ to be in $M'$, we can think of the weight of this matching as being one of two partitions of the weight of $S_{o}$, $w_{1}$ and $w_2$, where $w_{1} \leq w_{2}$. Since we pick the lighter perfect matching of $S_{o}$, $w_1$ is the partition whose weight represents the weight of $M'$. Since $w_{1} \leq w_{2}$, 
$$2w_{1} \leq w_{1} + w_{2} \quad (\text{where} \ w_{1} + w_{2} = w(S_{o}) \quad \text{and} \quad w_{1} = w(M'))$$
And since we have proven that 
$$w(S_{o}) \leq w(S)$$
We can conclude that
$$w(M') \leq \frac{1}{2}w(S)$$
---

Since any minimum-weight perfect matching $M$ of $G[O]$ will have at most the weight of $M'$, we can thus also claim that $M$ has at most half the weight of $S_o$, and since we proved that the weight of the travelling salesman tour of $G[O]$ is at most the weight of the travelling salesman tour of $G$, we can further claim that $M$ has at most half the weight of the travelling salesman tour of $G$.
#### (4)

 A vertex $x_{i_{j}}$ occurs exactly once in the sequence defining $C'$, with the exception of the first and last positions of the sequence, which must belong to the same vertex. Since the first and last vertices of the sequence are the same, $C'$ must be a cycle. And since all the other vertices in $G$ occur exactly once in $C'$, and since $G$ is complete, $C'$ is a Hamiltonian cycle. 
#### (5)

Building $C'$ by including the first occurrence of every vertex $v$ in $C$ tells us that the difference between the edges in $C$ and $C'$ occurs when two vertices are consecutive in $S$ but not in $C'$. Let such vertices be $v$ and $u$, by letting $v$ and $u$ be consecutive in $C'$, we are connecting them through the edge $(v,u)$ rather the series of edges they were originally connected with in $C$. As we proved in $(3)$, doing so will always ensure that the weight of the edge $(v,u)$ is at most the sum of the weights of the edges between $v$ and $u$ in $C$ that we skip over. And therefore, the total weight of $C'$ will be at most that of $C$. Since we have shown that the weight of $T$ is at most the weight of the travelling salesman tour of $G$ and that the weight of $M$ is at most half of the weight of the travelling salesman tour of $G$

$$w(C) = w(T) + w(M) \implies w(C) \leq w(H) + \frac{1}{2} w(H) \implies w(C) \leq \frac{3}{2} w(H)$$
Where $H$ is the travelling salesman tour of $G$. And therefore, 

$$w(C') \leq w(C) \implies w(C') \leq \frac{3}{2} w(H)$$
Which proves that $w(C')$ is no more than $3 / 2$ times the weight of the travelling salesman tour of $G$.