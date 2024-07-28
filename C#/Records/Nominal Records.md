- Created using the [[Object Initializer]] synatax
- Using nominal creation, then, _we can say that records are not immutable by default_.

```csharp
public record Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
}
```

```csharp
static void Main(string[] args)
{
    var person = new Person
    {
        FirstName = "Dave",
        LastName = "Brock"
    };
    
    // I'm Dave Brock
    Console.WriteLine($"I'm {person.FirstName} {person.LastName}"); 
    // We can overwrite the property
    person.FirstName = "Bob";
    // I'm Bob Brock
    Console.WriteLine($"I'm {person.FirstName} {person.LastName}"); 
}
```

- As stated, the properties are not immutable *by default*
- We can make the properties immutable by using the [[init keyword]]:

```csharp
public record Person
{
    public string FirstName { get; init; }
    public string LastName { get; init; }
}
```

- This approach may be required if we want to avail of the [[Equality Comparisons]] aspects of a Record but dont want every property to be immutable.