---
~
---
**Branching and [[Kernelization]]:** a problem can have a very efficient branching algorithm but not a small kernel, but a small kernel without an efficient branching algorithm is not very useful.

The main idea behind branching is finding an **elementary choice** that we make in constructing a solution to the problem. Earlier choices influence later choices, and we just have to argue that we don't miss any optimal solutions.

\textbf{([[Branching vector]])} if an input of size $n$ makes $t \geq 2$ choices, each bounded by $n- b_1, n - b_2, \ldots, n - b_t$, then the [[Branching vector]] is $(b_1, b_2, \ldots, b_t)$.

A branching algorithm makes $O(c^n)$ recsurive calls where $b$ is the maximum of the [[Branching vector]] and $c$ is the smallest real root of $x^b - \sum_{i - 1}6{t}x^{b - bi}$ ($c$ is called the \textbf{[[Branching number]]}).