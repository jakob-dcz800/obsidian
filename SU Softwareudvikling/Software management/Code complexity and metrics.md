# Code complexity and metrics

## Learning goals 
Develop an understanding of software metrics and metrics for estimating.
Classify, compare and select appropriate metrics. 
Apply metrics to software and interpret results


## Software metrics

Project planning consists of two primary tasks: 
• analysis 
• estimation (effort of programmer months, development interval, staffing levels, testing, maintenance costs, etc.).

### Black-box metrics 
(cost estimation)
• Function Points 
• [[#COCOMO]]
### White-box metrics
(Testing effort) 
(Maintainability effort)
• Lines of Code (LOC) 
• Halstead’s Software Science (skipped) 
• McCabe’s Cyclomatic Complexity (See for slides of B3-15 Whitebox Testing)
• Information Flow Metric 
• Syntactic Interconnection 
• Structural Coupling 
• Semantic Coupling 
• Object-oriented metrics

#### Linguistic Metrics
measuring the properties of program/specification text without interpretation or ordering of the components. 
Lines of code/statements (LOC) perhaps the simplest.
SLOC = (Effective) Source Lines of Code (without comments, whitespaces, …)
Simple to use: 
if errors occur at 2% per line, a 5000-line program should have about 100 errors. • If it required 30 tests to find an error, then could infer the expected number of tests needed per line of code.

#### Structural Metrics:
based on structural relations between objects in program; • usually based on properties of control/data flowgraphs (e.g., number of nodes, links, nesting depth), fan-ins and fan-outs of procedures, etc. 

• [[#McCabe’s Cyclomatic Complexity]]
• Control Flow Graphs 
• Information Flow Metric 
• Object-oriented metrics
#### Hybrid Metrics:
based on combination (or on a function) of linguistic and structural properties of a program.

## Verification vs. metrics

Complete testing is impossible. Therefore we set priorities. We focus on particularly error-prone parts of the software! How to efficiently do we identify these parts ?
Susceptibility to errors correlates with the complexity of software components. We then determine the complexity of the software components with metrics.
Compare metric values for different components and against historical data. Abnormal values can indicate quality problems => **test more intensively**.
![[Pasted image 20250505102453.png]]

## Forms of complexity

• **Structural Complexity**: The expression of the topological relationships of a system's components. 
• **Computational Complexity**: The algorithms' computational difficulty, often given as a characterization of the time to process given elements. 
• **Logical Complexity**: Systematic difficulty of decision-making flows. 
• **Conceptual Complexity**: An organizational view which takes human cognitive and resource factors into account. 
• **Textual Complexity**: Analysis of program source texts.

## Function Oriented Metrics

Examples of use include:
- productivity $FP/\text{person-month}$ 
- quality $\text{faults}/FP$ 
- cost $\$/FP$
- Documentation $\frac{\text{doc-pages}}{\text{FP}}$

$FP:$ function points are calculated with this table:
![[Pasted image 20250505103039.png]]

$$
\text{FP}=\text{total-weight}\times[0.65+0.01\times \text{SUM}(F_{i})]
$$

![[Pasted image 20250505103236.png]]
![[Pasted image 20250505103259.png]]

### Example
#### 1
![[Pasted image 20250505103319.png]]

#### 2
![[Pasted image 20250505103411.png]]

## COCOMO
**The Constructive Cost Model**
The model parameters are derived from fitting a regression formula using data from historical projects.

The overall resources for software project must be estimated:
- Development costs (i.e., programmer-months) 
- Development interval 
- Staffing levels 
- Maintenance cost

## McCabe’s Cyclomatic Complexity

Determines the logical complexity of a graph
• Typically, the graph is a flow graph of a function or method (control flow) 
• can also be a graphical representation of an FSM

### Definition:
• **Independent path**: any path that introduces at least one new set of statements or a new condition; must move along at least one edge that has not been traversed before. 
• **Basis set**: a maximal set of independent paths (covers all conditions and statements)

## Information flow metric
Attempts to measure the complexity of the code by measuring the flow of information from one procedure to another in terms of fan-ins and fan-outs.

Flows represent: 
• the information flow into a procedure via the argument lists and 
• flows from the procedure due to return values of function calls.

• **fan-in**: number of local flows into a procedure plus the number of global structures read by the method. 
• **fan-out**: number of local flow from a procedure plus the number of global structures updated by the method.

Thus, the complexity of the procedure, $p$, is given by $C_{p} = (\text{fan-in} \times \text{fan-out})^2$

## Degree of coupling

Degree of coupling: $d$ (asymmetric)
![[Pasted image 20250505104418.png]]