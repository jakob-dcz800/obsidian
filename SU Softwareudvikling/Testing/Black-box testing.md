# Black-box testing

i.e. specification-based testing

**Unit**: single or few classes
**Unit testing**: Testing of unit against its specification
- Specification: Interfaces, including their properties in comments

**Test suite**: Test cases designed to collectively discover ideally all errors
- Test case: Execution of code in unit with sample data 
- Error: Result of execution does not satisfy specification. 
- Test suite execution must be programmatic to facilitate automatic, repeated execution

Black-box test suite design:
- **Specification-driven** construction of a test suite: Based on analysis of specification
- Test suite design does not require access to the code (code is black box)

## Property-based black-box testing

Generate test cases automatically (by oracle)??
	Test multiple (many!) values in each equivalence class
Requires executable specification of property to be tested
	Brute force: Checking whether or not output is error or not for any input.

![[Pasted image 20250324133414.png]]

## Boundary Value Analysis

When choosing values from an equivalence class to test, use the values that are **most likely to cause the program to fail**.

Errors tend to occur at the **boundaries** of equivalence classes rather than at the "center"

**Good practice** for choosing values from equivalence class: 
- Include ‘typical’ value 
- values on the boundary to other equivalence classes

![[Pasted image 20250324133646.png]]

Don't get so wrapped up in testing boundary cases that you neglect to test "normal" input values
	Values that users would typically enter during mainstream usage


### Examples

Numeric values are often entered as strings which are then converted to numbers internally
This conversion requires the program to distinguish between digits and non-digits
A boundary case to consider: Will the program accept / and : as digits?
![[Pasted image 20250324133914.png]]



![[Pasted image 20250324133806.png]]


[[Testing principles]]