# Mediator pattern

A mediator promotes the loose coupling of objects by avoiding an explicit relationship between the involved objects.

• Idea: 
	• An object operates as an intermediary between the other objects. 
	• Communication between all involved objects always takes place via the intermediary. 
	• Further objects can be connected very easily.
A lot like the [[Façade]] pattern

[[Loose coupling]]

• Comparison with the facade pattern: 
	• A facade provides a more convenient interface to simplify the use. 
	• A facade supports a unidirectional protocol between classes. 
	• A mediator supports multidirectional protocol to simplify the collaboration of objects. 

• The observer pattern can be used for support: The mediator observes partners to determine their communication needs.

• Remarks: 
	• The distribution of the behavior to many objects is usually the basis for the good changeability and reusability of object oriented systems. 
	• But: Too many relationships between too many objects reduce the changeability and reusability because building such object structures is complex.

![[Pasted image 20250311131656.png]]

![[Pasted image 20250311132451.png]]