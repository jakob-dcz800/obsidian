# Open/closed principle

OCP
"Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification”

Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification that is, such an entity can allow its behavior to be extended without modifying its source code 

This is especially valuable in a production environment, where changes to source code may necessitate code reviews, unit tests, and other such procedures to qualify it for use in a product.

## Polymorphic Open/Closed Principle

All member variables should be private
Global variables should be avoided
## Meyer's Open/Closed Principle

Implementation of a class should only be modified to correct errors. 
Changes or new features require that a different class be created (Interfaces)