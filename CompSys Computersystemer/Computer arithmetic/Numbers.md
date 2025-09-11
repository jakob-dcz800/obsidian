## Representation of integers

In C, if you declare an unsigned integer ([[#Unsigned|UINT]]) it actually becomes the unsigned integer type of representation.
If you let the compiler infer the type of a negative number, it becomes a [[#Biased numbers|biased integer]]

### Unsigned
Unsigned integers or UINT

8-bit numbers have range 0-255:
```
00000000 = 0
00000001 = 1
11111111 = 255
```

**INT_MIN < -INT_MAX** 

Or, stated otherwise, the positive value `-INT_MIN` is out of bounds since the value of the operation is larger than `INT_MAX`.
### Signed

**Negation may overflow for signed arithmetic**

Signed integers (INT) or two's compliment
1 bit for signing and 7 bits for numerical values

8-bit numbers have range -128-127:
```
00000000 = 0
00000001 = 1
10000000 = -127 (lowest point)
10000001 = -126
11111111 = -1
01111110 = 126
01111111 = 128
```

Its called two's compliment cause each of the 7-value bits have a compliment on the other side of zero

For signed types, [[Values and data#Bit sets and bitwise operators|bit operations]] work with the binary representation. The shift operations then become really messy. The semantics of what such an operation is for a negative value is not clear.

**Use unsigned types for bit operations.**
### Biased numbers
This acts as an unsigned integer and works by subtracting a constant from every single value(here 127)

Range is -127-128
You never manually set the bias, it is part of the definttion

This is usually best practice

```
00000000 = -127
00000001 = -126
11111111 = 128
```

[[Integral binary numbers]]
[[Floating points]]