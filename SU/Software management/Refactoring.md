---
tags:
  - Programming
  - Analysis
  - Software-development
---
# Refactoring

Refactoring is improving a piece of software's **internal structure** without altering its **external behavior**.

Refactoring is not the same thing as:
* adding features
* debugging code
* rewriting code

Refactoring does **not fix bugs**, but it may help find bugs by scrutinizing code. 
It may also reduce the further introduction of bugs by **cleaning-up code**.
Refactoring does **not add new functionality** to the system, but it will ease the further adding of new functionality.
It is an essential part of [[agile software development]] such as Extreme Programming or incremental development.
## Code maintenance

**Definition**: Maintenance is modification or repair of a software product after it has been delivered.

Purposes: 
* fix bugs
* improve performance
* improve design
* add features

It is harder to maintain code than write your own new code.
* "house of cards" phenomenon (do not touch it!)
* must understand code written by another developer, or code you wrote at a different time with a different mindset

## Why?

Each part of your system's code has three purposes: 
1. to execute its functionality
2. to allow change
3. to communicate well to developers who read it

If the code does not do one or more of these, it is "**broken**“.
Refactoring improves software's design and makes it easier to understand.

## Dangers

* code that used to be:
	* well commented, now (maybe) is not 
	* fully tested, now (maybe) is not 
	* fully code reviewed, now (maybe) is not
* easy to insert a bug into previously working code (regression!)
	* a small initial change can have a large chance of error
## When to refactor?

When is it best for a team to refactor their code?
* best done continuously (like testing) as part of the process
* hard to do well late in a project (like testing)
Refactor when you identify an area of your system that: 
* Is not well designed 
* Is not thoroughly tested, but seems to work so far 
* now needs new features to be added

More importantly, when using [[iterative development]], a major refactoring stage should precede the beginning of the development of a new build. This will remove slight design problems and ease the addition of further functionality.
In this case, refactoring counterbalances the productivity-driven software development practices implied by agile incremental software development.

### Signs you should refactor
* code is duplicated 
* a routine is too long 
* a loop is too long or deeply nested 
* a class has poor cohesion 
* a class uses too much coupling
* inconsistent level of abstraction
* too many parameters

* to compartmentalize changes (change one place must change others) 
* to modify an inheritance hierarchy in parallel
* to group related data into a class 
* a "middle man" object does not do much 
* poor encapsulation of data that should be private 
* a weak subclass does not use its inherited functionality 
* a class contains unused code
### Tech debt

Implied cost of additional rework caused by choosing an easy (limited) solution now instead of using a better approach that would take longer.

## IDE support for refactoring 
Most IDEs support: 
* variable / method / class renaming 
* method or constant extraction 
* extraction of redundant code snippets 
* method signature change 
* extraction of an interface from a type 
* method inlining 
* providing warnings about method invocations with inconsistent parameters 
* help with self-documenting code through auto-completion
## Types of refactoring

* refactoring to fit design patterns 
* renaming (methods, variables) 
* extracting code into a method or module 
* splitting one method into several to improve cohesion and readability 
* changing method signatures 
* performance optimization 
* moving statements that semantically belong together near each other 
* naming (extracting) "magic" constants 
* exchanging idioms that are risky with safer alternatives 
* clarifying a statement that has evolved over time or is unclear 
* See also http://www.refactoring.org/catalog/

### Exam question: Refactoring: How?
* Each refactoring is **implemented as a small behavior**, preserving transformation. 
* Behavior-preservation is achieved through **pre- and post-transformation testing**. 
* Refactoring process: **test-refactor-test**

![[Pasted image 20250512101604.png]]

## Method

### Plan 1
- save code
- write unit tests
- analyze code and assess risk of refactoring
### Plan 2
- Refactor the code. 
	- Some unit tests may break. Fix the bugs. 
	- Perform functional and/or integration testing. Fix any issues.
- Code
	- Code review the changes.
- Check in your refactored code
	- Keep each refactoring small; refactor one issue / unit at a time. 
	- Your check-in should contain only your refactor.

## Regressions
*What if refactoring introduces new bugs in previously working functionality ("regressions")? How can this be avoided?*

