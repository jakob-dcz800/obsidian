# 2.1 Policy, mechanism and threat models

a) Explain the difference between a policy and a mechanism, and give an example of one specific policy that could be upheld by two different mechanisms.

A policy defines what the system is supposed to do.
The mechanism is the actual implementation: How does it do it?

If we want to gain access to an object we can:
1.	Have a role with certain permissions that grant us access, or
2.  Have the object grant us access by maintaining an access list

b) A company writes in its documentation: “The system is secure because all traffic is encrypted”. Explain what is missing from the claim, and what the company would need to add for the claim to be meaningful.

1. The company would need to add *when* the traffic is encrypted (end-to-end for example)? If it can be read before encryption, the system is not 'secure'.
2. The company should state that keys are inaccessible to outsiders as well

c) Explain why a threat model must state what is out of scope, and give an example of an attacker that a small company might reasonably exclude.

1. Technology (and especially the internet) is built on top so many pieces and sub-systems that maintaining a threat model would provide no real value since protecting every aspect would be infeasible and expensive.
2. [MANGLER]


d) Assurance is the third aspect of studying a secure system. Explain what assurance
means, and why it is difficult to achieve.

1. Assurance provides confidence that security mechanisms are working correctly and that the system meets its security requirements (policy).
2. Assurance could involve a detailed explanation of complicated systems and maths which can require vast knowledge and resources. Testing can provide assurance, but not always to the point of full assurance. 

# 2.2 Authentication

a) Explain what a replay attack is, and describe one mechanism that prevents it. 
1. A replay attack can be performed by intercepting packages from the sender who is logging in. When having gained these, the attacker can resend the packages without having to decrypt the contents to gain access to the system.
2. Two-factor auth (2FA) can prevent this when the system requires confirmation from the client. The attacker would have to gain access to the 2FA method too to gain access.

b) A bank requires customers to enter a password, and then confirm the login in an app on their phone. Explain what the second step protects against that the password alone does not. 
1. This is an example of separation of privilege: no single device or client should access a system.
2. This can for example protect against a replay attack.
3. Typically a 2FA provides a code that should be confirmed with the server. This code is then refreshed. This provides freshness since the code is available only for a single login.
4. Even if the attacker obtained the code, it'd be useless.

c) Explain why a system should give the same error message whether the username or the password was wrong. 
1. If different messages are shown, the attacker can infer if the username or the password was wrong.
2. This narrows down what the attacker needs to find out by a lot - making it easier to attack the system.

d) Explain what it means to store a password securely, and why the storage method matters even though users never see it.
1. Passwords should be encrypted such that an attacker cannot read them should they get access.
2. Also, passwords may not look the same even though the raw text is the same. Common passwords would be obvious and easy to guess.
3. Therefore the passwords should be salted before storage

#  Access control and privilege

a) Explain the difference between an access control list and a capability, in terms of where the access rights are stored. 
1. The ACL, the object (for which a principal wants to gain access) controls access and stores the rights. 
2. For capabilities, principals stores rights which are then checked by the object.

b) Explain what it means to revoke access, and explain why revocation is harder with capabilities than with access control lists. 
1. A principal can have its access to an object revoked. This should be instantaneous such that access isn't allowed after revokation.
2. Since the principal owns the rights list, it can be hard to revoke, since you'd have to update it on behalf of the subject.

c) A program needs to write to one specific system file, and is therefore given full administrator rights. Name the design principle being violated, and describe what an attacker gains if the program contains a bug. 
1. The principal of least privilege is violated
2. If the program contains a bug, an attacker might be able to act as an administrator and execute malicious code.

d) Explain how auditing contributes to security.
1. Auditing provides transparency and responsibility to actions performed on the system.
2. An attacker may want to avoid being logged and will then need to circumvent the logging system in order to attack. 

#  Attacks and defenses in software

a) Explain what it means that an attack “treats data as code”, and give two different examples of attacks that are enabled by treating data as code. 
1. When a system needs to process user input (like usernames), systems may see the input as code and run it. Attackers can thus execute code by providing it as data, and then have the program run the code.
2. SQL- and script injections do this

b) Explain why a memory-safe programming language removes a whole class of vulnerabilities, and name one reason a company might still choose a language that is not memory-safe. 
1. Memory vulnerabilities provide attackers with tools that allow them to execute arbitrary code. Memory safe languages remove these vulnerables.
2. Handing memory handling over to the programming language can free up development time for companies. Some companies might however use an unsafe language to exactly manage memory and security in specific places (assurance).

c) Explain the difference between detecting an attack and preventing an attack, and give one example of each from the defenses against buffer overflows.
- Preventing an attack is an active countermeasure - like putting a lock on your door.
- Detection is noticing an active attack. Detection *can* also function as a countermeasure - like setting up cameras.

- Detection method: Use static code analysis tools or runtime monitoring to identify memory access beyond buffer boundaries.
- Prevention method: Perform bounds checking and use memory-safe programming languages (e.g., Rust) to prevent writing beyond allocated memory.

