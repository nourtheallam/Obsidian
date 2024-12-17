---
~
---

**Idea:** We ==define== a half integral solution and ==prove== that it is feasible and optimal. 


**Steps:**

**Claim:** A ==feasible== [[Half-integral]] solution to the multiway vertex cut is defined as follows

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
	**Idea:** We will show that they both maintain [[Complementary slackness]], which ==automatically implies== that they are both optimal.

Consider the following primal and dual

$$
\begin{gathered}\text{Minimize } \sum_{v \in V \setminus T} w_vx_v\\\begin{aligned}\text{s.t. } \sum_{v \in P} x_v &\ge 1 && \forall P \in \mathcal{P}\\x_v &\ge 0 && \forall v \in V \setminus T.\end{aligned}\end{gathered}
$$

$$\begin{gathered}\text{Maximize } \sum_{P \in \mathcal{P}} y_P\\\begin{aligned}\text{s.t. } \sum_{v \in P} y_P &\le w_v && \forall v \in V\setminus T\\y_P &\ge 0 && \forall P \in \mathcal{P}.\end{aligned}\end{gathered}$$
We interpret $y_{P}$ as being the objective function value of all the terminal-to-terminal paths that $v$ lies on. 

 **Claim:** If $\hat{x}_{v} \geq 0$, then $\sum_{v \in P}y_{P} = w_{v}$

**Proof:** 
	**Idea:** If $\hat{x}_{v} \geq 0$ then it must be that $\hat{x}_{v} \in Q_{1} \cup Q_{2}$. 
		We will show that if every path $P$ has either exactly one vertex from $Q_{2}$ or exactly two vertices from $Q_{1}$ on it. 

