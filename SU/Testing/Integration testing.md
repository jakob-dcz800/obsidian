---
tags:
  - Testing
  - Software-development
---
# Integration testing

• Integration involves combining the individual software units into larger functional units 
• If the units work individually, why wouldn't they work when you put them together? 
• Example: Interactions between units may be flawed
	• Mars Orbiter disaster caused by one module assuming English units and another assuming Metric units

• The entire system is viewed as a collection of subsystems (sets of classes) determined during the system and object design. 
• The order in which the subsystems are selected for testing and integration determines the testing strategy 
	• Big bang integration (non-incremental) 
	• Bottom-up integration 
	• Top-down integration 
	• Sandwich testing 
	• Variations of the above

![[Pasted image 20250512104531.png]]

### Unit Testing or Integration Testing?
• Sometimes people who claim to be doing unit testing are actually doing bottom-up integration testing 
• How do you tell the difference? 
	• Unit testing uses stubs to isolate the module under test from its dependencies 
	• Bottom-up integration testing does not (i.e., modules call their “real” dependencies)
## Types of integration testing
• Big-Bang integration 
	• Entire system is integrated at once 
	• The system doesn't work, and you don't know why 
• Incremental integration 
	• Add a piece, retest the system, Add a piece, retest the system, … 
	• If it breaks, you know what caused the problem (i.e., the last piece you added) 
	• Integration Testing is testing that's done during integration to ensure that the system continues to work each time a new piece is added

## Examples

### Three Layer Call Hierarchy
![[Pasted image 20250512103848.png]]

...

### Big-Bang Approach
![[Pasted image 20250512103921.png]]

## Bottom-up Integration Testing

![[Pasted image 20250512103944.png]]

### Pros and Cons
• **Bad** for functionally decomposed systems: 
	• Tests the most important subsystem (UI) last 
• **Useful** for integrating the following systems 
	• Object-oriented systems 
	• real-time systems 
	• systems with strict performance requirements

## Top-down Integration Testing

![[Pasted image 20250512104119.png]]

### Pros and Cons

<mark class="hltr-orange">• Test cases can be defined in terms of the functionality of the system (functional requirements)</mark> 
<mark class="hltr-orange">(is this enough?)</mark>
• Writing stubs can be difficult: Stubs must allow all possible conditions to be tested. 
• Possibly a very large number of stubs may be required, especially if the lowest level of the system contains many methods. 
• One solution to avoid too many stubs: Modified top-down testing strategy 
	• Test each layer of the system decomposition individually before merging the layers 
	• Disadvantage of modified top-down testing: Both, stubs and drivers are needed

## Sandwich Testing Strategy

![[Pasted image 20250512104400.png]]

• Combines top-down strategy with bottom-up strategy 
• The system is viewed as having three layers 
	• A target layer in the middle 
	• A layer above the target 
	• A layer below the target 
	• Testing converges at the target layer 
• How do you select the target layer if there are more than 3 layers? 
	• Heuristic: Try to minimize the number of stubs and drivers

### Pros and Cons
• Top and Bottom Layer Tests can be done in parallel 
• Does not test the individual subsystems thoroughly before integration 
• Solution: Modified sandwich testing strategy

### Modified Sandwich Testing Strategy

![[Pasted image 20250512104507.png]]

• Test in parallel: 
	• Middle layer with drivers and stubs 
	• Top layer with stubs 
	• Bottom layer with drivers 
• Test in parallel: 
	• Top layer accessing middle layer (top layer replaces drivers) 
	• Bottom accessed by middle layer (bottom layer replaces stubs)