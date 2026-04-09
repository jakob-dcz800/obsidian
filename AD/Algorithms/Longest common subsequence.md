# Longest Common Subsequence (LCS)

Last Updated : 23 Jul, 2025

Given two strings, ****s1**** and ****s2****, the task is to find the length of the Longest Common Subsequence. If there is no ****common subsequence****, return `0`. A ****subsequence**** is a string generated from the original string by deleting 0 or more characters, without changing the relative order of the remaining characters.

For example, subsequences of "ABC" are "", "A", "B", "C", "AB", "AC", "BC" and "ABC". In general, a string of length $n$ has $2^n$ subsequences.

## Schema

![[Pasted image 20260404121545.png]]

Reglen er:
- række og kolonne 1 er 0.
- Hvis et bogstav er ens i $c_{i, j}$ sæt da en pil. Værdien er så diagonalen +1.
- Hvis et bogstav ikke er ens, skal værdien være maks af de to øverste eller det forrige tal i rækken
	 ![[Pasted image 20260404121806.png|197]]
- 