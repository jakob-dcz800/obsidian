# Testing of Object-Oriented Programs

Object-oriented programming may lead to complex situations that are difficult to test between the code segments (methods)

- Execution of a method may update the state of the object
	- and of any other object it can reach, changing that may influence later executions.

>Every call of `Add` changes the state of the list object.

- Inheritance creates (hidden) dependencies. 
	- The code executed in a subclass may be "far away"
- Overriden methods/dynamic binding lead to duplication of possible paths
	- The method called in a class may or may not be the method declared in the same class
- Encapsulation by of the object state complicates the testing of methods whose properties depend on the state the object is in
	- The creation of an object in a certain state may be difficult
	- Requesting a state is possibly difficult

## Object oriented complications

Consequences of the use of specialization/inheritance:

- Errors in the superclass are inherited by the subclass.
- Testing of the subclasses is not possible without including the superclass. (makes composition better)
- Changes in superclass always require retesting of all subclasses. 
- Objects of subclasses can replace the objects of the super classes (LSP): 
	- If the software is tested with references/pointers to superclasses, then objects of all subclasses eventually have to be included in the testing, too. 
	- If a subclass is changed, the usage of the superclass may have to be checked too.

Consequences of the use of dynamic binding (virtual methods):

- The program flow cannot be derived from the program code. 
- **All invocations of a virtual method in all subclasses of class sequences have to be tested.** 
- Methods from different layers in the inheritance hierarchy work in different combinations together and have to tested in (all) possible combinations.

## Testing

Helpful for testing of object-oriented programs is to **group** the methods into stateless methods, commands and queries.

- Stateless methods (functions): 
	- The state of the object has no impact on their behavior
	- Thus, there are no dependencies between the method calls and by this, there are no sequences of calls necessary to bring the object into a certain state
- Queries: 
	- The method does not update the state; only the input/output relation has to be tested.
- Commands:
	- The state has impact on the behavior of the methods.
	- Commands have to be called to put an object into a certain state.

## Operationalization of Test Realization

To increase trust in the correctness of the implementation, it is necessary to execute **always**
Specification-driven testing (black box) and structure-oriented testing (white box) together.

- Already small examples show that often a (very) high number of test cases are needed. 
- The execution of tests has to happen systematically. 
- Tests have to be documented comprehensibly. 
- Tests have to be repeated after every change of the software.