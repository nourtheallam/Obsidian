
## Question 1

We run the [[Ford-Fulkerson]] algorithm on a network $N(V, E)$ with $n$ vertices and $m$ edges for at most $I$ iterations. In each iteration, constructing the [[Residual Network]] $N^f$, based on the flow $f$ from the previous iteration, takes $O(m)$ time since we check each edge to determine whether it meets the conditions for inclusion in $N^f$. To find an $s$-$t$ path in $N^f$, we perform a depth-first search (DFS) starting from $s$, terminating when $t$ is encountered, which takes $O(n + m)$ time. If an $s$-$t$ path is found, the augmentation subroutine requires $O(m)$ time to find the minimum [[Residual Capacity]] by scanning the edges in the chosen $st$-path and $O(m)$ to update the flow of every edge in the path. Consequently, the total runtime of the [[Ford-Fulkerson]] algorithm, without preprocessing, is $O(I(n + m))$.

However, if we preprocess the network by running DFS from $s$ before the first iteration, identifying all vertices reachable from $s$, and restricting the algorithm to only these vertices and edges, then each subsequent DFS in future iterations would take $O(m)$ time, as the network would already be known to be connected with $O(m)$ edges. The total running time of all the iterations thus becomes $O(Im)$. Since this preprocessing step uses DFS, it takes $O(n+m)$ time and therefore, the total running time of the algorithm becomes $O(Im) + O(n + m) = O(n + Im)$. 

## Question 2

To prove that each iteration of the [[Ford-Fulkerson]] algorithm strictly increases the objective function value of the flow, we note that in each iteration, an $st$-path is identified in the current [[Residual Network]]. Along this path, the flow from $s$ to $t$ is augmented by the minimum [[Residual Capacity]] of the edges in the path. Since only the edges in this specific $st$ path have their flow values updated, the additional flow introduced is not affected out by any other changes in the network. Consequently, the total flow is guaranteed to increase by a positive amount, strictly improving the value of the objective function in each iteration.

Assuming all edges $(x, y)$ have integer capacities $u_{x,y}$ bounded by some value $L$, **and since the [[Ford-Fulkerson]] initializes all the flow assignments in the network to $0$ (an integral value)**, we know that the minimum [[Residual Capacity]]
$$\delta = \min(u^f_{x,y}) = \min(f_{y,x} + u_{x,y} - f_{x,y})$$
By which the flow from $s$ to $t$ is augmented in each iteration, must also be an integer. Since the [[Ford-Fulkerson]] algorithm initializes the flow on all edges to $0$, and in each iteration, it only updates the flow along the edges of the selected $st$-path in the [[Residual Network]], and since that update is defined as
$$
\begin{aligned}
f'_{y,x} &= f_{y,x} - \min\bigl(\delta, f_{x,y}\bigr) \\
f'_{x,y} &= f_{x,y} + \max\bigl(0, \delta - f_{y,x}\bigr)
\end{aligned}
$$
For any two adjacent vertices $x, y$ in the network, the flow remains an integer, as it results from adding or subtracting integer values in each iteration. 

Since we have proven that the objective function value of the flow strictly increases with each iteration and that all edges in the network have integral flows, we can conclude that, in every iteration of the [[Ford-Fulkerson]] algorithm on a network with non-negative, integral edge capacities, the flow from $s$ to $t$ increases by at least $1$.

Next, we establish bounds for the objective function value. The initial flow on all edges is set to $0$ which satisfies flow conservation and is therefore feasible. Given that the flow increases at each iteration, the minimum value of the objective function is $0$. The maximum flow that can be sent from $s$ into the network is the sum of the capacities of all edges directed from $s$ to a vertex that lies on an $st$-path. Since the maximum flow is achieved when no flow is sent back to $s$ while maintaining feasibility, the upper bound of the objective function value is equal to this sum. 
And therefore, given that the maximum capacity of any edge is $L$, **and since $s$ has $\leq n-1$ out-edges (where $n$ is the total number of vertices in the network)**, the upper bound on the objective function value is $O(Ln)$. 

Since we established that the flow in this network increases by at least $1$ in every iteration, 
and since the objective function will be at least $0$ and at most $O(Ln)$, we conclude that the maximum number of iterations is achieved when the algorithm begins with the minimum objective function value, and then increases this value by $1$ at each iteration to eventually obtain $O(Ln)$ as the final objective function value. And therefore, that the number of iterations is $O(Ln)$. 

Given the bound we obtained in question 1, the final bound on the running time of the [[Ford-Fulkerson]] algorithm on the described network is $O(n + (Ln)m)$ which is equivalent to $O(Lnm)$

