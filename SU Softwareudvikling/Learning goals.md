# Learning goals

## B3-05 Testing basics
* Understanding the concepts of basic testing of program code
* Understanding and applying [[Test-Driven Development]]  
* Understand structure and impact of coding guidelines
## B3-06 Object oriented modelling 1
* To understand the purpose and intent of [[UML Terminology#UML Terminology|UML modelling]]
* To read and discuss 4 kinds of UML diagrams  
* To apply UML diagrams to model very simple [[UML Terminology#Terminology Application/Solution Domain|solution domains]]
## B3-08 Debugging error analysis
* Debugging to improve program correctness  
* Understand debugger and other tools capabilities to locate bugs  
* Develop and follow an engineering approach for debugging (The Strategy) 
* Documenting bug fixes
## B3-09 Design patterns
* To understand generalized solutions of often occurring problems  
* To abstract from a concrete problem to a context less solution  
* To identify problems that can be solved by applying [[Design patterns|design patterns]] to this context

## B3-12 Defensive programming and design by contract
* **Describing**
	* semantic model of object in [[Terminology#Object-oriented programming|object-oriented programming]] as private state combined with and public methods  
	* method as combination of query and command  
	* queries as functions that return a result without updating the state
	* commands as functions that update the state without returning a separate result
* **Defining** observable properties of objects: true logical statements involving only public methods of objects 
* **Formulating** [[Design#Pre- and postconditions|pre- and postconditions]] to specify method properties  
* **Formulating** [[Terminology#Interface|interface]] contract as
	* observable properties an object (server) promises to have vis a vis any client, in exchange for
	* its client promising not to lead to a program crash for any server having those properties  
* **Explaining** design by contract as
	* finding an [[Design#Interface contract|interface contract]] with low coupling
	* designing and implementing server satisfies interface contract  
	* designing and implementing client(s) to solely based on interface contract (not any particular server implementation)  
* **Deploying** assert statements as confirmations/tests of properties that must be true according to interface contract  
	* Promised by server, respective client code programmer) to always hold  
	* If it is not hold, signal that client (precondition violation) or server (postcondition violation) has failed interface contract 
* **Distinguishing between** assert statements (design by contract, condition expected to always hold) and if-then-else statements (defensive programming, condition may be false)
	* Assert statement: Precondition asserted 0 or 1 times (by server)
	* [[Design#Defensive programming|Defensive programming]]: Test with extensive error handling code executed 2 times (client and server).

## B3-13 Specifying program properties
Formal Specification - Techniques for the unambiguous specification of software
* To explain how formal specification techniques
	* capture component and system properties rigorously and precisely (mathematically)
	* provide a basis for testing (specification-based testing)
	* aid thinking-before-doing system design (in particular test-driven development)
	* facilitate early discovery of problems in system requirements  
* To describe the use of
	* algebraic techniques (for interface specification) and
	* model-based techniques (for behavioural specification)
* To introduce [[Abstract State Machine Model]]

## B3-14 Black-box testing
* Identify and describe the key components of programming: specification, code and their relation to each other: code satisfying a [[Terminology#Specification|specification]] or not.
* Describe **testing as a systematic process of finding errors**, evidence of code not satisfying its specification.
* Describe test design as a methodology for **finding as many errors as possible** with **limited** data, human and system resources.
* Describe and apply [[Black-box testing|black-box]] (specification-based) test design by generating a test suite of example inputs driven by analysis of the specification
	* Apply, argue and criticize [[Equivalence partitioning|equivalence class partitioning]] for test suite construction.
* Name and identify testing of non functional code properties
	* Performance evaluation (latency, throughput, scalability) through experimentation (system, workload, metrics, experiments)
	* Security (guaranteed absence of undesirable functionality) testing by fuzz testing  
	* Usability evaluation (effective use by humans) testing by observation experiments and user documentation evaluation
	* Robustness (resilience against external events) testing
	* Configuration (successful deployment on multiple platforms and contexts) testing
## B3-15 White-box testing
* Describing the basic concepts of [[white-box testing]]
* Explaining and applying white-box testing as a test design method
* Explaining code coverage rate measures C0, C1 and applying them to design and evaluate test suites
* Applying white-box testing to implement test suites using NUnit in C# projects  
* Discussing the differences between black-box testing and white-box testing as different systematic ways of coming up with test suites with high likelihood of uncovering errors
## B4-01 Code quality
* Can distinguish various qualities of software
* Can analyze trade-offs between [[Code quality|software qualities]] 
* Can identify tasks within quality management processes
## B4-02 Object oriented analysis
* To identify concepts in [[Object oriented analysis and design#Domains|problem domains]]
* To specify concept attributes and association  
* To develop a problem architecture  
* To handle complex problem domains 
## B4-03 Object oriented design
* To identify concepts in problem domains  
* To specify concept attributes und association  
* To develop and design a problem architecture  
* To handle complex problem domains
## B4-04 Code complexity metrics
* Develop an understanding of software metrics and metrics for estimating.  
* Classify, compare and select appropriate metrics.
* Apply metrics to software and interpret results.
## B4-05 Refactoring
* Understands the role of refactoring in code quality assurance
* Can analyze code for refactoring potential
* Can apply appropriate refactoring methods
* Can integrate regular code refactoring in [[SDLC]]
## B4-06 Acceptance and integration testing
* Understand the spectrum of testing methods and their applications
* Understand how tests are organized (roles)
* Understand how to develop a testing strategy
## B4-07 Code Reviews
* Understand the intentions and process of code reviews
* Understand difference between code walks and (formal) code reviews
* Can conduct simple code review in a group  
* Understand the importance of code reviews for industrial software quality
## B4-08 Software Development Lifecycle
• To introduce the general phases of the software (development) life cycle 
• To survey the main types of model, 
• To describe various generic software process models and their pros and cons 
• To consider how to choose between them.