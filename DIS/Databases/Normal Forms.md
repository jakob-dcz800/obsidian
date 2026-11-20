# Normal Forms

## 1NF
>1st normal form


- The domain of each attribute contains only atomic values (Codd)
- There are no duplicate rows
- Each entry contains exactly one value from the applicable domain (and nothing else)
- All columns are regular
- Often implemented by types and constraints

## 2NF
>2nd normal form
>(“the whole key”, no partial dependencies)

This means the table has no partial dependencies 
(i.e., no non-prime attribute is dependent on a part of a candidate key).

- Is 1NF
- Every non-prime attribute is dependent on each full key 
	- (i.e., not on a proper subset of any key).

## 3NF
>3rd normal form
>(“nothing but the key”, no **transitive dependencies**)

- Is 2NF
- Every **non**-prime attribute is directly dependent on each **superkey** of the table.

>[!IMPORTANT]
>A table is in Third Normal Form (3NF) if, for every non-trivial functional dependency (i.e. not X -> X) X→Y, at least one of the following holds:
>1. X is a **superkey**: This means that the attribute(s) on the left-hand side of the functional dependency (X) must be a superkey (a key that uniquely identifies a tuple in the table).
>2. Y is a prime attribute: This means that every element of the attribute set Y must be part of a candidate key (i.e., a prime attribute).
### Transitive dependency
For example, if we have the following relationship between attributes:
- A -> B (A determines B)
- B -> C (B determines C)
- Meaning A -> B -> C => A -> C
This means that A indirectly determines C through B, creating a **transitive dependency**.

## Decomposition into 3NF


## BCNF
  Boyce-Codd Normal Form

Boyce-Codd Normal Form (BCNF) is an advanced version of 3NF used to reduce redundancy in databases.
>It ensures that for every functional dependency, the left side must be a superkey. This helps create cleaner and more consistent database designs, especially when there are multiple candidate keys.

𝑅 is in BCNF if the only non-trivial FDs that hold over 𝑅 are key constraints.
### Rules for BCNF
- Rule 1: The table should be in the 3rd Normal Form.
- Rule 2: X should be a super-key for every functional dependency (FD) X−>Y in a given relation. 
