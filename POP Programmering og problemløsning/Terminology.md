---
tags:
  - POP
  - Programming
---
# Terminology

[[#Lingo]]
[[#Basics]]
[[#Interface]]
[[#Data types]]
[[#Testing]]
[[#Programming paradigms]]
[[#Runtime]]
[[downcast]]
## Lingo

### Programming vs. coding
**Programming** consists of:
1. **Specification**: What is computed? Which functions, what are their properties?
2. **Coding**: How is it computed? How are the functions implemented (“code”)?  
3. **Verification**: Which explicit evidence is there for the program code meeting its specification (correctness)?  

Verification always requires both, program code and specification.  
	Program code may be correct with respect to one specification and incorrect with respect to another specification. 
Avoid statements such as “My code works”.  
	With respect to which specification?  
	Does it always work and can you provide conclusive evidence for that, for all valid inputs and in all conceivable contexts, or just sometimes?

### Properties
A **logical statement** is a statement that is either true or false
A **logical property** of one or more functions is a true logical statement involving the function(s).

A universally quantified property has the form $∀x, y, . . . , P(x, y, . . .)$. 
In words: For all $x, y, . . .$ the property $P(x, y, . . .)$ is true.
Examples:  
	For all $x ∈$ Number, add `x (I 0) = x`.  
	For all $x ∈$ Number, add `x (F 0.0) = x`

### Specification
Module specification: Contract between user and implementor.  
	In F#: Written in `.fsi` file.  
	User to implementor: “All I want to know needs to be written in the module specification 
	(`.fsi` file). How I use it is none of your business.  
	Don’t make me look at your code.”  
	Implementor to user: “All you need to know is written in the module specification (.fsi file). How I implement it is none of your business.
	Don’t ask to look at my code.”  

What if specification and code are inconsistent?  
	If you cannot change the specification: Fix your code.  
	If you can change the specification without negotiation with users: Fix either code or specification. 
	Otherwise: Negotiate a change of specification with the users.  
	
Common problem: 
	Most modules are underspecified. User tries out code and relies on unspecified behaviour of implementation. 
	Implementor subsequently changes the code. Changes propagate to user code and cause hard-to-detect and hard-to-localize errors

### Computations and side-effects
Plus is a computation. It has no side effect.
Separate computations (no side effects) and actions (side effects)
## Basics

### Value
A value is a mathematical object such as the number 5, a particular string, a pair of values, a memory reference.

Most values can be denoted by a literal (also called value expression)
	5, "Bob", (5, "Bob").  
	
There are no literals for memory references in F#.  

### Literal
In computer science, a **literal** is a textual representation (notation) of a value as it is written in source code.

### Function

### Function value
A function value is a [[#Value|value]] of [[#Function|function]] type.  
A function value is represented at run time by a function closure (aka [[lexical closure]]) of the form 
($b, λx.e$) where
	$x1$, . . . are the formal parameters (parameter names);  
	$e$ the function body;  
	$b$ is an environment consisting of a binding for each name that occurs $e$, but is not a formal parameter, if any
#### Example
$({x = 18}, λy.x + y)$
Represents the mathematical function that maps $y$ to $x + y$ where $x = 18$
The function value $({x = 18}, λy.x + y)$ can be written as

```kotlin
let x = 18  
fun y -> x + y  
```

Function values are ordinary values; for example, they can be elements of lists, and they can both input and return (other)
## Interface

## Data types

### Types
Types define valid input and output to a function
A type denotes a set of values; e.g.  
	`int`
	`int list`
A type is not an object that is stored in memory at run time.  
	A type is not value.  
	Types and values are different “kinds of things”.  
	Values are elements of types.  
	Types are *not* elements of types.  

An expression is evaluated to a value.  
A definition is a binding of an expression to an identifier (variable).  
For example, `x + 8` is evaluated to `17` if `x` is bound to the value `9`

In F#, types are checked early, before the program executes. This is called [[#static type checking|static type checking]].
### Abstract data type (ADT)
An abstract data type (ADT) is a type together with operations on the type and a precise description (specification) of what operations do. 

An **ADT** consists of 
- an [[#Interface|interface]] containing the declarations of the [[#Types|type]], its operations ([[#Function|functions]]) and their [[#Specification|specification]] (what they do)
- an implementation containing the definitions (source code) of the operations
- examples illustrating use of the operations

>[!NOTE]
ADT form the foundation for the concept of classes. In languages that support classes, you can implement each abstract data type as its own class. 
**Classes** usually involve the additional concepts of [[#inheritance]] and [[#Polymorphism|polymorphism]]. One way of thinking of a class is as an abstract data type plus inheritance and polymorphism.
### Recursive data types

### Generic type
A generic type is a type that is parameterized by one or more type parameters.

Other terms for “generic type” are 
	(parametric) polymorphic type, 
	parameterized type
	type constructor

The [[#Types|type]] `’a list` is the type of built-in F# lists with elements of type `’a`, where `’a` is a type parameter that can be instantiated to any type, for example
- `int list`
- `string list` 
- `int list list`
- `’a list list`

`T list` is synonymous with `list<T>` in F#

### Discriminative unions

Union of two or more [[Serier og sæt#Sets|sets]] in mathematics: the set of elements in any of the sets. 
	We don’t know from which set an element in the [[Serier og sæt#Union|union]] comes from
	It could occur in multiple input sets.

Discriminative union (aka disjoint union): The union of two or more sets whose elements are tagged to indicate unambiguously from which set they come.  
	Common mathematical notations: $S \cup T$ or $S + T$ 
	(Note: Tag is not explicitly mentioned.)  
	In F# (schematically):  

```fsharp
type U = CFun1 of T1 | ... | CFunk of Tk
```

Introduces constructors `CFun1 : T1 -> U, ..., CFunk : Tk -> U`, which serve as tags and can be used in pattern matching.  
	Constructors must have a capital first letter.  
	of unit may be left out; then constructor has type U. 
#### Example

```fsharp
type Number = I of int | F of float

let add (v: Number) (w: Number) =  
match (v, w) with  
	(I i, I j) -> I (i + j) // integer addition  
|   (I i, F j) -> F (i + f) // float addition  
|   (F i, I j) -> F (i + f) // float addition  
|   (F i, F j) -> F (i + f) // float addition
```

## Testing

Testing is (partial) verification by
	executing code on inputs and checking whether the result is evidence of a [[#specification|specification]] violation
	systematically constructing the inputs to maximize their likelihood of demonstrating a specification violation.  

### Testing terminology:  
**Formal verification**: Mathematical proof that there exists no valid input that results in a specification violation.  
	**Testing**: The systematic discipline of finding “nasty” inputs that maximize the likelihood of finding specification violations.  
		Not being able to “break the code” is taken as evidence (not proof) that the code may be correct with respect to its given specification. 
	**Trying out, illustrating, exemplifying**: Applications of the code showing that it satisfies its specification for some inputs (if there is a  specification) or that it does something useful (if there is no specification, only informal requirements).  
	
*Don’t use the term “test”* unless you have both specification and code and you are systematically looking for specification violations.
	Use “illustrate” or “exemplify” or “try out” instead
### Specification-driven function testing
Recall: All forms of testing require both specification and code.  
	No specification, no testing.  
Specification-driven function testing: Analyse specification and systematically 
	find valid inputs with maximal likelihood to expose a specification violation of the code
	determine corresponding expected outputs from the specification.  
		Don’t look at the code in this process.  
Also called specification-based testing, external testing, [[#Black-box testing|black-box]] testing. 
	“Black-box testing” is not used here since unfortunately much nonsense is written on the web on that
### Unit testing

### Input partitioning
Input partitioning is a method for testing specifications.  

Given a function specification, partition its valid inputs into a finite set of partitions, that is into pairwise disjoint subsets whose union is the entire set of inputs.
	From each partition,  
		choose a typical element and one or more boundary elements 
		determine the expected output for each element according to the *function specification*, not the code.  
		
**Test suite**: The chosen input/expected output pairs. The boundary elements increase the likelihood of finding a specification violation.  

**Test execution**: Run the function on the inputs in the test suite;
check that it produces the corresponding expected outputs.  

> [!NOTE]
> Input partitioning is also called **equivalence partitioning** or **equivalence class partitioning**.
> 

#### Property-based testing
Property represented as a Boolean function. 
Check that it is true for all inputs in the test suite
## Programming paradigms

### Functional programming

#### Higher order functions
A higher-order function is a function that takes (other) [[#Function|functions]] as input. 

Higher-order functions facilitate *(re)factoring* multiple function definitions into a joint skeleton function and changing parts that instantiate its *parameters*.
	The changing parts may themselves be functions.
#### lambda functions

### Imperative programming

### Object-oriented programming

#### Classes
In object-oriented programming, a **class** defines the shared aspects of objects created from the class. The capabilities of a class differ between programming languages, but generally the shared aspects consist of state (variables) and behaviour (methods) that are each either associated with a particular object or with all objects of that class.

Object state can differ between each instance of the class whereas the class state is shared by all of them. The object methods include access to the object state (via an implicit or explicit parameter that references the object) whereas class methods do not.
#### Objects
An **object** is an encapsulation of data, by containing data with the functions that work with the data:  
	• **Properties**, data (aka. attributes, fields)
	• **Methods** er funktioner  
An object is a value, which has a type. We typically create objects from a class which declares a new type.

Objects and classes are used to obtain abstraction of data.

#### Polymorphism
Polymorphism means "*many forms*", and it occurs when we have many classes that are related to each other by inheritance. Like we specified in the previous chapter; Inheritance lets us inherit attributes and methods from another class. Polymorphism uses those methods to perform different tasks.

A key concept in object-oriented programming that allows objects of different classes to be treated as objects of a common type

#### Encapsulation
**Encapsulation** refers to the bundling of data with the mechanisms or methods that operate on the data. It may also refer to the limiting of direct access to some of that data, such as an object's components.
#### Inheritance
Inheritance in object-oriented programming is based on a hierarchical relationship between classes, where a derived class (also known as a subclass or child class) inherits the characteristics of a base class (also known as a superclass or parent class).
#### Interface (Object-oriented programming)
In object-oriented programming, an **interface** or **protocol** type is a data type that acts as an abstraction of a class. It describes a set of method signatures, the implementations of which may be provided by multiple classes that are otherwise not necessarily related to each other. 

A class which provides the methods listed in a protocol is said to _adopt_ the protocol, or to _implement_ the interface.
## Runtime

### Static type checking

With static type checks, you know that your program will not fail at runtime because a function is given a wrong type. These errors are eliminated early!