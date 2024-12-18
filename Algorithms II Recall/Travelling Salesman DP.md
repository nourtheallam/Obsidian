##### Idea

A naive implementation: 
- Considers all permutations of vertices, 
- Check if the cycle represented by each actually exists 
- Remember the cheapest cycle
This yields $O^*(n!)$ time. 

$\rightarrow$ Maybe we can find the TST of the graph without each vertex $u$ then reincorporate $u$ as cheaply as possible?
	 **No. An optimal TST isn't composed of smaller TSTs.** 
