# Façade pattern

Goal is **simplification**. Hiding complexity behind a façade. Take a complex [[Terminology#Interface (Object-oriented programming)|interface]] and hide some functionality.

Pros:
* Access is simplified
* **decoupling**
* isolation of faults
* easy to do
Cons:
* Façade can be big and complicated
* It’s a **bottleneck** of functionality
* A facade can become [a god object](https://refactoring.guru/antipatterns/god-object) coupled to all classes of an app.

![[Pasted image 20250612114325.png]]
## Use when

Use the Facade pattern when you need to have a limited but straightforward interface to a complex subsystem.

 Use the Facade when you want to structure a subsystem into layers.
