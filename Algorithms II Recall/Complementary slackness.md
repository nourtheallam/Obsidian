---
~
---

Again, given the following primal LP and its dual 

$$
\begin{gathered}\text{Maximize } cx\\\begin{aligned}\text{s.t. }Ax &\le b\\x &\ge 0\end{aligned}
\\ \\
\text{Minimize } b^Ty\\\begin{aligned}\text{s.t. }A^Ty &\ge c^T\\y &\ge 0.\end{aligned}\end{gathered}
$$
We know from [[Strong LP duality]] that $c\hat{x} = b\hat{y}$ for ==optimal== solutions, we can use this fact and rearrange some terms to eventually obtain 
$$\left( \hat yA^T - c^T \right)\hat x= 0$$
Which, since none of these terms is negative, implies that 
$$ \text{Either }\hat{x} = 0 \quad  \text{or} \quad \hat{y}A^T= c \quad \tag{Primal}$$
We can also obtain 
$$ \text{Either }\hat{y} = 0 \quad  \text{or} \quad A\hat{x}= b \quad \tag{Dual}$$
In English, this means that $\hat{x}$ and $\hat{y}$ are optimal solutions **if and only if** primal and dual complementary slackness both hold. 