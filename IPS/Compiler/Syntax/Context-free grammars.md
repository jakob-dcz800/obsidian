# Context-free grammars

Like [[regular expressions]], context-free grammars describe sets of strings, i.e., languages

>[!QUESTION]
>What is the right-hand side of a production?
>See [slides](file:///C:/Users/jakis/Documents/Datalogi/IPS/lectures/9-SyntaxAn.pdf) page 33/61

## Terminals
A context-free grammar also defines structure on the strings in the language it defines. 
A language is defined over some alphabet, for example the set of tokens produced by a lexer or the set of alphanumeric characters. 
The symbols in the alphabet are called **terminals**.

A context-free grammar recursively defines several sets of strings.
Each set is denoted by a name, which is called a **nonterminal**.
The set of nonterminals is [[Disjoint sets|disjoint]] from the set of terminals.

## Ambiguity

The grammar is said to be ambiguous if there exists a word that can be derived in two ways corresponding to different syntax trees

![[Pasted image 20260611172901.png]]

> [!TIP] You can't decide if a grammar is ambiguous
> Ambiguity is in general undecidable, i.e., there is no method that for any grammar can answer the question “Is this grammar ambiguous?”
> However, in many cases, it is not difficult to detect & prove ambiguity.
>For example, 
>$$N → NαN \mid β$$
> is ambiguous, where α and β are any sequences of grammar symbols.
> $N$ exists both right and left of $\alpha$
### Example
![[Pasted image 20260611173451.png|174]]Very ambiguous grammar

## Defining Operator Associativity

- Left-associative if expression $x ⊕ y ⊕ z$ should be grouped from left to right: 
$$
(x ⊕ y) ⊕ z
$$
	- + and /

- Right-associative if expression $x ⊕ y ⊕ z$ should be grouped from right to left: 
$$
x ⊕ (y ⊕ z)
$$
	- exponentiation ^, assignment :=
- Non-associative if expressions such as $x ⊕ y ⊕ z$ are disallowed
	- relational < and =
- Associative if both left-to-right and right-to-left groupings lead to the same result (a semantic property).


## Resolving Operator Associativity by Recursion

![[Pasted image 20260611174549.png]]

### Equal precedence level
![[Pasted image 20260611174829.png]]

If two productions have different precedence levels, do **not** put them on the same non-terminal:

![[Pasted image 20260611174945.png]]

![[Pasted image 20260611175020.png]]

## Resolving Operator Precedence

> At grammar level: This can be accomplished by introducing one nonterminal for each level of precedence.

![[Pasted image 20260611175208.png]]

Finally, one can resolve associativity as discussed [[#Resolving Operator Associativity by Recursion|before]]
>At grammar level: This can be accomplished by introducing new nonterminals that establish associativity by recursion type:

![[Pasted image 20260611175315.png]]


