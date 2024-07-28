It is sometimes necessary to compare two values for equality. In some cases, you are testing for _value equality_, also known as _equivalence_, which means that the values that are contained by the two variables are equal. In other cases, you have to determine whether two variables refer to the same underlying object in memory. This type of equality is called _reference equality_, or _identity_.

## Reference Equality
- Two object references refer to the same underlying object.
- Use the [ReferenceEquals](https://learn.microsoft.com/en-us/dotnet/api/system.object.referenceequals) method to determine whether two references refer to the same object.

## Value Equality
- Two objects contain the same value or values. 
- This can be done using the == operator
- For the following types, the the == operator can be used:
	- primitive types (`int`, `bool`) 
	- [[! What is a Record|Records]], 
	- Strings
- For [[! What is a class?|classes]] and [[! What is a Struct|structs]] however, extra functionality needs to be added in order to make Value Equality work. Please see [How to define value equality for a type](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type)