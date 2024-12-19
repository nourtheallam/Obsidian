
We consider the cost per **newly covered element** at each iteration
$$\frac{w_{S_{i}}}{|S_{i} - C|}$$
And choose the set $S_{i}$ that minimizes it.

#### Proof of Approximation Ratio 

**Claim:** The algorithm computes an $H_{n} = \sum_{i=1}^n \frac{1}{i}$-approximation of an optimal set cover.

**Proof:**

Order the elements (not sets!) in $C$ by the order in which they were added to yield the sequence $\langle e_{1}, \dots, e_{n} \rangle$. 

Let 
$$p_{e_{i}} = \frac{w_{S_{i}}}{|S_{i} - C|}$$
Be the **price** that we assigned to each element in $S$ for a given iteration.

Assign each element $e$ not yet in $C$ to **exactly one** set $S'$ also not in $C$.
$$p'_{e_{i}} = \frac{w_{S'}}{|S'|}$$

Let $C^*$ be an optimal set cover, and $C' \subseteq C^*$ be the subset of elements in $C^*$ that were not yet included in $C$ at some $i^{th}$ iteration. Then, 
$$\sum_{e \in C'} p_{e} = w(C')  \leq w(C^\star ) = OPT$$
Which implies
$$\frac{\sum_{e \in C'} p_{e}}{|C'|} \leq \frac{OPT}{|C'|} = \frac{OPT}{|U - C|}$$
In which there must exist an element that satisfies
$$p_{e} \leq \frac{OPT}{|U-C|}$$
Because $\frac{\sum_{e \in C'} p'_{e}}{|C'|}$ is the average.

Furthermore, observe that **because** we consider $C'$ to be the set of elements not yet added at the $i^{th}$ iteration
$$n - i + 1 \leq |U-C| \implies \frac{OPT}{n - i + 1} \geq \frac{OPT}{|U-C|} \implies p_{e} \leq \frac{OPT}{n-i+1}$$
Finally, note that $H_{n} = \Theta(\log n)$, and 

![[Pasted image 20241219182141.png]]




