---
tags:
  - Testing
  - Software-development
---
# Testing

[[Demorgans laws]]

• Testing is a black art, but many rules and heuristics are available 
• Testing consists of component-testing ([[unit testing]], [[Integration testing]]) and [[System testing]] 
• [[Design patterns]] can be used for integration testing 
• Testing has its own lifecycle 
• [[Testing principles#Customer Acceptance Testing|Acceptance testing]] for testing user requirements

![[Pasted image 20250512110438.png]]
## Learning goals

* Identify and describe the key components of programming: specification, code and their relation to each other: code satisfying a specification or not
* Describe testing as a systematic process of finding errors, evidence of code **not satisfying its specification**
* Describe **test design** as a methodology for finding as many errors as possible with limited data, human and system resources.
* Describe and apply [[Black-box testing|black-box]] (specification-based) test design by generating a test suite of example inputs driven by analysis of the specification
	* Apply, argue and criticize equivalence class partitioning for test suite construction
* Name and identify testing of non-functional code properties
	* Performance evaluation (latency, throughput, scalability) through experimentation (system, workload, metrics, experiments)
	* Security (guaranteed absence of undesirable functionality) testing by fuzz testing
	* Usability evaluation (effective use by humans) testing by observation experiments and user documentation evaluation
	* Robustness (resilience against external events) testing
	* Configuration (successful deployment on multiple platforms and contexts) testing

## Specification and code

**Code**: Unit of executable program
**Specification**: Properties code is expected to have
Expressed as:
- executable code 
- logical and mathematical formulae
- falsifiable natural language statements
Code either satisfies its specification; or it does not
**Formal verification**: Mathematical proof that the code satisfies its specification in all specified contexts
**Testing**: Methodology for effectively finding counterexample to code satisfying its specification
	Not finding a counter-example despite great effort counts as evidence of code possibly satisfying its specification.

## When are we done testing? 
• "You're never done testing, the burden simply shifts from you to your customer." 
• "You're done testing when you run out of time or you run out of money."
• You're done testing when: 
	• All "show stopper" bugs have been fixed 
	• The rate at which new bugs are being found falls below some acceptable threshold 
	• If your testing is thorough, the rate at which you're finding new bugs is correlated to how many bugs still remain

### Can we predict when we'll be done testing in advance?
*An estimation and scheduling problem*

• How about this? 
	• Record the rate at which you're finding bugs each week 
	• Once you've got several data points, fit a curve to the data that can be used to predict the date at which the bug rate will be low enough to ship 
	• This might be better than guessing

### Additional links:
[[Stubs and drivers]]
[[Testing of Object-Oriented Programs]]
