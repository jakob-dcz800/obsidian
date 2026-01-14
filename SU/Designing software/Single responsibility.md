---
tags:
  - Design
  - Pattern
  - Software-development
---
## Single responsibility

SRP
“There should never be more than one reason for a class to change.”

Every class, function, variable should define a single responsibility, and that responsibility should be entirely encapsulated by the context.

It is important to keep a class focused on a single concern is that it makes the class more robust

Each responsibility should be a separate class, because each responsibility is an axis of change. 
A class should have one, and only one, reason to change. 
If a change to the business rules causes a class to change, then a change to the database schema, GUI, report format, or any other segment of the system should not force that class to change.