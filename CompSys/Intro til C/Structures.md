---
tags:
  - Datastructure
  - Programming
  - Computer
---
## Structures
Structures are an [[Aggregate data types|aggregate data type]]
These combine items that may have different [[CompSys/Intro til C/Types|base types]]

**Structures can be assigned.**

**Structures can not be compared with == or !=.**
### Simple structures to access fields by name

```c
struct birdStruct {
	char const* jay;
	char const* magpie;
	char const* raven;
	char const* chough;
};

struct birdStruct const aName = {
	.chough = "Henry",
	.raven = "Lissy",
	.magpie = "Frau",
	.jay = "Joe",
};
```

![[Pasted image 20250908125719.png]]

Please note that in this example, the individual members again only refer to the [[Strings]]. For example, the member `aName.magpie` refers to an entity "Frau" that is **located outside the box** and is not considered part of the struct itself.

### Typesetting

Forward-declare a struct within a typedef using the same identifier as the tag name

The typedef mechanism can also be used for types other than structures

**A typedef only creates an alias for a type but never a new type.**
