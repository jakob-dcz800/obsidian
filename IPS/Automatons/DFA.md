# DFA

>[!DEFINITION] Definition
>Let Σ be an alphabet of (input) characters. A DFA consists of 
>- The alphabet $Σ$ of input characters, 
>- A finite set $S$ of states: 
>- A start (initial) state $s_0 ∈ S$ 
>- A set of final (accepting) states $F ⊆ S$, and 
>- A function **move** : $S × Σ ⇀ S$ describing state transitions. 
>	($⇀$ means that $S$ may be *undefined*)

## Move

$$
\text{move}(s_1,c) = s_2
$$

If in state $s_1$ with input character $c$, go to $s_2$

> [!Note] 
> $\text{move}(s_1,c)$ can be undefined, i.e., is a partial function.

No $ϵ$ transitions, no 2 identically labelled transitions from a state.

>[!IMPORTANT] Important
>**At most one** transition possible from any state, uniquely identified by current state & input char.

