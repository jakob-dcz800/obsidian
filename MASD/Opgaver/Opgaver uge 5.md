# 1

[[Probability]]

![[Pasted image 20251105175301.png]]$$
\begin{align}
P(\text{coffee}) & = \frac{7}{10} \\
P(\text{cake}) & = \frac{4}{10} \\
P(\text{coffee, cake})  & = \frac{2}{10}
\end{align}
$$
Hence:
[[Conditional probability]]
$$
\begin{align}
P(\text{coffee}|\text{cake}) & =
\frac{P(\text{coffee} \cap \text{cake})}{P(\text{cake})} \\
 & = \frac{2/10}{4/10} \\
 & = \frac{1}{2}
\end{align}
$$
# 2

[[Set laws]]

![[Pasted image 20251105180043.png]]

#### a)
$$
P(A|B)=\frac{P(A \cap B)}{P(B)}=\frac{0.2}{0.35}
= \frac{4}{7}
$$
#### b)
$$
P(C|B)=\frac{P(C \cap B)}{P(B)}=\frac{0.15}{0.35}
= \frac{3}{7}
$$
#### c) 
$$
P(B|A \cup C)=
\frac{P(B \cap (A \cup C))}{P(A \cup C)}
= \frac{0.2+0.05}{0.2+0.1+0.15}
= \frac{0.25}{0.7}
= \frac{5}{14}
$$
#### d)
$$
P(B|A, C)=P(B|A \cap C)
$$
$$
P(B|A \cap C) = 
\frac{P(A \cap B \cap C)}{P(A \cap C)}
= \frac{0.1}{0.2}
$$
$$
P(B|A ,C)
= \frac{P(B \cap A \cup C)}{P(A \cup C)}
= \frac{0.1+0.1+0.05}{0.1+0.2+0.15+0.1+0.1+0.05}
$$
I.e. NO

# 3
![[Pasted image 20251105200000.png]]

a. 
$$
P(a \leq X \leq b) = c(b-a)
$$
Since $P(0 \leq X \leq 10)$ let's say $c = \frac{1}{10}$, thus
$$
P(2\leq X\leq 5)=\frac{5-2}{10}=\frac{3}{10}
$$
b.
$$
\begin{align}
P(X \leq 2|X\leq 5) & = \frac{P(X \leq 2 \cap X\leq 5)}{P(X\leq 5)} \\
& =\frac{P(X \leq 2 \text{ and } X\leq 5)}{P(X\leq 5)} \\
& = \frac{P(X \leq 2)}{P(X\leq 5)} \\
& = \frac{P(0\leq X \leq 2)}{P(0 \leq X\leq 5)} \\
 & = \frac{2/10}{5/10}=0.4
\end{align}
$$
# 4

600 students

200 on campus
400 off campus
$$
\begin{align}
P(\text{lives on campus}) & = \frac{1}{3} \\
P(\text{lives off campus}) & = \frac{2}{3}
\end{align}
$$
120 A's in total


$$
P(\text{gets an A}) = \frac{120}{600} = \frac{1}{5}
$$
80 lived off campus and got A's
Probability of getting an A and NOT living on Campus:
$$
P(A \cap C^c)= \frac{80}{600} = \frac{2}{15}
$$
Therefore
$$
P(A \cap C) = P(A)-P(A-C^c)
= \frac{1}{5} - \frac{2}{15} =\frac{1}{15}
$$
And
$$
P(A)\cdot P(C)
= \frac{1}{5} \cdot \frac{1}{3}=\frac{1}{15}
$$
Therefore they're **independent**.