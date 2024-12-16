This is the same as computing a minimum-weight [[Matching]] after negating all the edge weights. 

But, we are not necessarily dealing with a [[Complete Bipartite Graph]], so we can't get a [[Perfect matching]] unless we do it on an auxiliary graph $G''$, defined as the original graph $G$ and an identical copy of it $G'$ with an edge whose weight is $0$ between every edge and its twin. 

Note that we can reduce the running time of [[The Hungarian Algorithm]] to $O(n^2 \log n + nm)$. 

**Claim:** If we take every edge in the minimum-weight [[Perfect matching]] $M''$ of $G''$ that actually exists in $G$, we get a a minimum-weight [[Perfect matching]] $M$ of $G$. 

**Proof:**

Consider the minimum-weight [[Perfect matching]] $M''$ of $G''$. 

Then, $M'' = M + M'$ where $M$ is the set of edges from $M''$ in $G$, with the same relation applying for $M'$ and $G'$.

Let $M^*$ be the **minimum-weight** [[Matching]] of $G$, we want to show that the weight of $M$ **is exactly the weight of $M^*$**. 

First, observe that 
$$w(M) \geq w(M^*) \implies w(M') \geq w(M^*)$$

Now, consider, for the sake of contradiction, that $w(M) > w(M^*)$. This implies that 
$$w(M'') = w(M) + w(M') > 2\cdot w(M^*)$$
Which is a contradiction because we can construct a [[Matching]] of all the edges in $M^*$ and their twins in $G'$ (and all the edges between vertices that are not in $M^*$ and their twins) whose weight would be exactly $= 2 \cdot w(M*) < w(M'')$. 

Therefore, it can only be true that $w(M) \leq w(M^*)$, and since we claimed that $w(M) \geq w(M^*)$, it must be true that $w(M) = w(M^*)$. 

