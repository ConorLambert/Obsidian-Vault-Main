## Explain the `ref` and `out` parameter modifiers and how they differ
- Both keywords are used to *pass an argument by reference*.
	- This means any changes made to this argument in the method will be reflected in that variable when the control returns to the calling method.
- `ref` requires the argument to be *initialized* first whilst `out` does not
- `ref` indicates that the parameter *may* be modified whilst `out` indicates that the parameter *must* be modified.
	- The compiler will throw an error if the `out` parameter is not assigned/re-assigned in the method.

## Explain when to use `ref` vs `out` keywords
==`out` is used a lot more then `ref`==
###### ref
- Large value types where the cost of copying the content in memory is expensive.
	- And this value type is not required to change in the method being called.
###### out
- Good for `TryX` methods such as `TryParse()` or some method that returns both a boolean and a value. Because we know the parameter will always be set (not always, check documentation) then we don't have to manually check against `null` later on in the code.
```C#
bool isValid = int.TryParse("100", out int result = 0);
```

## Explain the `in` parameter modifier 
- Used to state that the parameter passed *cannot* be modified by the method.

## Discuss the difference between `constants` and `readonly` variables and when to use each.
- Explained:
	- `constants` evaluated at compile time, `readonly` evaluated at run time.
	- `constants` can only hold value types and strings, `readonly` can additionally hold reference types.
	- `readonly` variables can only be initialised at the time of declaration or in a constructor.
- Use Cases:
	- `constants` should be used when the value is not changing during run time
	- `readonly` variables are used mostly when their actual value is *unknown* before run time.

## Differentiate between `public` and `static`
- `private static` (or `static`) is accessible only to enclosing class.
- `public static` is accessible globally.
- `public` declares an instance-based member that is accessible to external callers (those with access to the type itself).

## What is the purpose of the `using` statement, and what interface is used to support it ?
- When using an `IDisposable` object, declare and instantiate that object in a `using` statement.
- The `using` statement calls the `Dispose` method on the object in the correct way.

## What is the `yield` keyword used for and what interface is it commonly used in conjunction with ?
- `yield` is used for *iterators* which are functions that return `IEnumerable` objects.
- Iterators are generally used by `foreach` loops to iterate over an `IEnumerable` collection.
- It creates a state machine "under the covers" that remembers where you were on each additional cycle of the function and picks up from there.
- Without yield, all the items are returned at once. With yield, items are returned one by one.
```c#
IEnumerable<int> ProduceEvenNumbers(int upto)
{
    for (int i = 0; i <= upto; i += 2)
    {
        yield return i;
    }
}

foreach (int i in ProduceEvenNumbers(9))
{
    Console.Write(i);
    Console.Write(" ");
}
```

## What are `sealed` classes in C# ?
- When a class is marked with the `sealed` keyword, it prevents another class from inheriting it.

## Why use the `internal` access modifier ?
- This situation where you have multiple projects in a single solution (which is incredibly common in enterprise development).
- We want some class or class member to be accessible to only the project it's contained within.
- We can't use `public` because that will be seen by all projects.
- We can't use `private` because that would restrict the type to within the same class.
- This is where `internal` is used.

## Explain the different Access Modifiers
###### public
- Accessible to all classes.
###### private
- Accessible only within the same class.
###### protected
- Accessible only within the same class and classes that inherit from this class.
###### internal
- Accessible from any file within the same assembly but not from another assembly.
###### protected internal
- Accessible from any file within the same assembly and within a derived class in *another* assembly (just the derived class, not the whole assembly where the derived class resides). 
	- In the case of a separate assembly, the member can only be accessed through an instance of the derived class and not an instance of the base class.
	- See [here](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected-internal#example) for an example.
###### private protected
- Accessible by types of the same class (not the whole assembly) or derived classes *but only if the derived classes are within the same assembly as the base class*.
- If the derived class is part of a different assembly, then private protected members are not accessible.