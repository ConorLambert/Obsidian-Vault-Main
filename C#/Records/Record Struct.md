### Overview
- You can define a `record struct` to create a record that is a [[value type]].

### Purpose of `record struct`
- It adds additional functionality at compile-time that can be useful when using a struct.
- Really good answer [here](https://stackoverflow.com/questions/74892321/what-is-the-purpose-of-a-record-struct)
	- Single Line definition
	- Overrides == and !=, whereas struct only has Equals by default.
	- More informative `ToString` default method 
	- Has performance benefits.

### Note On Positional Records
- ==Because it’s a struct you have to set the **readonly** keyword to make the `record struct` immutable:==
```csharp
public readonly record struct Product(string Name, int CategoryId);
```