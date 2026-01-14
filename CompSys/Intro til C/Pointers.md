---
tags:
  - Programming
  - Computer
---
## Definition

Entities that refer to an object in [[CompSys/Hardware/Memory hierarchy|memory]].

**Opaque data type**
This means we will only be able to deal with pointers through the operations that the [[C language]] allows for them

One particular property of pointers that distinguishes them from other variables is their state.
**Pointers are valid, null, or invalid.**

We now have seen the concept of pointers pop up in several places, in particular as a `void*` argument and return type and as char `const*const` to manipulate references to [[Strings|string literals]].

**Always initialize pointers**
Their main property is that they do not directly contain the information that we are interested in: rather, they refer, or point, to the [[Values and data|data]]. The pointer points to an address within the [[Addressing#Virtual addressing|virtual address space]]

```c
char const*const p2string = "some text";
```

![[Pasted image 20250908124955.png]]

Compare this to the earlier [[Aggregate data types#Arrays|array]] jay0, which itself contains all the characters of the string that we want it to represent: 
```c
char jay0[] = "jay";
```
![[Pasted image 20250908125027.png]]

### Example

```c
char c = 'k'; // assign variable that gets stored in memory
&c; // is the value of the address (0x07 for example)
char* p = &c; // is the actual pointer stored as a variable

```

## Updating a pointer

```c
#include<stdio.h>

int main(void) {
	int x = 2;
	printf("x: %d\n", x); // -> 2
	printf("p: %p\n", (void*)&x); // cast to void ptr -> [address]
	// (void*) tells compiler, that theres a ptr to something
	
	int* px = &x;
	
	// x has type T
	// &x has type T*
	printf("x: %d\n", (void*)px); // address of x
	printf("p: %p\n", (void*)&px); // address of px
	
	// go to the address that is pointed to by pointer and assign 5 
	*px = 5; // dereferencing. x is now 5
	
	printf("x: %d\n", x)
	
}
```
## Null pointer

**Initialization or assignment with `nullptr` makes a pointer null.**
Take the following as an example: 
```c
char const*const p2nothing = nullptr;
```
![[Pasted image 20250908125203.png]]

This is different from the empty string `""`

**In logical expressions, pointers evaluate to false if they are null.** 
Note that such tests can’t distinguish valid pointers from invalid ones. So, the really “bad” state of a pointer is invalid, since this state is not observable.

**Invalid pointers lead to program failure**
An example of an invalid pointer could look like this:
```c
char const*const p2invalid;
```

![[Pasted image 20250908125326.png]]

## Symbols

| Symbol | Meaning                                    |
| ------ | ------------------------------------------ |
| `&B`   | The address of `B`                         |
| `*C`   | The value pointed to by `C`                |
| `**D`  | The value at the address pointed to by `D` |
| `*&E`  | The value of `E`                           |
