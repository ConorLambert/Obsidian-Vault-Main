---
	tags: object-initializers, compiler, parameterless, constructor, default, example
---

`Object Initializers` can initialize type objects in a declarative manner without explicitly invoking a constructor for the type.

### Compiler
- The compiler processes object initializers by first accessing the parameterless instance constructor and then processing the member initializations.

### Default Constructor Required
- If object initializers are used on classes that define only a custom constructor, then the default parameterless constructor must also be explicitly defined on the class.

### Example
```csharp
public class HowToObjectInitializers
{
    public static void Main()
    {
	    // Uses the default constructor
        StudentName student1 = new StudentName("Craig", "Playstead");
        // Uses the Object Initializer
        StudentName student4 = new StudentName
        {
            FirstName = "Craig",
            LastName = "Playstead",
            ID = 116
        };
        // Uses the Object Initializer
        StudentName student3 = new StudentName
        {
            ID = 183
        };
    }

    public class StudentName
    {
        // Required because we have defined a custom constructor
        public StudentName() { }

        // Custom constructor
        public StudentName(string first, string last)
        {
            FirstName = first;
            LastName = last;
        }

        // Properties.
        public string? FirstName { get; set; }
        public string? LastName { get; set; }
        public int ID { get; set; }
    }
}
```
