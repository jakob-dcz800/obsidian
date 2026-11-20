
# Saltzer and Schroeder’s security design principles

- Economy of mechanism
	- Keep the design as simple and small as possible to make inspection and verification easier
- Fail-safe defaults
	- Base access decisions on explicit permission (default deny) rather than exclusion.
- Complete mediation
	- Every access to every object must be checked for authority, ensuring no cached or bypassed checks are allowed.
- Open design
	- The security of a mechanism should not depend on the secrecy of its design or implementation.
- Separation of privilege
	- Where feasible, a protection mechanism that requires two distinct keys or conditions (such as dual authorization) is more robust than a single-key system.
- Least privilege
	- Every program and user should operate using the minimum set of privileges necessary to complete a job.
- Least common mechanism
	- Minimize the amount of mechanism common to and shared by multiple users, reducing covert channels and inter-user dependencies.
- Psychological acceptability
	- Security controls should not make the resource more difficult to use than if the controls were not there, ensuring users apply them routinely.

# Elements of security:
1. Policy: Defines the rules and guidelines that specify what needs to be protected and who is allowed to access information or resources.
2. Mechanism: The tools and methods used to enforce security policies, such as passwords, encryption, firewalls, and access controls.
3. Assurance: Provides confidence that security mechanisms are working correctly and that the system meets its security requirements.

In simple terms:
- Specification/Policy: What should be protected?
- Implementation/Mechanism: How is it protected?
- Correctness/Assurance: How do we know the protection works?


## Security properties 

The C-I-A triad/the security triad 
• Confidentiality 
	• Kept secret 
• Integrity 
	• Kept from being modified 
• Availability 
	• Possible to access 
	
Newer additions (ISO 7498-2) 
• Authentication 
	• Confirm identity of sender 
• Nonrepudiation/accountability 
	• No deniability

# The gold standard 
• Authenticating 
	• Identify the right person 
• Authorizing 
	• Grant the right privileges 
• Auditing 
	• Keep a log of who does what
