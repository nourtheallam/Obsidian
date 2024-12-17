**Idea:** We can obtain a solution to the vertex cover problem by first finding an [[Extreme point solution]] to it.

**Steps:** 

**Claim:** Any [[Extreme point solution]] of the vertex cover problem is [[Half-integral]]. 
**Proof:** 
	**Idea:** We want to show that if $\hat{x}$ is a solution such that $\exists \ \hat{x}_{v}$ that is ==not== a multiple of $\frac{1}{2}$, then $\hat{x}$ ==cannot be an [[Extreme point solution]].==

Define $\hat{y},  \hat{z}$ as the following
$$\hat y_v = \begin{cases}\hat x_v - \epsilon & \text{if } 0 < \hat x_v < \frac{1}{2}\\\hat x_v + \epsilon & \text{if } \frac{1}{2} < \hat x_v < 1\\\hat x_v & \text{otherwise}\end{cases}$$
$$\hat z_v = \begin{cases}\hat x_v - \epsilon & \text{if } 0 < \hat x_v < \frac{1}{2}\\\hat x_v + \epsilon & \text{if } \frac{1}{2} < \hat x_v < 1\\\hat x_v & \text{otherwise}\end{cases}$$
Where 
$$\epsilon = \min\left( \hat{x}_{v}, |\hat{x}_{v} - \frac{1}{2}|, |\hat{x}_{v} - 1| \right)$$

If we do the math, this implies that

- $\hat{y}$ and $\hat{z}$ are feasible
- $\hat{x}$  = $\frac{1}{2}(\hat{y} + \hat{z})$

Which means that $\hat{x}$ is ==not== an extreme point solution.

**Claim:** We can find a half-integral vertex cover solution by finding an extreme-point solution and choosing
$$C = \{ v \in V | \tilde{x}_{v} > 0 \}$$
