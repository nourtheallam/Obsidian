
A very nice, very cool way to store the solutions of sub-problems that we already solved such that they can be used to solve sub-problems that we haven't solved yet. 

This works great when the number of subproblems, and the amount of time taken to solve a subproblem, are both polynomial.

But what about [[NP-Hard]] problems? Applying DP might still help reduce the [[Exponential]] time needed to solve the problem if **there are many overlapping subproblems**, but more specifically, applying DP through a parameterized algorithm could help us reign-in the amount of space as it would be exponentially dependent only on the [[Hardness parameter]].