Kernelization is a set of [[Reduction rule]]s such that: 

- $k' \leq k$

- For some (monotonically non-decreasing) $f(k)$, if $(I',k')$ is a **fully-reduced** instance and $|I'|  > f(k)$ then it is **has to** either be a yes or no instance.

- Getting to a fully-reduced instance from a non-reduced instance $(I, k)$ should take $O(|I|^c)$ time for some constant $c$. 

Assuming we can solve **any instance** $(I,K)$ in $O(g(|I|))$ time, the running time of the parameterized algorithm given by the kernelization procedure is:
![[Pasted image 20241213201433.png]]
