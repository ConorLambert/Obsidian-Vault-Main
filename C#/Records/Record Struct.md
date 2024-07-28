By default, a record is a [[reference type]]. 
You can define a `record struct` to create a record that is a [[value type]].

### Note On Positional Records
- Positional records on a struct doesn’t make the record immutable as a record class.
- ==Because it’s a struct you have to set the **readonly** keyword to make the record struct immutable:==

```csharp
public readonly record struct Product(string Name, int CategoryId);
```