# Integrity constraint

IC: condition that must be true for **any** instance of the database 
	• Domain constraints 
	• Key constraints 
	• Foreign key constraints (later)

ICs are based upon the semantics of the real-world enterprise that is being described in the [[database]] relations

We can check a database instance to see if an IC is violated, but we can **NEVER** infer that an IC is true by looking at an instance.
• An IC is a statement about all possible instances! 
• From example, we know name is not a key, but the assertion that sid is a key is given to us.

>Key and foreign key ICs are the most common; more general ICs supported too.