---
tags:
  - Software-development
---

# UML Terminology

**Unified Modelling Language** is a standard for modelling [[Terminology#Object-oriented programming|object-oriented]] software. It is a general-purpose visual modelling language that is intended to provide a standard way to visualize the design of a system.

First, a bit of terminology to help understand *why* and how we model.
## Modelling lingo

Why model software? A single programmer cannot manage this amount of code in its entirety. Code is not easily understandable by developers who did not write it. We need simpler representations for complex systems and modelling is a way to handle complexity.

- **System** can be anything. Consists of interconnected components and has a clearly defined [[Terminology#Interface|interface]] exposed to it's environment.  The system designer makes a clear distinction between what is inside the system and what is left out. For instance a plane may be considered as a system by some designers, while others will focus on the wing or the motor

- **Abstractions** are simplifications because they ignore irrelevant details and they only represent the relevant details. Abstractions classify [[#Terminology Concepts and Phenomena|phenomena]] into concepts (e.g. Jakob into "person").

- **Model**: an abstraction describing a *subset* of a system. Modelling consists of building an abstraction of reality. What is relevant or irrelevant depends on the purpose of the model. Development of abstractions to answer specific questions about a set of phenomena while ignoring irrelevant details.

- **View**, depicts selected aspects of a model.

- **Notation** is a set of graphical or textual rules for depicting views. 

### Example

**System** Aircraft
**Models** Flight simulator, scale model
**Views** All blueprints, electrical wiring, fuel system
**Example Concept**: Type and Instance
- **Type**: An abstraction in the context of programming languages, e.g. *int*
- **Instance**: Member of a specific type, e.g. *1*
- The type of a variable represents all possible instances the variable can take

### Common problems
Common problems when designing **systems** are:
* Emerging properties (surprising result of interaction across components)
* Propagation of effects (due to dependencies across components)
* Incommensurate scaling (not all components scale alike)
* Trade-offs (balancing win-lose across components)

![[Pasted image 20250308113950.png]]
## Terminology: Concepts and Phenomena

**Concept**: An object in the world of a domain as you perceive it.
Example: The lecture you are attending
Example: My watch

**Phenomenon**: A description of the properties of related phenomena.
Example: Lectures on software engineering
Example: Watches with metallic bracelet  

The concept is a 3-tuple:
*Name* To distinguish it from other concepts
*Purpose* Properties that determine if a phenomenon is a member of a concept
*Members* The set of phenomena which are part of the concept

## Terminology: Application/Solution Domain

**Application Domain**: The environment in which the system is operating
**Solution Domain**: The available technologies to build the system