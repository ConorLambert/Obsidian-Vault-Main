# Definitions
- Design an interface in such a way that you don't force clients to implement methods they don't need.

# Purpose
- Having a bulky interface will force classes to implement all the methods many of which they may not need. 
	- Generally occurs with the Repository pattern.

### Violations
- Large Interfaces
- NotImplementedException
- Code uses small subset of larger interface

# Implementation
### Follow other principles
- Cohesion and SRP
- LSP
### Split Interface
- Split a bulky interface into separate interfaces
- If the original interface is still needed, then just make that interface implement the split out interfaces.
- Example explained [here](https://youtu.be/kF7rQmSRlq0?t=270) with the Repository pattern problem.
### Adapter
- For large interfaces you have no control over.