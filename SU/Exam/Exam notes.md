---
tags:
  - Assignment
---
You may very well get questions about the structure of your GitHub repository, teamwork, pair-programming, associations and responsibilities of code concepts, and more.

A **system** is a set of interconnected components with a well-defined interface to its environment
## To-do

- Go through code and decide whether functions are commands or queries
	- Object modelling
- UML Sequence for power ups and picking those up
	- Or just a sequence diagram (not UML)
- Understand cohesion
- White box testing
	- Create a control flow graph
- implement DRY (dont repeat yourself)
- **Stubs and drivers**
	- Along with strategy
- sig noget om refactoring når man foreslår ændringer
- Arrange, act, assert (PlayerTests)
- Code smells

Consider the merits and trade-offs of each alternative by applying the design principles

**Design**: The process of converting the system specification (requirements) into a software structure that realizes that specification.

![[Pasted image 20250617193830.png]]
![[Pasted image 20250617221105.png]]
![[Pasted image 20250617223925.png]]
![[Pasted image 20250617224507.png]]
## Complexity
There are many interconnections, this is a sign of complexity

For each list of things in the power point, come up with one extra point that is omitted
### fix
keep it modular
interactions contained in the class

- Best case is simple interface, a lot of functionality
    - good abstraction, hiding complexity

Classes are organized in layers.

give a good example
and a bad example from the code

**Make one sequence diagram of movement**
Maybe a class diagram with an instance of a class?

## Testing

![[Pasted image 20250613103014.png]]

If you use an interface, you can "mock" interfaces and inject stubs
Nice code == easy to test
![[Pasted image 20250613180246.png]]
## Things to improve

distinctions between **analysis vs. design**

Exception handling
Always expect the unexpected... Catch exceptions!
Test with exceptions as well (Assert exception)

Call-backs for looking for collisions
![[Pasted image 20250428112433.png]]
### Oh the smell!

Go through smells in the code

### The patterns we've neglected

We **could** have used a [[Façade|facade]] for game running
Good for layering, may have become a god object

Balls could very well have been a composite object. I.e. when it doubles, nodes are created

Do we have a decorator/wrapper component? 
Powerups might be a wrapper for the base component unless it is an abstract class + can they be a stack of stacked behavior. 
If they are not a decorator, they should have been

We use **strategy** for ball movement and player movement?
Ball is also strategy since it is decided externally.
	State is a field that decides behavior within the class while strategy provides methods

**Iterator** could be used to abstract ball iterations and block iterations and more

Observer is just events
Right now, game running acts as a mediator between registering events

Timer should have been a singleton, to control the global variables better

![[Pasted image 20250612120344.png]]Make object diagrams

![[Pasted image 20250612145025.png]]

Evaluate design


## Player strategy

Resembles the decorator **not** exactly the strategy
The decorator then holds strategies that can apply to the player

## Covariance

> _Covariance lets you safely go “up” an inheritance hierarchy when producing/returning values._

#### Covariance does NOT apply
- When passing values _in_ (parameters) → that’s **contravariance**

## Inheritance

Prefer composition over inheritance
Inheritance forces implementations. Not all power ups need disengage() and setup()
> Change is the enemy of perfect design


![[Pasted image 20250613181618.png]]
![[Pasted image 20250613181635.png]]

## Object modelling


Application domain: The environment in which the system is operating
	**what** the system needs to do
Solution domain: the available technologies to build the system with
	**how** it will be implemented using specific technologies and programming concepts.



![[Pasted image 20250614143201.png]]
![[Pasted image 20250614143909.png]]

![[Pasted image 20250617150931.png]]