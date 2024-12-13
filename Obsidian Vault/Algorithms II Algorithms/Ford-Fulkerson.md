For each iteration, look for the [[Residual Network]] $G^f$ of $G$. If there exists any $st$-path $P$ in this network:
- Find the minimum [[Residual Capacity]] in $P$, call it $\delta$
- If $\delta$ is that of $(x,y)$, then $f_{y,x}$ gets set to $0$ and $f_{x,y}$ gets set to the capacity, otherwise
 ![[Pasted image 20241208172806.png | center | 300]]
 **Note that the Ford-Fulkerson may not terminate for some inputs.**

**Correctness**

Once we prove that every iteration maintains a feasible flow, and since this terminates once there do not exist any [[Augmenting Path]] $P$ in the network: 

- The flow across the network, $F_{s}$ is bottle-necked by the some edges.
- Since we run Ford-Fulkerson until these bottle-neck edges are filled up, and since these edges are going to have the minimum capacities, then the $st$-cut involving those edges is a  **minimum $st$-cut whose capacity = $F_{s}$**. 
- By the [[Max-flow Min-cut]] theorem, this implies that the current flow is a maximum flow.


 