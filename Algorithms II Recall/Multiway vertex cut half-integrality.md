---
~
---

**Idea:** We ==define== a half integral solution and ==prove== that it is feasible and optimal. 


**Steps:**

**Claim:** A ==feasible== [[Half-integral]] solution to the multiway vertex cut is defined as follows

Given that $\tilde{x}$ is an ==optimal, fractional== solution, we have the following labels

![[Pasted image 20241217143819.png]]

Where anything within a region is $\tilde{x}_{v} = 0$.

We define $\hat{x}$ as 
$$\hat{x}_v = \begin{cases}1           & \text{if } v \in Q_2\\\frac{1}{2} & \text{if } v \in Q_1\\0           & \text{otherwise}.\end{cases}$$
**Proof:** 

1. The region of two terminals never overlaps. 

Since $\sum_{v \in P} \hat{x}_{v} \geq 1$, there has to be at least one vertex between two regions. 

2. If there exists exactly one vertex, then that vertex has to be in $Q_{2}$

And if it is in $Q_{2}$, then we know that $\hat{x}_{v} = 1$, and therefore, the solution is feasible. 

3. If there exists two or more vertices, then they belong to $Q_{1} \cup Q_{2}$. 

Which would also sum up to $\geq 1$. 

**Claim:** $\hat{x}$ is optimal

**Proof:** 
	**Idea:** We will show that if $\hat{y}$ is an optimal dual solution, and using the fact that $\tilde{x}$ is an optimal primal solution, that $\hat{x}$ and $\hat{y}$ maintain [[Complementary slackness]]. 

Consider the following primal and dual

$$
\begin{gathered}\text{Minimize } \sum_{v \in V \setminus T} w_vx_v\\\begin{aligned}\text{s.t. } \sum_{v \in P} x_v &\ge 1 && \forall P \in \mathcal{P}\\x_v &\ge 0 && \forall v \in V \setminus T.\end{aligned}\end{gathered}
$$

$$\begin{gathered}\text{Maximize } \sum_{P \in \mathcal{P}} y_P\\\begin{aligned}\text{s.t. } \sum_{v \in P} y_P &\le w_v && \forall v \in V\setminus T\\y_P &\ge 0 && \forall P \in \mathcal{P}.\end{aligned}\end{gathered}$$

 1.  If $\hat{x}_{v} > 0$, then $\sum_{v \in P}\hat{y}_{P} = w_{v}$
$$\hat{x}_{v} > 0 \implies v \in Q_{1} \cup Q_{2} \implies \tilde{x}_{v} > 0 \implies \sum_{v \in P}\hat{y}_{P} = w_{v}$$
(Because $\hat{y}$ and $\tilde{x}$ must maintain complementary slackness).

2. If $\hat{y}_{P} > 0$ then $\sum_{v \in P} \hat{x}_{v} = 1$

We will show that if every path $P$ has either ==exactly one== vertex from $Q_{2}$ or ==exactly two== vertices from $Q_{1}$ on it. 

$(1)$ Observe that $\tilde{x}_{v} \geq 1$ for all $v \in Q_{2}$ because $v$ would be the only vertex on the boundary between two regions for ==some== path $P$
$(2)$ Also observe that if $\hat{y}_{P} > 0$ then $\sum_{v \in P} \tilde{x}_{w} = 1$ (because they are both optimal)

Let $u \in Q_{2}$ be a vertex that lies on the path between two terminals and assume, for the sake of contradiction, that there either existed another vertex $v$ in $Q_{2}$ or in $Q_{1}$. 

![[Pasted image 20241217162822.png]]

By the first observation, we know that $\tilde{x_{u}} \geq 1$, and since $v$ is also a boundary vertex, we know that $\tilde{x}_{v} > 0$, which implies that
$$\sum_{v \in P} \tilde{x}_{v} > 1$$
Which contradicts the complementary slackness condition observed by $(2)$. 

Therefore, there is always ==exactly one== vertex from $Q_{2}$ in a path $P$ between two terminals if $\hat{y}_{P} > 0$, which means that $\hat{x} = 1$ will be satisfied (due to our definition of $\hat{x}$).

