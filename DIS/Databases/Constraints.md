# Constraints

![[Pasted image 20260618174016.png]]

## Constraints Over Multiple Relations
![[Pasted image 20260618174043.png]]

# DBMS

A Database Management System (DBMS) is a software package designed to store and manage [[Database|databases]]

A Database Management System (DBMS) provides efficient, reliable, convenient, and safe multi-user storage of and access to massive amounts of persistent data.

We will focus on Relational DBMS (RDBMS)

## Why Use a DBMS?

• Data independence and efficient access. 
• Reduced application development time. 
• Data integrity and security. 
• Uniform data administration. 
• Concurrent access and recovery from crashes

# ER Modeling

>Entity / Relation modeling

# Arrows

## Many-one
![[Pasted image 20260618144840.png]]
![[Pasted image 20260421125952.png]]

## Referential Integrity
![[Pasted image 20260618145017.png]]

# Entities
## Weak Entities
A weak entity can only be identified uniquely by considering the **primary key of another** (owner) **entity** (possibly in combination with a key attribute of the weak entity)

![[Pasted image 20260618145558.png]]
Owner entity set and weak entity set must participate in a one-to-many relationship set (one owner, many weak entities).

## ISA Hierarchies

Similar to [[Object oriented analysis and design#Domain Modelling|object-oriented modeling]]
E/R entities have representatives in all subclasses to which they belong
Rule: if entity e is represented in a subclass, then e is represented in the superclass. 
(and recursively up the tree)

![[Pasted image 20260618145905.png]]

# Examples

## Example 1

![[Pasted image 20260423144100.png]]

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

# Integrity constraint

IC: condition that must be true for **any** instance of the database 
	• Domain constraints 
	• Key constraints 
	• Foreign key constraints (later)

ICs are based upon the semantics of the real-world enterprise that is being described in the [[database]] relations

We can check a database instance to see if an IC is violated, but we can **NEVER** infer that an IC is true by looking at an instance.
• An IC is a statement about all possible instances! 
• From example, we know name is not a key, but the assertion that sid is a key is given to us.

>Key and foreign key ICs are the most common; more general ICs supported too.

# Keys

## Key
> {ssn} is a key for Employees.
## Superkey
> The set {ssn, name} is a superkey.
## Primary key

Primary key is in [[SQL]] denoted by `PRIMARY KEY` (e.g. `id`)

## Foreign keys
>[!DEFINITION]
>Set of fields in one relation that is used to “refer” to a tuple in another relation
>• Must correspond to **primary key** of the second relation 
>• Like a “logical pointer”.

If all foreign key constraints enforced, referential integrity is achieved, i.e., no dangling references. 
	• Not like HTML links!

### Enforcing Referential Integrity
What if a new `Works_In` tuple is added that references a non-existent employee? 
	(Example from [[ER Modeling#Example 1|here]])
	• Reject it!

What if an Employee tuple is deleted? 
	• Also delete all `Works_In` tuples that refer to it. 
	• Disallow deletion of Employee tuple that is referred to. 
	• Set `ssn` to some default value 
	• Set `ssn` in Works_In to null, denoting `unknown`
	• Similar if primary key of Employee tuple is updated

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

# SQL

## SELECT
The utmost basic structure
```SQL
SELECT [DISTINCT] target-list
FROM relation-list
[WHERE qualification]
GROUP BY grouping-list
HAVING group-qualification
```

```SQL
SELECT 
	S.sname 
FROM 
	Sailors S, 
	Reserves R -- cross join
WHERE 
	S.sid = R.sid 
	AND R.bid=103
```

### Example
Find sid’s of sailors who’ve reserved a red or a green boat

```SQL
SELECT 
	S.sid
FROM 
	Sailors S, 
	Boats B, 
	Reserves R
WHERE S.sid=R.sid 
	AND R.bid=B.bid
	AND (B.color=‘red’ OR B.color=‘green’)
```

OR:

```SQL
SELECT 
	S.sid
FROM 
	Sailors S, 
	Boats B, 
	Reserves R
WHERE 
	S.sid=R.sid 
	AND R.bid=B.bid
	AND B.color=‘red’
 
UNION -- removes duplicates
SELECT 
	S.sid
FROM 
	Sailors S, 
	Boats B, 
	Reserves R
WHERE 
	S.sid=R.sid 
	AND R.bid=B.bid
	AND B.color=‘gr
```

## INSERT

```SQL
INSERT 
	INTO Students (sid, name, login, age, gpa)
VALUES 
	(53688, ‘Smith’, ‘smith@ee’, 18, 3.2)
```

Or with a `SELECT` statement:
```SQL
INSERT 
	INTO Students(sid, name, login, age, gpa)
	SELECT NULL, name, login, age, 0.0 --NULL assumes IDENTITY column
	FROM Other_Students
	WHERE school = ‘KU’
```

## DELETE

```SQL
DELETE FROM Table
WHERE Condition
```

```SQL
DELETE FROM Students S 
WHERE S.name = ‘Smith’
```

## UPDATE

```SQL
UPDATE Table
SET 
	A1=Expr1,
	A2=Expr2,
	…,
	An=Exprn
WHERE Condition
```

Update all tuples satisfying some condition
```SQL
UPDATE Employees
SET 
	salary = salary * 1.1
WHERE 
	age >= 36

```

## Cross Join
Cartesian Product

```sql
SELECT 
	S.*, 
	E.* 
FROM 
	MovieStar S, 
	MovieExec E
```

If no WHERE clause is specified, it evaluates to the N-ary bag product S × E
Same as:

```sql
SELECT *
FROM MovieStar CROSS JOIN MovieExec
```

## GROUP BY

Find the age of the youngest sailor with age ≥ 18, for each rating with at least one such sailor

```sql
SELECT 
	S.rating, 
	MIN(S.age)
FROM Sailors S
WHERE S.age >= 18
GROUP BY S.rating
```

### HAVING

Find the age of the youngest sailor with age >= 18 for each rating level with at least 2 such sailors
```sql
SELECT S.rating, MIN(S.Age)
FROM Sailors S
WHERE S.age >= 18
GROUP BY S.rating
HAVING COUNT(*) > 1
```


- For each rating with at least 2 sailors (of any age)
- Find the age of the youngest sailor 
- With age ≥ 18, 
```sql
SELECT S.rating, MIN(S.age)
FROM Sailors S
WHERE S.age >= 18
GROUP BY S.rating
HAVING 1 < (SELECT COUNT (*)
			FROM Sailors S2
			WHERE S.rating = S2.rating)
```

List the `sid`’s of all sailors along with their reservation count
```sql
SELECT 
	sid,
	SUM(
		CASE
		WHEN R.bid IS NULL THEN 0
		ELSE 1
	)
FROM Sailors
 NATURAL LEFT OUTER JOIN
 Reserves R
GROUP BY sid
```

>[!Note]
>`Count(*)` counts all rows; 
>Otherwise, aggregations over columns ignore `NULL` values and return `NULL` when aggregating the empty set

# ORDER BY
ORDER BY can only appear in top-most query
	Otherwise results are unordered!

```sql
SELECT 
	S.rating, 
	AVG(S.age) AS avgage
FROM Sailors S
GROUP BY S.rating
ORDER BY avgage
```

# JOIN

```sql
SELECT 
	S.*, 
	E.*
FROM MovieStar S
 JOIN MovieExec E
 ON S.name = E.name
```

Corresponds to a [[Relational algebra#Joins|theta join]]

## Alternative Syntax for Equijoins

```sqlite
SELECT 
	* 
FROM 
	MovieStar S 
INNER JOIN 
	MovieExec E 
	USING (name)
```

Matching tuples are returned, but equijoin columns coalesced
**Results in a single name col**

## NATURAL JOIN

```sqlite
SELECT *
FROM MovieStar
 NATURAL JOIN MovieExec
```

Matching attribute-names are taken as join columns
**Duplicate columns are merged**

## Outer joins

List the `sid`’s of all sailors; 
for each sailor with reservations, list also the `bid`’s of boats she reserved
```sqlite
SELECT 
	DISTINCT S.sid, 
	R.bid
FROM Sailors S
 LEFT OUTER JOIN Reserves R
 ON S.sid = R.sid
```

Non-matching tuples paired with NULLs:
![[Pasted image 20260617200557.png]]

Find `sid`’s of sailors who have not reserved boat #103

```sqlite
SELECT S.sid
FROM Sailors S
 LEFT OUTER JOIN
 (
	 SELECT sid
	 FROM Sailors NATURAL JOIN Reserves R
	 WHERE R.bid = 103
) AS S_103
ON S.sid = S_103.sid
WHERE 
	S_103.bid IS NULL
```

## WITH
Find sid of sailors who have **not** reserved boat #103:
```sqlite
WITH S_103(sid) AS (
 SELECT 
	 sid
 FROM 
	 Sailors 
	 NATURAL JOIN Reserves
 WHERE 
	 bid = 103
)

SELECT 
	S.sid
FROM 
	Sailors S
	LEFT OUTER JOIN S_103
	ON S.sid = S_103.sid
WHERE 
	S_103.sid IS NULL
```


## EXCEPT
```sqlite
SELECT S.sid
FROM Sailors S

EXCEPT
	SELECT S.sid
	FROM 
		Sailors S, 
		Reserves R
	WHERE 
		S.sid = R.sid
		AND R.b
```

## EXISTS
Find names of sailors who have reserved boat #103:
```sqlite
SELECT S.sname
FROM Sailors S
WHERE EXISTS 
(SELECT *
 FROM Reserves R
 WHERE R.bid=103 AND S.sid=R.sid)
```

Find names of sailors who have NOT reserved boat #103:
```sqlite
SELECT S.sname
FROM Sailors S
WHERE NOT EXISTS 
(SELECT *
 FROM Reserves R
 WHERE R.bid = 103 AND R.sid = S.sid)
```

# NULL

What if S.Age is NULL?
S.Age > 25 returns NULL!

Implies a predicate can return 3 values
1. True
2. false
3. NULL

`WHERE` clause eliminates rows that do not return true:
```sql
SELECT sname
FROM Sailors
WHERE age > 25 -- no NULL values
```

# Strings

## LIKE

`LIKE` is used for string matching 
- `_` matches a single arbitrary character 
- `%` matches for 0 or more arbitrary characters.

# Division in SQL

## With EXCEPT
Find sailors who’ve reserved *all* boats
```sqlite
SELECT S.sname
FROM Sailors S
WHERE NOT EXISTS (
	 (SELECT B.bid FROM Boats B)
	 EXCEPT
	 (SELECT R.bid 
	 FROM Reserves R 
	 WHERE R.sid = S.sid)
 )
```

## Without EXCEPT
Find sailors who’ve reserved all boats.

- Sailors S such that ... 
	- there is no boat B without ... 
		- a Reserves tuple showing S reserved B
```sqlite
SELECT S.sname
FROM Sailors S
WHERE NOT EXISTS 
	(SELECT B.bid
	 FROM Boats B
	 WHERE NOT EXISTS 
		 (SELECT R.bid
		  FROM Reserves R
		  WHERE R.bid=B.bid
		  AND R.sid))
```

# Set-Comparison Operators

op ANY, op ALL
op can be >, <, =, <=, >=, <>

## Example
Find sailors whose rating is greater than that of all sailors called lubber:

```sql
SELECT *
FROM Sailors S
WHERE S.rating > ALL 
	(SELECT S2.rating
	 FROM Sailors S2
	 WHERE S2.sname='lubber')
```


# Regular Expressions
> The Swiss Army Knife of the Working Programmer

• `Ø` is a regular expression (does not match anything) 
• `e` is a regular expression (matches the empty string "") 
• `a` is a regular expression (matches the string "a") 
• `r+s` is a regular expression if and are regular expressions 
	(matches any string that `r` or `s` match) 
• `rs` is a regular expression if and are regular expressions 
	(matches any string that can be split into a prefix that matches `r` and a suffix that `s` matches) 
• `r*` is a regular expression if is a regular expression 
	(matches the empty string "" and any string that can be split into substrings each of which `r` matches)
## Example
![[Pasted image 20260423145034.png]]


>[!DEFINITION] Language of an expression
>Language of a regular expression r = set of strings that r matches
>Regular language = infinite set that can be represented finitely by a regular expression

a regular expression cannot count
Time complexity: linear in the size of `regular expression` and `string`

# Tools

## Bash

**grep**: find matching substrings in a text 
**sed**: replace matching substrings in a text

## Python

**re** library https://docs.python.org/3/library/re.html

```python
re.fullmatch(r'(a+b)*baa','abbaa') 
# -> <re.Match object; span=(0, 5), match='abbaa'>
re.findall(r'w[a-z]*', 'whisper words of wisdom let it be') 
# -> ['whisper', 'words', 'wisdom']

```

# Features

![[Pasted image 20260618142706.png]]
![[Pasted image 20260618142715.png]]

# Domain independence

Here both sides must exist in DB
![[Pasted image 20260505105454.png]]

Here, only one must exist in DB
![[Pasted image 20260505105509.png]]

Domain independent implies safe (not vice versa)
Unsafe implies Not domain independent

# RANF

>[!DEFINITION] Relational algebra normal form

Intention is to produce something simple

set of rules.
> Relational algebra normal form

fv(a) = fv(b) (free variables are the same for a and b)
ranf(a): a is in ranf

>[!DEFINITION] Codd’s Theorem 
>For every domain-independent relational calculus query there exists an equivalent query in RANF


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

# Relational Calculus

## Language

![[Pasted image 20260617101326.png]]

![[Pasted image 20260617101422.png]]

# Examples
## Example 1
Choose ssn, name, lot from Employees where the name is John:
`Employees(ssn,name,lot) ∧ name ≈ “John”`

Choose ssn, lot where name is John
`Employees(ssn,“John”,lot)`

Choose ssn from employees named John
`∃lot. Employees(ssn,“John”,lot)`


