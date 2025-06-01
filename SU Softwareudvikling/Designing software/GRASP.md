# GRASP

> [!NOTE] Definition
> **G**eneral **R**esponsibility **A**ssignment **S**oftware **P**atterns

## GRASP patterns

### Information Expert
(cf. information hiding) 
Determines where to delegate responsibilities, e.g., methods and computation
### Creator
Who is the creator?
Determines responsibility for object creation
### Controller
Who is pushing things - can be confusing?
Non-user interface object responsible for receiving or handling system events
### Low Coupling
Measures of how strongly one element is dependent on other elements
Low amount of interactions between components

![[Pasted image 20250311145153.png]]
### High Cohesion
cf. Code Complexity lecture B4-03
Responsibilities of given set of elements are strongly related and highly focused on rather specific topic
All necessary functionality should be coupled within the component.

![[Pasted image 20250311145237.png]]
### Polymorphism
Defining variation of behaviours based on type is assigned to the type for which this variation happens
### Pure Fabrication
Entity is service and does not represent concept in problem domain.
### Indirection
Assigns responsibility of mediation between them to intermediate object instead of direct connection (man-in-the-middle)

*Enter a IP-address which is translated to another, decouples access to address.*
Single point of failure
### Protected variations
Protects elements from variations on other elements by wrapping focus of instability with interface and using polymorphism (cf. OCP)

You need to variate things, fx. in an [[Abstract factory]].
