## Definition

Entities that refer to an object in memory.

**Opaque data type**
This means we will only be able to deal with pointers through the operations that the C language allows for them

One particular property of pointers that distinguishes them from other variables is their state.
**Pointers are valid, null, or invalid.**

We now have seen the concept of pointers pop up in several places, in particular as a `void*` argument and return type and as char `const*const` to manipulate references to string literals.

**Always initialize pointers**
Their main property is that they do not directly contain the information that we are interested in: rather, they refer, or point, to the data.

```c
char const*const p2string = "some text";
```

![[Pasted image 20250908124955.png]]

Compare this to the earlier array jay0, which itself contains all the characters of the string that we want it to represent: 
```c
char jay0[] = "jay";
```
![[Pasted image 20250908125027.png]]

### Null pointer

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