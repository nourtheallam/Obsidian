## Question 1

##### (1)

**Base case:** $m = 1$

If $m=1$, then we see that the input of $f$ is either $0$ or $1$, where each input value can have a corresponding value of either $0$ or $1$. 

To map, $0$ to $0$ and $1$ to $1$, we can apply the circuit $NOT \circ NOT$ to the input as $\lnot(\lnot a) = a$ for any $a \in \{0,1\}$. To map $0$ to $1$ and $1$ to $0$, we can apply the circuit consisting of a single $NOT$ gate to  the input as $\lnot 0 = 1$ and $\lnot 1 = 0$.

**Base case:** $m = 2$

If $m = 2$, then we see that the input of $f$ is either $(0,0), (0,1), (1,0),$ or $(1,1)$ where each input can be mapped to either $0$ or $1$. For any input $(a,b)$, we may either negate $a$, negate $b$, keep both the same, or negate both. 