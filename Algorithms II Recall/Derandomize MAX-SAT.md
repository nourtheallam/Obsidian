We aim to improve on the [[MAX-SAT randomized rounding]] algorithm.
##### Ideas

When performing **naive guessing**, deterministically choose values for some variable $x_{1} \dots x_{n}$ such that they are guaranteed to make the expectation value higher.  

![[Pasted image 20241219213503.png]]

Which is equal to their **average**, and therefore, if we choose **whichever** **one that is greater**, we will not dip below the original expectation value.

When performing **randomized rounding**, use a similar strategy

![[Pasted image 20241219213848.png]]

This is equivalent to a **biased average** of the two, and therefore, guarantees that of we pick the larger one we're still in the clear. 

##### Steps

![[Pasted image 20241219214034.png]]
**Rather than applying one or the other with probability $\frac{1}{2}$**

##### Correctness

![[Pasted image 20241219214415.png]]
**Note that we reintroduce determinism in our analysis, too.**

