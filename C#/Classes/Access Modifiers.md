---
	tags: public, protected-internal, protected, internal, private-protected, private, declared-accessibility, default
---

Access modifiers are used to control the visibility and accessibility of [[class members]] from other parts of the program.

==**private** is the default if no access modifier is specified==

![[Pasted image 20230508194535.png]]

-   [public](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/public): The type or member can be accessed by any other code in the same assembly or another assembly that references it. *The accessibility level of public members of a type is controlled by the accessibility level of the type itself*.
-   [private](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private): The type or member can be accessed only by code in the same `class` or `struct`.
-   [protected](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected): The type or member can be accessed only by code in the same `class`, or in a `class` that is derived from that `class`.
-   [internal](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/internal): The type or member can be accessed by any code in the same assembly, but not from another assembly. In other words, `internal` types or members can be accessed from code that is part of the same compilation.
-   [protected internal](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected-internal): The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived `class` in another assembly.
-   [private protected](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private-protected): The type or member can be accessed by types derived from the `class` that are declared within its containing assembly.

