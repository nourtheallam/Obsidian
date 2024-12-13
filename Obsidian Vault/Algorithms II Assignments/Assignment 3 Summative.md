
### Question 1 

##### (1)

**Relating routes to vertices, edges to possible flight plans**

We represent the input of the flight scheduling problem as a network where each route $R_{i}$ is represented by a pair of vertices $f_{i}, t_{i}$ corresponding to the departure and destination cities of $R_i$ respectively, and which are connected to each other via a directed edge from $f_i$ to $t_i$. We draw a directed edge from $t_i$ to $f_j$ if $R_{j}$ can be flown after $R_{i}$ by the same plane.

**Relating flow assignments to flight plans**

If the flow assignment $f_{u,v}$ on an edge $(u,v)$ is $1$, then the same plane visits the city represented by $u$, followed by the city represented by $v$. More specifically, if the flow $f_{f_j, t_j}$ on the edge between two vertices $f_j$ and $t_j$ (representing the departure and destination cities of a route $R_j$) is equal to $1$, then that route $R_j$ is serviced by a plane. If there the flow $f_{t_i, f_j}$ between the destination city of route $R_i$ and the departure city of route $R_j$ is equal to $1$, then some plane services $R_{i}$ followed by $R_{j}$ (the routes are serviced by the same plane).

**Assigning edge capacities and demands**

We assign a capacity $c_{(u, v)} = 1$ for every edge $(u,v)$ to ensure that no plane takes the same path twice. We also assign a demand $d_{(u,v)} = 1$ if the edge $(u,v)$ is between two vertices corresponding to the same route ("between its departure and destination cities"), and $d_{(u, v)} = 0$ if it connects vertices of different routes. 

**Creating additional vertices to control the flow (number of planes)**

We also  create three additional vertices $s, s'$ and $t$ such that we can control the total flow ("total number of planes") in the graph. Flow can only be created or absorbed by $s$ and $t$. We draw a directed edge from $s$ to $s'$, a directed edge from $s'$ to every departure ($f_{i}$) vertex in the network, and a directed edge from every destination ($t_{i}$) vertex in the network to $t$. To control the total flow in our network, we set the capacity of $(s, s')$ to be $k$ and its demand to $1$. We set the capacity to $1$ and the demand to $0$ for every other one of these new edges. 

#### (2)

**Constructing flow from solution to flight scheduling problem + showing it abides by defined edge capacities and demands**

A solution to the flight scheduling problem consists of a set of subsets of routes that can all be flown by the same plane. Since the routes have to be flown in some sequence by their plane, we more specifically define a solution to the flight scheduling problem as a set of non-repetitive sequences $\{R_{i} | R_{i} = \langle R_{i_{1}}, \dots, R_{i_{n_{i}}} \rangle \}$  such that each sequence represents routes that can all be flown by the same plane in that sequence.

We thus know that for any two routes $R_{i_{j}}$, $R_{{i_{j+1}}}$ that are placed consecutively in some sequence $R_{i}$, we will have at most one plane, the same plane, servicing them and thus the flow of any edge $(t_{i_{j}}, f_{i_{j+1}})$ connecting two such routes will be $1$
$$ \begin{aligned}
d_{t_{i_{j}}, f_{i_{j+1}}} < f_{t_{i_{j}}, f_{{i_{j+1}}}} = 1 = c_{t_{i_{j}}, t_{i_{j+1}}} \\
\end{aligned}
$$
Since a solution ensures that every route will be serviced, we also know that for any edge $(f_{i_{j}}, t_{i_{j}})$ whose vertices correspond to the departure and destination vertices of the same route $R_{i_{j}}$, the flow of that edge will be $1$

$$d_{t_{i_{j}}, f_{i_{j}}} = f_{t_{i_{j}}, f_{{i_{j}}}} = 1 = c_{t_{i_{j}}, t_{i_{j}}}$$

Since we know that any two routes $R_{i_{j}}, R_{k_{l}}$ that are not chosen to be in the same subset will not have any planes flying between them. We know that for any other edge $(f_{i_{j}}, t_{k_{l}})$ connecting the destination vertex of on of them to the departure vertex of the other the flow will be $0$ 
$$d_{f_{i_{j}}, t_{k_{l}}} = f_{f_{i_{j}}, t_{k_{l}}} = 0 < c_{f_{i_{j}}, t_{k_{l}}}$$

