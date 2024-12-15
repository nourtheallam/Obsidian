##### (1)

The ILP of the [[Vertex Cover]] problem is
$$\begin{gathered}
\text{Minimize} & \sum_{v \in V} x_{v} \\ \\
\text{s.t.} & x_{v} + x_{u} \geq 1 & \forall (u,v) \in E \\
&x_{v} \in \{0,1\} & \forall v \in V
\end{gathered}$$
##### (2)

And its LP relaxation is 
$$\begin{gathered}
\text{Minimize} & \sum_{v \in V} x_{v} \\ \\
\text{s.t.} & x_{v} + x_{u} \geq 1 & \forall (u,v) \in E \\
& 0 \leq x_{v} \leq 1 & \forall v \in V
\end{gathered}$$

Consider the column vector $x$ whose elements are the variables $x_v$ for all $v \in V$. Let $A$ be an $m \times n$ matrix, and define $\mathbf{1}$ and $\mathbf{0}$ as the $m$-element column vectors filled with $1$ and $0$, respectively. We can express the above LP as follows:

$$\begin{gathered}
\text{Minimize} & x \\ \\
\text{s.t.} & Ax \geq \mathbf{1} \\ \\

& x\geq \mathbf{0} & \\
\end{gathered}$$
Each column of $A$ represents a vertex in $G$ while each row of represents and edge. An entry of $A$ is set to $1$ if the vertex represented by its column is an endpoint of the edge represented by its row, and set to $0$ otherwise. 

The [[Dual]] of this LP is
$$\begin{gathered}
\text{Maximize} & y \\ \\
\text{s.t.} & A^Ty \leq \mathbf{1}  \\ \\

& y\geq \mathbf{0} & \\
\end{gathered}$$
For some $m$-element column vector $y$ filled with the set of [[Dual]] variables $\{y_{i} | 0 \leq i \leq m\}$. 

##### (3)

Let each edge in $G$ correspond to an entry in $y$. Given our previous definition of $A$, each row of $A^T$ represents a vertex in $G$, while each column represents an edge. An entry of $A^T$ is set to $1$ if the vertex represented by its row is connected to the edge represented by its column. If we consider the ILP corresponding to the [[Dual]] LP:

$$
\begin{gathered}
&\text{Maximize} \quad y \\  
&\text{s.t.} \quad A^T y \leq \mathbf{1} \\  
& \quad \quad \quad y \in \{0,1\}
\end{gathered}
$$

the constraint $A^T y \leq \mathbf{1}$ enforces that for each row of $A^T$  (vertex in $G$), at most one of its non-zero entries (representing edges it's connected to in $G$) has a corresponding entry in $y$ that is equal to $1$. This ensures that no two edges selected in the solution share the same vertex. 

An optimal solution of this ILP will then correspond to a set of edges such that no two selected edges share a common vertex and the number of selected edges is maximized. This is precisely the definition of a maximum [[Matching]] in $G$. Therefore, an optimal solution of this ILP corresponds directly to a maximum [[Matching]] in the graph.  

While an optimal solution of the [[Dual]] LP allows for fractional values in $y$, the set of edges connected to each vertex can still contribute at most $1$ to the total objective function value, making the upper bound on the objective function value of an optimal solution to the [[Dual]] LP also an upper bound on the objective function of an optimal solution of its ILP. And consequently, the objective function value of an optimal solution to the [[Dual]] LP sets an upper bound on the size of a maximum [[Matching]] of $G$.
##### (4)

The [[Weak Duality]] theorem tells us that if $\hat{x}$ is a feasible solution of a primal minimization LP and $\hat{y}$ is a feasible solution of its [[Dual]] maximization LP then
$$\hat{x} \geq \hat{y}$$
Since we have associated minimizing the objective function of the primal LP we constructed with finding a minimum [[Vertex Cover]] and maximizing its [[Dual]] LP with finding a maximum valid [[Matching]], this tells us that the number of vertices in a feasible [[Vertex Cover]] will always be $\geq$  the number of edges in a feasible [[Matching]] of a graph $G$. And therefore, that the number of vertices in a minimum [[Vertex Cover]] will be $\geq$  the number of edges in a maximum [[Matching]] of a graph $G$. 

##### (5)

A maximal [[Matching]] of a graph $G$ is a [[Matching]] $M$ such that no edges can be added to $M$ without invalidating it. This definition implies that if there existed an edge $e \notin M$, then at least one of the endpoints of $e$ must be the endpoint of an edge that does exist in $M$ (otherwise, there would be no reason for the addition of $e$ to invalidate $M$). Therefore, if we were to take the set of endpoints of edges in $M$, then each edge in the graph will have at least one endpoint in that set. Since such a set is precisely the definition of a [[Vertex Cover]], we can conclude that the set of endpoints of the edges in a maximal [[Matching]] are a [[Vertex Cover]].

##### (6)

Since the set of endpoints of edges in a maximal [[Matching]] are a [[Vertex Cover]], then for a maximal [[Matching]] $M$ of a graph $G$ and its corresponding [[Vertex Cover]] $C$
$$2|M| = |C| $$
Since we explained in (4) that the size of a feasible [[Vertex Cover]] will always be $\geq$ the size of a  feasible [[Matching]], we know that for some maximum [[Matching]] $M'$ of $G$
$$|C| \geq |M'|$$
Which thus implies that
$$2|M| \geq |M'| \implies |M| \geq \frac{1}{2} |M'|$$
And therefore, we can conclude that the number of edges in a maximal [[Matching]] is always at least half as much as the number of edges in a maximum one.
##### (7)

Every maximum [[Matching]] $\hat{M}$ of some graph $G$ is a maximal [[Matching]]. Otherwise, it would be possible to add more edges to $\hat{M}$, contradicting the fact that it's a maximum [[Matching]]. 

Therefore, by the properties of a maximal [[Matching]], we can conclude that a maximum [[Matching]] $\hat{M}$ of some graph $G$ shares at least one endpoint with any maximal [[Matching]] $M$ of the same graph. Since there are two endpoints per edge in any graph,  we can express this relationship as 
$$\frac{\text{2 endpoints in } M}{\text{1 edge in } M} \cdot \frac{\text{1 edge in $\hat{M}$}}{\geq \text{ 1 endpoint in M}} = \frac{\text{2 edges in $\hat{M}$}}{\geq \text{1 edge in }M}$$
And therefore, the size of a maximal [[Matching]] $|M|$ of any graph $G$ is at least half the size of a maximum [[Matching]] $|\hat{M}|$ of the same graph. 
