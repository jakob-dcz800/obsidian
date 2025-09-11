
**Values have a type and a binary representation.**
## Binary representation

The binary representation of a type is a model that describes the possible values for that type. It is not the same as the in-memory object representation that describes the more or less physical storage of values of a given type.

**The same value may have different binary representations.**

### Bounds for scalar types

![[Pasted image 20250908111111.png]]

**The maximum value of any integer type is of the form $2^p − 1$.**

Where p is the precision (or width)

## Bit sets and bitwise operators

A bit set is a different interpretation of an unsigned value, where we assume that it represents a subset of the base set $V = \{0, \dots , p −1\}$ and where we take element i to be member of the set, if the bit $b_i$ is present.

There are three binary operators that operate on bit sets:

| Operator | Math    | Explanation          |
| -------- | ------- | -------------------- |
| \|       | $A ∪ B$ | Set union            |
| `&`      | $A ∩ B$ | Intersection         |
| `^`      | $AΔB$   | Symmetric difference |

For an example, let us choose A = 240, representing {4, 5, 6, 7}, and B = 287, the bit set {0, 1, 2, 3, 4, 8}
![[Pasted image 20250908112313.png]]

The complement ~A would have value 65295 and would correspond to the set {0, 1, 2, 3, 8, 9, 10, 11, 12, 13, 14, 15}. This bit complement always depends on the precision p of the type.

All of these operators can be written with identifiers: `bitor`, `bitand`, `xor`, `or_eq`, `and_eq`, `xor_eq`, and `compl` if you include header `<iso646.h>`.

A typical usage of bit sets is for flags, variables that control certain settings of a program:

```c
enum corvid { magpie, raven, jay, chough, corvid_num, }; 
#define FLOCK_MAGPIE 1U 
#define FLOCK_RAVEN 2U 
#define FLOCK_JAY 4U 
#define FLOCK_CHOUGH 8U 
#define FLOCK_EMPTY 0U 
#define FLOCK_FULL 15U 

int main(void) { 
	unsigned flock = FLOCK_EMPTY; 
	
	... 
	
	if (something) flock |= FLOCK_JAY; 
	
	... 
	
	if (flock&FLOCK_CHOUGH) 
		do_something_chough_specific(flock);
 }
```

Membership in a flock can then be handled through the operators: `|=` adds a corvid to flock, and `&` with one of the constants tests whether a particular corvid is present.

Observe the similarity between operators `&` and `&&` or `|` and `||`. 
If we see each of the bits $b_i$ of an unsigned as a truth value, `&` performs the logical and of all bits of its arguments simultaneously.

On the other hand, keep in mind that the operators || and && have short-circuit evaluation, so be sure to distinguish them clearly from the bit operators

## Shift operators

The next set of operators builds a bridge between interpretation of [[Numbers#Unsigned|unsigned values]] as numbers and as bit sets.

A left-shift operation `<<` corresponds to the multiplication of the numerical value by the corresponding power of two.

For `A = 240`, the set `{4, 5, 6, 7}`, `A << 2` is $240 · 2^2 = 240 · 4 = 960$
which represents the set `{6, 7, 8, 9}`.

There is an analogous right-shift operation `>>` that shifts the binary representation toward the less-significant bits. Analogously, this corresponds to an integer division by a power of 2

**Observe that for this operation, the precision of the type isn’t important**

There are also corresponding assignment operators <<= and >>=
### Overflow
Resulting bits that don’t fit into the binary representation for the type are simply omitted.
In our example, A << 9 would correspond to set {13, 14, 15, 16} (and value 122880), but since there is no bit 16, the resulting set is {13, 14, 15}, value 57344.

**The second operand of a shift operation must be less than the precision**

## Boolean

Treating `bool` as an unsigned type is a stretch of the concept

You will probably rarely need bool variables. They are only useful if you want to ensure that the value is always reduced to false or true on assignment.

## Signed integer

Signed types are a bit more complicated than unsigned types. A C implementation has to decide about two points: 
	• What happens on arithmetic overflow? 
	• How is the sign of a signed type represented?

**Positive values are represented independently from signedness.**
Or, stated otherwise, a positive value with a signed type has the same representation as in the corresponding unsigned type.

The following two functions are basically all that is needed to interpret unsigned values as signed values:

```c
bool is_negative(unsigned a) { 
	constexpr unsigned int_max = UINT_MAX/2; 
	
	return a > int_max; 
} 

bool is_signed_less(unsigned a, unsigned b) { 
	if (is_negative(a) != is_negative(b)) 
		return a > b; 
	else return a < b; 
}
```

## Precision

The width (and thus the precision) of the integer types that we have seen so far can be inspected by using macros from `<limits.h>`, such as UINT_WIDTH and LONG_WIDTH. The C standard only guarantees a minimal width for them. For the unsigned types, these are

![[Pasted image 20250908120026.png]]


<stdint.h>:
Nowadays, platforms usually provide uint8_t, uint16_t, uint32_t, and uint64_t unsigned types and int8_t, int16_t, int32_t, and int64_t signed types

## Float

The include file <float.h>, has constants `DBL_MIN` and `DBL_MAX` that provide us with the minimal and maximal values for double. But be aware that here, `DBL_MIN` is the smallest number that is strictly greater than 0.0; 
the smallest negative double value is `-DBL_MAX`.

### Infinite fractions

[[Floating points]]

Fractions like $\frac{1}{3}$ are dealt with by cutting off the expansion.
The position where the expansion is cut is “floating” (thus the name) and depends on the magnitude of the number in question.

In a view that is a bit simplified, a floating-point value is computed from the following values: 
- $s$ Sign (±1) 
- $e$ Exponent, an integer 
- $f_1, . . . , f_p$ values `0` or `1`, the mantissa bits

The floating-point value is then given by this formula:
$$
s\cdot 2^{e} \cdot \sum^p_{k=1}f_{k}2^{-k}
$$
![[Pasted image 20250908121132.png]]

**Floating-point operations are neither associative, commutative, nor distributive**
So, basically, floating points lose all the nice algebraic properties we are used to when doing pure math.
The problems that arise from that are particularly pronounced if we operate with values that have very different orders of magnitude.

**Never compare floating-point values for equality**