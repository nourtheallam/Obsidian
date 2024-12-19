
Given a boolean formula, we want to satisfy as many clauses as possible. We writ the ILP for this by defining: 
$$
\begin{gathered}
C_{i}^+ = \text{ unnegated variables in clause $C_{i}$} \\
C_{i}^- = \text{ negated variables in clause $C_{i}$}
\end{gathered}
$$
And the following ILP: 
$$
\begin{gathered}
\max{\sum_{i = 1}^m w_{i}y_{i}} \\ 
\text{s.t.} \sum_{x_{j} \in C_{i}^+} x_{j} + \sum_{x_{j} \in c_{i}^-}(1-x_{j}) \geq y_{i} \\
x_{j }\in \{ 0,1 \}\\
y_{i} \in \{ 0,1 \}
\end{gathered}
$$
Where $x_{j}$ corresponds to a boolean variable while $y_{i}$ corresponds to a clause. 