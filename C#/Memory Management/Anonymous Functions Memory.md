#### Overview
- The [[captured variables]] used by an anonymous function are stored and accessed via fields of an object that is stored on the Heap.
#### Explained
- The compiler generates a class which holds the [[captured variables]].
- It creates an instance of this class inside the containing method and copies the required local variables into fields on that object.
- The code inside the anonymous function then uses the fields on that class. 
- *Some variables that appear to be local variables (i.e. live on the stack) of anonymous functions are in fact fields of an object living on the heap.*
- This also applies to local functions and delegates.