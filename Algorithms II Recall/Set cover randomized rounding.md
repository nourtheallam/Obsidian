---
~
---
##### Idea

We create a [[From Monte Carlo to Las Vegas]] algorithm where the Monte Carlo part is
$$P[\hat{x} = 1] = 1 \cdot\tilde{x}$$
Given the variable $x_{S}$, it will be set to $1$ as often as $\tilde{x}_{S}$ of the time. Therefore, we run an algorithm that sets the values of $\hat{x}$ for $t = \ln(|U|) +2$ times.
##### Steps

For $i \leq t$
	$\hat{x}^i_{S} = 1$ with probability $\tilde{x}_{S}$

For $S \in \mathcal{S}$
	Set $S$ to be the in cover if $\hat{x}_{S}$ is set to $1$ **at least once.** 

##### Correctness

We **claim** that this gives us a $4t$-**approximation** of an optimal set cover with a $\frac{1}{2}$ **probability of failure.**

We need to show that the **two failure modes**
1. The probability of the computed cover not being feasible is $\frac{1}{4}$
2. The probability of the objective function value not meeting the approximation guarantee is $\frac{1}{4}$

Start with the second claim:

![[Pasted image 20241219145749.png]]


For the first claim, consider the probability that the $i^{th}$ cover $\mathcal{C}^i$ leaves some element $e$ uncovered.

![[Pasted image 20241219150506.png]]


![[Pasted image 20241219151109.png]]
**Where $e$ here is Euler's number**

The probability that all covers $\mathcal{C}^i$ leave it uncovered is multiplying this probability $t$ times: 

![[Pasted image 20241219151448.png]]

