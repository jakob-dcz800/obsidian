
## Definition

The probability of $A$ given $B$
$$
P(A\mid B) = \frac{P(A \cap B)}{P(B)}, \text{ when } P(B)>0
$$
![[Pasted image 20251006163459.png]]
## Explanation

There is $0.3$ chance that it rains: $P(rain)=0.3$
There is $0.9$ chance that it rains if it is cloudy: $P(rain|clouds)=0.9$

## Example

### 1

Example. Roll a fair die, what is the probability that the outcome is an even
number given it was less than or equal to 3, i.e.,
$$
\begin{align}
A & =\set{2, 4, 6} \\
B & =\set{1, 2, 3} \\
\end{align}
$$
Note that
$$
\frac{|A \cap B|}{|B|} = \frac{\frac{|A \cap B|}{|S|}}{\frac{|B|}{|S|}}
= \frac{P(A \cap B)}{P(B)}
$$
# Axioms

- For any event $A$, $P(A \mid B) \geq 0$
- Conditional probability of $B$ given $B$ is $P(B\mid B)=1$
- If $A_{1}, A_{2},\dots$ are [[Serier og sæt#Disjoint sets|disjoint events]], then 
$$
P(A_{1}\cup A_{2}\cup\dots\mid B )
= 
P(A_{1}|B)+
P(A_{2}|B)+
P(A_{3}|B)+
\dots
$$
![[Pasted image 20251006163956.png]]

## Example

![[Pasted image 20251006164156.png]]

## Special cases

- $A$ and $B$ are [[Serier og sæt#Disjoint sets|disjoint]], then
$$
P(A\mid B) = \frac{P(A \cap B)}{P(B)}=\frac{0}{P(B)}=0
$$
![[Pasted image 20251006164508.png]]

- $A \subset B$, then
$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
= \frac{P(A)}{P(B)}
$$
![[Pasted image 20251006164600.png]]

- $B \subset A$, then
$$
P(A \mid B) = 
\frac{P(A \cap B)}{P(B)}=\frac{P(B)}{P(B)}=1
$$
![[Pasted image 20251006164701.png]]