# Singleton pattern

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

