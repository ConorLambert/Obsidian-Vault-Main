### Overview
- Called by the garbage collector when the object is no longer in use
- Can be overwritten to perform cleanup of unmanaged resources used by the object.
- The programmer has no control over when the destructor is called because this is determined by the garbage collector.

```C#
class Car
{
    ~Car()  // destructor
    {
        // cleanup statements...
    }
}
```

### Destructors and Finalize()
- Destructors implicitly call the [[Finalize()]] method on the base class of the object.
- Even when we override the destructor, Finalize() will still be called.
- More info [here](https://stackoverflow.com/a/13988346/17385921)