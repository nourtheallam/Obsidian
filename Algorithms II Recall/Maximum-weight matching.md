
##### Main idea

We're going to use the [[Hungarian algorithm]] by reducing this problem to computing the minimum-weight perfect matching of an auxiliary graph.

##### Steps

- We negative all the edge weights.

- For every vertex $v$, we create a twin $v'$ and link them together by en edge of weight $0$, call this graph $G''$.

- We then calculate the minimum-weight perfect matching $M''$ of $G''$ and claim that if we remove all vertices and edges that don't exist in $M''$ to obtain a matching $M$ of $G$, then that matching is  a minimum-weight matching of $G$.

##### Proof

Observe that $M'' = M + M'$ where $M$ is the set of edges from $M''$ in $G$, with the same relation applying for $M'$ and $G'$.

Let $M^*$ be the **minimum-weight** matching of $G$, we want to show that the weight of $M$ **is exactly the weight of $M^*$**. 

First, observe that 
$$w(M) \geq w(M^*) \implies w(M') \geq w(M^*)$$

Now, consider, for the sake of contradiction, that $w(M) > w(M^*)$. This implies that 
$$w(M'') = w(M) + w(M') > 2\cdot w(M^*)$$
Which is a contradiction because we can construct a matching of all the edges in $M^*$ and their twins in $G'$ (and all the edges between vertices that are not in $M^*$ and their twins) whose weight would be exactly $= 2 \cdot w(M*) < w(M'')$. 

Therefore, it can only be true that $w(M) \leq w(M^*)$, and since we claimed that $w(M) \geq w(M^*)$, it must be true that $w(M) = w(M^*)$. 

##### Running time

The same as the running time of the [[Hungarian algorithm]], which is $O(n^4)$ without the improvements.