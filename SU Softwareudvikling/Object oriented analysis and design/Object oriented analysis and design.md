# Object oriented analysis

Structured process from problem to solution.

![[Pasted image 20250428112433.png]]

This can go on forever, but:
You are done when you go through it and dont discover something new.
## Domains

![[Pasted image 20250428102304.png]]
### Application domain

The environment in which the system is operating

### Solution domain

The available technologies to build the system

Application domain model is the analysis-part.

### Problem domain

Domain = subject area 
Problem domain = program topic/theme/subject

“A **problem domain** is the area of expertise or application that needs to be examined to solve a problem. A problem domain is simply looking at only the topics you are interested in and excluding everything else.”

## Domain Modelling

The goal of domain modelling is to understand how system-to-be will work

We do domain modelling based on sources: 
	• Knowledge of how system-to-be is supposed to behave (from requirements analysis, e.g., use cases) 
	• Studying the work domain (or, problem domain) 
	• Knowledge base of software designs 
	• Developer’s past experience with software design

### Use Cases vs. Domain Model

![[Pasted image 20250428102820.png]]
### 

Step 1: Identifying the boundary concepts
	Ask users, what do you need/provide to the system?
	These are boundary concepts
Step 2: Identifying the internal concepts

![[Pasted image 20250428103355.png]]

Boundary concepts are stable concepts, i.e. they don't change that much over time

## Use case: unlock

![[Pasted image 20250428103920.png]]

### Extracting responsibilities

![[Pasted image 20250428103944.png]]

Single responsibility approach

### Domain model

![[Pasted image 20250428104616.png]]

"is a"

Not UML
![[Pasted image 20250428104826.png]]

#### Extracting associations

![[Pasted image 20250428105458.png]]


#### Extracting attributes

![[Pasted image 20250428105659.png]]

### Traceability Matrix

![[Pasted image 20250428105920.png]]

![[Pasted image 20250428105943.png]]

This is a way to see what is meant in in respect to use cases.

## Pre- and postconditions

![[Pasted image 20250428111714.png]]

NOT UML:
![[Pasted image 20250428112008.png]]

![[Pasted image 20250428112143.png]]
