## Syntax
- Created using the following syntax.

```csharp
public record Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
}
```

## Not Immutable
- ==Using nominal creation, the records are *not* immutable by default.==

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

##  `init` keyword
- We can make the properties immutable by using the [[C#/Properties/init keyword]]:

```csharp
public record Person
{
    public string FirstName { get; init; }
    public string LastName { get; init; }
}
```

## Use Cases
- This approach may be required if we want to avail of the [[Equality Comparisons]] aspects of a Record but don't want every property to be immutable.