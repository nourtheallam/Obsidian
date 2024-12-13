
## Question 1
#### (1)

Since the dominating set problem is a subset selection problem where we choose a subset $D \subseteq V$ of vertices to be the dominating set, we shall represent $D$ as the set of variables $\{x_v∣ v \in V\}$ such that $x_v=1$ if $v \in D$ and $x_v = 0$ if $v \notin D$. The weight of the dominating set $D$ is then

$$w(D)= \sum_{v \in V} w_{v} x_{v}$$

And is the objective function to be minimized. The constraints of the ILP need to enforce that $D$ is a dominating set. To be able to define the dominating set of this graph, we need to introduce the concept of the **closed neighbourhood** of a vertex $v$ in a graph $G$. The **closed neighbourhood** of a vertex $v$ in a graph $G$, denoted $N_G[v]$, is the subgraph of $G$ composed of the vertices adjacent to $v$, all edges connecting vertices adjacent to $v$, and $v$ itself. We denote the set of vertices in the closed neighbourhood of vertex $v$ in a graph $G$ as $N_G[v].V$==.== Our goal is to choose the vertices of our dominating set such that for any vertex $v$, there exists at least one vertex in its closed neighbourhood that is in $D$. This can be translated into the following constraint 
$$\begin{align}
\sum_{u \in N_{G}[v].V} x_{u} \geq 1 && \forall \ v \in V
\end{align}$$
Combining the above constraint with the defined objective function yields the following ILP
$$\begin{gathered}
\text{Minimize} \ w(D)= \sum_{v \in V} w_{v} x_{v} \\ \\
\text{s.t.} \sum_{u \in N_{G}[v].V} x_{u} \geq 1 && \forall \ v \in V \\
x_{v} \in \{0, 1\} && \forall \ v \in V 
\end{gathered}$$

#### (2)

We need to prove that a solution to this ILP, $\hat{x}$, is feasible if and only if it corresponds to a dominating set of $G$.

**Claim: If $\hat{x}$ is feasible, then it corresponds to a dominating set of $G$.**

**Proof:** 

Assume $\hat{x}$ is a feasible solution to the ILP, and let it correspond to a set $D \subseteq V$. Suppose, for the sake of contradiction, that $D$ is not a dominating set of $G$. This implies that there exists a vertex $v \in V$ such that $v \notin D$ and none of the vertices in the closed neighbourhood $N_{G}[v]$ of $v$ belong to $D$. In terms of the ILP, this means that for this vertex $v$, none of the variables corresponding to vertices in $N_{G}[v]$ have an objective value of $1$.

However, this contradicts the feasibility of $\hat{x}$ because one of the constraints of the ILP requires that for every vertex $v$, the sum of the variables corresponding to the vertices in $N_{G}[v]$ must be at least $1$. Therefore, our assumption that $D$ is not a dominating set leads to a contradiction, and thus $D$ must be a dominating set.

**Claim: If $\hat{x}$ corresponds to a dominating set of $G$, then it is feasible. 

**Proof:**

Assume that $\hat{x}$ is a solution to the ILP and that it corresponds to a a dominating set of $G$, $D \subseteq V$. Suppose, for the sake of contradiction, that $\hat{x}$ is not a feasible solution, then this implies that for some vertex $v$, $\sum_{u \in N_{G}[v].V} x_{u} < 1$ which means that there exists a vertex $v$ in $V$ that is neither in the dominating set $D$ nor is it adjacent to a vertex in $D$. 

However, this contradicts our assumption that $D$ is a dominating set as it implies that not every vertex $v \in V \setminus D$ has a neighbour in $D$. Therefore, our assumption that $\hat{x}$ is not a feasible solution leads to a contradiction, and thus $\hat{x}$ must be a feasible solution. 

#### (3)

We need to prove that $\tilde{x}$ is an optimal solution of the ILP if and only if it corresponds to a dominating set of $G$, $D$, of minimum weight. 

**Claim: if $\tilde{x}$ is an optimal solution of the ILP then it corresponds to a dominating set $D$ of minimum weight**

**Proof:**

