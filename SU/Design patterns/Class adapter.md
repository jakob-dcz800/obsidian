---
tags:
  - Pattern
---
# Class adapter pattern
An adapter is used when ready-to-use solutions should be used, which do not fit exactly to the given requirements.
In particular, adapters are used when classes from libraries are to be used


Enables the connection of items with different [[Terminology#Interface (Object-oriented programming)|interfaces]].
An adapter is complete. Adapters are cheap, meaning generalized adapters should be considered. Functionality can be reused. If classes do not match, construct an adapter. 

Adapters can be cluttered and are hard to evolve and update. Multiple [[Terminology#Inheritance|inheritance]] ([[UML Basics#Relations|Aggregate]]) *can* be a solution to the adapter problem.

![[Pasted image 20250612112204.png]]
## Problem

Classes cannot communicate due to differences in parameters 

## Solution 

This is a special object that **converts** the interface of one object so that another object can understand it. 
It thus takes the needed object and transforms it.

## Pros / cons

_Open/Closed Principle_. You can introduce new types of adapters into the program without breaking the existing client code

_Single Responsibility Principle_. You can separate the interface or data conversion code from the primary business logic of the program.

The overall complexity of the code increases because you need to introduce a set of new interfaces and classes. Sometimes it’s simpler just to change the service class so that it matches the rest of your code.
## Use this when

Use the pattern when you want to reuse several existing subclasses that lack some common functionality that can’t be added to the superclass.

You could extend each subclass and put the missing functionality into new child classes. However, you’ll need to duplicate the code across all of these new classes, which [smells really bad](https://refactoring.guru/smells/duplicate-code).

The much more elegant solution would be to put the missing functionality into an adapter class. Then you would wrap objects with missing features inside the adapter, gaining needed features dynamically. For this to work, the target classes must have a common interface, and the adapter’s field should follow that interface. This approach looks very similar to the [Decorator](https://refactoring.guru/design-patterns/decorator) pattern.

## UML

![[Pasted image 20250612113958.png]]

Here, it inherits from two classes. This is not possible in csharp
[[Object adapter]]
