## Integral binary numbers

We note binary as: $10010101_2 = 149_{10}$
Since all digits can be represented as binary, we want to explore representing binary fractions.
I.e. - can we have a comma in our binary number?

![[Pasted image 20250907130819.png]]

Here, we break up the number 123,456 as powers of 10 (this is base 10)
Generally for all bases we can say:
![[Pasted image 20250907130925.png]]

### Base-2

![[Pasted image 20250907131016.png]]

Bits to the right of the "binary point" is fractional powers of 2
These are rational numbers

| Value            | Binary   |
| ---------------- | -------- |
| $5 \frac{3}{3}$  | `101.11` |
| $2 \frac{7}{8}$  | `10.111` |
| $1 \frac{7}{16}$ | `1.0111` |
- Shift right to divide by 2
- Shift left to multiply by 2
- Numbers of the form `0.111` are below `1.0`
	- $1/2 + 1/4 + 1/8 + ... 1/2^n + \dots \sim 1.0$
	- Use notation $1.0 - \epsilon$ (very small value)
- Trailing zeroes are ignored

Limitation 1:
	Can only represent fractions of form $\frac{x}{2^k}$
	The other rational numbers have repeating bit representation:
		`1/3 = 0.0101010101[01]...`
		`1/5 = 0.001100110011[0011]...`
		`1/10 = 0.0001100110011[0011]...`
Limitation 2:
	Just one setting of a binary point within the  $w$ bits
		Limited range of numbers

For `1111111.1 = 127.5` - here we cannot say .25 since we only have one bit to represent the fraction.
If you go half-half you can only go up to 16: `1111.1111 = 15.9375`