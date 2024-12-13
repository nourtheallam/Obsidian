
Two greedy strategies to solving the [[Set Cover]] problem come to mind: 

- Pick the cheapest sets first 
- Pick the sets that cover the most elements first

However, each may be ineffective on its own, depending on the given input. 

So, we try to combine them. We look at the weight per element covered, which means minimizing
$$\frac{w_{Si}}{|S_{i}|}$$
However, this can also be ineffective as we should be paying more attention to the elements **not yet covered** at each choice we make. 

So, we consider the cost per **newly covered element** at each iteration
$$\frac{w_{S_{i}}}{|S_{i} - C|}$$
![[Pasted image 20241209162211.png]]


#### Proof of Approximation Ratio 

**Claim 1:** The algorithm computes an $H_{n} = \sum_{i=1}^n \frac{1}{i}$ [[Approximation]] of an optimal [[Set Cover]]. 

**Proof 1:**

Let 
$$p_{e} = \frac{w_{S}}{|S - C|}$$
Be the **price** that we assigned to each element in $S$ for a given iteration.
__
**Claim 1.1:** $$p_{e_{i}} \leq \frac{OPT}{n - i + 1}$$**Proof 1.1:** 
_ 
**Claim 1.1.1:**

Order the elements (not sets!) in $C$ by the order in which they were added to yield the sequence $\langle e_{1}, \dots, e_{n} \rangle$. Consider the $i^{th}$ element being added to $C$ and the set that contains it, $S'$. Prove that 
$$\frac{w_{S'}}{|S' - C|} = p_{e_{i}} \leq \frac{OPT}{n - i + 1}$$

**Proof 1.1.1:** 

Assign each element $e$ not in $C$ to **exactly one** set $S'$ also not in $C$. Let the collection of such sets be called $C'$, and let 
$$p'_{e} = \frac{w_{S'}}{|S'|}$$
Observe that
$$\sum_{e \in C'} p'_{e} = w(C')  \leq w(C^\star ) = OPT$$
- [ ] #todo How do we know that it's <= OPT?

$$\frac{\sum_{e \in C'} p'_{e}}{|C'|} \leq \frac{OPT}{|C'|} = \frac{OPT}{|U - C|}$$
In which there must exist an element that satisfies
$$p'_{e} \leq \frac{OPT}{|U-C|}$$
Because $\frac{\sum_{e \in C'} p'_{e}}{|C'|}$ is the average.
_

Since each set must contain at least one element, and since the $e_{i}$ elements are not yet in $C$, 
$$n - i + 1 \leq |U-C| \implies \frac{OPT}{n - i + 1} \geq \frac{OPT}{|U-C|} \implies p_{e} \leq \frac{OPT}{n-i+1}$$
__

Finally, note that $H_{n} = \Theta(\log n)$, and 

![[Pasted image 20241209172948.png]]
▨

