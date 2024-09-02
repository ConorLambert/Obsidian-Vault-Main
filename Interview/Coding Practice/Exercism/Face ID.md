[Source](https://exercism.org/tracks/csharp/exercises/faceid-2)

# Lessons Learned
- Should use a `HashSet` instead of a `List` for registering identities.
	- Requirement that Identities are unique
	- Requirement that a true is returned when identity added
		- `HashSet.Add` returns true if the object was added, `false` if object already exists.
- Use shorthand syntax for initializing new type
	- `private HashSet<Identity> _registeredIdentities = new();`
- Don't need to specify the `override` keyword for implementing a method from an interface
- Use `HashCode.Combine` to combine hash code of fields.
- Overriding the `Equals` method does *not* override the "== ". 
	- "== " still refers to the *references* of the object operands unless the == has been overridden.
- When overriding `Equals` and comparing the members of the object, make sure to only use "== " on primitive types and call the `Equals` method on nested complex objects. 
- For object reference comparison, use `ReferenceEquals` instead of == because == can be overridden.
	- Safer to call for `null`. 
		- `Equals` can't be called on a `null` object 
	- Cannot be overridden like `Equals` or ==
	- More info [here](https://stackoverflow.com/questions/3869601/c-sharp-equals-referenceequals-and-operator)