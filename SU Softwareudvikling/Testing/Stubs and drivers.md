# Stubs and drivers

## Stubs

![[Pasted image 20250512103346.png]]

What do stubs do? 
	• Do nothing 
	• Validate the method inputs 
	• Validate method call sequence (including parameter values) 
	• Send a message to a log 
	• Return a hard-coded answer regardless of the input 
	• Select an answer from a pool of hard-coded answers 
	• Cycle through the pool or randomly select one 
	• Randomly generate an answer 
	• Prompt the user for the answer

• Simple implementation of the module that is slower, less accurate, or somehow **less capable than the real module**
• Pause for a while to simulate the time taken by the real module 
• Generate errors (e.g., throw exceptions) that are hard to produce for real

## Drivers

What do drivers do? 
	• Invokes the class with fixed inputs 
		• If an oracle is available, inputs can be generated rather than fixed 
	• Compares actual outputs with expected outputs 
	• Records failure if expected and actual outputs don’t match 
	• Normally continues to execute even if a test case fails 
	• Generates report detailing what worked and what didn’t 
	**• Drivers and stubs must be designed together** 
	• Since stubs don’t produce “real” outputs, the expected results in the driver must take into account the “fake” behavior of the stubs