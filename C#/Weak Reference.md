[Source](https://learning.oreilly.com/library/view/c-in-a/0596001819/re175.html)

### Overview
- The garbage collector cannot collect an object in use by an application while the application's code can reach that object. 
- In this case, the application is said to have a **strong reference** to the object.
- A weak reference permits the garbage collector to collect the object while still allowing the application to access the object. 
- A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist. 
- When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected. However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.
- To create a weakly referenced object, pass the name of the object to the [[C#/API/WeakReference/0. Explained|WeakReference]] constructor.

### Use Cases
- Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.
- Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user. If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.
- When the user switches away to another part of the application, you can use the WeakReference class to create a weak reference to the tree and destroy all strong references. When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.