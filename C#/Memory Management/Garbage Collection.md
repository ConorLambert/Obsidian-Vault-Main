[Source](https://learn.microsoft.com/en-us/dotnet/standard/garbage-collection/fundamentals#conditions-for-a-garbage-collection)
## Overview
- The garbage collector in C# is responsible for identifying and reclaiming memory occupied by objects that are no longer accessible or in use. 

## Thread Suspension
- Before a garbage collection starts, all managed threads are suspended except for the thread that triggered the garbage collection.

## Generations
###### Purpose
- To optimize the performance of the garbage collector, the managed heap is divided into three generations, 0, 1, and 2, so it can handle long-lived and short-lived objects separately.
- It's faster to compact the memory for a portion of the managed heap than for the entire managed heap.
###### Survival and Promotions
- Objects that survive collections are promoted and stored in higher generations.
- By promoting objects to higher generations, the garbage collector doesn't have to reexamine the same objects each time it performs a collection of generation 0.
###### Collection
- If an application attempts to create a new object when generation 0 is full, the garbage collector performs a collection to free address space for the object.
- A collection of generation 0 alone often reclaims enough memory to enable the application to continue creating new objects but if a collection of generation 0 doesn't reclaim enough memory for the application to create a new object, the garbage collector can perform a collection of generation 1 and then generation 2 (if generation 1 doesn't reclaim enough memory).
###### Generation 0
- Newly created objects are added here (excluding large objects)
- Temporary variables are an example
- Collection occurs most frequently in this generation
###### Generation 1
- Contains short-lived objects 
- Serves as a buffer between short-lived objects and long-lived objects.
- Objects that survive a collection on generation 0 are promoted here
###### Generation 2
- Contains long-lived objects
- Example is an object in a server application that contains static data that's live for the duration of the process.
###### Generation 3 (LOH)
- If a newly created object is a large object, they go on the [[(LOH) Large Objects Heap]], which is sometimes referred to as generation 3. 
- Collected as part of generation 2.
- No compacting phase takes place here due to performance issues.

## Garbage Collection Process
1. **Marking Phase:** 
	- The object graph is traversed starting from known root objects such as global variables or objects on the stack. 
	- It marks reachable objects and identifies those that are unreachable.
2. **Compacting Phase:**
	- Optional phase
	- Rearranges the memory, compacting live objects to reduce fragmentation. 
		- Compaction can enhance memory locality and, consequently, improve performance.
	- Objects are promoted to the next generation higher.
3. **Releasing Phase:** 
	- Memory occupied by unreachable objects is released, making it available for new allocations.

## Object Graph Traversal
- The **Marking Phase** of the collection process must commence the traversal starting from the *roots* which are the global variables or references contained in the frame of each Stack.
- ???

## What Triggers Garbage Collection ?
**Low Physical Memory**:
- When the application allocates memory for new objects, the garbage collector may be invoked to reclaim space for the new allocation.
**Generation Thresholds:**
- Each generation has a threshold, and when it is reached, a garbage collection cycle is initiated. 
- Generation 0 collections are more frequent, while higher-generation collections are less frequent but involve more objects.
**Explicit Invocation:**
- Developers can explicitly trigger garbage collection using `System.GC.Collect()`

## Unmanaged Resources ?
- Garbage collection can perform most memory management tasks automatically.
- However, if an object is wrapping an unmanaged resource such as a file handle, window handle or network connection, then we need to explicitly release the resource using the `IDisposable` interface because the garbage collector doesn't have specific knowledge about how to clean up the resource .