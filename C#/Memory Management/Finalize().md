### Overview
- The Finalize method is used for releasing unmanaged resources as part of the [[Garbage Collection#Garbage Collection Process|garbage collection process]]. 
- It's invoked by the garbage collector before reclaiming memory occupied by an object. 
- The [[Destructor#Destructors and Finalize()|destructor]] implicitly calls Finalize() on the base class of the object. 
- It is very rare that you need to write a finalizer.

### Finalize() vs Dispose()
- While Finalize provides a safety net for resource cleanup, it's less predictable and efficient compared to [[Dispose()]].