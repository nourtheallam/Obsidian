Assume that $s$ initially "holds" an amount of flow (litres of water) equivalent to the sum of the capacities of its out edges. 

We can make this water flow to the rest of the graph by raising $s$'s altitude, so the water "trickles" down.

While lifting $s$ and its other vertices, we may have excess at some of the other nodes. We can raise these nodes **above $s$** so that the excess flows back into $s$. 

We use the following algorithm
	$\rightarrow$ Initialize the height of $s$ to be the number of vertices in the network.
	$\rightarrow$ For every edge $(x,y)$ in the **[[Residual Network]]** $G^f$, the difference between the height of $x$ and the height of $y$ never exceeds $1$. 
	$\rightarrow$ If there exists any excess flow at a vertex $x \neq s,t$, and there is a vertex $y$ whose height is $h(x) - 1$, **push** the smaller of that excess and the [[Residual Capacity]] of $(x,y)$ down to $y$.
	$\rightarrow$ If $x$ does not have a $y$ whose height is less than $x$, then we **relabel** the height of $x$ to be $1$ higher than its shortest neighbour. 

**As long as $f$ is not a feasible $st$-flow, either PUSH or RELABEL are applicable**

If $f$ is not feasible, then there exist an excess flow at one of the vertices.

**There is no path between $s$ and $t$ in the [[Residual Network]] at termination**

If there is, then there exists a [[Residual Capacity]] at every edge on that path. The existence of a [[Residual Capacity]] on every edge means that every vertex on that path is at most one unit of **height** higher than the one before it. This gives us 
$$
\begin{aligned}
h_{s} = n \\
h_{s} \leq h_{t} + k \leq h_{t} + n-1 = n-1
\end{aligned}
$$
Where $k$ is the number of vertices on the path, which would be at most $n-1$. This gives us a contradiction and, therefore, proves our point.

**The flow after termination is feasible**

Since there is no path between $s$ and $t$ in the [[Residual Network]] at termination, by the [[Max-flow Min-cut]] theorem, $f_{s}$ equals the capacity of some $st$-cut, which makes it a maximum flow. 

**Running time**

First, we should prove that t**here always exists a path between a vertex $x$ and $s$ in the residual network of $G$.** 
	Let $W$ be the set of vertices (other than $t$) reachable from $x$ in $G^f$, and assume that $s$ is not among those vertices. Then the sum of the excess flow at all vertices in $W$ is
	![[Pasted image 20241214190430.png]]
	Which implies that there exists an edge $(z,y)$, and therefore, that $z$ must also be reachable form $x$.
- [ ] #todo how is this specific to $s$?

==**s AND t ARE NEVER RELABELLED**==

**Every vertex $x \neq s,t$ has a height of at most $2n-1$**

Since we showed that there always exists a path between $x$ and $s$ in $G^f$. We know that the height of $x$ will be at most the height of $s - \text{the sum of the heights on the path between} \ x \ \text{and} \ s$. 
Since the height of $s$ is initialized to $n$ and there are at most $n-1$ vertices on the path, each of them at most one unit of height higher than the one before. If we relabel $x$, we may end up increasing the height of all the vertices on this path by $1$ as well, thus yielding a total height difference of $k + h_{s} = k + n - 1$. 

**We perform at most $2n(n-1)$ relabel operations**

Since $s$ and $t$ are never relabelled and the height of $x$ is at most $2n-1$, with each relabel increasing the height of $x$ by at least $1$, we can conclude that $x$ is relabelled at most $2n-1$ times. Since there are $n-2$ vertices that could get relabelled, the total count is $(n-1)(2n-1)$. 

**We perform at most $2nm$ saturating push operations**
$\rightarrow$ Instead, let's show that there are at most $2n$ saturating push operations per edge. 

Considering the saturating push operation from $x$ to $y$. Here the height of $x$ is $l$, one greater than the height of way. Since this is a saturating push, we would have to relabel $y$, push from it to $x$, then relabel $x$ so that it can push to $y$. Therefore, the height of $x$ increases by $2$ **between** each two saturating push operations on the edge $(x,y)$. Since we showed that the height of $x$ is at most $2n-1$. This yields at most $\frac{2n - 1}{2} = O(n)$ saturating push operations per edge. Since the same argument applies to $y$, this adds up to a total of $O(2n)$ saturating push operations on $(x,y)$, and therefore, $O(2nm)$ saturating push operations for all the edges. 

**At most $8n^2m$ non-saturating push operations**

Define the **potential** of an iteration as the sum of the heights of the excess vertices.

$\rightarrow$ A **relabel** operation increases the potential by at most $2n-1$ for each vertex.
$\rightarrow$ A **saturating push** operation from $x$ to $y$ may result in $y$ becoming an excess vertex when it wasn't before, and therefore, 