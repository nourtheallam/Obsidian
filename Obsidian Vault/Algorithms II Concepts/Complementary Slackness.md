
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
**Note: $\hat{x}$ and $\hat{y}$ are both optimal solutions $\iff$ they both satisfy complementary slackness**

 - [ ] #todo Find an example of this