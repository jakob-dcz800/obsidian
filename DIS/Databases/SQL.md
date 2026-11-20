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

