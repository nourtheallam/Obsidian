Given the following primal LP and its dual 

$$
\begin{gathered}\text{Maximize } cx\\\begin{aligned}\text{s.t. }Ax &\le b\\x &\ge 0\end{aligned}
\\ \\
\text{Minimize } b^Ty\\\begin{aligned}\text{s.t. }A^Ty &\ge c^T\\y &\ge 0.\end{aligned}\end{gathered}
$$

We observe that 
$$
A^Ty \geq c^T \implies y^TA \geq c \implies cx \leq (y^TA)x
$$
And since 
$$Ax \leq b$$
This further implies that

$$y^TAx \leq y^Tb$$
Which finally gives us
$$cx \leq y^Tb$$

In English, this means that **any feasible solution of the primal (assuming it's a maximization problem) will always have an objective function value that is $\leq$ that of the a feasible solution of its dual**.