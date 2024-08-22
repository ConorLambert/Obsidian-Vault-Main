To enforce value comparison and other semantics, the compiler generates several methods for your record type (both for `record class` types and `record struct` types):

-   An override of [Object.Equals(Object)](https://learn.microsoft.com/en-us/dotnet/api/system.object.equals#system-object-equals(system-object)).
-   A virtual `Equals` method whose parameter is the record type.
-   An override of [Object.GetHashCode()](https://learn.microsoft.com/en-us/dotnet/api/system.object.gethashcode#system-object-gethashcode).
-   Methods for `operator ==` and `operator !=`.
-   Record types implement `System.IEquatable<T>`.

