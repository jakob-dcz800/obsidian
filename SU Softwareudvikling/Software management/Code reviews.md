# Code reviews

![[Learning goals#B4-07 Code Reviews]]


## Definition

A constructive **review** of a fellow developer’s code. 
A required sign-off from another team member before a developer is permitted to check in changes or new code.

## Mechanics of code reviews

**who**: Original developer and reviewer, sometimes together in person, sometimes offline. 

**what**: Reviewer gives suggestions for improvement on a logical and/or structural level, to conform to previously agreed upon set of quality standards. 
	• Feedback leads to refactoring, followed by a 2nd code review. 
	• Eventually reviewer approves code. 

**when**: When code author has finished a coherent change that's otherwise ready for check-in 
	• change shouldn't be too large or too small 
	• before committing the code to the repository or incorporating it into the new build

## Why Bother?

More than 1 person has seen every piece of code 
	Prospect of someone reviewing your code raises quality threshold. 
Forces code authors to articulate their decisions Hands-on learning experience for rookies without hurting code quality 
	Pairing them up with experienced developers 
Team members involved in different parts of the system 
	Reduces redundancy, enhances overall understanding 
Author and reviewer both accountable for committing code

## Essential elements of a formal code review
* **Identify problems** 
	* Find problems with the software such as missing items, mistakes, etc.
* **Follow rules** 
	* Amount of code to be reviewed, how much time will be spent, etc.
* **Prepare**
	* Each participant should prepare in order to contribute to the review
* **Write a report**
	* Summarize the results of the review, make report available to the development team.

## Informal code inspections

Peer reviews:
	• An informal small group of programmers and/or testers act as reviewers. 
	• Participants should follow the 4 essential elements even through the review is informal.
Walkthroughs:
	• A more formal process in which the author of the code formally presents the code to a small group of programmers and/or testers. 
	• The author reads the code line by line explaining what it does, reviewers listen and ask questions. 
	• Participants should follow the [[#Essential elements of a formal code review|4 essential elements]].

### Tips
* Authors should annotate source code before the review 
* Use checklists 
* Establish a process for fixing defects found 
* Foster a positive code review culture

*Do not review for more than 60 minutes at a time* 
When people engage in any activity requiring concentrated effort over a period of time, performance starts dropping off after about 60 minutes. Studies show that taking breaks from a task over a period of time can greatly improve quality of work.
### What to look for 
▪ Bad Design. 
▪ Lack of clarity. 
▪ Lack of conformity. 
▪ Performance hazards. 
### What’s not important? 
▪ Optimization. 
▪ Skill and experience gaps. 
▪ Personal style.
## Variations
• **inspection**: A more formalized code review with: 
	• roles (moderator, author, reviewer, scribe, etc.) 
	• several reviewers looking at the same piece of code 
	• a specific checklist of kinds of flaws to look for 
	• possibly focusing on flaws that have been seen previously 
	• possibly focusing on high-risk areas such as security 
	• specific expected outcomes (e.g., report, list of defects) 
• **walkthrough**: informal discussion of code between author and a single reviewer 
• **code reading**: Reviewers look at code by themselves (possibly with no actual meeting)

## Examples

[[#Checklist for data reference errors]]
[[#Checklist for data declaration errors]]
[[#Checklist for computation errors]]
[[#Checklist for comparison errors]]
[[#Checklist for control flow errors]]
[[#Checklist for subroutine parameter errors]]
[[#Checklist for input/output errors]]
[[#Checklist for other potential checks]]
[[#Checklist for non-functional requirements/code qualities]]
### Checklist for data reference errors
* Is an un-initialized variable referenced? 
* Are array subscripts integer values and are they within the array’s bounds? 
* Are there off-by-one errors in indexing operations or references to arrays? 
* Is a variable used where a constant would work better? 
* Is a variable assigned a value that’s of a different type than the variable? 
* Is memory allocated for referenced pointers? 
* Are data structures that are referenced in different functions defined identically?

### Checklist for data declaration errors
• Are the variables assigned he correct length, type, storage class? 
	• E.g. should a variable be declared a string instead of an array of characters? 
• If a variable is initialized at its declaration, is it properly initialized and consistent with its type?
• Are there any variable with similar names? 
• Are there any variables declared that are never referenced or just referenced once (should be a constant)? 
• Are all variables explicitly declared within a specific module?

### Checklist for computation errors
*  Do any calculations that use variables have different data types? 
	* E.g., add a floating-point number to an integer 
*  Do any calculations that use variables have the same data type but are different size? 
	* E.g., add a long integer to a short integer 
*  Are the compiler’s conversion rules for variables of inconsistent type or size understood?

* Is overflow or underflow in the middle of a numeric calculation possible? 
* Is it ever possible for a divisor/modulus to be 0? 
* Can a variable’s value go outside its meaningful range? 
	* E.g., can a probability be less than 0% or greater than 100%? 
* Are parentheses needed to clarify operator presence rules?

### Checklist for comparison errors
* Are the comparisons correct? 
	* E.g., `<` instead of `<=` 
* Are there comparisons between floating-point values? 
	* E.g., is 1.0000001 close enough to 1.0000002 to be equal? 
* Are the operands of a Boolean operator Boolean? 
	* E.g., in C 0 is false and non-0 is true

### Checklist for control flow errors
* Do the loops terminate? If not, is that by design? 
* Does every switch statement have a default clause? 
* Are there switch statements nested in loops? 
	* E.g., careful because break statements in switch statements will not exit the loop … but break statements not in switch statements will exit the loop. 
* Is it possible that a loop never executes? Is it acceptable if it doesn’t? 
* Does the compiler support short-circuiting in expression evaluation?

### Checklist for subroutine parameter errors
* If constants are passed to the subroutine as arguments, are they accidentally changed in the subroutine? 
* Do the units of each parameter match the units of each corresponding argument? 
	* E.g., English versus metric 
	* This is especially pertinent for [[SOA components]] 
* Do the types and sizes of the parameters received by a subroutine match those sent by the calling code?

### Checklist for input/output errors
* If the file or peripheral is not ready, is that error condition handled? 
* Does the software handle the situation of the external device being disconnected? 
* Have all error messages been checked for correctness, appropriateness, grammar, and spelling? 
* Are all exceptions handled by some part of the code? 
* Does the software adhere to the specified format of the date being read from or written to the external device?

### Checklist for other potential checks
• Does your code pass the lint test? 
	• E.g., How about gcc compiler warnings? 
• Is your code portable to other OS platforms? 
• Does the code handle ASCII and Unicode? 
• How about internationalization issues? 
• Does your code rely on deprecated APIs? 
• Will your code port to architectures with different byte orderings? 
	• E.g., little (increasing numeric significance with increasing memory addresses) versus big (the opposite of little) endian?

### Checklist for non-functional requirements/code qualities
• Clarity 
	• Is the code clear and easy to understand? 
	• Did the programmer unnecessarily obfuscate any part of it? 
	• Can the code be refactored to make it clearer? 
• Maintainability 
	• Will other programmers be able to maintain this code? 
	• Is it well commented and documented properly?
Accuracy
	• Does the code accomplish what it is meant to do? 
	• If an algorithm is being implemented, is it implemented correctly?
Readability and Robustness
	• Is the code fault-tolerant? Is the code error-tolerant? 
	• Will it handle abnormal conditions or malformed input? 
	• Does it fail gracefully if it encounters an unexpended condition?
Security
	• Is the code vulnerable to unauthorized access, malicious use, or modification?
Scalability 
	• Could the code be a bottleneck that prevents the system from growing to accommodate increase load, data, users, or input? 
Reusability 
	• Could this code be reused in other applications? 
	• Can it be made more general? 
Efficiency 
	• Does the code make efficient use if memory, CPU cycles, bandwidth, or other system resources? 
	• Can it be optimized?