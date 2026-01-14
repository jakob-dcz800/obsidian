---
tags:
  - Testing
  - Software-development
---
# White box testing

![[Learning goals#B3-15 White-box testing]]
## Definition

Code driven: **Find inputs that exercise all parts of the source code**
### Code coverage
Basic coverage criteria for all parts: 
	C0: Ensure all control flow **nodes** are executed at least once. 
		all statements
	C1: Ensure all control flow **edges** are executed at least once.
		all paths
Coverage rate: 
	all (statements or paths) = 100%
	Otherwise: fraction of nodes, respectively edges executed at least once

You can also extend tests by:
- Ensuring that different execution paths through conditions are exercised 
- Ensuring that nodes in loops are executed multiple times.

![[Pasted image 20250614145140.png]]
## Usage

### Statement coverage $C_{0}$-test
Every statement in the source code has to be executed **at least** once. 
Every node in the control flow graph is reached by at least one test case.

Statement coverage driven test design:
- Detects unreachable statements: Impossible to find inputs that reach them. 
- Does not exercise all control flows (edges) in control flow graph 
- Does not test loops thoroughly (single iteration is sufficient) 
- Does not exercise multiple ways of satisfying a Boolean condition

Coverage rate ($G$) of test = $(\text{under T covered statements}) / (\text{all statements})$ 

For example:
$\text{Calculate(1, 0, 1, 2)}$ has $G = 1.0$ 
$\text{Calculate(1, 3, 3, 1)}$ has $G = 0.857$
### Path coverage $C_{1}$-test
Or: branch coverage (C1-Test) 

> Because statement coverage only leads to insufficient assertions:

Every alternative branch in the source code is passed at least one time. = Every edge of the diagram is used at least one time.

Complete path coverage is **often impossible or infeasible** because of its high combinatory complexity
An expensive alternative is k-bounded path coverage.
#### Annotation
• Branch coverage **always includes statement coverage**. 
• There possibly exist difficult-to-reach branches, if it is hard to create the necessary conditions. 
• At conditional statements and while/for-loops, there are empty branches that have to be exercised for branch coverage.
• **It is sufficient to iterate loops zero times and once.**

#### Control flow graphs with loops have infinitely many paths.

Pragmatic alternative
**k-bounded** control flow path: 
Control flow path in which each statement node occurs at most k times (for given k >= 0)

k-bounded path coverage: 
All k-bounded control flow paths are executed at least once.
A test case may execute a statement more than k times.

- Typically a small value of $k$ is used, e.g. $k=2$
- Path coverage with $k=2$ includes path coverage with $k=1$

#### Quality
- Coverage ratio G = (paths covered by T) / (all possible paths) 
- All possible paths = all k-bounded paths that can be executed (for k-bounded path coverage) 
- Note: Normally, not all paths can be executed, thus it is difficult to determine the ratio
## Branch coverage driven test design:

- Detects unreachable branches and unreachable statements
- Does not consider dependencies between branches
- Complex conditions are tested only rudimentarily
	- For disjunctions, one subexpression sufficient to set value to true
	- for conjunctions, one subexpression sufficient to set value to false

- Examples, that cover both branches with by only two assignments of values to $a,b,c,d$:
![[Pasted image 20250614150502.png]]

## Multiple Condition Coverage

Multiple Condition Coverage = Branch coverage extended with: 
- Every possible combination of Boolean values of atomic predicates is executed

Note: 
- Multiple condition coverage includes statement coverage.
- Multiple condition coverage includes branch coverage.

There can be unrealizable combinations of Boolean values
Example: 
- The expression `( nr > 1 && error < 0 ) || abort` has three atomic predicates
- eight test cases have to be created.

Problem: for $n$ subexpressions there exist $2^n$ test cases.
This can be unusable

## Modified Condition/Decision Coverage

Pragmatic version of the multiple condition coverage:

Branch coverage plus: 
- For every atomic predicate, it has to be shown, that the predicate can influence the result of the evaluation of the condition independent of the other atomic predicates

Precisely: 
- For every atomic predicate there have to be two test cases that only differ in the value of this concrete predicate and change the result of the condition.

First simple example: 
- The expression `a | b | c` needs four test cases: 
- `a` changes only the result if `b | c == false`, thus `b==false` and `c==false`
	- thus the test cases are `false,false,false` and `true,false,false` 
- `b` changes only the result if `a | c == false`
	- thus the test cases are `false,true,false` and `false,false,false` 
- `c` changes only then the result, if `a | b == false`
	- thus the test cases are `false,false,true` and `false,false,false`

Note:
- Modified condition/decision coverage includes statement and branch coverage. 
- Modified condition/decision coverage may require too large a number of cases, too.
- The example shows that the test cases for different predicates can be equal. For $n$ predicates, $2^n$ or fewer test cases are necessary.

- For $n$ atomic predicates there are least $n+1$ and at most $2^n$ test cases.
- In general, there exists multiple combinations of test cases that satisfy the modified condition/decision coverage with $G=1.0$
- Are atomic predicates dependent on each other, then the modified condition/decision coverage cannot achieve coverage ratio $G=1.0$

## White-Box Testing for Program Units

Presented so far: 
Test suite of method (without method calls, exceptions) is designed by systematically finding test cases that cover all statements, branches, paths

For **bigger program units**, white-box testing is driven by finding test cases that cover the **parts** of these units:
- Coverage of the methods provided by a class. 
- Coverage of the called methods of a certain class. 
- Coverage of the triggered/treated exceptions.