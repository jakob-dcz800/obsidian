## Basic types

Basic types like `int` and `double` come built-in while `bool`  and  `size_t` fx. must be included in the header.

This second level is organized by type semantics, specifying what properties a particular type brings to the programmer.

All basic values in C are numbers, **but there are different kinds of number**s
As a principal distinction, we have two different classes of numbers, each with two subclasses each:
1. unsigned 
	1. [[Numbers|integers]]
	2. signed integers
2. real 
	1. [[Floating points|floating-point numbers]]
	2. complex floating-point numbers
Each of these four classes contains several [[types]]. They differ according to their [[Values and data#Precision|precision]] , which determines the valid range of values that are allowed for a particular [[Abstract state machine#Type|type]]

![[Pasted image 20250907220944.png]]

Types with a gray background don’t allow for [[Operations#4.1 Value operators|arithmetic]]; they are promoted before doing arithmetic.
Type `char` is special since it can be unsigned or signed, depending on the platform. 
*All* types in this table are considered to be distinct types, even if they have the same class and precision.

## Best practice

Natural numbers $\mathbb{N}$:
- Use `size_t` for sizes, cardinalities, or ordinal numbers.
- Use `unsigned` for small quantities that can’t be negative
- Use `signed` for small quantities that bear a sign
- Use `ptrdiff_t` for large differences that bear a sign.

Rational numbers $\mathbb{R}$:
- Use `double` for [[Floating point operations|floating-point calculations]].
- Use `double complex` for complex calculations.

![[Pasted image 20250907221857.png]]
The [[C language|C]] standard defines a lot of other types, among them other arithmetic types that model special use cases.

## Specifying values


| Literal    | Explanation                         |                                                                               |
| ---------- | ----------------------------------- | ----------------------------------------------------------------------------- |
| 123        | Decimal integer literal             |                                                                               |
| 077        | Octal integer literal (don't use)   |                                                                               |
| 0xFFFF     | Hexadecimal integer literal         |                                                                               |
| 0b1010     | Binary integer literal              |                                                                               |
| 1.7E-13    | Decimal floating-point literals     |                                                                               |
| 0x1.7aP-13 | Hexadecimal floating-point literals |                                                                               |
| ’a’        | Integer character literal           | ’a’ corresponds to the integer code for the character a of the Latin alphabet |
| "hello"    | String literals                     |                                                                               |
All literals except the last are numerical constants: they specify numbers.
String literals are an exception and can be used to specify text that is known at compile time.

**Numerical literals are never negative.**

When you write `-34`, `'-'` is actually the negate operator and the leading sign is not considered part of the number.
The minus sign in the exponent **is** considered to be part of a floating-point literal.

**Decimal integer literals are signed.**

---

Examples for literals and their types, under the supposition that signed and unsigned have the commonly used representation with 32 bits
![[Pasted image 20250907223222.png]]

Suffixes for integer literals and their types
![[Pasted image 20250907223447.png]]
For example, `1U` has value 1 and type `unsigned`, `1L` is `signed long`, and `1ULL` has the same value `1` but type `unsigned long long`.
So with suffixes, integer literals can be forced to have a type with minimal rank.

## Literals and values

**Different literals can have the same value.**
`0`, `0x0`, and `’\0’` are all the same value, a `0` of type `signed int`.

For integers, this rule looks almost trivial, but for floating-point literals, it is less obvious. Floating-point values are only an approximation of the value they present literally because binary digits of the fractional part may be truncated or rounded.

Hence

**The effective value of a decimal floating-point literal may be different from its literal value**
![[Pasted image 20250907223958.png]]

## Implicit conversion

As we have seen in the examples, the type of an operand has an influence on the type of an operator expression, such as -1 or -1U. Whereas the first is a signed int, the second is an unsigned int. The latter might be particularly surprising for beginners because an unsigned int has no negative values, so the value of -1U is a large positive integer.

The type rules become even more complicated for operators that have two operands, such as addition and multiplication because these then may have different types. Here are some examples of operations that involve floating-point types:
![[Pasted image 20250907224319.png]]

**Avoid operations with operands of different signedness.**
**Use unsigned types whenever you can**

## Const

**An object of const-qualified type is read-only.**
String literals are read-only

## Enumerations

C has a simple mechanism to name small integers as we needed them in the example, called enumerations
![[Pasted image 20250907225726.png]]

This declares a new integer type enum corvid for which we know four different values.

**If all enumeration constants of a simple enumeration type fit into signed int, they have that type.**

## Macros

Macros are basically constants that are replaced with a value in compile-time

```
# define M_PI 3.141’592’653’589’793’238’46
```

A macro definition consists of five different parts: 
	(1) A starting # character that must be the first non-blank character on the line 
	(2) The keyword define 
	(3) An identifier that is to be declared, here M_PI 
	(4) The replacement text, here 3.141’592’653’589’793’238’46 
	(5) A terminating newline character

*Macro names are in all caps*

## Compound literals

For types that don’t have literals that describe their constants, things get even more complicated. For macros, we have to use compound literals on the replacement side. 
Such a compound literal has the form  `(T){ INIT }` 
That is, a type in parentheses, followed by an initializer.

**A compound literal defines an object>**

```c
# define CORVID_NAME /**/ \
(char const*const[corvid_num]){ \
	[chough] = "chough", \
	[raven] = "raven", \
	[magpie] = "magpie", \
	[jay] = "jay", \
}

for (unsigned i = 0; i < corvid_num; ++i) 
	printf("Corvid %u is the %s\n", i, CORVID_NAME[i]);
```

Whereas compound literals in macro definitions can help us declare something that behaves similarly to a constant of a chosen type, it isn’t a constant in the sense that we have previously discussed.

### Pitfalls

Overall, this form of macro has some pitfalls: 
	• Compound literals, as introduced so far, aren’t suitable for ICE (An integer constant expression). 
	• For our purpose here, to declare named constants, the type `T` should be const-qualified. This ensures that the optimizer has a bit more slack to generate good binary code for such a macro replacement. 
	• There must be at least one space character between the macro name and the `()` of the compound literal, here indicated by the `/**/` comment. 
	Otherwise, this would be interpreted as the start of a definition of a function-like macro.
	• A backspace character `\` at the very end of the line can be used to continue the macro definition to the next line. 
	• There must be no `;` at the end of the macro definition. Remember, it is all just text replacement.

## Constexpr

```c
# define CORVID_NAMES /**/ \ 
(constexpr char[8][corvid_num]){ \ 
	[chough] = "chough", \ 
	[raven] = "raven", \ 
	[magpie] = "magpie", \ 
	[jay] = "jay", \ 
}
```

For all these characters, by using `constexpr`, the compiler now knows that they are not intended to change during execution, and the `const` qualification is implied.
