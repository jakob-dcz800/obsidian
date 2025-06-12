# Singleton pattern

Use the Singleton pattern when a class in your program should have just a single instance available to all clients; for example, a single database object shared by different parts of the program.

Use the Singleton pattern when you need stricter control over global variables.
Unlike global variables, the Singleton pattern guarantees that there’s just one instance of a class. Nothing, except for the Singleton class itself, can replace the cached instance.

 [Abstract Factories](https://refactoring.guru/design-patterns/abstract-factory), [Builders](https://refactoring.guru/design-patterns/builder) and [Prototypes](https://refactoring.guru/design-patterns/prototype) can all be implemented as [Singletons](https://refactoring.guru/design-patterns/singleton).
## Description

A Singleton ensures that there is only one single object from a class.

Motivation: 
	• There are classes, of which only one object can exist at runtime. 
	• Example: Assigning unique keys, such as order numbers, customer numbers, etc.

Idea: 
	• The class itself ensures that there is only one object: 
	• The implementation depends on the possibilities of the programming language. 
	• Access to constructors must be restricted, (e.g. by preventing access: The constructors are agreed privately! 
	• Instead of the constructor, special static methods control the creation of only one object.

> [!Important]
> Please be very sure that its relevant before using, since it is very overused and easy to understand. Have a very good motivation -comes with a heavy pricetag.
> \- Boris Düdder

Construct a [[Static#static keyword|static]] class method, and a self-reference.

Problem: 
	Concurrent processes (threads) can overlap during production!
	Single point of failure
	All calls go through `singleton.GetInstance()`
	It's replacing global variables - which are bad.
	Safer (and more cumbersome) ways are to pass around refs (prop-drilling).

Advantage: Shared object between entities, acces via one control point: 
	`singleton.GetInstance()`

There are frameworks that do this better, and provide much more functionality.

![[Pasted image 20250311133315.png]]

![[Pasted image 20250311134523.png]]

![[Pasted image 20250311134555.png]]

![[Pasted image 20250311134606.png]]

## Pros and cons

❌ Violates the _Single Responsibility Principle_. The pattern solves two problems at the time.
❌ The Singleton pattern can mask bad design, for instance, when the components of the program know too much about each other.
❌ The pattern requires special treatment in a multithreaded environment so that multiple threads won’t create a singleton object several times.
❌It may be difficult to unit test the client code of the Singleton because many test frameworks rely on inheritance when producing mock objects. Since the constructor of the singleton class is private and overriding static methods is impossible in most languages, you will need to think of a creative way to mock the singleton. Or just don’t write the tests. Or don’t use the Singleton pattern.

✅ You can be sure that a class has only a single instance.
✅ You gain a global access point to that instance.
✅ The singleton object is initialized only when it’s requested for the first time.