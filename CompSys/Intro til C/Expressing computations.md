---
tags:
  - Programming
  - Fundemental
---
## Operands and operators

### size_t
When the result of an [[Numbers#Representation of integers|integer]] expression (of type `size_t`) falls out of range, it causes an **arithmetic overflow**.

Division with `/` counts how many times the integer fits within the other. 
`a == (a/b)*b + (a%b)`
Division by zero is forbidden.

*Unsigned / and % are only well defined if the second operand is not 0*
When a value overflows it 'wraps' around the range of possible values. 
This means for `size_t` values, `SIZE_MAX + 1` is equal to `0`, and `0 - 1` is equal to `SIZE_MAX`.

### Logical operators

The operators && and || have a particular property called short-circuit evaluation .
This barbaric term denotes the fact that the evaluation of the second operand is omitted if it is not necessary for the result of the operation.

```c
// This never divides by 0. 
if (b != 0 && ((a/b) > 1)) { 
	++x; 
}
```

```c
if (b) { // 0 == false
// This never divides by 0. 
	if (a/b > 1) { 
		++x; 
	} 
}
```

## The comma

The comma `(,)` evaluates its operands in order, and the result is the value of the right operand.
`(f(a), f(b))` first evaluates `f(a)` and then `f(b)`; the result is the value of `f(b)`.

 `A[i, j]` is not a two-dimensional index for matrix `A`, but results in `A[j]`.