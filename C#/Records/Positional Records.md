## Syntax
```C#
public record Person(string FirstName, string LastName);
```

## Immutable
- Records created using the `positional` style are immutable by default
- However, declaring a `struct` using positional notation does not make it immutable as explained [[Record Struct#Note On Positional Records|here]].