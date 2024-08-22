- A `with` expression produces a copy of its operand with the specified properties and fields modified. 
- A `with` expression allows for `non-destructive mutation`.
- Uses [[Object Initializer]] syntax to specify what members to modify and their new values:

```csharp
var p1 = new NamedPoint("A", 0, 0);
var p2 = p1 with { Name = "B", X = 5 };
```