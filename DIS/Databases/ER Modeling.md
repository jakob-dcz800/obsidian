# ER Modeling

>Entity / Relation modeling

# Arrows

## Many-one
![[Pasted image 20260618144840.png]]
![[Pasted image 20260421125952.png]]

## Referential Integrity
![[Pasted image 20260618145017.png]]

# Entities
## Weak Entities
A weak entity can only be identified uniquely by considering the **primary key of another** (owner) **entity** (possibly in combination with a key attribute of the weak entity)

![[Pasted image 20260618145558.png]]
Owner entity set and weak entity set must participate in a one-to-many relationship set (one owner, many weak entities).

## ISA Hierarchies

Similar to [[Object oriented analysis and design#Domain Modelling|object-oriented modeling]]
E/R entities have representatives in all subclasses to which they belong
Rule: if entity e is represented in a subclass, then e is represented in the superclass. 
(and recursively up the tree)

![[Pasted image 20260618145905.png]]

# Examples

## Example 1

![[Pasted image 20260423144100.png]]