Since we know that a solution to the flight scheduling problem utilizes at least one plane and at most $k$ planes, we know that at most $k$ flow will be "produced" by the source node $s$, and therefore that $$d_{s, s'} = 1 \le f_{s, s'} \leq k = c_{s, s}$$
Moreover, since we know that only one plane services each subset of route $R_{i}$, we know that at most one unit flow will be assigned from $s'$ to any other vertex and therefore, for any edge $(s, f_{i_{j}})$ between $s'$ and the departure vertex of a route, the flow will be at most $1$ 
$$d_{s', f_{i_{j}}} < f_{s', f_{i_{j}}} \leq 1 = c_{s', f_{i_{j}}}$$
And therefore, we also know that at most one unit of flow will be travelling from a destination vertex $t_{i_{j}}$ to $t$, making the flow of such an edge at most $1$
$$d_{t_{i_{j}}, t} < f_{t_{i_{j}}, t} \leq 1 = c_{t_{i_{j}}, t}$$

Since the above cases cover all possible edges in the network and their flow assignment, we know that the constraint $d_{u,v} \leq f_{u,v} \leq c_{u,v} \forall (u,v) \in E$  is met by any solution to the flight scheduling problem. 

**Proving that flow assignments can never be fractional in a feasible flow + summarizing constructed flow**

Now, consider the case where any edge in the network is assigned a fractional flow. If this occurs, it would be impossible for that flow to feasibly reach the terminal vertex $t$. This is because the flow must pass through at least one edge that connects a "departure" vertex to a "destination" vertex of some route. The capacity and demand of such edges are both defined as 1 (an integer). Therefore, assigning a fractional flow to these edges would violate feasibility. Thus, for the flow to be feasible, the amount of flow assigned to any edge along an $st$-path must be integral. This allows us to further specify the flow from $s'$ to any vertex, from any vertex to $t$, and from $s$ to $s'$ 
$$\begin{aligned}
f_{s, s'} \in \{1, \dots, k\}\\
f_{s', u} \in \{0,1\} && \forall \ u \in V\\
f_{u, t} \in \{0,1\} && \forall \ u \in V
\end{aligned}$$

To summarize the flow assigned by a solution of the flight scheduling problem to the edges of the network we defined

$$\begin{aligned}
f_{s, s'} \in \{1, \dots, k\}\\
f_{s', u} \in \{0, 1\} \\
f_{u, t} \in \{0, 1\}\\ \\
f_{f_{i_{j}}, t_{i_{j}}} = 1 && \forall \  1 \le i \le k, \ 1 \le j \le n\\
\\
f_{t_{i_{j}}, f_{m_{l}}} = \begin{cases}
1 & \text{if} \ i = k \ \text{and} \ l = j+1 \\
0 & \text{otherwise}
\end{cases} && ∀ \  1≤i,m≤k, \  1≤j,l≤n
\\ \\
\end{aligned}$$


**Proving that flow is conserved**

To prove flow conservation, consider the fact that we can construct an $st$-path for each sequence $R_i$ by following these steps:

1. Start with the edge from $s$ to $s'$.
2. Then, add the edge from $s'$ to the departure vertex of the first route in $R_i$.
3. For each route in $R_i$, add the edge from its departure vertex to its destination vertex.
4. If the sequence continues with another route, add the edge from the destination vertex of the current route to the departure vertex of the next route.
5. Finally, add the edge from the destination vertex of the last route in $R_i$ to $t$.

Since each sequence is serviced by only one plane, there will be exactly one unit of flow passing through each path. This implies that for all consecutive edges $(u, v)$ and $(k, u)$ in a path
$$
\sum_{(u, v) \in V} f_{u,v} - \sum_{(k,u) \in V} f_{k,u} = 0
$$
Since the flow through any edges not belonging to such a path would be 0, satisfying the above constraint implies satisfying flow conservation for all vertices $v \notin \{s, t\}$ in the network.

Finally, since there can be at exactly one unit of flow on any edge between $s'$ and another vertex $v$, we can conclude that if $s$ sends $l \leq k$ units of flow to $s'$, there will be $l$ distinct $st$-paths, each carrying one unit of flow. Consequently, the terminal node $t$ will receive exactly $l$ units of flow, ensuring flow conservation by absorbing the incoming flow.

**Conclusion**

Therefore, by proving that the constructed flow conserves flow at every vertex an across the entire network, and abides by all edge capacities and demands, we have shown that we can construct a feasible flow from a solution to the flight scheduling problem. 
##### (3)

**Constructing a solution to the flight scheduling problem from a feasible flow**

Given a feasible flow in our network, we want to construct at most $k$ subsets of routes, where each subset can be flown by a single plane. We compute a set of vertex-disjoint $st$-flows of our network, each of which correspond to a subset in a solution to the flight scheduling problem.

We iterate through the following steps to construct our solution
- Pick a departure vertex $f_{i}$ such that $f_{s', f_{i}} = 1$, we create a new set called $R$, and add the route $R_{i}$ to it. 
- Perform a depth first search starting at $f_{i}$, adding each pair of departure and destination vertices, $f_{j}, t_{j}$, that we encounter to the set $R$ in the form of of the route they correspond to, $R_{j}$, as long as the condition that the edge connecting our current vertex and $f_{j}$ has a flow of 1.
- Mark all the vertices visited in this search, including $f_{i}, t_{i}$, such that they are not visited again by future search. 

These steps effectively compute $st$-flows in the network as:
- Any edge $(s', f_i)$ will be preceded by the edge $(s, s')$.
- We follow edges with a flow of $1$, where any flow will eventually need to be absorbed by $t$ (as there are no edges leading back to $s$). This implies that our search ends when we reach $t$, and ensures that flow is conserved along the path discovered by our search.

We claim that the set of "$R$" sets that we found is effectively the set of of subsets of routes that represent a solution to the flight scheduling problem. To prove this claim, we need to prove that  the subsets are disjoint, that there are at most $k$ of them, and that the routes added to each subset can be serviced by a a single plane.

**Proving that the computed subsets are disjoint**

To prove that the subsets are disjoint, we point to the fact that we mark the vertices encountered in each iteration (in which an iteration corresponds to the "filling" of a single subset) as visited, ensuring that they are note visited again by future iterations, and therefore, that the route corresponding to each pair of departure-destination vertices is not added to more than one subset.

**Proving that there are at most $k$ subsets**

To prove that there are at most $k$ such subsets, we recall the fact that the capacity of the edge $(s, s')$ is $k$ and that we follow the path taken by one unit of flow at each iteration. This implies that there would be at most $k$ iterations and, since we create one subset per iteration, at most $k$ subsets would be created.

**Proving that the routes in each subset can all be serviced by the same plane**

To prove that the routes in each subset can all be serviced by the same plane, we recall the fact that we constructed our network such that a directed edge is drawn from the destination vertex $t_{i}$ of some route $R_i$ to the departure vertex $f_{j}$ of another route $R_{j}$ only if $R_{j}$ can be flown after $R_{i}$. This means that if we are constructing each subset $R_{i}$ by following the flow starting at some vertex $f_i$ then we know that the next vertex added to $R_{i}$ will correspond to a route that can be serviced after the route represented by $f_{i}$ without breaking the laws of physics or neglecting servicing our plane. 

**Conclusion**

Therefore, we have proven that by following the steps described above, we can construct a solution to the flight scheduling problem from a feasible flow of our network. 

### Question 2

#### (1)

**Note:** we assume that $N$ is represented as a complete graph with the capacity and demand of any non-existent edges being $0$.

**Constructing $N'$ from $N$**

Let $d_{min}$ be the minimum value of an edge demand in $N$. We can convert $N = (V, E)$ to $N' = (V, E')$ by adding $|d_{min}|$ to all edge capacities, demands, and flow assignments in $N$
$$\begin{gathered}
d'_{u,v} = d_{u,v} + |d_{min}| \\
c'_{u,v} = c_{u,v} + |d_{min}| \\
\end{gathered}$$
This ensures that for edges $(u,v)$ with $d_{u,v} = |d_{min}|$, their demand in $N'$ becomes $d'_{u,v} = 0$, while edges with a higher demand are assigned a positive $> 0$ value. This also ensures that all capacities in $N$ are nonnegative in $N'$, as the minimum value of any edge capacity will always be greater than or equal to the minimum edge demand in $N$. 

To map a flow $f$ in $N$ to a flow $f'$ in $N'$, we add $|d_{min}|$ to all the flow assignments in $f$
$$f'_{u,v} = f_{u,v} + |d_{min}|$$
To map a flow $f'$ in $N'$ to a flow $f$ in $N$, we subtract $|d_{min}|$ from all the flow assignments in $f'$
$$f_{u,v} = f'_{u,v} - |d_{min}|$$

**Proof that flow in $N'$ is feasible if corresponding flow in $N$ is feasible**

Assume that the flow $f$ in $N$ is feasible, then the following constraints hold
$$
\begin{aligned}
d_{u,v} &\leq f_{u,v} \leq c_{u,v} && \forall u, v \in V, \\
\sum_v(f_{u,v} - f_{v,u}) &= 0 && \forall u \in V \setminus \{s, t\}.
\end{aligned}
$$
We aim to demonstrate that the following constraints hold in for the corresponding flow $f'$ in $N'$

$$
\begin{aligned}
d'_{u,v} &\leq f'_{u,v} \leq c'_{u,v} && \forall u, v \in V, \\
\sum_v(f'_{u,v} - f'_{v,u}) &= 0 && \forall u \in V \setminus \{s, t\}.
\end{aligned}
$$
To prove that the first constraint holds, we observe that 
$$d'_{u,v} \leq f'_{u,v} \leq c'_{u,v}$$
Is equivalent to 
$$d_{u,v} + |d_{min}|\leq f_{u,v} + |d_{min}|\leq c_{u,v}+ |d_{min}|$$
Which is the equivalent to adding $|d_{min}|$ to all the terms of
$$d_{u,v} \leq f_{u,v} \leq c_{u,v}$$
The fact that the above inequality holds true for all vertices $u,v$ in $N$  implies that 
$$d'_{u,v} \leq f'_{u,v} \leq c'_{u,v} \ \ \forall u, v \in V$$
To prove that the second constraint holds, we observe that 
$$\sum_v(f'_{u,v} - f'_{v,u})$$
Is equivalent to 
$$\sum_v((f_{u,v} + |d_{min}|) - (f_{v,u}+|d_{min}|)) = \sum_v(f_{u,v} - f_{v,u})$$
Which, given our assumption that the flow in $N$ is feasible, evaluates to $0$ for all $u \in V \setminus \{s, t\}$, and thus implies that
$$\begin{aligned}
\sum_v(f'_{u,v} - f'_{v,u}) &= 0 && \forall u \in V \setminus \{s, t\}.
\end{aligned}$$

**Proof that flow in $N$ is feasible if corresponding flow in $N'$ is feasible**

Assume that the flow $f'$ in $N'$ is feasible, then the following constraints hold
$$
\begin{aligned}
d'_{u,v} &\leq f'_{u,v} \leq c'_{u,v} && \forall u, v \in V, \\
\sum_v(f'_{u,v} - f'_{v,u}) &= 0 && \forall u \in V \setminus \{s, t\}.
\end{aligned}
$$
We aim to demonstrate that the following constraints hold in for the corresponding flow $f$ in $N$
$$
\begin{aligned}
d_{u,v} &\leq f_{u,v} \leq c_{u,v} && \forall u, v \in V, \\
\sum_v(f_{u,v} - f_{v,u}) &= 0 && \forall u \in V \setminus \{s, t\}.
\end{aligned}
$$

To prove that the first constraint holds, we observe that 
$$d_{u,v} \leq f_{u,v} \leq c_{u,v}$$
Is equivalent to 
$$d'_{u,v} - |d_{min}|\leq f'_{u,v} - |d_{min}|\leq c'_{u,v} - |d_{min}|$$
Which is the equivalent to subtracting $|d_{min}|$ from all the terms of
$$d'_{u,v} \leq f'_{u,v} \leq c'_{u,v}$$

The fact that the above inequality holds true for all vertices $u,v$ in $N'$  implies that 
$$d_{u,v} \leq f_{u,v} \leq c_{u,v} \ \ \forall u, v \in V$$
To prove that the second constraint holds, we observe that 
$$\sum_v(f_{u,v} - f_{v,u})$$
Is equivalent to 
$$\sum_v((f'_{u,v} - |d_{min}|) - (f'_{v,u}-|d_{min}|)) = \sum_v(f'_{u,v} - f'_{v,u})$$

Which, given our assumption that the flow in $N'$ is feasible, evaluates to $0$ for all $u \in V \setminus \{s, t\}$, and thus implies that
$$\begin{aligned}
\sum_v(f_{u,v} - f_{v,u}) &= 0 && \forall u \in V \setminus \{s, t\}.
\end{aligned}$$

**Proof that the mappings preserve the objective function value**

*Assume that $f$ is a maximum flow of $N$. We want to prove that if $f$ is a maximum flow of $N$ then its corresponding flow $f'$ in $N'$ is a maximum flow of $N'$* 

Suppose, for the sake of contradiction, that there existed a flow $\hat{f}'$ in $N'$ such that 

$$\sum_{v} \hat{f}'_{s,v} - \hat{f}'_{v,s} > \sum_{v} f'_{s,v} - f'_{v,s}$$
If we map $\hat{f}'$ to a flow $\hat{f}$ in $N$, and map $f'$ back to $f$
$$\sum_{v} ((\hat{f}'_{s,v} - |d_{min}|) - (\hat{f}'_{v,s} - |d_{min}|)) > \sum_{v} ((f'_{s,v} - |d_{min}|) - (f'_{v,s} - |d_{min}|))$$
$$\sum_{v} (\hat{f}_{s,v} - \hat{f}_{v,s}) > \sum_{v} (f_{s,v} - f_{v,s})$$
Then we would be implying that there exists a flow $\hat{f}$ in $N$ whose objective function value is greater than that of $f$ which contradicts our assumption that $f$ is a maximum flow of $N$. 

Therefore, if $f$ is a maximum flow of $N$ then its corresponding flow $f'$ in $N'$ is a maximum flow of $N'$.

*Assume that $f'$ is a maximum flow of $N'$. We want to prove that if $f'$ is a maximum flow of $N'$ then its corresponding flow $f$ in $N$ is a maximum flow of $N$* 

Suppose, for the sake of contradiction, that there existed a flow $\hat{f}$ of $N$ such that 

$$\sum_{v} \hat{f}_{s,v} - \hat{f}_{v,s} > \sum_{v} f_{s,v} - f_{v,s}$$
If we map $\hat{f}$ to a flow $\hat{f}'$ in $N'$, and map $f$ to $f'$
$$\sum_{v} ((\hat{f}_{s,v} + |d_{min}|) - (\hat{f}_{v,s} + |d_{min}|)) > \sum_{v} ((f_{s,v} + |d_{min}|) - (f_{v,s} + |d_{min}|))$$
$$\sum_{v} (\hat{f}'_{s,v} - \hat{f}'_{v,s}) > \sum_{v} (f'_{s,v} - f'_{v,s})$$

Then we would be implying that there exists a flow $\hat{f}'$ in $N'$ whose objective function value is greater than that of $f'$ which contradicts our assumption that $f'$ is a maximum flow of $N'$. 

Therefore, if $f'$ is a maximum flow of $N'$ then its corresponding flow $f$ in $N$ is a maximum flow of $N$.

By proving that $f$ is a maximum flow of $N$ $\iff$ its corresponding flow in $N'$, $f'$, is a maximum flow of $N'$, we have proven that the mappings we provided preserve the objective function value.

#### (2)

Note: We assume that $N'$ is represented as a complete network where any edge that doesn't exist in it has a flow, demand, and capacity of $0$. This shouldn't affect the below arguments, but just for the sake of dealing with discrepancies in my notation ...


Since $N''$ is a network with nonnegative flow assignments
$$0 \leq f''_{e} \leq c''_{e} \ \ \forall e \in E''$$
Hence, despite the edges in $N''$ having no demand, the non-negativity of $N''$ enforces an implicit demand of $0$ on all of them.

**Constructing feasible flow in $N'=(V', E')$ from feasible flow with value $D$ in $N''=(V'',E'')$

To construct a feasible flow $f'$ in $N'$ from a feasible flow $f''$ with value $D$ in $N''$, we need to assign a flow value $f'_{e}$ for all edges $e \in E'$ (all edges that exist in $N'$) that maintains the following conditions 
$$\begin{aligned}
d'_{e} \leq f'_{e} \leq c'_{e} \\
\sum_{v}(f_{u,v} - f_{v,u}) = 0 && \forall u \in V' 
\end{aligned}$$

Let the flow $f'_e$ for each edge $e$ in $N'$ be defined as $f'_{e} = f''_{e} + d'_{e}$. Since we know that
$$0 \leq f''_{e} \leq c''_{e} \ \ \forall e \in E''$$
Then, since $N'$ is a subnetwork of $N''$, it must also be true that
$$0 \leq f''_{e} \leq c''_{e} \ \ \forall e \in E'$$
And therefore, it must also be true that 
$$d'_{e} \leq f''_{e} + d'_{e} \leq c''_{e} + d_{e} \ \ \forall e \in E'$$
Which, given that the capacity of any edge in $N''$ that also exists in $N'$ is defined as $c''_{e} = c'_{e} - d'_{e}$, is equivalent to 
$$d'_{e} \leq f''_{e} + d'_{e} \leq c'_{e} \ \ \forall e \in E'$$Therefore 
$$d'_{e} \leq f'_{e} \leq c'_{e} \ \ \forall e \in E'$$
Which is one of the conditions for a feasible flow in $N'$. 

To show that flow is conserved, consider the following summation for all $v \in V'$
$$\begin{aligned}
\sum_{u \in V''} (f''_{u,v} - f''_{v,k}) = 0 
\end{aligned}$$
Which can be expressed as 
$$\begin{aligned}
\sum_{u,k \in V'} (f''_{u,v} - f''_{v,u}) + f''_{s',v} - f''_{v, t'} \\
= \sum_{u \in V'} (f''_{u,v} - f''_{v,u}) + \sum_{u \in V'} d'_{u,v} - \sum_{u \in V'} d'_{v,u}
\end{aligned} $$
Which, given our definition of $f'$ for edges in $N'$, is equivalent to 
$$\sum_{u \in V'} (f'_{u,v} - f'_{v,u})$$
And therefore, 
$$\sum_{u \in V'} (f'_{u,v} - f'_{v,u}) = 0$$
Which proves that flow is conserved at each vertex $v$ in $N'$ by $f'$. 

To prove that flow is conserved overall across the network, we see that 
$$\begin{aligned}
\sum_{v \in V'} (f'_{u,v} - f'_{v,u}) && \forall u \in V' \\
= \sum_{u \in V'} \sum_{v \in V'} (f'_{u,v} - f'_{v,u}) \\ 
= 0
\end{aligned}$$
We have therefore constructed a feasible flow $f'$ from $f''$ and shown that it is feasible.

**Constructing a feasible flow $f''$ with value $D$ in $N''$ from a feasible flow $f'$ in $N'$**

We define the flow assignment of each edge in $N''$ as follows:

$$
\begin{aligned}
1. & \quad \forall \ v \in V \setminus \{s',t'\}: \\
& \quad f''_{s',v} = c''_{s',v}, \quad f''_{v,s'} = 0 \\
& \quad f''_{v,t'} = c''_{v,t'}, \quad f''_{t',v} = 0 \\
2. & \quad \forall \ (u,v) \in E' \ (\text{in } N'): \\
& \quad f''_{u,v} = f'_{u,v} - d'_{u,v} \\
3. & \quad \forall \ (u,v) \notin E' \cup \{(t,s), (s',u), (u,t')\}: \\
& \quad f''_{u,v} = 0 \\
\end{aligned}
$$
To demonstrate the feasibility of this construction, we first show that $f''_e \leq c''_e$ for all $e \in E''$. This is trivially true for edges described by cases 1, 3 since:

- In case 1, $f''_e = c''_e$ for all edges.
- In case 3, $f''_e = 0$.

For edges in case 2, the capacity in $N''$ is defined as $c''_e = c'_e - d'_e$. Since $f'_e$ is feasible in $N'$, we know that:

$$
f'_e \leq c'_e
$$

This implies:

$$
f'_e - d'_e \leq c'_e - d'_e = c''_e
$$

Therefore, the constraint holds for all edges in case 2 as well.

Next, we need to verify that flow conservation holds and that the value of $f''$ is $D$.

Assuming that $s'$ and $t'$ are the source/sink vertices of $N''$, we see that the value of $f''$ is $D$
$$\sum_{v \in V \setminus \{s', t'\}}(f''_{s',v} - f''_{v,s'}) = \sum_{v \in V \setminus \{s', t'\}}(c''_{s',v}- 0) = \sum_{v \in V \setminus \{s', t'\}}\left( \sum_{u \in V \setminus \{ s', t'\}}d'_{u,v} \right) = D$$
And moreover, that this is the maximum flow of $N''$ as we set the value of all the out-edges of $s'$ to be the capacity of those edges. 

Furthermore, we see that since the flow and demand of any edge $(u,v) \notin E' \cup \{(t,s), (s',u), (u,t')\}$ is set to $0$, then for any $v \notin \{ s', t' \}$ 
$$\begin{gathered}
\sum_{u, k \in V \setminus\{ v \}} f''_{u,v} - f''_{v,k}\\
= f''_{s',v}+ \left( \sum_{u, k \in V \setminus\{  s', t'\}} f''_{u,v} - f''_{v,k} \right) - f''_{v,t'} \\
= \sum_{u \in V \setminus \{ s',t' \}} d'_{u,v} +  \left( \sum_{u, k \in V \setminus\{ s', t'\}} \left(  f'_{u,v} - \sum_{u} d'_{u,v}  \right) - \left(  f'_{v,k} \sum_{k} - d'_{v,k} \right) \right) - \sum_{u \in V \setminus \{ s',t' \}} d'_{v,u} \\
= \sum_{u, k \in V \setminus \{ s',t' \}} f'_{u,v} - f'_{v,k} \\
= 0 \ (\text{since $f'$ is feasible})
\end{gathered}$$
Which, since we are assuming that flow is created and absorbed by $s', t'$ in $N''$,  implies that the overall flow across the network is conserved.
##### (3)

We define the [[Residual Network]] in a network with nonnegative edge capacities and demands as 
$$N^f = \{(x,y) \in E \mid f_{x,y} < c_{x,y}\} \cup \{(y, x) \mid (x, y)\in E \text{ and } f_{y,x} > 0\}$$
Where the residual capacity of an edge $(x,y) \in N^f$ is 
$$c^f_{x,y} = f_{y,x} - d_{y,x} + c_{x,y} - f_{x,y}$$
If $(x,y)∈N^f$ because $f_{x,y}<c_{x,y}$, then this means that the edge $(x,y)∈E$ is not used to its full capacity and we can move up to $c_{x,y}−f_{x,y}$ units of flow along this edge in an attempt to increase the flow from $s$ to $t$.

If $(x,y)∈N^f$ because $f_{y,x}>0$, then this means that we can move up to $f_{y,x} - d_{y,x}$ units of flow from $y$ back to $x$.

It is possible that the network contains both edges $(x,y)$ and $(y,x)$. In this case, we can move up to $c_{x,y}−f_{x,y}$ additional units of flow from $x$ to $y$ along the edge $(x,y)$, and we can move up to $f_{y,x} - d_{y,x}$ units of flow from $x$ to $y$ by pushing flow back along the edge $(y,x)$. This is captured by the [[Residual Capacity]] of the edge $(x,y)$ in $N^f$, which is the sum of these two quantities.

Given a feasible $st$-flow, $f$, in $N$ an [[Augmenting Path]] is a path from $s$ to $t$ in the [[Residual Network]] $N^f$ along which we could push more flow from $s$ to $t$. We determine how much flow we can push along each edge in $N^f$, and therefore, how much flow we can push along such a path using the three cases described above. 

We claim that to obtain a maximum flow in $N$ by repeatedly finding augmenting paths in $N^f$, pushing more flow along those paths, and then changing the flow assignments in $N$ accordingly. We stop doing so once there are no more augmenting paths left. We call this procedure "adding" a maximum flow $f'$ in $N^f$ to a pre-existing flow $f$ in $N$ to obtain a maximum flow of $N$, $\hat{f} = f + f'$. 

To prove that this claim is true, assume that $f$ and $f'$ are feasible, that $f'$ is a maximum flow in $N^f$, and suppose for the sake of contradiction that there existed a maximum flow of $N$, $\tilde{f} > \hat{f}$. The existence of $\tilde{f}$ implies that there existed a path in $N$, when $N$ was assigned flow $\hat{f}$, along which we could have pushed more flow from $s$ to $t$. This is precisely the definition of an [[Augmenting Path]], and therefore, the existence of $\tilde{f}$ implies that there existed an [[Augmenting Path]] whose additional flow could have been added to $f'$ to make it bigger, and therefore, that $f'$ was not a maximum flow in $N^f$, which contradicts our assumption that it is. Therefore, by contradiction, it must be true that "adding" maximum flow in $N^f$  to $f$ yields maximum flow in $N$. 
