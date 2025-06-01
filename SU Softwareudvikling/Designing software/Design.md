# Design

60% of exam

[[SOLID]] and [[GRASP]] principles

What are reasons for unsuccessful applications? 
	• Putting more functionalities on classes 
	• Implementing tight coupling between software components (i.e., between classes). If classes are dependent on each other, then change in one class will affect other classes also How to overcome these problems? 
	• Need to use correct design 
	• Need to follow design principles (i.e., [[SOLID]] Principles, [[GRASP]] Principles) 
	• Need to choose correct design patterns

[[open-closed principle]]
[[Interface segregation]]
[[Dependency inversion]]

• SRP: There should never be more than one reason for a class to change. • OCP: Software entities should be open for extension but closed for modification • LSP: Functions that use references to base classes must be able to use objects of derived classes without knowing it. • ISP: Clients should not be forced to depend upon interfaces that they do not use . • DIP: • High level modules should not depend upon low level modules. Both should depend upon abstractions. • Abstractions should not depend upon details. Details should depend upon abstractions
## Bad smells

• `if`-Statement, which distinguishes types -> OCP  (try polymorphism instead)
• Interface methods, which do not have to be implemented (in most cases) -> ISP 
• Modelling of IS-A relations, which do not fit -> LSP (inheritance doesn't work)
• Interface Pollution -> ISP 
• FAT Interfaces -> ISP 
• Method names like: `UpdateAndSaveCustomer()`, `VerifyAndSaveData()` -> SRP 
• Class names like: `CustomerManager` -> SRP

## Queries

Are methods that do not return state - but a value might be derived from state

Commands and queries: Benefits 
• Any sequence of queries is guaranteed not change the state of an object. 
	• The same query executed multiple times always yields the same result 
• Query results can be memoized (stored and looked up in an efficient data structure rather than recomputed) 
	• [[Memoization]] is invalidated by commands. 
• Queries can be used to inspect the state of an object before and after a command without changing the object state 
	• Important for testing of objects: Invoking queries on an object does not change what the command does 
• Compose a method that needs to both update the state and return a result from a command, followed by a query

## Command

Changes state

## Interface contract

• Interface contract: Logical properties of object(s) formulated in terms of public methods that must be true. 
	• Server object(s) implementing the interface must satisfy these properties. 
	• Client object(s) using the interface must not cause a crash for any correct server object. 
• Class contract: Same as interface contract, but for class’s interface 
	• Contract must be satisfied by all instances of the class 
	• Contract must be satisfied by all instances of all subclasses of the class (Liskov Substitution Principle)

## Pre- and postconditions

• Precondition for method f: T → U 
	• Logical property P of v that must hold before executing the body of f 
• Postcondition for method f: T → U 
	• Similar logical property Q about result and/or updated object state after executing the body of f if the associated precondition P(v) holds. 
• There is no requirement for the postcondition to hold if the precondition is violated! 
	• Pre- and postconditions of public methods are part of interface contract 
	• Constitute partial specifications 
	• Frequent preconditions: x != null, n >= 0, et

If precondition is violated, postcondition cannot be upheld.

![[Pasted image 20250317110013.png]]

## Object invariants

• Object invariant: 
	• Logical property P that must hold of all internal states an object is in. 
	• Must be preserved under all state updates. 
• Useful for proving post-conditions 
	• E.g., Invariant to prove that: counter >= 0.

## Class invariants

• Preconditions P and postconditions Q describe properties of individual methods 
• Need for global properties of instances which must be preserved by all routines 
	$0 \leq nb_{elements}$
	$nb_{elements} \leq max_{size}$

![[Pasted image 20250317113907.png]]

• A class invariant is an assertion appearing in the invariant clause of the class. 
• Must be satisfied by all instances of the class at all “stable” times (instance in stable state): 
	• on instance creation 
	• before and after every remote call to a routine (may be violated during call) 
• A class invariant only applies to public methods; private methods are not required to maintain the invariant.

**Class invariants only works in respect to observable behavior.**

![[Pasted image 20250317114222.png]]
# Design by contract

DBC

• Compositional system design 
	• Contractual relationship between server designer and client designer 
	• Server and client code can be changed freely without informing counterparty if contract is still satisfied by changes 
• Compositional system testing 
	• Interface contract serves as (partial) specification for generating test suite 
• Run-time contract monitoring (assertion checking) 
• Example: Ariane 5 crash, $500 million loss 
	• Conversion from a 64 bit # to 16 bit 
	• The number didn’t fit in 16 bits 
	• Analysis had previously shown it would, so monitoring that assertion was turned off

• Any time that two objects are interacting in a piece of software, there should be '**rules of engagement**' that specify the **protocols** for the interaction. 
1. What are the expectations of the client? 
2. What services does the supplier offer? 
3. Are there conditions or restrictions on either party? 
4. Who benefits from the exchange? 
• The idea behind DBC is that there should be a 'legal contract' that establishes answers to all of these questions.

• Recall the metaphor of wearing different hats 
	• Designer, Implementor, Client 
	• What are each of these responsible for? 
• In the DBC model, each of these takes on a specific role with respect to the contract 
	• The Designer is the Lawyer: creates the contract that binds the other two parties 
	• The Client and the Implementors are each party to the contract and therefore each have obligations and benefits


• Generally speaking, when two parties enter into a contractual relationship the obligations of Party A are viewed as a benefit by Party B, and the obligations of Party B are viewed as a benefit by Party A. 

• Examples: 
	• Employment contract 
	• Consignment shop contract 
	• International Treaty (e.g., NATO)

• Recall: the only mechanism that C# provides for objects to interact is what? 
	• Methods and method calls 
• So, it is regarding the method signatures that the contract must be written, since that is what forms the interface between the objects. 
	• What does a client need to know? 
	• What does a client NOT need to know? 
	• What does an implementor need to know? 
	• What does an implementor NOT need to know?
	
![[Pasted image 20250317113036.png]]

# Defensive programming

Want to make sure that pre- and postconditions are assured

• Defensive programming accepts all type-correct inputs to methods (no preconditions) and adds if-then-else code to handle unexpected inputs (null reference, negative number,...)

No assumptions about incoming props/inputs.

Often results in redundant checks (both client and server objects may check the same condition)

• In Design by Contract mutual responsibilities of server object and client object 
	• prevent redundant checks (checked at most once at all at run time) 
	• avoid error handling code (that should never be executed anyway) 
	• provide a (partial) specification of functionality

![[Pasted image 20250317114509.png]]![[Pasted image 20250317114728.png]]
![[Pasted image 20250317114759.png]]
![[Pasted image 20250317114817.png]]
