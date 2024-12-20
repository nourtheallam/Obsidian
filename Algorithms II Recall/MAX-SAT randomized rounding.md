
##### Ideas

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
Where: 
- $x_{j}$ corresponds to a boolean variable while $y_{i}$ corresponds to a clause.
- We say $\leq y_{i}$ because a clause is satisfied when **at least one** variable is.

We could either use:
	**LP rounding:** expectation value of  $(1 - \frac{1}{e}) \cdot OPT$
		Works well if size of each clause is very **small**.
	**Naive guessing:** expectation value of $\frac{1}{2}\cdot OPT$
		This is because every literal is false with probability $\frac{1}{2}$. 
		If there are $k$ literals in each clause, then the **probability of the entire clause being false is** $$\frac{1}{2^k}$$ because they would all have to fail.
		Therefore, the **larger the clause,** the lower this probability is.

What we actually do, **is apply either with a $\frac{1}{2}$ probability t**hat yields an expected value of $\frac{3}{4}\cdot OPT$. 

##### Expected values

**LP rounding** is $\geq \left( 1 - \left( 1 - \frac{1}{k} \right)^k \right)\cdot OPT$ assuming all clauses have size $\leq k$: 

- Given the following theorem
![[Pasted image 20241219210527.png]]
- We can simplify as follows: 
![[Pasted image 20241219210605.png]]
![[Pasted image 20241219210633.png]]
![[Pasted image 20241219210720.png]]
- Then further simplify as 
![[Pasted image 20241219211023.png]]

The **expected value of our algorithm** is $\frac{3}{4}\cdot OPT$:

![[Pasted image 20241219211131.png]]

