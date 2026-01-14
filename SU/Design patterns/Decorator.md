---
tags:
  - Pattern
  - Software-development
---
# Decorator pattern

**Decorator** is a structural design pattern that lets you attach new behaviours to objects by placing these objects inside special wrapper objects that contain the behaviours.

Allows the creation of heterogeneous (diverse in character or content) [[stack]] structures.

The class diagram leaves the impression, that the Decorator pattern is a simplified form of the [[#Composite patterns|Composite]] pattern. But decorator patterns are used with an entirely different purpose.
![[Pasted image 20250612120723.png]]

![[Pasted image 20250310102604.png]]

The atom is the base component which the interface must have.

Object pattern (during runtime) - not a class pattern.

The idea is to build **sequential structures**.

![[Pasted image 20250310102134.png]]
![[Pasted image 20250310102159.png]]

• A stack consists of structurally different elements, 
	• the last element without a successor and 
	• preceding elements, which have exactly one direct successor. 
**• The different elements offer different attributes and different behaviour.** 

* You can instantiate the decorators in an order and get desired behavior. 
![[Pasted image 20250612122124.png]]
• But the attributes and behaviour refer with regards to content always to all the following elements. 
**• Each additional element expands (= decorates) the existing elements.** 
• The entire stack has the same semantics like its second element. 
• Requirement: All elements must offer the same interface to the outside

• Application scenarios for such stacks: 
	• Further properties (= previous items) should be added dynamically to an output object (= the last element). 
	• With the addition of a property, the overall behaviour of the stack has to be changed, too. 
	• The order, in which properties can be added, should be arbitrary. 
	• The properties should also be able to be removed.