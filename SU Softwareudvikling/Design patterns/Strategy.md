# Strategy pattern

Operations should be independent from data structures

![[Pasted image 20250310104126.png]]

A Strategy pattern allows to change the behaviour of the methods of an object during execution.
Decision is done internally in `AClass`

• Examples: 
	• Arranging graphical elements in a window: Next to each other, among each other, in a grid, 
	• Design of text formatting: Left-aligned, right-aligned, centred,
• But: 
	• Various types of behaviour should be provided, without expanding the class of the executing object. 
	• The behaviour is supposed to be established only after the declaration of the class of the executing object.

### Idea of construction

• The behaviour, which has to be changed, is [[Terminology#Encapsulation|encapsulated]] in a separate strategy class, which maintains a given interface.
• The behaviour of a strategy object is accessed during the execution. 
• If changes are made, the strategy object is replaced

[[Design patterns]]

![[Pasted image 20250612123007.png]]

![[State#Difference between state and strategy]]
