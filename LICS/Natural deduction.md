# Natural deduction


Natural deduction has a collection of proof rules. They allow us to infer formulas from other formulas. By applying these rules in succession, we may infer a conclusion from a set of premises.

Suppose we have a set of formulas $φ_1, φ_2, φ_3, . . . , φ_n,$ which we will call premises, and another formula, $ψ$, which we will call a conclusion.

>[!Tip] e and i
>Elimination rules are denoted by $e_{n}$
>Introduction rules are denoted by $i$

## Sequents

By applying proof rules to the premises, we hope to get some more formulas, and by applying more proof rules to those, to eventually obtain the conclusion. This intention we denote by
$$
φ_1, φ_2, . . . , φ_n \vdash ψ
$$
![[Pasted image 20261116203800.png]]
From the premises Phi... it is *possible* to prove Psi

### Example
$$
p ∧ ¬q → r, ¬r, p \vdash q
$$
## Inference rules for natural deduction
There can be zero or more premises in an inference rule.
$$
\frac{\text{premise}}{\text{conclusion}} \text{name}
$$
### Conjunction
Allows us to conclude $φ ∧ ψ$, given that we have already concluded $φ$ and $ψ$ separately.
$$
\frac{\phi \qquad \psi}{\phi \land \psi}\land i.

$$
If these premises are true, their conjunction is true.
An *and-introduction* is written as $\land i$
The rules for and-elimination are these two:

$$
\frac{\phi \land \psi}{\phi} \land e_{1}
\qquad
\frac{\phi \land \psi}{\psi} \land e_{2}
$$
The rule $∧e_1$ says: if you have a proof of $φ ∧ ψ$, then by applying this rule you can get a proof of $φ$. The rule ∧e2 says the same thing, but allows you to conclude $ψ$ instead.

#### Example

$$
p ∧ q, r \vdash q ∧ r
$$
Premise: $p \land q$
Premise: $r$
Conclusion: $q \land r$

Apply a suitable sequence of proof rules.
In this case, we apply $∧e2$ to the first premise, giving us $q$.
Then we apply $∧i$ to this $q$ and to the second premise, $r$, giving us $q ∧ r$ 
We also usually number all the lines, and write in the justification for each line, producing this:

#### Example 1

| 1   | $p \land q$ | premise         |
| --- | ----------- | --------------- |
| 2   | $r$         | premise         |
| 3   | $q$         | $\land e_{2}$ 1 |
| 4   | $q \land r$ | $\land i$ 2, 3  |
#### Example 2
$$
(p ∧ q) ∧ r, s ∧ t \vdash q ∧ s
$$

	
| 1   | $(p ∧ q) ∧ r$ | premise                  |
| --- | ------------- | ------------------------ |
| 2   | $s ∧ t$       | premise                  |
| 3   | $q \land r$   | $\land e_{2}$ 1 (partly) |
| 4   | $q$           | $\land e_{1}$ 3          |
| 5   | $s$           | $\land e_{1}$ 2          |
| 6   | $q \land s$   | $\land i$ 4, 5           |

Can also be written as a tree:

$$
\frac{\frac{p \land q}{q} \land e_{2}\qquad r}{q \land r} \land i
$$
## Double negation
$$
\frac{\neg \neg \phi}{\phi} \neg \neg e\qquad \frac{\phi}{\neg \neg \phi} \neg \neg i
$$
#### Examples
![[Pasted image 20261116184947.png]]

## Eliminating implication
Modus ponens
$$
\frac{\phi\qquad\phi \to \psi}{\psi} \to MP / \to e
$$
## Modus tollens
$$
\frac{\phi \to \psi\qquad \neg \psi}{\neg \phi} \text{MT}
$$
> *‘If Abraham Lincoln was Ethiopian, then he was African. Abraham Lincoln was not African; therefore he was not Ethiopian.’*

![[Pasted image 20261116191116.png]]

## Implies introduction

$$
\frac{
\boxed{
\begin{matrix}
\phi\\
\vdots\\
\psi
\end{matrix}
}
}{
\phi \rightarrow \psi
}
\rightarrow i.
$$

## Disjunction introduction

![[Pasted image 20261120163756.png]]


## Disjunction elimination
![[Pasted image 20261120163814.png]]



# Exercises

![[Pasted image 20261120171100.png]]
