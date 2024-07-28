- If the properties accessors do not require any additional logic to be performed, then we can declare that property like so:
 
```csharp
public int Age { get; set; }
```

This is equivalent to:

```csharp
private int _age;
public int Age { get { return this._age; } set { this._age = value; } }
```