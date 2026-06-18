# Relational Calculus

## Language

![[Pasted image 20260617101326.png]]

![[Pasted image 20260617101422.png]]

# Examples


## Example 1
Choose ssn, name, lot from Employees where the name is John:
`Employees(ssn,name,lot) ∧ name ≈ “John”`

Choose ssn, lot where name is John
`Employees(ssn,“John”,lot)`

Choose ssn from employees named John
`∃lot. Employees(ssn,“John”,lot)`

