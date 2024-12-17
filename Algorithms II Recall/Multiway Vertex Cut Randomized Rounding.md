---
~
---

**Idea:** We ==define== a half integral solution and ==prove== that it is feasible and optimal. 


**Steps:**

**Claim:** A ==feasible== half-integral solution to the multiway vertex cut is defined as follows

Given the following labels

![[Pasted image 20241217143819.png]]

We define $\hat{x}$ as 
$$\tilde x_v = \begin{cases}1           & \text{if } v \in Q_2\\\frac{1}{2} & \text{if } v \in Q_1\\0           & \text{otherwise}.\end{cases}$$
**Proof:** 

1. The region of two terminals never overlaps. 

Since $\sum_{v \in P} \hat{x}_{v} \geq 1$, there has to be at least one vertex between two regions. 

2. If there exists exactly one vertex, then that vertex has to be in $Q_{2}$

And if it is in $Q_{2}$, then we know that $\hat{x}_{v} = 1$, and therefore, the solution is feasible. 

3. If there exists two or more vertices, then they belong to $Q_{1} \cup Q_{2}$. 

Which would also sum up to $\geq 1$. 

**Claim:** $\hat{x}$ is optimal

**Proof:** 
	**Idea:** We will use complimentary slackness. Show that the dual is feasible, and that they both maintain complementary slackness. 

