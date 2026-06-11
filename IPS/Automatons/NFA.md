# NFA

> [!DEFINITION] What is it?
> Nondeterministic Finite Automata
> Used to decide if the input string is a member of the language $L$:
> - Starting state
> - final states where execution ends if the input ∈ L, (accepting states),

![[Pasted image 20260611114048.png]]

A stepping stone towards implementing [[regular expressions]].
It is **nondeterministic** (there are many choices one can make to reach the same result)

Can be transformed to [[DFA]], which efficiently executes on real hardware

![[Pasted image 20260608163439.png|258]]
## Definition

An abstract machine with a finite number of 
- states: initial, final, intermediate, 
- transitions between states: labelled with a char $c \in \sum$ or with $\epsilon$

## Transitions

Used to reach a new state from the current state,
- either follow an $ϵ$ transition (no char of input is consumed) or
- consume the current char $c$ of the input and follow a transition labelled with $c$ from the current state (if such transition exists)

### Membership 
If there is a *possibility* to reach an accepting state after all input characters were consumed then $\text{input} ∈ L$ (input is in language).
*Possibility* refers to choices/guesses on what transition to follow!

>[!TIP] Acceptance
>If there exist a sequence of choices reaching an accepting state at the end of the input string.

### Notation for transitions:

$s_{i}^{c}s_{j} \in T$: may transition from state $s_i$ to $s_j$ on consuming char $c$
$s_{i}^{\epsilon}s_{j} \in T$: may freely transition from state $s_i$ to $s_j$
	(without consuming an input char)
Several options may exist, hence T is a relation.
**Acceptance**: if there exist a sequence of choices reaching an accepting state at the end of the input string.

# Converting Regex to NFA

Make a sort of tree of the expression.
A single final state is added at the end of the construction.

![[Pasted image 20260608161325.png]]

## Example 1

$$
(a\cdot b|a)\cdot(b|ε)
$$
![[Pasted image 20260608161624.png|412]]

## Example 2

![[Pasted image 20260608161728.png]]

