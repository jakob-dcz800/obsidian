## Complexity
There are many interconnections, this is a sign of complexity

### fix
keep it modular
interactions contained in the class

- Best case is simple interface, a lot of functionality
    - good abstraction, hiding complexity

Classes are organized in layers.

give a good example
and a bad example from the code

**Make one sequence diagram**

## Things to improve

Exception handling
Always expect the unexpected... Catch exceptions!
Test with exceptions as well (Assert exception)

Call-backs for looking for collisions

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

