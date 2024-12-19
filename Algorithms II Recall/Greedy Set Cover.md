
We consider the cost per **newly covered element** at each iteration
$$\frac{w_{S_{i}}}{|S_{i} - C|}$$
And choose the set $S_{i}$ that minimizes it.

#### Proof of Approximation Ratio 

**Claim:** The algorithm computes an $H_{n} = \sum_{i=1}^n \frac{1}{i}$-approximation of an optimal set cover.

**Proof:**

Let 
$$p_{e} = \frac{w_{S}}{|S - C|}$$
Be the **price** that we assigned to each element in $S$ for a given iteration.

Order the elements (not sets!) in $C$ by the order in which they were added to yield the sequence $\langle e_{1}, \dots, e_{n} \rangle$. 

Assign each element $e$ not yet in $C$ to **exactly one** set $S'$ also not in $C$.
$$p'_{e} = \frac{w_{S'}}{|S'|}$$
Let $C^*$ be an optimal set cover, and $C' \subseteq C^*$ be the subset of elements in $C^*$ that were not included in $C$ at some $i^{th}$ iteration. Then, 
$p'_{e} \leq w(C') \leq w(C^*) = OPT$$
If $p'_{e} \leq OPT$, then 
$$\frac{p'_{e}}{|C'|}$$

_

Since each set must contain at least one element, and since the $e_{i}$ elements are not yet in $C$, 
$$n - i + 1 \leq |U-C| \implies \frac{OPT}{n - i + 1} \geq \frac{OPT}{|U-C|} \implies p_{e} \leq \frac{OPT}{n-i+1}$$
__

Finally, note that $H_{n} = \Theta(\log n)$, and 

![[Pasted image 20241209172948.png]]