## Question 3

**Description of Mapping Between a Network $N = (V,E)$ with Rational Edge Capacities and $N' = (V,E)$ with Integer Edge Capacities**

Given a network $N = (V, E)$ with rational edge capacities, we want to convert these capacities to integer values in a new network $N'$. To do this, let $c_{u,v}$ be the capacity of edge $(u,v)$ in $N$, expressed as a fraction:

$$ c_{u,v} = \frac{n_{u,v}}{d_{u,v}} $$

where $n_{u,v}$ is the numerator and $d_{u,v}$ is the denominator of the capacity. The least common multiple (LCM) of all the denominators $d_{u,v}$ across all edges is denoted as $L$. 

For each edge $(u,v)$ in $N$, we define the capacity in $N'$ as

$$ c'_{u,v} = n_{u,v} \cdot \frac{L}{d_{u,v}} = L\cdot c_{u,v}$$

The fact that $d_{u,v}$ is a divisor of $L$ ensures that $c'_{u,v}$ is an integer, and since

$$ \frac{c'_{u,v}}{L} = \frac{n_{u,v} \cdot \frac{L}{d_{u,v}}}{L} = \frac{n_{u,v}}{d_{u,v}} = c_{u,v} $$

we can always recover $c_{u,v}$ from $c'_{u,v}$ by dividing by $L$. Thus, $c_{u,v} = \frac{c'_{u,v}}{L}$.

When we solve the flow problem in $N'$ (denoted by $f'$), we convert the flows back to the original network $N$ by dividing each flow by $L$

$$ f_{u,v} = \frac{f'_{u,v}}{L} $$

Thus

$$ f'_{u,v} = f_{u,v} \cdot L $$

Since $f_{u,v}$ is computed using operations on the capacities in $N$, which can be expressed as rational numbers with denominator $L$, we conclude that $f_{u,v}$ can also be written with a denominator $L$, ensuring that $f'_{u,v}$ is an integer.

**If $f'$ is Feasible, Then $f$ is Feasible**

Assume that the flow $f'$ in $N'$ is feasible. This implies

$$
\begin{aligned}
f'_{u,v} \leq c'_{u,v} \quad \forall (u,v) \in E \\
\sum_{u,v \in E} f'_{u,v} - \sum_{v,u \in E} f'_{v,u} = 0 \quad \text{(flow conservation)}
\end{aligned}
$$

We want to show that the flow $f$ in the original network $N$, derived from $f'$ by dividing by $L$, is also feasible. Since  $f_{u,v} = \frac{f'_{u,v}}{L},$ flow conservation is preserved as follows

$$
\sum_{u,v \in E} f_{u,v} - \sum_{v,u \in E} f_{v,u} = \frac{1}{L} \left( \sum_{u,v \in E} f'_{u,v} - \sum_{v,u \in E} f'_{v,u} \right) = \frac{1}{L} \cdot 0 = 0.
$$

Now, for the capacity constraints, if $f'_{u,v} \leq c'_{u,v}$, then

$$
\frac{f'_{u,v}}{L} \leq \frac{c'_{u,v}}{L} = c_{u,v}
$$

Which implies

$$ f_{u,v} \leq c_{u,v} \quad \forall (u,v) \in E. $$

This shows that $f$ satisfies the capacity constraints in $N$ and is thus feasible.

**If $f$ is Feasible, Then $f'$ is Feasible**

Assume that $f$ is feasible in $N$. This implies

$$
\begin{aligned}
f_{u,v} \leq c_{u,v} \quad \forall (u,v) \in E \\
\sum_{u,v \in E} f_{u,v} - \sum_{v,u \in E} f_{v,u} = 0
\end{aligned}
$$

Now, since $f'_{u,v} = f_{u,v} \cdot L$, we check that flow conservation is preserved in $N'$

$$
\sum_{u,v \in E} f'_{u,v} - \sum_{v,u \in E} f'_{v,u} = L \left( \sum_{u,v \in E} f_{u,v} - \sum_{v,u \in E} f_{v,u} \right) = L \cdot 0 = 0.
$$

For the capacity constraints, if $f_{u,v} \leq c_{u,v}$, then

$$
f'_{u,v} = f_{u,v} \cdot L \leq c_{u,v} \cdot L = c'_{u,v},
$$

so

$$ f'_{u,v} \leq c'_{u,v} \quad \forall (u,v) \in E. $$

Thus, $f'$ is feasible in $N'$.


