# Functional Dependencies

>[!TIP]
>Role of functional dependencies (FDs) in detecting redundancy
>An FD is a statement about all allowable instances.

Consider a relation R with 3 attributes, ABC 
- No FDs hold: No redundancy. 
- A → B: Tuples having the same A value should have the same B value.

## Candidate key

>[!DEFINITION] Candidate key
>Is a minimal set of attributes of a relationship that can be used to identify a tuple uniquely.
>For Example, each tuple of EMPLOYEE relation can be uniquely identified by E-ID and it is minimal as well. So it will be the Candidate key of the relationship.


K is a candidate key for R means that K → R
- However, K → R does not require K to be minimal!
>minimal?

A candidate key may or may not be a primary key.
**Super Key** is a set of attributes of a relationship that can be used to identify a tuple uniquely.

>[!Note]
>A candidate key is always a super key but vice versa is not true.

### Example
The set of attributes whose [[#Closure|attribute closure]] is a set of all attributes of the relation is called the super key of the relation.

Let us calculate the attribute closure of different sets of attributes:
![[Pasted image 20260619105106.png]]
As (E-ID)+, (E-ID, E-NAME)+, (E-ID, E-CITY)+, (E-ID, E-STATE)+, (E-ID, E-CITY, E-STATE)+ give set of all attributes of relation EMPLOYEE. So all of these are super keys of relation.

>[!IMPORTANT]
>The minimal set of attributes whose [[#Closure|attribute closure]] is a set of all attributes of relation is called the candidate key of the relation.
## Armstrong’s Axioms

![[Pasted image 20260618174333.png]]
![[Pasted image 20260618174413.png]]
### Example

![[Pasted image 20260618174440.png]]

## Closure
**Attribute Closure:** The set of attributes that are functionally dependent on the attribute A is called **Attribute Closure** of A and it can be represented as $A^+$

### Steps to Find the Attribute Closure
Given the FD set of a Relation R, The **attribute closure set** S is the set of Attribute Closure A.
- Add A to S.
- Recursively add attributes that can be functionally determined from attributes of the set S until done.

#### Example
```c
R (E-ID, E-NAME, E-CITY, E-STATE)

FDs = { 
	E-ID->E-NAME; 
	E-ID->E-CITY;
	E-ID->E-STATE;
	E-CITY->E-STATE 
}
```

The attribute closure of E-ID can be calculated as:

- Add E-ID to the set {E-ID}
- Add Attributes that can be derived from any attribute of the set. 
	- In this case, E-NAME and E-CITY, E-STATE can be derived from E-ID. 
	- So these are also a part of the closure.
- As there is one other attribute remaining in relation to be derived from E-ID. So the result is:

```c
(E-ID)^{+ = {E-ID, E-NAME, E-CITY, E-STATE }}
```

Similarly,
```c
(E-NAME)^{+ = {E-NAME}}
(E-CITY)^{+ = {E-CITY, E_STATE}}
```

#### Example 2

Find the attribute closures of given FDs:
```c
R(ABCDE) = {AB->C, B->D, C->E, D->A}. 
```

To find (B)+, we will add an attribute in the set using various FDs which have been shown in the table below.
![[Pasted image 20260619104405.png]]

1. B is FC of itself
2. `B -> D`
3. `B -> D -> A`
4. Since both A, and B are in set:
	1. `AB -> C`
5. C is also in set:
	1. `C -> E`

#### Example 3
Find the attribute closures of given FDs:
```c
R(ABCDE) = {AB->C, B->D, C->E, D->A}. 
```

Find `(C, D)+` 

1. `{C, D}` trivial
2. `{C, D, E, A}` 
3. `B` and therefore `AB` is not FT of any element in set