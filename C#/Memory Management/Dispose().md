### Overview
- The `IDisposable` interface declares the `Dispose()` method.
- The `Dispose` method is used to release unmanaged resources *explicitly*. 
- It's typically implemented in classes that use unmanaged resources such as file handles, database connections, or network sockets. 
- By calling Dispose, developers can release these resources immediately, ensuring timely cleanup and preventing resource leaks.

### Dispose vs Finalize()
- [[Finalize()]] can also be used to release unmanaged resources but it is called by the [[Garbage Collection|garbage collector]].
- The problem here is that GC is non-deterministic meaning we don't know when or if it's going to be called.
- Therefore, the Dispose() method makes it possible to support deterministic cleanup which allows the caller to release any resources *sooner*.