# A parcel locker system
## Problem description. 
A delivery company installs parcel lockers outside supermarkets. Each locker is a cabinet with many compartments, and each compartment holds one parcel. The system works as follows:
	• When a parcel is placed in a compartment, **the recipient receives a text message containing a six-digit code**.
	• The locker stores the codes for all the parcels currently inside the locker, so that a code can be checked without contacting the server.
	• The recipient types a code on a keypad on the locker. If the code matches a
	parcel in the locker, the compartment holding that parcel opens.
	• **A code remains valid until the parcel is collected.**
	• Delivery drivers open the compartments with a master code, which is the same
	for all lockers in a city and is changed **once a year**.
	• The locker keeps a log of every opening, and stores the log on a server the
	delivery company operates.
	• If the locker loses its network connection, it continues to accept the codes it
	already holds, and reports the openings when the connection returns.
	The delivery company advertises the lockers as “more secure than leaving the parcel
	at the door”.
## Questions.

a) Using the elements of security, state the policy the parcel locker system should
uphold. Cover confidentiality, integrity and availability, and explain what each
property means for the parcel locker system specifically. [[Design principles#Elements of security|Elements of security]]
- Policy (What should be protected):
	- Only recipients and the deliverer should be able to access the package in the compartment that is sent to the recipient
	- deliverers should be able to access all compartments
	- Each access of a compartment should log time, place and principal
- Confidentiality for this system means:
	- No one should be able to see who owns the package in a compartment
- integrity 
	- No one other than the deliverer should access the package in transit.
- availability
	- The package should be easy to retrieve for the recipient 


b) State the threat model. Describe at least two different attackers, and for each
attacker explain what capabilities you are assuming and which capabilities you
are excluding.
- The malicious package pirate wanting to steal one or more packages. I assume that this person does not have technical capabilities.

c) The parcel locker system contains at least one weakness. Identify one weakness,
and explain what consequences it can lead to. Also describe an attacker that can
exploit the weakness.
- Updating the master code once a year is not secure. Drivers may get fired or have their code stolen. A year is simply too long: the master code should be updated at least daily since it is a single point of failure. Attackers may have access to all compartments in a city if they obtain the master code. The master code should also be different for each parcel locker system. This would abide the principle of least mechanism.
- An attacker may also read the information sent on text and thereby gain access to one compartment

d) Evaluate the delivery company’s claim that the lockers are more secure than
leaving the parcel at the door. Explain what trust the recipient placed in leaving
the parcel at the door, and where that trust has moved in the locker system. Use
at least two of Saltzer and Schroeder’s design principles in your answer.

# A school’s computer system 
## Problem description
A secondary school has 900 students and 80 teachers. The school’s computer system is used for grades, attendance, lesson plans and internal messages. The current setup is as follows:
	• ==🔴Every teacher has their own account, which can read and change the grades of every student in the school==. 
	• There is also a ==🔴shared account used on the staff room computer, which any teacher can log in with.== The shared account has the same rights as a teacher’s own account. 
	• The head teacher has an account that can do everything a teacher account can do, and that can also create and delete accounts. 
	• ==🟢Students have their own accounts, and can read their own grades but cannot change them. ==
	• When a teacher leaves the school, ==🔴the office is supposed to delete their account, but there is no procedure for checking that the deletion happened.== 
	• The system records which account changed a grade, and when. ==🔴A parent has complained that their child’s grade was changed without explanation, and the school cannot determine who changed it.== 

## Questions. 

a) Formulate an access control policy for the school’s grade records: 
	who should be able to read grades, who should be able to change them, and what the school should be able to establish afterwards about a change. 
	State the policy separately from any mechanism. 

b) State the threat model for the school’s computer system. Include attackers inside the school, and explain what each attacker’s goal would be. 
- Students: students might want to change their grades in order to obtain a higher grade.
- External hackers might want to gain access to the school in order to retrieve personal information.

c) Explain why the school cannot determine who changed the grade, even though the system keeps a record of every change. Name the design principles the current setup violates, and explain how each violation contributes to the problem. 
- This might be caused by the shared account since it is not tied to a specific principal. This violates:
	- Least common mechanism since there are lots of common mechanism between teachers (and other actors that know the credentials). This also breaks the "Authenticating" part of the gold standard by not identifying the right person.
	- Least privilege. Not every teacher may need the rights of the shared account. This breaks the "Authorizing" part of the gold standard by not necessarily granting the right privileges to the right people.	
	- Separation of privilege ?
- Auditing clearly breaks when the Authorizing and Authenticating doesn't work properly.

d) Propose a revised access control arrangement for the school. Explain which mechanism you would use, how the mechanism upholds the policy from part a), and what the revised setup costs the school in administration and in convenience for teachers. 
- The shared teacher account should be removed or at least all access should be revoked. This would cost the school nothing.
- The teachers would have to login to their own accounts each time.

# A fitness tracking service 
## Problem description
A company runs a fitness tracking service. Users wear a device that records their location and heart rate, and can track different activities such as running and cycling. When a user starts an activity, the device records the route they take. All device data is uploaded and stored on the company’s servers. The service works as follows: • Users can choose to share their routes with friends, and the sharing setting is on by default. • The company publishes a public map showing where people exercise most often, built from all users’ routes. • Users can download their own data at any t