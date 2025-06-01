# Code quality

What is code quality?
## What is product quality?

This is problematical for software systems  
	• Tension between customer quality requirements (efficiency, reliability) and developer quality requirements (maintainability, reusability, ...)  
	• Some quality requirements are difficult to specify in an unambiguous way  
	• Software specifications are usually incomplete and often inconsistent  
	• The quality compromise: we cannot wait for specifications to improve before paying attention to quality, and procedures must be put into place to improve quality in spite of imperfect specification

Quality attributes are frequently conflicting and increase development costs, so there is a need for  
weighting and balancing 

Software engineering is concerned with the cost- effective development of good software

## Product quality attributes

Attributes of good software (beyond delivering the required functionality):  

Efficiency
	• Software should not make wasteful use of system resources (disk and memory space, CPU time, etc.) and should present appropriate response times
Usability (ease of use)  
	• Software must be usable by the users for which it was designed
Dependability (reliability, availability, security, safety,...)
	• Software must be trustworthy  
	• Maintainability (ease of maintenance)  
	• Software must evolve to meet changing needs  
	• Software costs more to maintain than it does to develop. For systems with a long life, maintenance costs may be several times development costs  

Other quality attributes:
	Resilience  
	Robustness  
	Understandability  
	Testability  
	Adaptability  
	Modularity  
	Simplicity  
	Portability  
	Reusability  
	Learnability

## Main dimensions of dependability

• **Reliability** - Probability of failure-free system operation over a specified time in a given environment for a given purpose
• **Availability** - Probability that a system, at a point in time, will be operational and able to deliver the requested services
	• It’s possibly to have high availability with low reliability if failures are repaired quickly!  
• **Safety** - System’s ability to operate, normally or abnormally, without danger of causing human injury or death and without damage to the system’s environment  
• **Security** – The system’s ability to protect itself from accidental or deliberate external attack 

## Software Quality Assurance (SQA)
The purpose of SQA is to find and report defects AND succeed in getting them fixed

What is a software defect?
• Definition #1: There is a mismatch between the program and its requirements spec or functional spec 
	• This definition is fine if a requirements specification exists and is complete and correct (not always true)
• Definition #2: The program does not do what its end user reasonably expects it to do  
	• This definition always applies, even when there's no specification

### Categories of defects

* Functional defects
	* The program’s features don’t work as they should
* User Interface defects
	* Usability problems
* Performance defects
	* Too slow, Uses too much memory/disk space/bandwidth/etc
* Error Handling defects
	* Failure to anticipate and handle possible errors, or deal with them in a reasonable way
* Security defects
	* Attackers can compromise the system and access sensitive data or other resources
* Load defects
	* Can't handle many concurrent users, can't handle large data sets
* Configuration defects
	* Doesn't work on the required hardware/OS/browser configurations
* Race conditions
	* Behaviour depends on the interleaving of concurrent activities
* Documentation defects
	* User manuals or online help isn't clear, complete, well-organized

## Improve the quality of code

To improve any process, we need to know where we are and where we want to be.
To get from point A to point B we need to know where they are

How can we identify where we are 
Need a defined process that is repeatable and cost effective  
Code Reviews are useful but costly, not free of emotion
Need to continually assess software quality to assess progress of improvements (compare code quality)

## What can we do?

• Software Requirements Validation
	• Validate requirements to ensure that they are correct, unambiguous, complete, and verifiable
• Software Architecture Verification  
	• Verifies that the code written adheres to the technical architecture design  
• Code Quality Management
	• Static & Dynamic Code Analysis to find programming errors
	• Utilise agreed quality criteria so that the process is easily repeatable – gauge quality over time  
• Helps define clear quality gates between each phase in the SDLC