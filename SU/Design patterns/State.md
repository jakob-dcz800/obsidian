---
tags:
  - Pattern
  - Software-development
---
## State pattern

```typescript
const [state, setState] = useState<>();
```

allows object to alter its behaviour when its internal state changes.
Game has states: show title screen, options, playing, pausing, ending

**State pattern is not strategy pattern**

![[Pasted image 20250310104735.png]]

Context 
	• defines the interface of interest to clients 
	• maintains instance of a ConcreteState subclass that defines the current state. 
State 
	• defines interface for encapsulating behavior associated with a particular state of Context. 
Concrete State 
	• each subclass implements behavior associated with state of Context

**Some games have state as a tree.**

It encapsulates varying behaviour for same object, based on its internal state. This can be cleaner way for object to change its behaviour at runtime without resorting to conditional statements and thus improve maintainability

## Difference between state and strategy

Strategy pattern: application chooses strategy **externally**  
State pattern: state is determined by state machine **internally**

| Feature             | State Pattern                                        | Strategy Pattern                          |
| ------------------- | ---------------------------------------------------- | ----------------------------------------- |
| Purpose             | Change behavior based on internal state              | Choose an algorithm at runtime            |
| Focus               | Object state transitions                             | Interchangeable algorithms                |
| Control of behavior | Controlled internally (by the context or state)      | Set externally (by the client)            |
| Behavior change     | Often automatic, due to state change                 | Manual, client sets the strategy          |
| Example             | TCP connection states (Connected, Closed, Listening) | Sorting strategies (QuickSort, MergeSort) |