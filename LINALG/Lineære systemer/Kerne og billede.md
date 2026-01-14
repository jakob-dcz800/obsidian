---
tags:
  - Matrices
  - Math
  - LINALG
---
# Kerne og billede

Primært vedr. notation som skal på plads
## Definition

[[Lineære transformationer#Definition|Lineære transformationer]] har en **kerne** og et **billede**.

![[Pasted image 20250506214737.png]]

**Kernen** (kernel) er de vektorer i $\mathbb{R}^n$ for hvem den lineære transformation giver 0
**Billedet** (range) er de lineære transformationer i $\mathbb{R}^n$ for hvem vektorerne (inputtet) hører til $\mathbb{R}^n$ (altså alle de værdier vi kan få frem)

### Sammenhæng med matricer
$\text{ker } T = \text{null }A$, kernen af $T$ er lig [[Nulrum|nulrummet]] af $A$
$\text{ran }T =\text{col A } (= \text{row A}^T)$, billedet af $T$ er lig [[Søjlerum|søjlerummet]] for A, og [[Rækkerum|rækkerummet]] af den transponerede A
Søjlerummet er $\text{span } A$ (altså alle de resultater vi kan udlede af underrummet)

## Eksempel

### 1

Vi fandt altså ud af nulrum og søjlerum af eksemplet fra tidligere:

![[Pasted image 20250506214751.png]]
