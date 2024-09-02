[Source](https://exercism.org/tracks/csharp/exercises/developer-privileges)

# Lessons Learned
- Having only a `get` accessor method is sufficient to initialise the property inside the class where the property is declared: 
	- `public string Name { get; } = "John"`. 
- The `init` keyword is used for situations of assigning a value during object construction:
	- `var john = new Person { Name = "John" };`
- Use the following shorthand syntax for the setting the key when initializing a dictionary:
```c#
var example = new Dictionary<string, Identity>
{
	["Bertrand"] = new Identity
	{
		Email="bert@ex.ism", 
		...SOME CODE HERE..
	},
	["Anders"] = new Identity 
	{
		Email="anders@ex.ism", 
		...SOME CODE HERE..
	}
};
```

