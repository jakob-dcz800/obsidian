
## Example

> $\sqrt{ 2 }$ is not rational

Assume towards a contradiction that $\sqrt{ 2 }$ is rational. 
Let Q be the (nonempty) [[Set laws|set]] of rationals that are equal to $\sqrt{ 2 }$. 
Let $\frac{a}{b}$ be the element in Q with minimum value of $|a| + |b|$. 

Now,
$$
\begin{align}
\sqrt{ 2 }  & =\frac{a}{b} \\
\iff 2 &  =\frac{a^{2}}{b^{2}} \\
\iff 2b^2 & =a^2
\end{align}
$$
From this, we can see that $a$ is an even number.
So $a=2c$ where $c \in \mathbb{N}$ is an arbitrary number with $c\neq 0$.
$$
\begin{align}
\iff 2b^2 & = (2c)^{2} \\
\iff b^2 & = 2c^{2} \\
\iff \sqrt{ 2 } & = \frac{b}{c}
\end{align}
$$
So $\frac{b}{c} \in Q$, but $|b| + |c| < |a| + |b|$ which contradicts the choice of $\frac{a}{b}$ .