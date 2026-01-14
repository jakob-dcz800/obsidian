---
tags:
  - Computer
  - Math
  - Programming
---
## 4.1 Value operators

**Arithmetic operators do math. They operate on values.
Comparison operators compare values and return 0 or 1**

The `Form` column gives the syntactic form of the operation, where `@` represents the operator and `a` and possibly `b` denote values that serve as [[Definitions#Operand|operands]].

For arithmetic and bit operations, the type of the result is a type that reconciles the types of `a` and `b`.

For some of the operators, the Nick (nickname) column gives an alternative form of the operator or lists a combination of operators that has special meaning.

![[Pasted image 20250907204328.png]]

the operators `+` and `-` have unary variants. 
`-b` gives the negative of `b`: a value `a` such that `b + a` is `0`. 
`+a` simply provides the value of `a`.

```c
size_t c = (+a + -b)*2;
```
## 4.2 Object operators

**Assignment operators modify objects**

The Form column gives the syntactic form of the operation, where `@` represents the operator, `o` denotes an object, and a denotes a suitable additional value (if any) that serves as an operand.

An additional `*` in the Type column requires that the object `o` be addressable.

![[Pasted image 20250907205028.png]]

## 4.3 Type operators

These operators return an integer constant (ICE) of type `size_t`. They have function-like syntax with the operands in parentheses.

![[Pasted image 20250907205056.png]]