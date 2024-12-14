Assume that $s$ initially "holds" an amount of flow (litres of water) equivalent to the sum of the capacities of its out edges. 

We can make this water flow to the rest of the graph by raising $s$'s altitude, so the water "trickles" down.

While lifting $s$ and its other vertices, we may have excess at some of the other nodes. We can raise these nodes **above $s$** so that the excess flows back into $s$. 

We use the following algorithm
	$\rightarrow$ Initialize the height of $s$ to be the number of vertices in the network.
	$\rightarrow$ For every edge $(x,y)$ in the **residual network** $G^f$, the difference between the height of $x$ and the height of $y$ never exceeds $1$. 
	$\rightarrow$ If there exists any excess flow at a vertex $x \neq s,t$, and there is a vertex $y$ whose height is $h(x) - 1$, **push** the smaller of that excess and the residual capacity of $(x,y)$ down to $y$.
	$\rightarrow$ If $x$ does not have a $y$ whose height is less than $x$, then we **relabel** the height of $x$ to be $1$ higher than its shortest neighbour. 

**As long as $f$ is not a feasible $st$-flow, either PUSH or RELABEL are applicable**

If $f$ is not feasible, then there exist an excess flow at one of the vertices.

**There is no path between $s$ and $t$ in the residual network**

If there is, then there exists a residual capacity at every edge on that path. The existence of a residual capacity on every edge means that every vertex on that path is at most one unit of **height** higher than the one before it. This gives us 
$$
\begin{aligned}
h_{s} = n \\
h_{s} \leq h_{t} + k \leq h_{t} + n-1 = n-1
\end{aligned}
$$
Where $k$ is the number of vertices on the path, which would be at most $n-1$. This gives us a contradiction and, therefore, proves our point.