Assume the $\tilde{x}$ is an optimal solution of the ILP and that it corresponds to a dominating set $D$. Suppose, for the sake of contradiction, that there exists a dominating set of vertices $D'$ such that $w(D') < w(D)$, implying that $D$ is not a minimum weight dominating set. If we let $\tilde{x}'$ be the solution of the ILP corresponding to $D'$, then this implies that $\sum_{v \in V} w_{v} \tilde{x}'_{v} < \sum_{v \in V} w_{v} \tilde{x}_{v}$. 

However, this contradicts our assumption that $\tilde{x}$ is an optimal solution. Therefore, our assumption that $D$ is not a minimum weight dominating set leads to a contradiction, and thus $D$ must be a minimum weight dominating set. 

**Claim: if $D$ is dominating set of minimum weight then its corresponding ILP solution $\tilde{x}$ is an optimal solution**

**Proof:**

Assume that f $D$ is dominating set of minimum weight and that it has a corresponding ILP solution $\tilde{x}$. Suppose, for the sake of contradiction that $\tilde{x}$ was not an optimal solution, implying that there exists a solution $\tilde{x}' \neq \tilde{x}$ such that $\sum_{v \in V} w_{v} \tilde{x}'_{v} < \sum_{v \in V} w_{v} \tilde{x}_{v}$. Let the dominating set represented by $\tilde{x}'$ be $D'$. Since $w(D') = \sum_{v \in V} w_{v} \tilde{x}'_{v}$ and $\sum_{v \in V} w_{v} \tilde{x}_{v}$, it must be true that $w(D') < w(D)$. 

However, this contradicts our assumption that $D$ is a dominating set. Therefore, our assumption that $\tilde{x}$ is not an optimal solution leads to a contradiction, and thus $\tilde{x}$ must be an optimal solution of the ILP. 


## Question 2

#### (1)

**Claim: The solution of the ILP for this set $S$ has objective function value $1$.**

**Proof:** Since all the intervals in $S$ all overlap ($(l_i, r_i] \cap (l_j, r_j] \ne \emptyset$ for all $1 \leq i < j \leq n$), we can only select at most one interval for our solution. In the ILP, this means setting $x_i = 1$ for some $1 \leq i \leq n$ and $x_j = 0$ for all $j \neq i$ such that the constraints
$$\begin{gathered}
\begin{aligned}
    \text{s.t.}\ x_i + x_j &\le 1 && \forall 1 \le i < j
\le n \text{ s.t. } (l_i, r_i] \cap (l_j, r_j] \ne \emptyset\\
    x_i &\in \{0, 1\} &&\forall 1 \le i \le n.
\end{aligned}
\end{gathered}$$
Are satisfied with maximal value. Therefore, the sum $\sum_{i=1}^n x_i$, which represents the objective function, must equal 1.

**Claim: The LP relaxation of the ILP has a fractional solution with objective function value $\frac{n}{2}$**

An LP relaxation of this ILP would look identical to the ILP except that the constraint $x_i \in \{0, 1\}\ \ \forall\ 1 \leq i \leq n$ is relaxed to be $0 \leq x_i \leq 1\ \ \forall\ 1 \leq i \leq n$.

**Proof:** While it is also true that all the intervals in $S$ overlap in this case, the LP relaxation gives us the option of setting  $x_i = \frac{1}{2}$ for all $1 \leq i \leq n$ such that the constraints 
$$\begin{gathered}
\begin{aligned}
    \text{s.t.}\ x_i + x_j &\le 1 && \forall 1 \le i < j
\le n \text{ s.t. } (l_i, r_i] \cap (l_j, r_j] \ne \emptyset\\
    0 \leq x_i \leq 1 &&\forall 1 \le i \le n.
\end{aligned}
\end{gathered}$$
are satisfied with maximal value. Therefore, the sum $\sum_{i=1}^n x_i$, which represents the objective function, must equal $n(\frac{1}{2}) = \frac{n}{2}$.

#### (2)

First, let's prove that if a solution $\hat{x}$ is feasible then the intervals in $I_{\hat{x}}$ are pairwise-disjoint. Assume that $\hat{x}$ is a feasible solution and suppose that $I_{\hat{x}}$ was not pairwise-disjoint. This would imply that for some point $p$, at least two of the intervals in $I_{\hat{x}}$ are also in $S_p$. However, this would mean that $\sum_{(l_i, r_i] \in S_p} x_i \geq 2$ which, since it was shown that $\sum_{(l_i, r_i] \in S_p} x_i \leq \sum_{(l_i, r_i] \in S_{r_j}} x_i$, also implies that $\sum_{(l_i, r_i] \in S_{r_j}} x_i \geq 2$ which breaks one of the constraints of the ILP and thus contradicts the assumption that $\hat{x}$ is a feasible solution. Therefore, by contradiction, it must be true that if $\hat{x_v}$ is a feasible solution, then $I_{\hat{x}}$ is pairwise disjoint.

Now, let's prove that if the intervals in $I_{\hat{x}}$ are pairwise disjoint, then $\hat{x}$ is a feasible solution. Assume that $I_{\hat{x}}$ is pairwise disjoint and suppose that $\hat{x}$ was not a feasible solution. If $\hat{x}$ is not a feasible solution, then we know that the statement $\sum_{(l_i, r_i] \in S_{r_j}} x_i \leq 1\ \ \forall 1 \leq j \leq n$ does not hold and that therefore, there must be some point $r_j$ that exists in more than one of the intervals that were chosen to be in $I_{\hat{x}}$, implying that the elements of $I_{\hat{x}}$ are not pairwise disjoint and thus contradicting our assumption. It must, therefore, be true that  if the interval $I_{\hat{x}}$ is pairwise disjoint, then $\hat{x}$ is a feasible solution. 

#### (3)

 Let's first prove that if $\hat{x}$ is an optimal solution then $I_{\hat{x}}$ has maximum cardinality among all subsets of pairwise disjoint intervals in $S$. Assume that $\hat{x}$ is an optimal solution and consider if $I_{\hat{x}}$ was not the subset of pairwise disjoint intervals with maximum cardinality. This implies that there exists a subset $S_m \subseteq S$ such that all pairs in $S_m$ satisfy the constraint that all its elements are disjoint from each other, and that $|S_m| > |I_{\hat{x}}|$. Since, if we were to represent all the elements of $S_m$ as a solution to the ILP then that solution would be maximizing the objective function while ensuring that the constraints are met, it must be false that $\hat{x}$ was an optimal solution to begin with (since we know that $I_{x} \neq S_m$ but that the objective function value of $S_m$ would be higher). Therefore, it must be true that if $\hat{x}$ is an optimal solution then $I_{\hat{x}}$ has maximum cardinality among all subsets of pairwise disjoint intervals in $S$.

Now let's prove that if $I_{\hat{x}}$ has maximum cardinality among all subsets of pairwise disjoint intervals in $S$ then $\hat{x}$ is an optimal solution. Assume that $I_{\hat{x}}$ has maximum cardinality among all subsets of pairwise disjoint intervals and suppose that  $\hat{x}$ is not an optimal solution. If $\hat{x}$ is not an optimal solution then we know that there exists a solution $\hat{x'}$ such that the objective function value of $\hat{x'}$ is greater than that of $\hat{x}$. In order for that to be true, we know that $\hat{x'}$ must correspond to a set of intervals $I_{\hat{x'}}$ such that there are more intervals in it than $I_{\hat{x}}$ which contradicts our assumption that $I_{\hat{x}}$ has maximum cardinality among all subsets of pairwise disjoint intervals. It must, therefore, be true that if $I_{\hat{x}}$ has maximum cardinality among all subsets of pairwise disjoint intervals in $S$ then $\hat{x}$ is an optimal solution. 

#### (4)

We assume that $\hat{x}^{j-1}$ is a feasible solution and that  $r_{h}$ is the leftmost right interval endpoint of all intervals whose corresponding variables have fractional values in $\hat{x}^{j-1}$.

Let $(l_{h}, r_{h}] \in S_{r_{j}}$. Since $\hat{x}^{j-1}_{h}$ is a fractional value, then it must be true that all other intervals $(l_{i}, r_{i}] \in S_{r_{j}} | (l_{i}, r_{i}] \neq (l_{h}, r_{h}]$ have a corresponding value in $\hat{x}^{j-1}$ that is either fractional or equal to zero. Since an interval that has a fractional value in $\hat{x}^{j-1}$ and contains $r_{j}$ must also contain $r_{h}$, and since any such interval gets its corresponding value in $\hat{x}^j$ set to zero while that of $(l_{h}, r_{h}]$ gets set to $1$, then it must also be true that $\sum_{(l_{i}, r_{i}] \in S_{r_{j}}} \hat{x}^j_{i} = \hat{x}^j_{h} + \sum_{(l_{i}, r_{i}] \in S_{r_{h}}} \hat{x}^j_{i}= 1 + 0 = 1$. Since any interval that does not overlap with $(l_{h}, r_{h}]$ has its corresponding value in $\hat{x}^j$ remain the same as it was $\hat{x}^{j-1}$, then it must be true that that $\sum_{(l_{i}, r_{i}] \notin S_{r_{j}}} \hat{x}^j_{i}\leq 1$ and $\hat{x}^j_{i} \geq 0 \ \ \forall (l_{i}, r_{i}] \notin S_{r_{j}}$. 

Therefore, given that $\hat{x}^{j-1}$, $\hat{x}^j$ must be feasible.

#### (5)

Given that both $\hat{x}^j$ and $\hat{x}^{j-1}$ are feasible, there exists some subset $S_{r_{i}}$ such that, in the conversion between $\hat{x}^j$ and $\hat{x}^{j-1}$, $h \in S_{r_{i}}$. 

Describe the objective function value of $\hat{x}^{j-1}$ as $$\begin{gathered}
\sum_{(l_i, r_i] \in S_{r_{i}}} \hat{x}^{j-1}_{i} + \sum_{(l_k, r_k] \in S_{r_{k}}} \hat{x}^{j-1}_{k} && \forall & 1 \leq k \leq n, & \exists \ \ 1 \leq i \leq n, & k \neq i \\
& & & \text{s.t.} & (l_h, r_h] \in S_{r_{i}}
\end{gathered}$$
Since we have shown in (4) that all of the elements of $S_{r_{i}}$ would have fractional or zero values in $\hat{x}^{j-1}$, we know that $$\sum_{(l_i, r_i] \in S_{r_{i}}} \hat{x}^{j-1}_{i} \leq 1$$
Since we have also shown in (4) that 
$$\sum_{(l_i, r_i] \in S_{r_{i}}} \hat{x}^{j}_{i} = 1$$
We can conclude that 
$$\sum_{(l_i, r_i] \in S_{r_{i}}} \hat{x}^{j-1}_{i} \leq \sum_{(l_i, r_i] \in S_{r_{i}}} \hat{x}^{j}_{i}$$
If we describe the objective function value of $\hat{x}^j$ as 
$$\begin{gathered}
\sum_{(l_i, r_i] \in S_{r_{i}}} \hat{x}^{j}_{i} + \sum_{(l_k, r_k] \in S_{r_{k}}} \hat{x}^{j}_{k} && \forall & 1 \leq k \leq n, & \exists \ \ 1 \leq i \leq n, & k \neq i \\
& & & \text{s.t.} & (l_h, r_h] \in S_{r_{i}}
\end{gathered}$$
Then we see that the following inequality must also be true 
$$\begin{gathered}
\sum_{(l_i, r_i] \in S_{r_{i}}} \hat{x}^{j-1}_{i} + \sum_{(l_k, r_k] \in S_{r_{k}}} \hat{x}^{j-1}_{k} \leq \sum_{(l_i, r_i] \in S_{r_{i}}} \hat{x}^{j}_{i} + \sum_{(l_k, r_k] \in S_{r_{k}}} \hat{x}^{j}_{k}
\end{gathered}$$
Which is equivalent to $$\sum_{i=1}^n \hat x_i^j
\ge \sum_{i=1}^n \hat
x_i^{j-1}$$
#### (6)

In the mapping from $\hat{x}^{j-1}$ to $\hat{x}^j$, we select at least one variable $\hat{x}^{j-1}_{h}$ and set its value to 1, replacing its original fractional value. Any other variable $\hat{x}^{j-1}_{i}$ that is fractional and overlaps with the interval of $\hat{x}^{j-1}_{h}$ is set to zero, while the remaining variables are directly mapped to $\hat{x}^{j}$. As a result, the number of variables with fractional values in $\hat{x}^{j-1}$, $|F_{j-1}|$, will always decrease by at least $1$ in the mapping from $\hat{x}^{j-1}$ to $\hat{x}^j$, and therefore,  $|F_{j}| < |F_{j-1}|$
