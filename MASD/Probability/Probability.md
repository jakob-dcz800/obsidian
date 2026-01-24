
## Definition

$P(A):$ the portion of times that event $A$ is observed in a large number of runs of the [[Experiment|experiment]].

If we have an [[Experiment#Random experiments|event]] $A$, we say that the probability of A is $P(A)$
I.e. the probability of a collection of possible outcomes.

## Axioms

A probability measure $P(.)$ is a function that maps events in the [[Sample space]] $S$ to real numbers.
Such that:
- For any event $A$, $P(A)\geq 0$
- Probability of the sample space $S$ is $P(S)= 1$
- For any countable collection of sets $A_{1},A_{2},A_{3},\dots$ of disjoint events
$$
P(A_{1}\cup A_{2} \cup A_{3}\dots)=
P(A_{1})+
P(A_{2})+
P(A_{3})+\dots
$$
### Example 1
Rolling a fair die has equal chance for each number:
$$
\begin{align}
P(
\set{1}\cup
\set{2}\cup\dots\cup
\set{6}
) & 
=
P(\set{1})+
P(\set{2})+\dots+
P(\set{6}) \\
& = P(S) \\
 & =P(\set{1, 2, 3, 4, 5, 6}) \\
 & = 1 
\end{align}
$$
Each outcome is equally likely because:
![[Pasted image 20251006161011.png]]

The probability of A is the number of elements in A over number of elements in S
### Example 2

![[Pasted image 20251006161053.png]]

### Example 3

$P(Ø)=0$ because:
$$
P(Ø)=P(S^c)=1-P(S)=1-1=0
$$
### Example 4

$P(A\leq 1$ because:
$$
P(A)=1-P(A^c) \implies P(A)\leq 1, P(A^c) \geq 0
$$
## Law of total probability

![[Pasted image 20251006165737.png]]

$$
\begin{align}
A_{i} & = A \cap B_{i} \\
P(A) & = P(A_{1})+P(A_{2})+\dots \\
P(A) & = \sum^m_{i=1}P(A_{i})=\sum^m_{i=1}P(A\cap B_{i}) \\
P(A \mid B_{i})  & = \frac{P(A \cap B_{i})}{P(B_{i})} \implies
P(A|B_{i})P(B_{i})
\end{align}
$$

### Example 1

Three coins are in a bag:
a) Coin 1: probability of heads is $0.9$. $P(H|C1) = 0.9$
b) Coin 2: probability of heads is $0.6$. $P(H|C2) =0.6$
c) Coin 3: probability of heads is $0.3$. $P(H|C3) = 0.3$
I draw a coin at random and toss it. What is the probability of heads?

Each coin is equally likely, so $P(C_1) = P(C_2) = P(C_3) = \tfrac{1}{3}$ 
$P(H) = \frac{1}{3}(0.9 + 0.6 + 0.3) = \frac{1}{3}(1.8) = 0.6$

**Answer:** $P(H) = 0.6$ 

# Bayes rule

![[Pasted image 20251006170446.png]]![[Pasted image 20251006170522.png]]


### Example 1
In the previous problem, suppose that we know the result is heads; what is the probability that Coin 1 was chosen?

We want $P(C_1 \mid H)$
By **[[Bayesian learning|Bayes’ rule]]**:

$P(C_1 \mid H) = \frac{P(H \mid C_1) P(C_1)}{P(H)}$  

From the problem:
$P(H \mid C_1) = 0.9$
$P(C_1) = \tfrac{1}{3}$
$P(H) = 0.6$ (from before)

Now compute:

$P(C_1 \mid H) = \frac{0.9 \times \tfrac{1}{3}}{0.6}$  
$= \frac{0.3}{0.6}$  
$= 0.5$  

**Answer:** $P(C_1 \mid H) = 0.5$

### Example 2

A library software recommends books based on user preferences. Out of $1200$ books, $800$ are
recommended by the system. Of the recommended books, $600$ are liked by the users.
However, not all liked books are recommended by the software. In fact, $2/3$ of all liked books are recommended by the software. 
If a user likes a specific book, what is the probability that this book was recommended by the software? (Hint: Use [[Probability#Bayes rule|Bayes Theorem]])

![[Pasted image 20251006171013.png]]
