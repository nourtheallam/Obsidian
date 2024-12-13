### Question 1

The described circuit acts on the input state $\ket{00}$ in the following manner
$$\begin{gathered}
\ket{00} & \mapsto \ket{+}\ket{0}  = \left( \frac{\ket{0} + \ket{1}  }{\sqrt{ 2 }} \right)\ket{0} = \frac{1}{\sqrt{ 2 }}(\ket{0}\ket{0} + \ket{1}\ket{0}) & \text{(after applying ($H \otimes I$))} \\
& \mapsto \frac{1}{\sqrt{ 2 }}(\ket{0} \ket{0 \oplus f(0)} + \ket{1}\ket{0 \oplus f(1)}  ) =  \frac{1}{\sqrt{ 2 }}(\ket{0} \ket{f(0)} + \ket{1}\ket{f(1)}  ) & \text{(after applying $U_{f}$)} \\
& \mapsto \frac{1}{\sqrt{2}}(\ket{+} \ket{f(0)} + \ket{-}\ket{f(1)}) & \text{(after applying ($H \otimes I$))} \\
\end{gathered}$$
If $f$ is constant, then 
- If $f(0) = 0$, then $f(1) =  0$ and the state of the system becomes 
$$\begin{gathered}
\frac{1}{\sqrt{2}}(\ket{+} \ket{f(0)} + \ket{-}\ket{f(1)})\\
= \frac{1}{\sqrt{2}}(\ket{+} \ket{0} + \ket{-}\ket{0}) \\
= \frac{1}{\sqrt{ 2 }} \left( \frac{1}{\sqrt{ 2 }}  \ket{0}\ket{0} +  \frac{1}{\sqrt{ 2 }}  \ket{1}\ket{0} + \frac{1}{\sqrt{ 2 }}  \ket{0}\ket{0} -  \frac{1}{\sqrt{ 2 }}  \ket{1}\ket{0}\right)\\
=  \frac{1}{2}  \ket{0}\ket{0} +  \frac{1}{2}  \ket{1}\ket{0} + \frac{1}{2}  \ket{0}\ket{0} -  \frac{1}{2}  \ket{1}\ket{0} \\
=  \frac{1}{2}  \ket{0}\ket{0} + \frac{1}{2}  \ket{0}\ket{0}\\
= \ket{0}\ket{0}  
\end{gathered}$$
- If $f(0) = 1$ then $f(1) = 1$ and the state of the system becomes
$$\begin{gathered}
\frac{1}{2}  \ket{0}\ket{1} +  \frac{1}{2}  \ket{1}\ket{1} + \frac{1}{2}  \ket{0}\ket{1} -  \frac{1}{2}  \ket{1}\ket{1} \\
= \frac{1}{2}  \ket{0}\ket{1} + \frac{1}{2}  \ket{0}\ket{1} \\
\ket{0}\ket{1}  
\end{gathered}$$

If $f$ is balanced, then 
- If $f(0) = 0$, then $f(1) =  1$ and the state of the system becomes 
$$\begin{gathered}
\frac{1}{2}  \ket{0}\ket{0} +  \frac{1}{2}  \ket{1}\ket{0} + \frac{1}{2}  \ket{0}\ket{1} -  \frac{1}{2}  \ket{1}\ket{1} \\
\end{gathered}$$
- If $f(0) = 1$, then $f(1) =  0$ and the state of the system becomes 
$$\frac{1}{2}  \ket{0}\ket{1} +  \frac{1}{2}  \ket{1}\ket{1} + \frac{1}{2}  \ket{0}\ket{0} -  \frac{1}{2}  \ket{1}\ket{0}$$

As an example, if $f$ is constant and $f(0) = f(1) = 0$, then the correct answer occurs when the first qubit is measured in the computational basis as $0$. 

Assuming that it is equally likely for $f$ to be constant or balanced:

The probability the the first qubit is $0$ and that $f$ is balanced is $\frac{1}{2} \cdot \frac{1}{2}$ as in either values of $f$, there are two possible outcomes where the first qubit is $\ket{0}$, each with amplitude $\frac{1}{4}$. 

The probability that the first qubit is $0$ and that $f$ is constant is $1 \cdot \frac{1}{2}$ as the first qubit is always $\ket{0}$ in the constant case. 

Therefore, the probability that we obtain $0$ after measurement is $\frac{1}{4} + \frac{1}{2} = \frac{3}{4}$, which implies that the probability of obtaining the correct answer of our example is $\frac{3}{4}$. 

#### Question 2 

In an $n$ dimensional space, we can obtain a set of linearly independent elements whose size is at most $n$. Assume $n$ is the dimension of $\{ 0, s \} ^ \perp$, and assume that that $m \leq n$ (as the probability would be zero otherwise). 

At the first iteration, since the circuit outputs elements of $\{ 0, s \}$ uniformly at random, the probability of obtaining an element that is linearly independent is
$$\frac{2^n - 1}{2^n}$$
As we have not yet calculated any other elements, and we want to exclude the $0$ element from our calculation. 

In the next iteration, this probability becomes 

$$\frac{2^n - 2}{2^n}$$
And since we want to exclude the span of the element we obtained earlier, in which this span includes $2^1$ elements: the element itself and the $0$ element. 

In the following iteration, the probability becomes 
$$\frac{2^n - 2^2}{2^n}$$
As the span of the two elements we obtained includes their sum, each element on its own, and the $0$ element. Continuing with this logic, the size of the span of $k$ linearly-independent elements will always be $2^{k-1}$, and thus the probability of getting a linearly independent element at the $i^{th}$ iteration is 

$$\frac{2^{n} - 2^{i-1}}{2^n}$$
Which simplifies to 
$$1 - 2^{i-1- n}$$
Since we want to calculate the probability that $m$ consecutive iterations yield an element linearly independent from the ones we have obtained already, we multiply the probabilities of all the iterations together to obtain the desired probability

$$\prod^{m-1}_{i = 0} 1 - 2^{i-n}$$
(Note that I changed the iterations to be zero-indexed just to make this expression prettier).

