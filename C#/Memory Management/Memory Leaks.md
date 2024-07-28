Even though C# is a managed language, memory leaks can still occur.
This can come in the form of:
	1. Allocating memory longer then is actually needed:
		- Garbage collector will eventually collect it
	2. The garbage collector not being able to collect resources that are still referenced.

#### Event Handler Leak
- ???