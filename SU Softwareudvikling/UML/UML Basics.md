---
tags:
  - Software-development
  - Design
---
	
# UML Basics

**Unified Modelling Language** is a standard for modelling [[Terminology#Object-oriented programming|object-oriented]] software. It is a general-purpose visual modelling language that is intended to provide a standard way to visualize the design of a system.

Serves as a cornerstone for effectively communicating software design
Provides standardized way to visualize architecture, design, and behavior of a system.

UML consists of four types of diagrams:
1. <mark style="background: #FFB8EBA6;">Use-case</mark> diagram
2. <mark style="background: #FFB8EBA6;">Class</mark> diagram
3. <mark style="background: #FFB8EBA6;">Sequence</mark> diagram
4. <mark style="background: #FFB8EBA6;">Activity</mark> diagram
## Relations
Dotted arrow is "implementation of", and [[Terminology#Inheritance|inheritance]] is solid line arrow. "Application" in UML diagram means the remaining software. 

**Inheritance**: "*is a*"
**Association**: "*has a*"
	Association: "*Host knows about guest*"
	Aggregate: "*Host has a copy of guest*" - Guest and host are independent of each other
	Composition: "*Host has a copy of guest*" - Guest makes no sense without guest

Example:
	Association: Students *know* each other (line)
	Aggregation: Students *have some* courses (hollow diamond)
	Composition: Students *has an* ID card (whole diamond)

Hollow diamond: a class is part of another class but can leave at any time

![[Pasted image 20250308231548.png]]

![[Pasted image 20250612121308.png]]
### UML in LaTeX

![[Pasted image 20250308231707.png]]

### Type binding



![[Pasted image 20250310112332.png]]
![[Pasted image 20250310112419.png]]

## Uni- and bidirectional association

![[Pasted image 20250613210524.png]]

## Associations

For two objects `Foo` and `Bar` we have:

**Dependency:**
```csharp
class Foo
{
    ...
    fooMethod(Bar bar){}
    ...
}
```

**Association:**
```csharp
class Foo
{
    private Bar bar;
    ...
}
```

**Composition:** (When `Foo` dies so does `Bar`)
```csharp
class Foo
{
    ...
    private Bar bar = new Bar();
    ...
}
```

**Aggregation:** (When `Foo` dies, `Bar` may live on)
```csharp
class Foo 
{
    private List<Bar> bars;
}
```

https://stackoverflow.com/questions/12604031/c-sharp-code-for-association-aggregation-composition

