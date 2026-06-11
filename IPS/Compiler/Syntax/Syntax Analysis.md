# Syntax Analysis

> Aka. parsing

recombine tokens from the [[Lexical Analysis]]
Not back into a list of characters, but into something that reflects the structure of the text
This “something” is typically a data structure called the [[syntax tree]] of the text

In addition to finding the structure of the input text, the syntax analysis must also reject invalid texts by reporting **syntax errors**.

As [[syntax analysis]] is less local in nature than [[lexical analysis]], more advanced methods are required. We, however, use the same basic strategy: A notation suitable for human understanding and algebraic manipulation is transformed into a machinelike low-level notation suitable for efficient execution. This process is called parser generation.

The notation we use for human manipulation is context-free grammars, which is a recursive notation for describing sets of strings and imposing a structure on each such string.