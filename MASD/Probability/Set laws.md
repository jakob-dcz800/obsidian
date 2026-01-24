# De Morgans' law

$$
(A \cup B)^c = \overline{A \cup B} = A^c \cap B^c
$$
# Distributive law

$$
\begin{align}
A \cup (B \cap C)  & = (A \cup B)\cap(A \cup C) \\
A \cap (B \cup C)  & = (A \cap B)\cup(A \cap C)
\end{align}
$$
## Symbols

[[Serier og sæt|Set]] A is a **subset** of set B if every element of A is also an element of B. We write $A⊂B$, where "⊂" indicates "subset." Equivalently, we say B is a **superset** of A, or $B ⊃ A$.

Two sets are equal if they have the exact same elements. Thus, A=B if and only if A⊂B and B⊂A. For example, {1,2,3}={3,2,1}, and {a,a,b}={a,b}. The set with no elements, i.e., ∅={} is the **null set** or the **empty set**. For any set A, ∅⊂A.

## The universal set
The **universal set** is the set of all things that we could possibly consider in the context we are studying. Thus every set A is a subset of the universal set. In this book, we often denote the universal set by S (As we will see, in the language of probability theory, the universal set is called the _sample space_.) For example, if we are discussing rolling of a die, our universal set may be defined as S={1,2,3,4,5,6}, or if we are discussing tossing of a coin once, our universal set might be S={H,T} (H for heads and T for tails).

# Cartesian product

A **Cartesian product** of two sets A and B, written as A×B, is the set containing **ordered** pairs from A and B. That is, if C=A×B, then each element of C is of the form (x,y), where x∈A and y∈B:

$A×B=\{(x,y)|x∈A \land y∈B\}$.

For example, if A={1,2,3} and B={H,T}, then

$A×B={(1,H),(1,T),(2,H),(2,T),(3,H),(3,T)}$

Note that here the pairs are ordered, so for example, $(1,H)≠(H,1)$. Thus A×B is **not** the same as B×A.