---
tags:
  - Programming
  - Fundemental
---
# Interface segregation principle

ISP
“Many client specific interfaces are better than one general purpose interface”
Important: **“Clients should not be forced to depend upon interfaces that they do not use.”**

Big interface = bad

• It states that no client should be forced to depend on methods it does not use 
• ISP splits interfaces which are very large into smaller and more specific ones so that clients will only have to know about the methods that are of interest to them

Many specific interfaces are better than one general
Must-haves:
	• Design by contract (DbC) / Design to Interfaces
	• [[Test-Driven Development]] (TDD)