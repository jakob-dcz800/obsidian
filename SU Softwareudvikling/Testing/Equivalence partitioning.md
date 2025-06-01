# Equivalence partitioning

i.e. input partitioning

Partition valid inputs into equivalence classes
Create a test case for at least one value from each equivalence class

![[Pasted image 20250324120601.png]]
## Principle 

Find execution of $f$ that proves that it does not have a given property.
- Create new object $o$
- Find sequence of commands that ends with $o$ in state satisfying $R$
- Choose $v$ satisfying $P$
- Execute $o.f(v)$
- Check whether result satisfies $Q$
	- If does not: Error found!
	- If it does: Not error per se

Idea: 
- Partition $\set{ v : T \mid P(v) }$ into a *finite* number of [[disjoint subsets]] $E_{}1,...,E_{}n$ with $E_1 ⋃ \dots ⋃ E_n = \set{ v : T | P(v) }$ such that each element of $E_i$ is equally *likely* to manifest an error
- Test suite (for this method and this property): Choose few (1 to 3) representative values from each equivalence class $E_i$

## Equivalence classes

Partition the inputs into “equivalence classes”

Two inputs are considered **equivalent** if we expect the program to process them in the same way, i.e. identically by each function.

If we expect the program to process inputs in the same way, only test *one* of them 
- Chosen input is *test case* when executed by method.
- Good to add boundary cases, inputs at the *boundary* of an equivalence class
If all elements of an equivalence either lead to no error or to an error, then testing is complete: if no errors are found, code is correct.

### First-level partitioning

Partition inputs into valid vs. invalid inputs
- Valid: Satisfies precondition
- Invalid: Not valid

### Different interpretations

When designing test cases, you may use different definitions of “equivalence”, each of which will partition the test case space differently.

**Black-box test design**: The explicit reasoning for choosing a particular equivalence partitioning.
"In which way do we partition the input?"
