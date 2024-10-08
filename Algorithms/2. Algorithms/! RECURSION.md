### Overview
- Recursion is when a function calls itself.

### Two Parts
- When you write a recursive function, you have to tell it when to stop recursing. 
- That’s why every recursive function has two parts: 
	- The *recursive* case. 
		- When the function calls itself. 
	- The *base* case 
		- When the function doesn’t call itself.
		- Prevent the function from going into an infinite loop.

### Call Stack and Stack Frame
- When using recursion, you need to be aware of the *call stack* and *stack frame*:
	- A *stack frame* is a data structure that stores the local variables (including parameters) for a function
	- All function calls have their own *stack frame* and added onto the *call stack*.
	- The *call stack* is structured in a LIFO fashion based on the order of function calls.
	- During recursion, the *call stack* can get very large thus taking up a lot of memory which could lead to a stack overflow error.