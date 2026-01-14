---
tags:
  - Pattern
  - Programming
  - Software-development
---
# Iterator pattern

allows sequential access to the elements of a composite object ([[UML Basics#Relations|aggregate]], e.g. list or tree) without revealing its underlying structure.
Meant as **read** structure.
Programming e.g. next and prev methods in a list.

Examples: 
	• Sequential throughput through a list 
	• Sequential throughput through a binary tree 
	• Sequential throughput through a composite structure (n-ary tree with different types of nodes)

![[Pasted image 20250310105759.png]]

Iterator is an abstraction, where functionality is abstracted away from the data.

![[Pasted image 20250310105903.png]]

Abstraction of both sides, data and functionality.

![[Pasted image 20250310111541.png]]

• Advantages: 
	• The implementation of the data structure underlying the aggregate remains hidden. 
	• The aggregate objects can be exchanged without modifying the application, since the access via the iterator remains unchanged. 
• Disadvantages: 
	• Iterators require additional programming effort. 
	• Iterators may need to be informed of changes to the aggregate.

### Implementation

```csharp
interface IEnumberable { 
	IEnumerator GetEnumerator(); 
	// Returns an enumerator over a set of elements of type T. 
} 

interface IEnumerator { 
	public E Current; 
	// get current element in scope 
	public bool MoveNext(); 
	// move to next element 
	public void Reset(); 
	// Sets enumerator to initial position 
}
```

![[Pasted image 20250310112556.png]]

