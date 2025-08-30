# Intro + contents

I will be talking about my groups exam project Breakout, a classic Atari game

I will go through
1. Core problems that I've come across
2. Design solutions for these problems
3. Implementation with respect to some design decisions
4. Testing implementations and evaluating the program
5. Final remarks
# Core problems

First, ill pick out some problems that i have come across while constructing the game.
These problems have demanded good game design.

These are: 
- Information-sharing between many classes
- Ensuring extendibility throughout the program

Why can design help us with these types of problems?
A game can increase wildly in complexity when you get further ahead and when requirements change.
Therefore well thought out design and design patterns can make the program
- easily extendible
- maintainable
- testable
- readable
Good design therefore makes the development proces much easier for all developers and minimizes risk of bugs and errors.

This is partly done by writing some SOLID code!

> The enemy of great design is changing requirements.
# Design - Ensure extendibility

An example of where we used a design pattern is the block factory.
It is responsible for building blocks based on its parameters

This pattern is great for generating various objects of the same family.
It upholds the open/closed principle by isolating the creational logic from the available blocks.

> No need to change `CreateBlock` or the client code that uses it.
> Switch case option couples logic with available blocks

It does however introduce extra complexity and makes it harder to extend the code with more blocks.
## Example - block factory

Here, it you want to add another block, you'd have to alter the code in three places.
You'd have to
1. create the block
2. extend the enum with a type
3. and extend the dictionary within the factory
# Design - Tight coupling between classes

Another of these problems are tight coupling.
When for example a block is deleted, a powerup may be spawned.
Do we really want the blocks and powerups to be coupled together? 
And should we then couple our powerups to the player?

No - this results in tight coupling.
Tight coupling makes a system hard to test, extend and changes might ripple through the system in unintended ways.

Our solution to this was utilizing the eventbus provided by DIKUArcade
# Design - Handling of events

The eventbus is an observer-like functionality that we've designed as a singleton.
This is to ensure that all subscribers subscribe to the same bus. 

The event bus results in looser coupling since 

>What are we solving?   
        Looser coupling
        Open/Closed Principle
        You can introduce new subscriber classes without having to change the publisher’s code (and vice versa if there’s a publisher interface).

This is very easy to extend, because all classes can subscribe to and publish events to the eventbus without having to couple themselves to each other.

This ideally replaces the need for unnecessary dependencies between movable objects.

> example please

This does make the objects "dumb" in the sense that some objects have non knowledge of the sender of the message.

Therefore, sufficient information must be passed in the event.

>example: the ball death animation has no knowledge of the ball, it only receives the ball's location

# Implementation - collision detection

So how did we implement collision detection in the game?
Here, the ball(s) depends on the player and the balls in order to detect collisions.

This creates high coupling between seemingly unrelated classes. 
This makes the ball hard to test as a unit and violates the principle of:

- interface segregation
	- The ball only needs the extend and position for the player, it doesn't need to depend on the entire player class
	- clients shouldn’t be forced to depend on methods they do not use.
- single responsibility
	- the ball now has responsibility for collision detection.
	- It has several reasons to change now and handles too much functionality

> - Dependency Inversion Principle:
> 	The ball should depend on an abstraction
> 	e.g. ICollidable 


## fix this paragraph: 
Here, `gamerunning` is calling the strategy's `Move()` function
✅ Keep Ball class simple
❌ Breaks encapsulation

```csharp
ballContainer.Iterate(ball => {
	ball.DetectCollision(level, player);
	ball.MovementStrategy.Move(player, ball);
});
```

If i were to refactor: have the ball call the `Move()` method
Then it can pass `this`, reduces maintainability and Extensibility 

# Suggested improvement

I have come up with a solution to this issue caused by poor design choice
My proposal is to introduce a `CollisionDetector` mediator pattern.

This mediator would handle collision between it's subscribers on notify them when one has happened.

It has the benefit of encapsulating inter-object behavior and takes responsibility from the ball as an example.

> ✅ Use spatial partitioning or bounding volume hierarchies to reduce collision checks

It may introduce some downsides if not implemented carefully:
- It is a single point of failure - if it stops working, no collisions may work
- It may become a class with too much responsibility and functionality

> Fix: make relation specific mediators with tailormade functionality:
> 	ball - wall collision detector
> 
> You could add conditional checks
> 	"only check if ball - player collision if ball is below a certain point 
# Implementation - ball movement

The balls movement is at the moment tightly coupled to collision detection.
The ball is provided with a movement strategy from the game state.

This provides rather low coupling between how the ball moves and the ball and separates functionality.

This also enables movement strategy change at runtime.

Our implementation does however have some drawbacks:
- The DPI is violated 
- And it breaks encapsulation
	- ➡ `GameRunning` directly depends on `Ball`'s concrete internals (e.g. its `Strategy`).
	- ➡ `GameRunning` should depend on a higher-level abstraction (like `IMovable` or just trust `Ball.Update()`).

> In another world, **state pattern** would have fit better
> 	This provides better encapsulation.
> 	Game running now depends on the balls movement strategy
> 
> Game Running shouldn't control movement of the ball
> 	This spreads behavior responsibility and creates tight coupling between `Gamerunning` and movement logic.
# Testing

So how did we test Breakout?
Regression testing
Our primary testing strategy has been specification testing. 

> Mainstream usage testing (normal inputs)

“Although we didn’t apply white-box testing, parts like our level loader or collision handling could benefit from **branch or path coverage analysis**.”

DPI

Units preferably dont have side effects

Unit testing
**pros**
- Testing of unit against its specification
- Decrease future maintenance
- Reduce uncertainty in module behavior
- Detect specification violations early
**cons**
- Does not exploit knowledge of source code (*example*)
- May not exercise all the source code 
	- May overlook errors in rarely executed branches

Integration testing
- High code coverage
- Detecting bugs in early development
- Test modules as groups
- Performed after unit testing
- Requires real dependencies and finished code

Testing is as a systematic process of finding errors, evidence of code not satisfying its specification
Test design is as a methodology for finding as many errors as possible with limited data, human and system resources.

> Boundary Values

# Would have used:

Regression and back-to-back testing for collision detection
Maybe Performance Testing
Limit Testing (testing the .txt input)
Stress or Smoke Testing (number of elements on screen)
	No specified limits
Security Testing (try and increase rewards)
Usability Testing (have my mom play the game)
User Documentation Testing (first create documentation, then test it)
	Test all instructions given in the documentation

## White box testing

How?
Add preconditions as predicates that can be checked at run time *or as types, which are checked by the compiler*

Specify which exception to raise

Assert postcondition by changing type of output to accommodate calculation

Create a control flow graph

Branch coverage may not be necessary

- **All invocations of a virtual method in all subclasses of class sequences have to be tested.**
- Methods from different layers in the inheritance hierarchy work in different combinations together and have to tested in (all) possible combinations.

Should have grouped into queries and commands

Specification-driven testing: 
Test cases are created with use of equivalence classes based on the specification. 

Structure-oriented testing: 
Test cases are derived from coverages of the source code.

A lot of changes require a lot of testing.
# ekstra

Responsibility-Driven Design
Here, explain why we chose that some classes should keep track of collision and not others
Especially with SOLID in mind and with this:
![[Pasted image 20250612223009.png]]
