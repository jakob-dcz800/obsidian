---
tags:
  - Pattern
  - Analysis
  - Programming
---
# Coupling

- **Content coupling** - Modules accessing the content of each others. 
- **Common coupling** - Modules mutating common variables with bigger scope (like global variables). 
- **Control coupling** - Modules controlling the logic of other ones. 
- **External coupling** - Modules exchanging information to one another using an external mean, like a file. 
- **Stamp coupling** - Modules exchanging elements, but the receiving end doesn’t act on all elements. For example, an array passed to a module which doesn’t use all the array’s elements.
- **Data coupling** - Modules exchanging elements, and the receiving end use all of them. • CBO (Coupling Between Object) - How much objects acts upon another. 
- **CBE (Coupling Between Element)** - More precise variation of the CBO. It considers two (or more) elements coupled if there is any dependency between them, like access, or modification of implementation details to one another. 
- **CTM (Coupling Through Message passing)** - Measures the number of messages sent by a considered class to the other classes in the system. 
- **IC (Inheritance Coupling)** - Calculate the coupling due to inheritance. I’ve already written about coupling and inheritance in another article.

Semantic Coupling
- **CCM** - Conceptual Coupling Between Methods. 
- **CCMC** - Conceptual Coupling Between Method and Class. 
- **CCBC** - Conceptual Coupling Between two Classes, also called CSBC (Conceptual Similarity Between two Classes).