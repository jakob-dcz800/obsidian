---
tags:
  - Fundemental
  - Programming
---
Floats distinguish between positive and negative zero.

**Never compare floating-point values for equality**
## Normalized float

$v = (-1)^S \cdot M \cdot 2^E$
Here is when the exponent isn't `0...0` or `1...1`

you [[Operations#4.1 Value operators|shift]] the frac to make sure that it is always between 1..2

![[Pasted image 20250907132952.png]]

The exponent is a [[Numbers#Biased numbers|biased number]]
In a 32-bit float we have 8 bits to represent the exponent

### Example

`Value: float f = 15213.0` 
$$
\begin{align}
15213_{10} & = 11101101101101_{2} \\
& = 1.1101101101101_{2} \cdot 2^{13}
\end{align}
$$
Here we multiply be $2^{13}$ since we moved the decimal point 13 times.

Significand:
$$
\begin{align}
M =  1.&1101101101101_{2} \\
\text{Frac} =& 11011011011010000000000_{2}
\end{align}
$$
Here we add trailing zeroes.

Exponent:
$E$ is the number of times that the point was shifted 
$$
\begin{align}
E &= 13_{10} \\
\text{Bias} &= 127_{10} \\
\text{Exp} &= E + \text{Bias} = 140_{10} = 10001100_{2} 
\end{align}
$$
Result

| sign | exponent   | fraction                  |
| ---- | ---------- | ------------------------- |
| `0`  | `10001100` | `11011011011010000000000` |

## Denormalized float

Case if exponent is all zeroes.
$v = (-1)^S \cdot M \cdot 2^E$
Exponent: $E=1-\text{Bias}$

## Special values

When the exponent are all 1's
This represents $\pm \infty$
- Typically the result of an overflow
- Overflows *can* be negative
- Underflow happens when rounding results in zero
- Example:
$$
\begin{align}
\frac{1}{0}=\frac{-1}{-0}&=\infty \\
\frac{1}{-0} &= -\infty
\end{align}
$$
When Exp = `11...1`, Frac ins't `00...0`
- Not a number (`NaN`)
- Represents case when no numerical value can be determined
- Ex: `sqrt(-1)`, `∞ - ∞`, `∞ * 0`

## Example

8-bit floating point - this doesn't exist irl.
![[Pasted image 20250907135747.png]]

![[Pasted image 20250907135921.png]]

Note, that because of the [[Numbers#Biased numbers|bias]] - values aren't equally distributed.
There is a significant jump between 1 and 224
The possible values are many - close to zero - and few the farther you get out.

![[Pasted image 20250907140323.png]]

## Properties

[[Floating point operations#Addition|Addition]]? Ordering doesn't matter
- Commutative? **yes**
- Associative? **no**
	- Due do inexactness of rounding
	- `(3.14 + 1e10) - 1e10 = 0`
	- `3.14 + (1e10 - 1e10) = 3.14`
- 0 is additive identity? **yes**
- Does every value have an inverse to get zero (fx. 10 and -10)? **Almost**
	- `infty` and `NaN` do not
- Monotonicity? 
	- $a \geq {b} \implies a + c \geq b + c$? **Almost**
		- Infinity and NaN is the exception

[[Floating point operations#Multiplication|Multiplication]]
![[Pasted image 20250907143101.png]]

## Operations in C

![[Pasted image 20250907143123.png]]