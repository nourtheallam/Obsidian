
##### Main idea

We're going to use the Hungarian algorithm by reducing this problem to computing the minimum-weight perfect matching of an auxiliary graph.

##### Steps

- We negative all the edge weights.

- For every vertex $v$, we create a twin $v'$ and link them together by en edge of weight $0$, call this graph $G''$.

- We then calculate the minimum-weight perfect matching $M''$ of $G''$ and claim that if we remove all vertices and edges that don't exist in $M''$ to obtain a matching $M$ of $G$, then that matching is  a minimum-weight matching of $G$.

##### Proof

Observe that $M'' = M + M'$ where $M$ is the set of edges from $M''$ in $G$, with the same relation applying for $M'$ and $G'$.

Let $M^*$ be the **minimum-weight** [[Matching]] of $G$, we want to show that the weight of $M$ **is exactly the weight of $M^*$**. 

