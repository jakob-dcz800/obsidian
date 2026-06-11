# Context-free grammars

Like [[regular expressions]], context-free grammars describe sets of strings, i.e., languages

## Terminals
A context-free grammar also defines structure on the strings in the language it defines. 
A language is defined over some alphabet, for example the set of tokens produced by a lexer or the set of alphanumeric characters. 
The symbols in the alphabet are called **terminals**.

A context-free grammar recursively defines several sets of strings.
Each set is denoted by a name, which is called a **nonterminal**.
The set of nonterminals is [[Disjoint sets|disjoint]] from the set of terminals.