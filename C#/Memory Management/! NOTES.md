#### YouTube Video
- https://www.youtube.com/watch?v=aylUPfOVM90

------------------------------------------------------------------------
#### Stack and Heap
- Default sizes
	- The default size for 32 bit is 1 MB each
	- The default size for 64 bit is 4 MB each
- This Stack size is fixed
	- Why sometimes you get a Stack Overflow error
- The Heap size can grow and shrink dynamically based on the program’s memory requirements.
- Stack uses LIFO (Last-In-First-Out) principle
- The stack and heap both share the same address space.
	- The stack is located in the high address space. Items are added to the stack moving downwards going from high address space to low address space.
- Even though the stack and heap take up space towards each other the operating system will make sure that they don’t consume the same address space.
![Stack vs Heap](https://cdn.hashnode.com/res/hashnode/image/upload/v1669733320827/N9bq2ARxU.gif)

#### Value Types vs Reference Types
- Value Types that are local variables are always allocated on the stack
- However, Value Types that are members of an object are allocated inline
	- If the enclosing object is allocated on the Stack (e.g. struct) then the value type member will be allocated on the Stack
	- If the enclosing object is allocated on the Heap (e.g. class) then the value type member will be allocated on the Heap
- Reference Types are always added to the Heap
	- The reference/pointer to the Reference Type is added to the stack

#### `struct` Allocation
- The `struct` itself is allocated on the stack like any other value types.
- But if a member of a struct is a reference type, then it behaves accordingly 
	- i.e. That member is allocated on the heap and referenced from the stack (like any other reference type):

![[Pasted image 20230916113230.png]]

#### `class` Allocation
- The `struct` itself is allocated on the stack like any other value types.
- But if a member of the `struct` is a Reference Type, then it behaves accordingly :
	- That member is allocated on the heap and referenced from the stack:

![[Pasted image 20230916113857.png]]

#### Location and Contiguous Memory
- Objects themselves are stored in contiguous memory.
	- Each member of that object is stored in memory one after the other
- Any member which is a Value Type has its value stored inside this contiguous memory location.
- Any member that is a Reference Type has its reference/pointer stored inside this contiguous memory location but it's value is stored in a random location.
	- This random location can be on either the Stack or the Heap depending on where its related object is stored.

#### Arrays (Special Case for Value Types) 
- Arrays are Reference Types thus they are stored on the Heap and referenced from the Stack.
- ==Arrays are one of the special cases when the Value Type of an array is not allocated on the Stack but rather its allocated *inline* on the Heap.==
	- An array of value types will store the values on the Heap in a contiguous fashion:

![[Pasted image 20230916120422.png]]

- Likewise, an array of Reference Types will store the references/pointers *inline* on the Heap in a contiguous fashion but the objects they reference will be stored in random locations on the Heap:

![[Pasted image 20230916115807.png]]

#### Stack Frame
- Each method gets its own stack frame on the **Stack**
- The stack frame holds information about the parameters received, the caller function return address, and its internal variables.
- Each thread gets its own stack
	- If multiple threads call the same method `DoSomething()` then they each get their own stack frame.
- When we call a method, the allocations for that methods stack frame are done in this order:
	1. The parameters
	2. The return address of the caller method
		- The return address is necessary so the called method knows which address it should return both results and execution when its statements are finished.
	3. Then the local variables.
- Deallocation then works in the opposite order
	- Important to note that the calling method is responsible for deallocating the parameters of the method it has called.

#### Allocation Performance
- Allocation is actually fairly cheap in .NET. 
	- *".NET has faster memory allocation then in C++"* - Shiv Kumar
- The performance hit comes at the garbage collection stage.
- The more objects you create, the bigger performance hit you are going to take.
- Allocation/deallocation are faster on the Stack then Heap
	- The Stack can wipe out its allocated memory in one operation
		- It just references the address before the method in question was call
	- ==The Heap is where the garbage collection is happening==

#### Primitive Types
- These are types that .NET has a primitive understanding of:
	- .NET has a special relationship with these types
	- .NET has an intrinsic knowledge off

#### Deterministic Allocation vs Non-Deterministic
- Memory on the Stack is deallocated in a **deterministic** fashion:
	- We know the exact moment the memory will be freed.
- Memory on the Heap is deallocated in a **non-deterministic** fashion:
	- We don’t know the exact moment when this data is removed or even when they lose their context and are no longer needed

#### Class Metadata
- When we compile our C# code, metadata for each of the classes in our code is created.
- Some of this metadata is related to the size in memory for a new instance to be created and stored.
- This size information is used by the Heap during allocation/deallocation.
