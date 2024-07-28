The code to declare an immutable [[! What is a Property|property]] in a [[! What is a class?|class]]:
  
```csharp
public string Name { get; init; }
```

_init_ properties can be set only when the object is initialized, but they cannot be changed later.
In this way, it is possible to have an immutable model.