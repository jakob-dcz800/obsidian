---
tags:
  - DMA
  - Math
---

# Hele tal

## Division with remainder

divides into → $|$
does not divide into → $\nmid$

Any int can be written as $m = qd+r$

$r$ is remainder
$d$ = positive integer as divider
$q$ is quotient

$m$ % $d = r$

$12 \% 5 = 2$ where $q=2$
$5\%12=5$ where $q = 0$

$-12\%5=3$ hvor $q=-3$ → $12=(-3)5+3$
$5\%12=7$ hvor $q=-1$ → $-5=(-1)12+7$

Only $d$ must be a positive integer

if $r=0$ then we say:
- $m$ is a multiple of $d$
- $d$ is a divisor of $m$
- $d$ divides $m$ ($d|m$)

if $r\not=0$ then $d \nmid m$
## GCD / Euclid's algorithm

$d$ divides both a and $b$
All divisors of **36** are: 1,  2, 3, 4, 6, 9, 12, 18, 36
All divisors of **30** are: 1, 2, 3, 5, 6, 10, 15, 30

$$GCD(a, b) = GCD(a\%b, b)$$
Biggest number first

## LCM - least common multiple

lcm if $a|m$ and $b|m$

Multiples of **12** are: $12, 24, 36, 48, 60$
Multiples of **15** are: $15, 30, 45, 60, 75$

$LCM(12, 15) = 60$

$$
LCM(a, b) = \frac{ab}{GCD(a, b)}
$$
## Primes

A prime is any positive int that divides by itself and 1

Primes are greater than 1
You only need to check if numbers are a prime up to $\sqrt{p}$
All integers can be broken down into prime numbers

