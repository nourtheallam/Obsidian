**Claim:** Any extreme-point solution of the LP relaxation of [[Vertex Cover]] is half-integral. 
**Proof:** Assume $\tilde{x}$ is a feasible solution with $\hat{x}_{v}$ being **NOT** half-integral.

Let $\delta$ be the minimum between $\tilde{x}_{v}$, the **difference in magnitude** between $\tilde{x}_{v}$ and $1$, and that between it and $\frac{1}{2}$. 

Now, define
![[Pasted image 20241216123551.png]]

We **claim** that $\tilde{y}$ and $\tilde{z}$ are feasible solutions of the LP relaxation. 
**Proof:** $\tilde{y}$ is a feasible solution

By the definition of $\tilde{y}$, $\tilde{y}_{u} < \frac{1}{2}$. 

We want to show that $\tilde{y}_{u} + \tilde{y}_{v} \geq 1$. 

![[Pasted image 20241216124107.png]]

