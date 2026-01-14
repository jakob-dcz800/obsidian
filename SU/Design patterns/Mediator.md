---
tags:
  - Pattern
  - Programming
  - Software-development
---
# Mediator pattern

Use the Mediator pattern when it’s hard to change some of the classes because they are tightly coupled to a bunch of other classes.
The pattern lets you extract all the relationships between classes into a separate class, isolating any changes to a specific component from the rest of the components.

Use the pattern when you can’t reuse a component in a different program because it’s too dependent on other components.
## Description
A mediator promotes the loose coupling of objects by avoiding an explicit relationship between the involved objects.

• Idea: 
	• An object operates as an intermediary between the other objects. 
	• Communication between all involved objects always takes place via the intermediary. 
	• Further objects can be connected very easily.
A lot like the [[Façade]] pattern

[[Loose coupling]]

• Comparison with the facade pattern: 
	• A facade provides a more convenient **interface to simplify the use**. 
	• A facade supports a **unidirectional** protocol between classes. 
	• A **mediator supports multidirectional protocol** to simplify the collaboration of objects. 

• The observer pattern can be used for support: The mediator observes partners to determine their communication needs.

• Remarks: 
	• The distribution of the behavior to many objects is usually the basis for the good changeability and reusability of object oriented systems. 
	• But: Too many relationships between too many objects reduce the changeability and reusability because building such object structures is complex.

![[Pasted image 20250311131656.png]]

![[Pasted image 20250311132451.png]]