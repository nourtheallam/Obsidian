---
~
---

##### Idea

Given a Monte Carlo algorithm with probability of success $\rho$, we **embed it into** a Las Vegas algorithm that loops until the solution returned is correct.

##### Steps

While $C(S, I)$ is not true: 
	$S= M(I)$
Return $S$

Where $C$ is a checker algorithm with running time $T_{C}(n)$ and $M$ is a Monte Carlo algorithm with running time $T_{M}(n)$. 

##### Expected running time 

Instead of calculating a running time, we calculate an **expected** running time. We do that by considering the probability that the Monte Carlo algorithm fails each time in relation to the total number of loops executed: 
$$\sum_{i= 0}^{\infty} (1- \rho)^i = \frac{1}{\rho}$$
The above gives us the number of time the loop is executed, and therefore, the total expected running time is 
$$(T_{M}(n) + T_{C}(n))\left( \frac{1}{\rho} \right)$$
$$P[\hat{x}_{i} = 1] = \tilde{x}_{i} \implies E[\hat{x_{i}}] = (1 \cdot \tilde{x_{i}}) = \tilde{x}_{i}$$