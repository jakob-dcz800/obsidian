# Relational Algebra

Language for mathematical elegance
Precise communication
Exact description of what a database system does - [[SQL]] does not do that.

## Basic operations: 

| Operation                                                | Symbol   | Explainer                                   |
| -------------------------------------------------------- | -------- | ------------------------------------------- |
| [[#Selection\|Selection]]                                | $\sigma$ | Selects a subset of rows from relation      |
| [[#Projection\|Projection]]                              | $\pi$    | Deletes unwanted columns from relation      |
| [[#Cross-product\|Cross-product]]                        | $\times$ | Allows us to combine two relations          |
| [[#Union, Intersection, Set-Difference\|Set-difference]] | $-$      | Tuples in relation 1, but not in relation 2 |
| [[#Union, Intersection, Set-Difference\|Union]]          | $\cup$   | Tuples in relation 1 and in relation 2      |

### Selection
Selects rows that satisfy **selection condition**
**No duplicates** in result!
Schema of result **identical** to schema of (only) input relation

>[!TIP]
>Result relation can be the input for another relational algebra operation

![[Pasted image 20260617140317.png|326]]

![[Pasted image 20260617140331.png]]

### Projection
Deletes attributes that are not in projection list.
Schema of result contains **the exact fields** in the projection list, with the same names that they had in the (only) input relation


![[Pasted image 20260617135724.png|327]]![[Pasted image 20260617135734.png|329]]
```fsharp
∃sid,age. 
S2(sid, sname, rating, age)
```

![[Pasted image 20260617135829.png|323]]

```fsharp
∃sid,age, rating.
S2(sid, sname, rating, age)
```

### Union, Intersection, Set-Difference
These operations take two input relations that **must be union-compatible**
- Same number of fields
- “Corresponding” fields have the same type
![[Pasted image 20260617140738.png|157]]

![[Pasted image 20260617140647.png]]

### Cross-product

Each row of S1 is paired with each row of R1.
Result schema has one field per field of S1 and R1, with field names “inherited” if possible.
Conflict: Both S1 and R1 have a field called `sid`


![[Pasted image 20260617140945.png|176]]
![[Pasted image 20260617141021.png]]
## Additional operations:

| Operation                                              | Symbol              | Explainer               |
| ------------------------------------------------------ | ------------------- | ----------------------- |
| [[#Union, Intersection, Set-Difference\|Intersection]] | $\cap$              |                         |
| [[#Joins\|Join]]                                       | $\Join$             |                         |
| Antijoin                                               | $\vartriangleright$ | Equals $A - (A\Join B)$ |
| Division                                               | $\div$              |                         |
| [[#Renaming\|Renaming]]                                | $\rho$              |                         |
|                                                        |                     |                         |
|                                                        |                     |                         |
Each operation returns a finite relation, i.e., **operations can be composed!**
(Algebra is “closed”.)

### Renaming
The $\rho$ operator gives a new schema to a relation
$\rho_{R1(A1,\dots,An)}(R2)$ makes R1 be a relation with attributes A1,…,An and the same tuples as R2
> Tuples?

Simplified notation: R1(A1,…,An) := R2
[[#Cross-product|In our previous example]]: Res(sid1,sname,rating,age,sid2,bid,day) := S1 $\times$ R1

### Joins
Condition Join / Sometimes called a theta-join
$$
R \Join_{C}S = \sigma_{C}(R \times S)
$$
Where $C$ is a condition:
$$
S1 \Join _{S{1}.sid < R{1}.sid} R1
$$
Join S1 and R1 where S1.sid < R1.sid

![[Pasted image 20260617141844.png]]

>[!TIP] Duplicate column names!
>Result schema same as that of cross-product.

Fewer tuples than cross-product, might be able to compute more efficiently

#### Equijoin
A special case of condition join where the condition contains only equalities

![[Pasted image 20260617142043.png]]

Result schema similar to cross-product, but only one copy of fields for which equality is specified.

Natural Join $\Join$ Equijoin on all common fields.

# Possibilities

## Hard, but possible
![[Pasted image 20260617142628.png]]
"Find the employees with the highest salary"
• Intuition: 
	• Create “dominance” relation: e1 dominates e2 if e1 has salary higher than or equal to e2 
	• Divide “dominance” relation by original table: 
		Finds employees who dominate all others

## Impossible, but very useful
![[Pasted image 20260617142638.png]]
"Find the total amount paid in salaries by department"
**We do not know how to count!**

# Extensions
Relational query languages restrict expressiveness to obtain ease of use and of optimization
There are some very useful queries we cannot express in the relational algebra
Many extensions proposed to handle those queries made into [[SQL]]

## Division

A useful shorthand
>[!EXAMPLE]
>$A ÷ B$ contains all sailors $x$ such that for every boat $y$ in $B$, there is an $(x,y)$ reservation in $A$

## Extending Projection with Expressions
Using the same $\pi_{L}$ operator, we allow the list $L$ to contain arbitrary expressions involving attributes:
- Arithmetic on attributes, e.g., A+B -> C
- Duplicate occurrences of the same attribute.

Here, we add rating + sid and get rs
![[Pasted image 20260617142949.png]]

## Bags

>[!WARNING]
>Beware: Bag Laws != Set Laws
>The commutative law for union $R \cup S = S \cup R$ holds for bags, since addition is commutative
>Set union is **idempotent**, meaning that $S \cup S = S$
>For **bags**, if x appears n times in S, then it appears $2n$ times in $S \cup S$
>Thus $S\cup S != S$ in general, e.g., ${1}\cup {1} = {1,1} != {1}$.

A bag (or [[Serier og sæt#Multisets|multiset]]) is an unordered collection where duplicates are allowed
Example: {1,2,1,3} is a bag
Example: {1,2,3} is a bag that happens to also be a set.
SQL uses bag semantics

![[Pasted image 20260617143129.png]]

![[Pasted image 20260617143434.png]]

### Bag Union 
An element appears in the union of two bags the **sum** of the number of times it appears in each bag.

Example: 
$$
\set{1,2,1} \cup \set{1,1,2,3,1} = \set{1,1,1,1,1,2,2,3}
$$
### Bag Intersection
An element appears in the intersection of two bags the minimum of the number of times it appears in either.

Example:
$$
\set{1,2,1,1} \cap \set{1,2,1,3} = \set{1,1,2}
$$

### Bag Difference
An element appears in the difference A-B of bags as many times as it appears in A, **minus** the number of times it appears in B, but **never less than 0 times**.

Example:
$$
\set{1,2,1,1} -\set{1,2,3} = \set{1,1}
$$

## Duplicate Elimination
$$
R1 := \delta (R2)
$$
R1 consists of one copy of each tuple that appears in R2 one or more times

![[Pasted image 20260617144126.png]]

## Aggregation Operators

Aggregation operators are not operators of relational algebra.
Rather, they apply to entire columns of a table and produce a single result
The most important examples: SUM, AVG, COUNT, MIN, and MAX

![[Pasted image 20260617144209.png]]

## Grouping

![[Pasted image 20260617144854.png]]

$$
\gamma_{age,MAX(rating)} \to _{mr}(S2)
$$
Means have two groups, one for age column, and MAX(rating) aggregation column, and append mr to S2.

## Sorting
$\tau_{L}(R)$ is the list of tuples of R sorted first on the value of the first attribute on L, then on the second attribute of L, and so on.
$\tau$ is relation itself, but with tuples sorted.

## Outer join

Suppose we join $R \Join S$

$\overset{0}{\Join}$
A tuple of R that has no tuple of S with which it joins is called dangling. 
	• Similarly for a tuple of S.

![[Pasted image 20260617145415.png]]

Preserve left columns S1 even though there is no match in R1