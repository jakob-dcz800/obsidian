---
tags:
  - Functions
  - Programming
---
The main reasons motivating the concept of functions are modularity and code factorization:

• Functions avoid code repetition. In particular, they avoid easily introduced copy-and-paste errors and spare the effort of editing in multiple places if you modify a piece of functionality. Thereby, functions increase readability and maintainability. 

• Use of functions decreases compilation times. A given code snippet that we encapsulate in a function is compiled only once, not at each point where it is used. 

• Functions simplify future code reuse. Once we have extracted code into a function that provides certain functionality, it can easily be applied in other places that we did not even think of when implementing the function. 

• Functions provide clear interfaces. Function arguments and return types clearly specify the origin and type of data that flows into and out of a computation. Additionally, functions allow us to specify invariants for a computation: pre- and post-conditions. 

• Functions provide a natural way to formulate algorithms that use a “stack” of intermediate values.

## Simple functions

All the functions we have seen so far have a **prototype**: their declaration and definition, including a parameter type-list and a return type.

```c
bool leapyear(unsigned year) {
	/* All years that are divisible by 4 are leap years,
	unless they start a new century, provided they
	are not divisible by 400. */
	return !(year % 4) && ((year % 100) || !(year % 400));
 }
```


A declaration of that function (without a definition) could look as follows: 
```c
bool leapyear(unsigned year);
```

we could even omit the name of the parameter and/or add the storage specifier `extern`:
```c
extern bool leapyear(unsigned);
```

Called like this:
```c
extern double fbar(double);
...
double fbar2 = fbar(2)/2;
```

There are two special conventions that use the keyword void: 
• If the function is to be called with no parameter, the list is replaced by the keyword `void`, like `main` in our very first example (listing 1.1).
• If the function doesn’t return a value, the return type is given as `void`, for example `swap_double`

**All functions must have prototypes**

If the type of the function is void, the return (without expression) can even be omitted.

**Reaching the end of the body of a function is equivalent to a return statement without an expression.**

Reaching the end of the body of a function is only allowed for void functions.

## Main

Its prototype is enforced by the C standard, but it is implemented by the programmer

First, to suit different needs, it has several prototypes, one of which must be implemented. Two should always be possible:

```c
int main(void);
int main(int argc, char* argv[argc+1]);
```

**Use `EXIT_SUCCESS` and `EXIT_FAILURE` as return values for main.**

**Reaching the end of `main` is equivalent to a return with `EXIT_SUCCESS`.**

**Calling `exit(s)` is equivalent to the evaluation of `return s` in `main`.**

### Invocation

`argv[0]` points to the name of the program invocation.
`argv[argc]` is a [[Pointers#Null pointer|null pointer]]

## Recursion

**Each function call has its own copy of local variables and functions can be called recursively**

Local variables are only visible and alive until we leave the function, either via an explicit return or because execution falls out of the last enclosing brace of the function’s body.

Their identifiers (names) don’t conflict with other similar identifiers in other functions, and once we leave the function, all the mess we leave behind is cleaned up.

A function that directly or indirectly calls itself is called recursive, and the concept is called recursion.

**Multiple recursion may lead to exponential computation times**
### Example
As a first example, we will look at an implementation of Euclid’s algorithm to compute the greatest common divisor (gcd) of two numbers:

```c
inline size_t gcd2(size_t a, size_t b) [[__unsequenced__]] {
	assert(a <= b);
	if (!a) return b;
	size_t r = b % a;
	return gcd2(r, a);
}

```

Using the `assert` macro from . This would abort the program with an informative message if the function was called with arguments that didn’t satisfy that condition.

**Make all preconditions for a function explicit.**

In a recursive function, first check the termination condition. A missing termination check leads to infinite recursion.

**Ensure the preconditions of a recursive function in a wrapper function.**

```c
inline size_t gcd(size_t a, size_t b) [[__unsequenced__]] {
	assert(a);
	assert(b);
	if (a < b)
		return gcd2(a, b);
	else
		return gcd2(b, a);
}

```

This avoids having to check the precondition at each recursive call: the `assert` macro is such that it can be disabled in the final production object file.

#### Recursive call gcd2(18, 30)

![[Pasted image 20250908135616.png]]

### Example 2: Fibonacci

![[Pasted image 20250908135849.png]]
