---
	tags: singleton, design, pattern
---

### Explained
- ???


### Singleton vs Static
- Static classes cannot be inherited whereas Singleton classes can.


### Use Cases
- ???


### Code Example
``` csharp
public class Singleton
{
    private static Singleton _instance;

    private Singleton() { }

    public static Singleton Instance
    {
        get
        {
            if (_instance == null)
            {
                _instance = new Singleton();
            }
            return _instance;
        }
    }
}
```