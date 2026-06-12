# Bottom-Up Parsing

Builds syntax tree from the leaves going up.

- Search for parts of input string that match right-hand side of productions and rewrite these to left-hand side nonterminals, 
- [[Syntax tree]] is completed when the string has been rewritten by the inverse rightmost derivation to the start symbol. 

- Also called shift-reduce parsing: shifts input to stack, 
- then reduces right-hand side to left-hand side nonterminal, 
- until the start symbol is reached.

>[!tip]
>Uses a stack to keep track of the derivation sequence.

