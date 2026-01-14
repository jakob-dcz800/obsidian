---
tags:
  - Programming
  - Software-development
  - Design
---
# Liskov substitution	

LSP

“Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program” 

“Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.”'

It is a particular definition of a subtyping relation, called **behavioural** subtyping.
If S is a subtype of T, then objects of type T may be replaced with objects of type S without altering any of the desirable properties of that program

> [!NOTE] LSP
> As you extend objects the original functionality of the elements that makeup the object should not change. Any Base 10 calculator should produce a result of “4” when you press “2+2=“ regardless of the age or sophistication of the device. The original functionality of objects should preserved as you build on them.

Keys are (must-haves):
	• Polymorphism 
	• Test-Driven Development (TDD) 
	• Avoid Run-Time Type Information (RTTI)