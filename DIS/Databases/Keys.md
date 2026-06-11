# Keys

## Key
> {ssn} is a key for Employees.
## Superkey
> The set {ssn, name} is a superkey.
## Primary key

Primary key is in [[SQL]] denoted by `PRIMARY KEY` (e.g. `id`)

## Foreign keys
>[!DEFINITION]
>Set of fields in one relation that is used to “refer” to a tuple in another relation
>• Must correspond to **primary key** of the second relation 
>• Like a “logical pointer”.

If all foreign key constraints enforced, referential integrity is achieved, i.e., no dangling references. 
	• Not like HTML links!

### Enforcing Referential Integrity
What if a new `Works_In` tuple is added that references a non-existent employee? 
	(Example from [[ER Modeling#Example 1|here]])
	• Reject it!

What if an Employee tuple is deleted? 
	• Also delete all `Works_In` tuples that refer to it. 
	• Disallow deletion of Employee tuple that is referred to. 
	• Set `ssn` to some default value 
	• Set `ssn` in Works_In to null, denoting `unknown`
	• Similar if primary key of Employee tuple is updated