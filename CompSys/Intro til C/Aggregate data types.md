---
tags:
  - Programming
  - Abstraction
  - Types
---
There are four strategies for deriving data types. Two of them are called aggregate data types because they combine multiple instances of one or several other data types:

## Arrays

These combine items that all have the same base type
Arrays allow us to group objects of the same type into an [[Terminology#Encapsulation|encapsulating]] object.

Arrays and [[Pointers]] are closely related in C, and to explain them, we face a chicken and egg problem.
Arrays look like pointers in many contexts, and pointers refer to array objects.

**Arrays are not pointers.**
**An array in a condition evaluates to `true`.**
**There are array objects but no array values**
**Arrays can’t be compared.**
**Arrays can’t be assigned to.**

So, arrays can’t be [[Definitions#Operand|operands]] for the value operators in table 4.1, and there is no arithmetic declared on arrays themselves.
### Array declaration

```c
double a[4]; 
signed b[N];
```

![[Pasted image 20250908122205.png]]

The type that composes an array may itself again be an array, forming a multidimensional array.

The following two declarations declare variables of exactly the same type:
```c
double C[M][N]; 
double (D[M])[N];
```

![[Pasted image 20250908122312.png]]

`C[0][0]`, which is the same as `(C[0])[0]`, is also an object of type double

### Array operations
From table 4.2, we also know that there are only four operators left that work on arrays as object operators. And we know the operator `[]`.
There exist `array decay` operation, the `address` operator `&`, and the `sizeof` operator

### Length

There are two categories of arrays: constant-length arrays (CLAs) and variable-length arrays (VLAs)
**VLAs only can have default initializers**
**VLAs can’t be declared outside functions**

**The length of an FLA is determined by an integer constant expression or by an initializer**

Another important special case leads to an FLA: when there is no length specification at all. If the [] are left empty, the length of the array is determined from its initializer, if any:

```c
double E[] = { [3] = 42.0, [2] = 37.0, }; 
double F[] = { 22.0, 17.0, 1, 0.5, };
```

**If the length is not an integer constant expression, an array is a VLA**

The length of an array can be computed with the `sizeof` operator. That operator provides the size of any object, so the length of an array can be calculated using simple division.

Note also that the sizeof operator comes in two different syntactical forms. If applied to an object, as it is here, it does not need parentheses, but they would be needed if we applied it to a type.

**The length of an array `A` is `(sizeof A)/(sizeof A[0])`**

### Array as parameter

Because we cannot produce array values (takeaway 6.1.2 #2), array parameters cannot be passed by value, and thus array parameters as such would not make much sense.

**The innermost dimension of an array parameter to a function is lost**

**Don’t use the `sizeof` operator on array parameters to functions.**

**Array parameters behave as if the array is passed by reference**

Array as parameter:
```c
#include <stdio.h>

void swap_double(double a[static 2]) { 
	auto tmp = a[0]; 
	a[0] = a[1]; 
	a[1] = tmp; 
} 

int main(void) { 
	double A[2] = { 1.0, 2.0, }; 
	swap_double(A); 
	printf("A[0] = %g, A[1] = %g\n", A[0], A[1]); 
}
```

Here, swap_double(A) will act directly on array A and not on a copy. Therefore, the program will swap the values of the two elements of A.