* Code being refactored should have good unit test coverage, and other tests (system, integration) over it, before the refactor. 
	* If such code is not tested, add tests first before refactoring. 
	* If the refactor makes a unit test not compile, port it. 
	* If the method being tested goes away, the underlying functionality of that method should still be somewhere. So move the unit test to cover that new place in the code.
## Refactoring patterns
### Composing Methods 
* Extract Method 
* Inline Method; Inline Temp 
* Replace Temp with Query 
* Introduce Explaining Variable 
* Split Temporary Variable 
* Remove Assignments to Parameters 
* Replace Method with Method Object 
* Substitute Algorithm 
### Moving Features Between Objects 
* Move Method; Move Field 
* Extract Class
* Inline Class 
* Hide Delegate 
* Remove Middleman 
* Introduce Foreign Method 
* Introduce Local Extension 
### Organizing Data 
* Self-encapsulate Field 
* Replace Data Value with Object 
* Change Value to Reference; Change Reference to Value 
* Replace Array with Object 
* Duplicate Observed Data 
* Change Unidirectional Association to Bidirectional 
* Change Bidirectional Association to to Unidirectional 
### Simplifying Conditional Expressions 
* Decompose Conditional 
* Consolidate Conditional Expression 
* Consolidate Duplicate Conditional Fragments 
* Remove Control Flag 
* Replace Nested Conditional with Guard Clauses 
* Replace Conditional with Polymorphism 
* Introduce Null Object 
* Introduce Assertion
### Making Method Calls Simpler 
* Rename Method 
* Add/Remove Parameter 
* Separate Query from Modifier 
* Parameterize Method 
* Replace Parameter with Explicit Methods 
* Preserve Whole Object 
* Replace Parameter with Method
* Introduce Param eter Object 
* Remove Setting Method 
* Hide Method 
* Replace Constructor with Factory Method 
* Encapsulate Downcast 
* Replace Error Code with Exception 
* Replace Exception with Test 
### Dealing with Generalization 
* Pull Up Field; Method; Constructor Body 
* Push Down Method; Push Down Field 
* Extract Subclass; Extract Superclass; Interface 
* Collapse Hierarchy 
* Form Template Method 
* Replace Inheritance with Delegation (or vice versa) 
### Big refactoring
* Nature of the Game 
* Tease Apart Inheritance 
* Convert Procedural Design to Objects 
* Separate Domain from Presentation 
* Extract Hierarchy

## Examples

### Encapsulate downcast

A method returns an object that needs to be downcasted by its callers. 
Refactor by moving the [[downcast]] to within the method.

```csharp
Object lastReading() { 
	return readings.lastElement(); 
}
```

```csharp
Reading lastReading() { 
	return (Reading) readings.lastElement(); 
}
```

### Consolidate Conditional Expression

You have a sequence of conditional tests with the same result. 
Refactor by combining them into a single conditional expression and extract it.

```csharp
double disabilityAmount() { 
	if (_seniority < 2) return 0; 
	if (_monthsDisabled > 12) return 0; 
	if (_isPartTime) return 0; 
	// compute the disability amount
```

```csharp
double disabilityAmount() { 
	if (isNotEligibleForDisability()) return 0; 
	// compute the disability amount
```

### Consolidate Duplicate Conditional Fragments
The same fragment of code is in all branches of a conditional expression. 
Refactor by moving it outside of the expression

```csharp
if (isSpecialDeal()) { 
	total = price * 0.95; 
	send(); 
} else { 
	total = price * 0.98; 
	send(); 
}
```

```csharp
if (isSpecialDeal()) 
	total = price * 0.95; 
else 
	total = price * 0.98; 
send();
```

### Rename Method

The name of a method does not reveal its purpose. 
Refactor it by changing the name of the method.

```csharp
int getInvCdtLmt(){ 
	//… 
}
```

```csharp
int getInvoiceableCreditLimit(){ 
	//… 
}
```

### Pull Up Field

Two subclasses have the same field. 
Refactor it by moving the field to the superclass.

![[Pasted image 20250512102714.png]]

### Push Down Method
Behaviour on a superclass is relevant only for some of its subclasses. 
Refactor it by moving it to those subclasses.

![[Pasted image 20250512102744.png]]