**Maximum Flow in $N'$ Corresponds to Maximum Flow in $N$**

Let $f'$ be a maximum feasible flow of $N'$. Consider the objective function value of $f'$ $$\sum_{v \in E}(f'_{s,v} - f'_{v,s})$$ Let $f$ be the flow corresponding to the mapping of $f'$ into $N$. Assume, for the sake of contradiction, that there existed feasible flow in $N$, $\hat{f} \neq f$ whose objective function value was greater than that of $f$. This implies that $$\sum_{v \in E}(\hat{f}_{s,v} - \hat{f}_{v,s}) > \sum_{v \in E}({f}_{s,v} - {f}_{v,s}) $$ If we map each of $\hat{f}$ and $f$ to $N'$, we get $$D\sum_{v \in E}(\hat{f}_{s,v} - \hat{f}_{v,s}) > \sum_{v \in E}({f'}_{s,v} - {f'}_{v,s})$$ Let this mapping of $\hat{f}$ into $N'$ be called $\hat{f}'$. Since we have shown that the any mapping from $N$ to $N'$ maintains feasibility, we can conclude that that the above expression implies that there exists a feasible flow of $N'$ whose objective function value is greater than that of $f'$ which contradicts our assumption that $f'$ is a maximum feasible flow of $N'$.

### Using $N'$ to Find Bounds for $N$

Given any edge $(x, y)$ with capacity $c_{x,y}$ in $N$ and $c'_{x,y}$ in $N'$, we have established the relationship:
$$c_{x,y} = \frac{c'_{x,y}}{L}.$$
Since $N'$ has exclusively integral capacities, this implies that $c_{x,y}$ will always be a multiple of $\frac{1}{L}$. 

Since the [[Ford-Fulkerson]] algorithm initializes all flow assignments in $N'$ to $0$ (an integral value), and since the minimum [[Residual Capacity]] by which the flow from $s$ to $t$ is augmented by in each iteration over $N$ is defined as
$$\delta = \min(c^f_{x,y}) = \min(f_{y,x} + c_{x,y} - f_{x,y}).$$
 We see that $\delta$ is also always a multiple of $\frac{1}{L}$.
 
The [[Ford-Fulkerson]] initializes all the flow assignments of $N$ to $0$, and at each iteration, changes the flow along the selected $st$-path in the [[Residual Network]] by adjusting the flow on each edge on that path as follows 
$$
\begin{aligned}
f'_{y,x} &= f_{y,x} - \min\bigl(\delta, f_{x,y}\bigr), \\
f'_{x,y} &= f_{x,y} + \max\bigl(0, \delta - f_{y,x}\bigr).
\end{aligned}
$$
Which implies that the flow of any edge $(x,y)$ in $N$ will also always be a multiple of $\frac{1}{L}$, since each flow reassignment involves adding or subtracting multiples of $\frac{1}{L}$.

From Question 2, we know that each iteration of the [[Ford-Fulkerson]] algorithm strictly increases the value of the objective function in a network with nonnegative capacities, regardless of integrality. Therefore, the objective function value in $N$ increases by at least $\frac{1}{L}$ in each iteration.

**Bounding the Objective Function**

Initially, the flow on all edges is set to $0$, which is a feasible flow due to flow conservation. The minimum value of the objective function is therefore $0$.

The maximum flow that can be sent from $s$ into the network is bounded by the sum of the capacities of all edges directed from $s$ to vertices on an $st$-path. The maximum value of the objective function is achieved when no flow is sent back to $s$ while maintaining feasibility. Thus, the upper bound on the objective function is the sum of these capacities. Since the maximum capacity of an edge in $N$ is $\max(C)$, and $s$ has at most $n-1$ out-edges (where $n$ is the total number of vertices in the network), the upper bound on the objective function value is $O(\max(C)n)$.

Thus, the objective function value for $N$ will lie between $0$ and $O(\max(C)n)$.

**Number of Iterations**

Since the objective function starts at $0$ and increases by at least $\frac{1}{L}$ in each iteration, the maximum number of iterations is reached when the value of the objective function increases from $0$ to $O(\max(C)n)$. This means the number of iterations is:
$$O\left(\frac{\max(C)n}{\frac{1}{L}} \right) = O(\max(C) L n).$$

**Final Bound on Running Time**

Combining this result with the general bound obtained in Question 1, we conclude that the total running time of the [[Ford-Fulkerson]] algorithm on the described network is
$$O(n + (\max(C) L n) m)$$
(where $m$ is the total number of edges in the network).

Which is equivalent to 
$$O(\max(C) L nm)$$