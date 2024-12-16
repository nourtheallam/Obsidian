$\rightarrow$ A good example of applying this is the [[Bipartite Minimum-Weight Perfect Matching LP]] and its application in [[The Hungarian Algorithm]]. 

Consider a maximization LP

$$\begin{aligned}
\text{Maximize} \quad cx \\
\text{s.t.} \quad Ax \leq b \\
x \geq 0
\end{aligned}$$
And its [[Dual]]
$$
\begin{aligned}
\text{Minimize} \quad b^T y \\
\text{s.t.} \quad A^T y \geq c^T \\
y \geq 0
\end{aligned}
$$
If $\hat{x}$ and $\hat{y}$ are feasible solutions, then they satisfy complementary slackness if

##### 1

Every primal variable $x_{j}$ is either $0$ or its corresponding [[Dual]] is tight
 $$\hat{x}_{j} \neq 0 \iff \sum_{i=1}^{m} a_{ij}y_{i} = c_{j}$$
##### 2

Every [[Dual]] variable $y_{i}$ is either $0$ or its corresponding primal is tight
 $$\hat{y}_{i} \neq 0 \iff \sum_{i=1}^{n} a_{ij}x_{j} = b_{i}$$

**Claim: $\hat{x}$ and $\hat{y}$ are both optimal solutions $\iff$ they both satisfy complementary slackness**

**Proof:**

If $\hat{x}$ and $\hat{y}$ are optimal solutions, they are also feasible solutions, and therefore they satisfy 
$$Ax \le b \quad \quad A^Ty \geq c^T $$

Note that 

$$A^Ty \geq c^T \implies y^TA \geq c$$

So, we can plug this into the LP Duality condition to obtain
$$c x \leq (y^TA)x$$
And since $Ax \leq b$
$$c x \leq (y^TA)x \leq y^T b (=b^Ty)$$
By LP Duality, if they are both optimal solutions, then 
$$c x = b^T y$$
So, it must be true that 
$$c x = (y^TA)x = y^T b$$

From the above, we can derive
$$(y^TA - c)x = 0 \quad \quad y^T(Ax - b) = 0$$

Since $x$ is optimal, it must satisfy a non-negativity constraint. The same applies for $y^TA - c$ because, as shown above $y^TA \geq c$.

Therefore, either $x = 0$ or $y^TA = c$, which is precisely what complementary slackness enforces. We can make an analogous argument for the $y^T(Ax - b) = 0$ term.